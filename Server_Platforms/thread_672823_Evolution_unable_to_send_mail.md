---
title: "Evolution unable to send mail"
date: 2008-01-20
forum: Server Platforms
---

### Post by satimis on 2008-01-20
Hi folks,


Server: 
Ubuntu 7.04 server amd64
SquirrelMail 1.4.11

Workstation
Ubuntu 7.04 desktop
Evolution 2.10.1


IIRC before installed SM the workstation can send/receive mail on Evolution via the Server w/o problem.

SM is working w/o problem.  Just discovered Evolution can receive mails but can't send mails.  With the same password it can't authenticate to send mails, always complaining "Unable to authenticate to SMTP server.  Bad authentication response from server".  However the same password works to login SM.

Pls advise where to check and how to fix the problem.  TIA


B.R.
satimis

---

### Post by daengbo on 2008-01-20
Is Evolution retrieving mails using POP or IMAP? Is SMTP set to use SSL or TLS? What MTP do you have installed on the server? Exim or Postfix?

---

### Post by satimis on 2008-01-20
> **daengbo said:**
> Is Evolution retrieving mails using POP or IMAP? Is SMTP set to use SSL or TLS? What MTP do you have installed on the server? Exim or Postfix?
pop

Tried SSL, TLS and No encrytion.  None of them can work.

postfix


Just discovered the blockage of outgoing traffic on port 25 during installing Evolution on Ubuntu 7.10 desktop amd64.  Then I reconnected another HD on the same box which runs Ubuntu 7.04 desktop.  The Evolution on the latter OS ran perfect w/o problem before.  Now it can download mails on the server but can't send mails, always complaining "Unable to authenticate to SMTP server. Bad authentication response from server".


What I have done on the Mail Server were;

1) 
Installed SM, the webmail

2)
Configuring CentOS 5 (Guest OS) running on VMWare.  CentOS can browse Internet BUT Internet can't get into CenOS. 

I'm still trying to solve this problem.


B.R.
satimis

---

### Post by Seisen on 2008-01-20
Did you add the port number after your smtp server information in Evolution?

---

### Post by satimis on 2008-01-20
> **Seisen said:**
> Did you add the port number after your smtp server information in Evolution?
Sorry I don't follow.


I found if uncheck "server require authentical", Evolution can send mails to other users registered on the Mail Server".  But can't send mails to Internet with following warning;

RCPT TO <user1@abc.com> failed: <user1@abc.com>: Relay access denied


satimis

---

### Post by daengbo on 2008-01-21
Is your server set up for local-only delivery?

---

### Post by satimis on 2008-01-21
> **daengbo said:**
> Is your server set up for local-only delivery?
No, IIRC.  Previously it worked w/o problem.  I haven't run Evolution on workstation to send mails for sometimes since SquirrelMail running.  How to recheck it?  I'm running Postfix here.  TIA


satimis

---

### Post by MJN on 2008-01-21
What authentication methods have you configured Postfix to support? (post your config if you don't know)

Have you told Evolution to use the appropriate mechanism? (I've not used Evolution but many clients will offer to discover the support mechanisms to pre-fill the correct config).

Mathew

---

### Post by satimis on 2008-01-21
Hi Mathew,

> What authentication methods have you configured Postfix to support? (post your config if you don't know)


```

# Enable SMTP authentication support
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain
unknown_local_recipient_reject_code = 450
maps_rbl_domains = 
    bl.spamcop.net,
    xbl.spamhaus.org

```

$ cat /etc/postfix/main.cf```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.satimis.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = satimis.com
mydestination = mail.satimis.com, satimis.com, localhost.satimis.com, localhost.localdomain, localhost
relayhost =
#mynetworks = 127.0.0.0/8, 192.168.1.0/24
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
virtual_alias_maps = hash:/etc/postfix/virtual
# Specify your NAT/proxy EXTERNAL address here.
proxy_interfaces = 220.232.213.178
#proxy_interfaces = 1.2.3.4
#virtual_alias_domains = satimis.com satimis.changeip.net

# Enable SMTP authentication support
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain
unknown_local_recipient_reject_code = 450
maps_rbl_domains = 
    bl.spamcop.net,
    xbl.spamhaus.org

smtpd_recipient_restrictions =
     permit_mynetworks,
     permit_sasl_authenticated,
     reject_unauth_destination
     reject_invalid_hostname, 
     reject_non_fqdn_sender, 
     reject_non_fqdn_recipient, 
     reject_unknown_sender_domain, 
     reject_unknown_recipient_domain, 
     reject_unauth_pipelining, 
     reject_unauth_destination, 
     reject_maps_rbl, 

smtpd_client_restrictions = permit_mynetworks

```

> 
Have you told Evolution to use the appropriate mechanism? (I've not used Evolution but many clients will offer to discover the support mechanisms to pre-fill the correct config).

Which file I have to refer to?  Thanks.

I have to answer this question in another box, the Workstation


B.R.
satimis

---

### Post by MJN on 2008-01-22
> **satimis said:**
> ```

# Enable SMTP authentication support
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain

```

Okay, that looks fine. However, presumably you followed some form of HowTo - did that cover testing of the installation and did it pass? Does it pass now?

I've just tried to connect to your machine to see what methods are offered but it doesn't connect - do you have a problem?

Anyway, post the output of **telnet localhost 25** from your server.


> Which file I have to refer to?As mentioned I've never used Evolution but I'd be surprised if it was configured manually like that - more likely to be a GUI-based configuration but you'll have to find that one out for yourself.

Mathew

---

### Post by satimis on 2008-01-22
> **MJN said:**
> Okay, that looks fine. However, presumably you followed some form of HowTo - did that cover testing of the installation and did it pass? Does it pass now?`
It doesn't have problem at all.  Evolution worked fine before.  As I mentioned previously that after installing SquirrelMail I stopped running Evolution.  Just discovered this problem during setup Evolution on Ubuntu 7.10 desktop amd64.  This is a new installation.


> I've just tried to connect to your machine to see what methods are offered but it doesn't connect - do you have a problem?

Sorry, the Mail Server was turned off.  This box is for testing.  I just turned it on.  Please try again.  Thanks


> 
Anyway, post the output of **telnet localhost 25** from your server.

$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail.satimis.com ESMTP Postfix (Ubuntu)
ehlo satimis.com
250-mail.satimis.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.

```
No problem at all.


> 
As mentioned I've never used Evolution but I'd be surprised if it was configured manually like that - more likely to be a GUI-based configuration but you'll have to find that one out for yourself.
OK.  I'm now going to the workstation.


satimis

---

### Post by MJN on 2008-01-22
> **satimis said:**
> It doesn't have problem at all. Evolution worked fine before. As I mentioned previously that after installing SquirrelMail I stopped running Evolution. Just discovered this problem during setup Evolution on Ubuntu 7.10 desktop amd64.
 
Sorry, my mistake. I'd headed off down the path of assuming you thought it was a Postfix problem but reading back I see you didn't.
 
As mentioned I'm afraid I don't have any experience of Evolution so someone else will have to step in to help.
 
> ```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail.satimis.com ESMTP Postfix (Ubuntu)
ehlo satimis.com
250-mail.satimis.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.
```
 
I would advise you using the **smtpd_tls_auth_only=yes** directive in Postfix to only allow plaintext authentication once a TLS tunnel has been established otherwise your usernames/passwords could be sniffable between your clients and server. Note I'd only make this change once you have solved your current problem though - there's no point adding another layer of unnecessary complexity.
 
Mathew

---

### Post by satimis on 2008-01-22
Hi Mathew,


I'm now posting on Ubuntu 7.10 desktop amd64 (workstation)


On starting Evolution, it popup following window```

Enter Password for Personal

Please enter the IMAP password for sliums@192.168.0.10

[                          ]
[  ] Remember this password
				[Cancel][OK]

```

Why it needs IMAP password ?  I use POP to download mails on the server.


I satisfy it with the password for this user to login Ubuntu after booting up the PC.   However it popup again.  I have to satisfy it with the same password 2nd, 3rd time, etc. again and again.


Edit -> Preferences -> highlight "Personal [Default] imap -> Edit -> Sending Email

Server Type : SMTP
Server Configuration

Server: (tried) 
192.168.0.10 (Mail Server IP addr)
220.232.213.178 (public IP)
satimis.com
smtp.satimis.com
etc.


Security
Use Secure Connection [No encryption]

Having tried follows;
1)
uncheck "Server requires authentication"
2)
Authentication
Type:  PLAIN/Login

All failed


I'm now going back to the server.  Anything I have to try again on the server


Edit:

Disregarding whether I uncheck/check "Server requires authentication"

On sending mail it always popup```

Error while performing operation.

RCPT TO <rleekl@yahoo.com> failed:
<rleekl@yahoo.com>: Relay access denied

```

But I can send mail to any user on the Mail Server


satimis

---

### Post by MJN on 2008-01-22
As I keep saying, I've never used Evolution so I'm really of little use when it comes to any potential quirks of its configuration. Surely someone else reading this has?
 
Aside from Squirrelmail have you tried using any other client in order to narrow down the possibilities of where the fault(s) lie(s)?
 
Mathew

---

### Post by satimis on 2008-01-22
> **MJN said:**
> Aside from Squirrelmail have you tried using any other client in order to narrow down the possibilities of where the fault(s) lie(s)?

What other mail client?  I'll install it on the workstation to test this problem.

satimis

---

### Post by MJN on 2008-01-22
Any you like - kmail? (there must be a similar simple client in Gnome)

---

### Post by satimis on 2008-01-22
> **MJN said:**
> Any you like - kmail? (there must be a similar simple client in Gnome)
No I don't have Kdesktop installed


I found;

balsa - an email client for Gnome
cronosii - fast, light weight and functional Gnome e-mail client

Have you tried them before?


Edit:

Installation:-


$ sudo apt-get install cronosii```

[sudo] password for satimis:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cronosii: Depends: gdk-imlib11 but it is not going to be installed
            Depends: libgnome32 (>= 1.2.13-5) but it is not going to be installed
            Depends: libgnomeprint15 (>= 0.29-1) but it is not going to be installed
            Depends: libgnomesupport0 (>= 1.2.13-5) but it is not going to be installed
            Depends: libgnomeui32 (>= 1.4.2-3) but it is not going to be installed
E: Broken packages

```


$ sudo apt-get install balsa```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  balsa: Depends: libgpgme11 (>= 1.0.1) but it is not installable
E: Broken packages

```

I think I have to download the packages on their sites


satimis

---

### Post by MJN on 2008-01-22
I haven't, but then I don't use Gnome.
 
Go for 'balsa' - it sounds good.
 
Mathew

---

### Post by satimis on 2008-01-23
Hi Mathew,


After running Kmail to send mails I confirm that the problem concerned is solely on account of Evolution.  Kmail can send and receive mails on the Mail Server w/o problem.


On sending mails it does not require password.  If I need adding the option "server require authentication" which line/lines on main.cf (#9 posting) I have to change and how?  


Which Encrytion to be selected;
None
SSL
TLS
???


Which Authentication Method to be selected;
Login
Plain
Cram-MD5
Digest-MD5
NTLM
GSSAPI
???


B.R.
satimis

---

### Post by MJN on 2008-01-23
There should be a button in KMail's config page to detect the necessary security settings - see **Settings** > **Accounts** > **Sending** > **<outgoing account>** > **Modify** > **Settings** > **Security** > **Check what the server supports**.

Then, under the **General** tab, you need to tick the **Server requires authentication** box and fill in your details.

Remember that Postfix will trust a local client enough for it to send mail anywhere hence why you didn't need your password. Connect remotely however and it's a different story - you will need to authenticate.

Mathew

---

### Post by satimis on 2008-01-23
> **MJN said:**
> There should be a button in KMail's config page to detect the necessary security settings - see **Settings** > **Accounts** > **Sending** > **<outgoing account>** > **Modify** > **Settings** > **Security** > **Check what the server supports**.

Then, under the **General** tab, you need to tick the **Server requires authentication** box and fill in your details.
I did play around there w/o result.  It is the problem on Postfix.  Because it does not require authentication.


> 
Remember that Postfix will trust a local client enough for it to send mail anywhere hence why you didn't need your password. Connect remotely however and it's a different story - you will need to authenticate.

I just want to learn.  I also played around on main.cf.  Changing "smtp_sasl_auth_enable = no" to "yes" seems not the solution.

I won't use Kmail to send mail.  I'll run SquirrelMail instead.


satimis

---

### Post by MJN on 2008-01-23
> **satimis said:**
> I did play around there w/o result.  It is the problem on Postfix.  Because it does not require authentication.

In post #5 you said it did require authentication - by virtue of it saying 'relay access denied'. This shows that authentication was required.

However, as I mentioned, if you are localhost or a LAN client then authentication is not required because of the **permit mynetworks** setting under the **smtpd_recipient_restrictions** directive. To test this properly try connecting with a client _not on your LAN_ or try removing the 192.168.0.0/24 network from **mynetworks**, restarting Postfix, and trying again.

> I just want to learn.  I also played around on main.cf.  Changing "smtp_sasl_auth_enable = no" to "yes" seems not the solution.Correct. That setting effects your server authenticating with other servers (note the **smtp** bit - i.e. no 'd' hence it is referring to Postfix acting as the client as opposed to the server/daemon).

> I won't use Kmail to send mail.  I'll run SquirrelMail instead.If that suits your needs then go for it! I wouldn't necessarily give up though.

Mathew

---

### Post by satimis on 2008-01-25
> **MJN said:**
> In post #5 you said it did require authentication - by virtue of it saying 'relay access denied'. This shows that authentication was required.

However, as I mentioned, if you are localhost or a LAN client then authentication is not required because of the **permit mynetworks** setting under the **smtpd_recipient_restrictions** directive. To test this properly try connecting with a client _not on your LAN_ or try removing the 192.168.0.0/24 network from **mynetworks**, restarting Postfix, and trying again.

Correct. That setting effects your server authenticating with other servers (note the **smtp** bit - i.e. no 'd' hence it is referring to Postfix acting as the client as opposed to the server/daemon).

If that suits your needs then go for it! I wouldn't necessarily give up though.

Hi Mathew,


Thanks for your advice.  I'll test it later.


I'm now on the Workstation running F7.  New discovery;

Evolution running on F7 works seamlessly.  It can send and receive mails, with the same settings as on Ubuntu, via the Mail Server w/o problem.  This discovery makes me considering that Evolution on Ubuntu may has no problem.  Neither there is a problem on the Mail Server.  Ubuntu may has some misconfiguration causing the problem on "Relay access denied".


satimis

---

### Post by MJN on 2008-01-25
Are you sure it is authenticating, and not just being allowed to relay given it's location on the LAN? Post the mail log showing you sending a message from start to finish.

Otherwise, it sounds like it must be your Ubuntu Evolution configuration. I've never used it so someone else will have to confirm/deny whether authentication works - I'd be very surprised if it didn't.

Mathew

---

### Post by satimis on 2008-01-25
> **MJN said:**
> Are you sure it is authenticating, and not just being allowed to relay given it's location on the LAN?
 
On "sending mail" it does NOT require authentication.  On "receiving mail" it needs login and password to download mails from the Mail Server.


> 
Post the mail log showing you sending a message from start to finish.

Which /var/log/mail.log?  The successful one OR the failure?


> 
Otherwise, it sounds like it must be your Ubuntu Evolution configuration. I've never used it so someone else will have to confirm/deny whether authentication works - I'd be very surprised if it didn't.

I have been looking around on the GUI config of Evolution running on Ubuntu and could not find any item related to "Relay access denied".  On F7 it only requires a simple config on "sending mail".  Then it works seamlessly.  I haven't touched other items.


satimis

---

### Post by MJN on 2008-01-25
> **satimis said:**
> On "sending mail" it does NOT require authentication. On "receiving mail" it needs login and password to download mails from the Mail Server.
 
Authentication for receiving mail is nothing to do with Postfix. This is done with your IMAP/POP server.
 
> Which /var/log/mail.log? The successful one OR the failure?
 
Successfull. But in light of the above it sounds like you haven't set Evolution to authenticate anyway so it's probably not worth it.
 
> I have been looking around on the GUI config of Evolution running on Ubuntu and could not find any item related to "Relay access denied". On F7 it only requires a simple config on "sending mail". Then it works seamlessly. I haven't touched other items.
 
I've done as much as I can to help and am struggling to see what your problem is now. Can you authenticate with Postfix or not? What happens when you try? What authentication method have you told Evolution to use? Are you using TLS? What do the logs say? Where is your client? Is it off the LAN like I asked? Or have you removed the LAN addresses from mynetworks as suggested?
 
Come on Satimis - this is like pulling teeth!
 
Mathew

---

### Post by satimis on 2008-01-25
Hi Mathew,


Problem solved after running;

$ sudo apt-get --reinstall install evolution


Now Evolution on Ubuntu can send mails via the Mail Server without authentication.


Although it took time jumping from HD to HD and PC to PC, at least the problem is solved finally.

Anyway lot of thanks for your assistance.  I'm now going to the Mail Server testing authentication setup.


B.R.
satimis

---

### Post by MJN on 2008-01-25
> **satimis said:**
> Hi Mathew,
 
 
Problem solved after running;
 
$ sudo apt-get --reinstall install evolution
 
 
Now Evolution on Ubuntu can send mails via the Mail Server without authentication.
 
Eh? How's that 'problem solved'? You've configured Postfix to require authentication yet it's clearly not...? :confused:
 
Oh well - as long as you're happy!
 
Mathew

---

### Post by satimis on 2008-01-25
> **MJN said:**
> Eh? How's that 'problem solved'? You've configured Postfix to require authentication yet it's clearly not...? :confused:

No, I did not touch anything on main.cf.  Only reinstall Evolution on Ubuntu.


Now I test "authentication" on sending mails.


Mail Server
1)
Comment out the line "mynetworks = 127.0.0.0/8, 192.168.0.0/24" on main.cf

$ sudo /etc/init.d/postfix restart
No complain


2)
Kmail
F7

Sending

General
check "server requires authentication"

Security
click "Check What the Server Supports" ->
Encrytion - TLS
Authentical Method - PLAIN
(here I'm NOT allowed selecting other items ONLY PLAIN.  If selecting other items on clicking "Check What the Server Supports", it re-selects PLAIN again.


Mail can't be sent after typing in password with;

Warning```

Error - KMail
Sending failed:
Your SMTP server does not support PLAIN.
Choose a different authentication method.
The server responded: "5.7.0 Error: authentication failed: authentication failure"
The message will stay in the 'outbox' folder until you either fix the problem (e.g. a broken address) or remove the message from the 'outbox' folder.
The following transport protocol was used:
user1

```


Would it be caused by incorrect Certificate ?


I'll report other 2 cases re 'Evolution on Ubuntu' and 'Evolution on F7" respectively later.


satimis

---

### Post by satimis on 2008-01-25
Hi Mathew,


main.cf same as testing KMail on F7


Evolution on F7



Sending Email

check "Server requires authentication"

Security - No encryption 
(only allow to select "No encryption".  If selecting TLS/SSL, on clicking "Check for Supported Types" it re-selects "No encryption" again)


Type - I can select any item here.  Clicking "Check for Supported Types" has no effect on them.  Tried both login/PLAIN


Other items are:```

NTLM _SPA
GSSAPI
Digest-MD5
POP before SMTP

```


Mail can't be sent.  No login window popup instead following warning popup;

Evolution Error```

Error while performing operation.

RCPT TO <rlee@write.com> failed: <rlee@write.com>: Relay access denied

```





satimis

---

### Post by MJN on 2008-01-25
In post #11 you showed you do offer PLAIN (and LOGIN). Has this changed?
 
Given you said it used to work I suggest going back to whatever guide you followed and checking everything - including any testing that it covers.
 
Mathew

---

### Post by satimis on 2008-01-25
> **MJN said:**
> In post #11 you showed you do offer PLAIN (and LOGIN). Has this changed?

Same result diregarding using either one

>  
Given you said it used to work I suggest going back to whatever guide you followed and checking everything - including any testing that it covers.

Evolution came during installing Ubuntu desktop.  There was no guide for me to follow in the past.  I'll leave it as it is now continue running w/o authentication, until I discover the way to fix it.


Thanks again for your assistance and patience in supporting me.


satimis

---

### Post by MJN on 2008-01-25
> **satimis said:**
> There was no guide for me to follow in the past.
 
I meant the guide you followed for adding authentication to Postfix.
 
> Thanks again for your assistance and patience in supporting me.
 
No problem. It can get frustrating diagnosing faults remotely but it's not your fault - it is important to remember this is a complex area we're dealing with.
 
Mathew

---

