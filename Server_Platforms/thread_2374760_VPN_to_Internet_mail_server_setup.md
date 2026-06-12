---
title: "VPN to Internet mail server setup"
date: 2017-10-18
forum: Server Platforms
---

### Post by kandresen on 2017-10-18
For years I have been running an OpenVPN solution where all computers computers connect to my office VPN server. Externally I have a VPS server running my website and mail server. I have been ok with this setup but IMAP on the VPS server is somewhat slow and I would like to move it locally. I do however not want to expose the local server to the Internet. Postfix do allow many interesting options such as "smarthost" and "satellite", however, I don't think any of these are entirely what I am looking for, I might be wrong(?):

1) Allowing the external VPS servers mail server to receive and send e-mails to and from other mail servers, but deny mail-client access using IMAP/POP/Submission 
2) Setup the local server to only allow Subission/IMAP connections over VPN, relaying all outgoing mail to the VPS server and polling all new mail. 
3) The VPS postfix server should have a small storage for storing incoming mail in the event the internal server is down, but may delete mails verified to have been received by the internal IMAP server. 
4) The mailserver on VPN will do spam and malware scanning since this is where incoming and outgoing mails are stored in IMAP. 

Since all local e-mail go through OpenVPN, I kind of consider if I really still need to use STARTSSL. 

What is the best way for accomplishing such as setup?

---

### Post by SeijiSensei on 2017-10-19
I'll start by sketching out my setup which has some similarities to yours. I have two Linode VMs.  One accepts all inbound mail and forwards it over a [static]("http://openvpn.net/static.html") OpenVPN tunnel to the second VM for scanning with [MailScanner]("https://www.mailscanner.info/").  Mail destined for my personal use is then routed over another tunnel back to a server in my office.  Clients' traffic is delivered to local mailboxes on the second server.  This server handles all outbound SMTP transactions as well.  

To read their mail people connect to the first VM which forwards the connection back to port 143 on the second VM over a tunnel.

If on the unlikely chance that the second VM is down, mail queues up on the first VM in the directory /var/spool/mqueue until it can be delivered.  This is the standard practice for SMTP.  You don't need to do any configuration to make that happen.  The same process applies to primary and secondary MX servers.

I use xinetd on the front-end server to pass back IMAP connections.  The configuration file in /etc/xinetd.d looks like this:

```

service imap
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        bind            = external.ip.of.host
        log_on_failure  += USERID
        redirect        = 10.1.1.1 143
        per_source      = 10
        rlimit_cpu      = 5
}

```
The server with the mailboxes and the Dovecot IMAP server is 10.1.1.1.  I use xinetd because of its traffic control features like per_source and rlimit_cpu.  You can also write an iptables rule to handle this:

```
sudo iptables -t nat -A PREROUTING -d external.ip.of.host --dport 143 -j DNAT --to-destination 10.1.1.1:143
```
You can add rate limiting features to this rule as well.  See "man iptables" for details.

---

### Post by kandresen on 2017-10-20
I am trying to understand your setup; Since you are saying one of the VM's receive all inbound mail, I assume that VM is a public accessible server. 
That VM forward the incoming mail to the second VM with MailScanner.  
If it result the mail was for you personally, that mail is redirected to a third server located in your office through VPN. 
Your clients, however, are reading their e-mails from the VM with MailScanner, which is also the same server which do SMTP. 
If the VM with mailscanner is unavailable, all mails are kept on the public accessible mail server until the one with MailScanner is available again. 
 
If this is correct, it does indeed look similar to what I think except that you actually allow your clients to login to imap from the public server too using port forward? 

Am I understanding your setup correctly?

---

### Post by SeijiSensei on 2017-10-20
Yes, that's pretty much it.  The public server handles all inbound requests either for deliveries via SMTP or message retrieval via IMAP.  All inbound mail gets forwarded to the second server for scanning and delivery, either to local mailboxes or my office server.  The scanning machine also handles all outbound SMTP and appears as the certified sender in the SPF records for all my domains.  If the scanning server is down, obviously people won't be able to retrieve their mail until it comes back up.  However the public server will simply queue up the mail if it cannot forward it to scanning server.  That's just the way SMTP works.  (My Linode servers have uptimes well above 99% so this isn't really an issue in practice.)

The public server has a list of domains that are blocked as spammers, and only accepts mail addressed to domains I support.  That avoids any "open relay" problems.  I use sendmail rather than Postfix so these rules are stored in /etc/mail/access. You can accomplish the same kind of filtering in Postfix with the "[smtpd_helo_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_helo_restrictions")" and "[smtpd_sender_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_sender_restrictions")" directives in /etc/postfix/main.cf along with "[smtpd_relay_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions") =  reject_unauth_destination".  I use the Perl-compatible regular expression ("[pcre]("http://www.postfix.org/pcre_table.5.html")") method to build these rulesets.

All these connections take place over static OpenVPN tunnels.  I've configured the scanning server to be a centralized router for the half-dozen tunnels I maintain.

---

### Post by kandresen on 2017-10-20
So if I simply use the "Satellite" server configuration on my public VPS server, it will in fact store all incoming e-mail if my internal mail server is down, and automatically redirect all incoming mail when my internal server is up again? 
The smtpd restrictions; helo, sender and relay, are about restricting incoming mail. 
That part is indeed how I want it to be in this case! 

You are saying outgoing mails are sent by the MailScanner server, without going through the public server - that part I think I want to do somewhat different since my IMAP server wont have a public IP. 

I would really like to thank you for informing me that I apparently do not need any special setup to make the public mail server "cache" incoming mail while my IMAP server is down! 
I also like your idea about simply using port forwarding between the servers too! It really gave some good ideas I am now testing.

---

### Post by SeijiSensei on 2017-10-20
That "satellite" configuration must be a Postfix thing.  

First, if you have a primary and secondary MX server in your DNS records, and if the primary is offline, the mail will be sent to the secondary.  It will queue the mail until the primary comes online again.  As I said, there isn't anything special about this arrangement.

In my case the public-facing server has a rule to relay all the mail it accepts to the scanning server over the VPN.  You could do the same with the [relayhost](http://www.postfix.org/postconf.5.html#relayhost) directive.

---

