---
title: "Ubuntu Server Postfix Email Help Needed"
date: 2013-09-22
forum: Server Platforms
---

### Post by Tony_Lillie on 2013-09-22
I have Ubuntu Server 12.04 installed in my small home network on a dedicated computer behind my ISP's DSL router/modem. I have it set up as a LAMP server and am successfully hosting my web site ([www.mywebsite.com]("http://www.mywebsite.com")) on it with all of the necessary ports forwarded. I'm using no-ip's dynamic DNS service to point my domain at my dynamic IP address. The only problem I'm having is email. I've spent 20+ hours reading, studying and trying many different configurations. I CAN'T GET IT TO WORK! ](*,)I've re-configured Postfix 5 different ways at least and cannot get an email sent to my personal gmail address using the following command. ```
echo "Test mail from postfix" | mail -s "Test Postfix" myemail@gmail.com
``` 

I've decided to use Postfix because there seemed to be more information available for it than any of the other possible solutions. So I would appreciate help that focuses on Postfix and not other solutions UNLESS you have a very compelling reason to lead me down another path.

I don't think I want or need my server to be a full on mailserver (tell me if I'm wrong:confused:). I merely want my website contact form to work. PHP coding aside (different issue entirely), I presume that because my web site contact form resides on my server that my server must be able to send outgoing emails in order for it to work. Is that correct?? Because that's all I want. I don't want to receive emails through the server, and I have no other need to send emails from this server. It only hosts my small business web site, nothing more.

One last thing; I'm sure someone will want to leave me a link to a tutorial or other Postfix web site, but PLEASE only do this if your confidence level is extremely high that it will speak to my issue. I know I haven't read everything out there, but it feels like I have. My eyes are bloodshot from reading on this screen for the past 3 days, and I'm at the end of my rope. I desperately need help from someone with knowledgeable answers.

---

### Post by TheFu on 2013-09-22
Could your ISP be blocking outbound SMTP that does NOT use their email gateway servers?  Most do.  

If so, there is a way to tell postfix to use an email relay .... the setting is **relayhost = smtp.your-isp-email-gateway.com** inside the /etc/postfix/main.cf.

BTW, most email servers will block email from residential DHCP IPs using blocklists.  I do. It just isn't worth all the spam to allow the 5 people I know who run email servers from their homes access.

If this is not the issue, a little more data would be nice - can you telnet to gmail.com on port 25?  What does **postconf -n** show?  Normal postfix troubleshooting stuff.  At least you aren't trying to receive email on a residential ISP.

It is impossible to read everything out there for postfix.  Ignore everything except from postfix.org or ubuntu.com/.org sites.

BTW, you can use fetchmail to poll all your external email providers, pull the emails local, then they will be there when/if your internet goes down.  Email is designed to work on disconnected networks, after all.

---

### Post by Tony_Lillie on 2013-09-22
How do I know if my ISP is blocking the outbound SMTP, or is it just so common that I should assume they are?

I've tried a relayhost configuration that sets gmail as the smtp server and that didn't work. I will try using my ISP smtp settings.

I can telnet into the server on port 25, but I get the following when attempting gmail with the command telnet smtp.gmail.com 25
Trying 74.125.142.108...
Trying 74.125.142.109...
Trying 2607:f8b0:4002:c01::6d...
telnet: Unable to connect to remote host: Network is unreachable

Here are my results from postconf -n:
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = gmail.com localhost.localdomain, localhost
myhostname = UbuntuServer
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/255
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

Thank you for the advice about where to go for information. Linux has much more information available than Windows, but sometimes it's a mile wide and an inch deep.

I'll post back later after trying my ISP smtp settings in the relayhost.

---

### Post by TheFu on 2013-09-22
Is smtp.gmail.com the real name of the gmail gateway? I didn't look it up.   On my thick client, it is smtp.googlemail.com on port 465, but that is for sending authenticated email only. I don't think that gmail allows relaying to just anyone.

You'll need to lookup the DNS name and port for the ISP gateway.  Try it without authentication and it might work, but more and more ISPs are only allowing authenticated email through their systems.  Necessary to fight spammers.  There should be a support page at your ISP which explains.

Sometimes the gateway is the same as the MX DNS record.  Check that with **dig {FQDN} mx**  For gmail and ISPs, I would NOT assume that is the answer.  I send email using a different server than I receive email and I allow forwards only from authenticated clients or systems on the same subnet.

Sorry for the rambling and stories. Perhaps one of the details will help.

---

### Post by Tony_Lillie on 2013-09-22
Looks like smtp.gmail.com is correct for gmail, and I've tried it both with and without the port :587 or :465, no joy.

I've also tried my ISP's smtp setting, though the port setting was unclear, so I tried it with nothing and with :465 and no joy.

Just FYI, I am remembering to reload the configuration after each set of changes before testing using the following command ```
sudo /etc/init.d/postfix reload 

``` 

My ISP does block all SMTP emails on port 25. So, does that mean I can ONLY send outgoing mail by going through smtp.frontier.com? 

Here is what I got using the command ```
dig frontier.com mx


```  ```
; <<>> DiG 9.8.1-P1 <<>> frontier.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34241
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 3, ADDITIONAL: 5

;; QUESTION SECTION:
;frontier.com.                  IN      MX

;; ANSWER SECTION:
frontier.com.           300     IN      MX      10 mx.frontiernet.net.
frontier.com.           300     IN      MX      10 mx.dlls.pa.frontiernet.net.

;; AUTHORITY SECTION:
frontier.com.           69558   IN      NS      auth.roch.ny.frontiernet.net.
frontier.com.           69558   IN      NS      auth.lkvl.mn.frontiernet.net.
frontier.com.           69558   IN      NS      auth.dlls.pa.frontiernet.net.

;; ADDITIONAL SECTION:
mx.dlls.pa.frontiernet.net. 85707 IN    A       199.224.64.204
mx.frontiernet.net.     86348   IN      A       66.133.129.79
auth.lkvl.mn.frontiernet.net. 83534 IN  AAAA    2001:1960:20:8000::11
auth.roch.ny.frontiernet.net. 84126 IN  A       66.133.170.3
auth.roch.ny.frontiernet.net. 77043 IN  AAAA    2001:1960:20::303

;; Query time: 59 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Sep 22 16:11:20 2013
;; MSG SIZE  rcvd: 268


```

Does that information reveal anything to us?

Could I be missing some other plugin or something? Or are you convinced my issue is related to the Postfix settings?  During Postfix configuration I was very unsure about choosing either Internet site or Satellite and I've done it so many times now that I can't remember what it is currently set as.

---

### Post by TheFu on 2013-09-22
Are you authenticating when you send email from postfix to frontier?  UserID and password?  Seems that both your options (frontier and gmail) require that.  I've never done it, but I know that postfix can do it based on the sender.

Basically, you have to tell postfix to act like a normal "fat email desktop program" when sending email out.  It should relay though the ISP gateway, and your connection to that gateway must be authenticated.  I'm positive that people do this with gmail but they can only send using their GMAIL account, userid and credentials. No spoofing the "FROM" is allowed.

---

### Post by Tony_Lillie on 2013-09-22
I have a file /etc/postfix/sasl_passwd where my username and password for my ISP are stored, but I'm not sure about the authentication part. How do I know that Postfix is authenticating? What other settings need to be in place for it to authenticate?

---

### Post by Tony_Lillie on 2013-09-23
Well I finally have SOME good news. I am able to telnet into my ISP using the command ```
telnet smtp.frontier.com 25


```  but I still can't get it to send a succesful email.

Does the fact that I CAN tenet into my ISP's SMTP indicate I have the authentication settings correct? If not, what is the significance of being able to connect via telnet. It must indicate at least something is working correctly, right? What exactly is that?

If I know some settings are right, then at least I can move on to other possible issues.

---

### Post by SeijiSensei on 2013-09-23
Did you conduct a full SMTP session when you used telnet?  

You should see a banner in response to your connection.  If so, follow these steps:

```

[banner displayed]
[color=blue]helo your.server.name[/color]
[server replies]
[color=blue]mail from: you@yourdomain.com[/color]
[replies]
[color=blue]rcpt to: someone@anotherdomain.com[/color]
[replies with "DATA"]
[color=blue]Type a test message followed by a line with only a period in the first column.[/color]
[server should accept your message]

```

Type the entries in blue.  Obviously you need to replace things like "your.server.name" with the appropriate values for your machine.  If there is a problem, the server will reply with an error message.

---

### Post by Tony_Lillie on 2013-09-23
This is where I get lost. What is my "your.server.name"? Because my server has a name that is just one word "myserver".  Also, what IS my domain name? I know what my website domain name is, but is that what I use? What email address should I use in the mail from line? I tried it with my gmail address, my ISP (Frontier) address, and my website doamain email address. All three got me the same response: 501 5.1.7 Bad sender address syntax. See [http://postmaster.frontiernet.net](http://postmaster.frontiernet.net)

So I went to the URL indicated and found the following information:
**Frontier's mail servers:** 
[LIST]
[*]Will not accept connections from unsecured systems. This includes  open relays, open proxies, or any other system that has been determined  to be available for unauthorized use.

[*]Will not accept connections from known spam sources.

[*]**Will not accept connections from systems that use dynamically assigned or residential IP addresses.**    ***IS THIS THE ISSUE?***

[*]Will not accept connections from any IP addresses that do not have  reverse DNS (PTR record) and may refuse or rate limit connections from  hosts without a matching DNS A record. See [RFC 1912, section 2.1]("ftp://ftp.rfc-editor.org/in-notes/rfc1912.txt").

[*]Will not accept connections from systems that do not send a helo with a valid hostname or domain name.

[*]Will refuse bounce messages (i.e. messages with null sender) to more than one recipient. See [RFC 2821]("ftp://ftp.rfc-editor.org/in-notes/rfc2821.txt").

[*]Will refuse messages without a valid or properly formatted 'mail from' addresses.

[*]Will refuse messages sent through an http proxy.

[*]May refuse connections from systems that do not accept bounce messages.

[*]May rate limit connections or messages based on the number of  connections, messages sent, or recipients during a specific period of  time.

[*]May refuse connections from systems that, through their actions, cause a denial of service.
[/LIST]
  Additionally, all incoming and outgoing messages must pass anti-spam  and anti-virus checks based on current trends on the Internet.

Is that the ballgame?? Bottom line: Is it possible for me to get email working from my personal server behind Frontier's DSL modem/router??  If not, it's not possible to make my website contact form work from that same server, right??

---

### Post by Tony_Lillie on 2013-09-23
I refuse to believe I am the only person trying to do this! Somebody out there must have some answers that fit my situation. PLEASE read my initial post, so you understand my situation. I'm running my server behind my ISP's DSL router/modem with a dynamic IP address.

Here's where I get REALLY confused. I own a website domain name, and my server is a webserver hosting the files for that domain, but my server's "domain name" is not the same as my website domain name, right?? So then, WHAT is my server's domain name??

I'm sure some of you think I'm a total noob, but I'm not. Green and growing, but not a total noob. I just get really confused when trying to differentiate between all these domain names and hostnames etc...

I'm pointing this out because I'm fairly well convinced that I don't have the right names in the right places in the configuration.

---

### Post by Tony_Lillie on 2013-09-23
Well, if anyone wants to rejoice with me I've solved this issue by following the following guide: [http://rtcamp.com/wordpress-nginx/tutorials/linux/ubuntu-postfix-gmail-smtp/](http://rtcamp.com/wordpress-nginx/tutorials/linux/ubuntu-postfix-gmail-smtp/)

I totally removed postfix, then re-installed it (12th time is the charm:p) choosing satellite rather than internet site per the first part of this guide: [http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu](http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu)

I also think I was setting the FQDN incorrectly in previous installations. This time I used my website domain (mywebsite.com) and that seems to have helped. 

FINALLY am able to send emails from my personal web server!!!!!!!  YYYYYYEEEEEEEESSSSSSS!!

---

