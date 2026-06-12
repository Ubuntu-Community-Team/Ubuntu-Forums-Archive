---
title: "Email server"
date: 2010-03-20
forum: Server Platforms
---

### Post by avisonjohn on 2010-03-20
Ok, I have downloaded Ubuntu Server and installed apache2, mysql, and php5.
 
I currently have a website running from it and bought a domain name for it to.
 
I pointed the domain name to the ip address of the server and the website domain works perfectly.
 
I now want to be able to have my own email address for it ([EMAIL="webmaster@mydomain.com"]webmaster@mydomain.com[/EMAIL])
 
I am a complete noob when it comes to setting up mail servers as this has always been provided by the registrar when i buy domain names.
 
Can someone advise me how I go about seeting this up? I have search all over the net and configured postfix and dovecot correctly i think. Im sure I have also done the MX record properly.
I set a dns record to point mail.mydomain.com to my ipaddress too.
 
I have tried setting up an account in MS Outlook 2003 using IMAP and created the user account MailUser in Ubuntu. I can login to the mail server using that account but I cannot send or receive any mail. It appears to send and receive without any errors correctly but I get no incoming or outgoing mail.
 
Are there any tutorials on the net that will guide me through setting up DNS records with the registrar to setting up email accounts and sending/reciiving email?

All the tutorials I find only show parts of this but im looking for a complete step by step guide.
 
Any input or suggestions would be appreciated.
Many thanks
 
- AJ

---

### Post by noway2 on 2010-03-21
The first thing you will need to do is educate yourself about how email servers work by reading, a lot.  I do not mean to be glib, but email servers are not trivial and a solid understanding of what you are up against will help.  Be prepared to spend many hours working in the terminal getting very frustrated.  The process will require an understanding of many packages and programs, possibly including an understanding of SQL, at least if you wish to host virtual domains that aren't tied to user accounts.

One you understand the magnitude of what you are trying to accomplish, google the keywords, "how to ubuntu email server" and you will get a list of documents describing the procedure for various systems, including this one which seems to be popular: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/).  I personally found these two to be helpful: [http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/) and [http://dertompson.com/2008/02/13/mail-server-setup-for-debian-etch/](http://dertompson.com/2008/02/13/mail-server-setup-for-debian-etch/). I suggest you do search and read the various documents.  They are all different and it is my experience that none of them seem to work perfectly for anybody.

I haven't tried it, but a lot of people swear by zimbra.  You may want to investigate that.

---

### Post by jrssystemsnet on 2010-03-21
Or there's the one I wrote, [http://ubuntuwiki.net/index.php/Postfix,_Virtual_Domain_Setup](http://ubuntuwiki.net/index.php/Postfix,_Virtual_Domain_Setup) - but like the last guy said, setting up and running an MTA *is not trivial* and nothing is going to make it trivial.

There is a LOT to keep on top of.

---

### Post by Geoff918 on 2010-03-21
Honestly, I've tried many different walk-thoughs. And following step by step, it's still ridiculously difficult (for me). I have done many things with servers as a somewhat acquainted but unofficially trained individual.

This was pretty easy, and it's what I used, personally.

[http://www.iredmail.org/](http://www.iredmail.org/)

You can use the Ubuntu install.

PS - You will need to have an MX server handling setup with your hosting provider. (Necessary for any email server setup).

---

### Post by avisonjohn on 2010-03-21
I have got no problem understanding how servers work and especially no problem understanding SQL - my job revolves around maintaining linux server's running apache2 hosting a good handfull of websites most of which are MySql driven (including my own).
 
I tried sending an email from outlook coming from my [EMAIL="mailuser@mydomain.com"]mailuser@mydomain.com[/EMAIL] going to [EMAIL="MyRealEmail@yahoo.co.uk"]MyRealEmail@yahoo.co.uk[/EMAIL] and i get this appear in my inbox.
 
```

[SIZE=1]Your message did not reach some or all of the intended recipients.
Subject: Test Mail
Sent: 21/03/2010 19:16
The following recipient(s) could not be reached:
John Avison on 21/03/2010 19:16
554 5.7.1 [EMAIL="MyRealEmail@yahoo.co.uk"]MyRealEmail@yahoo.co.uk[/EMAIL]: Relay access denied

```
 
And when I send an email from my Yahoo account to my MyDomain account, i get no reponses or messages delivered.
 
I'll have another look at the links posted here and see if I can make any more sense of it all :(
[/SIZE]

---

### Post by avisonjohn on 2010-03-21
Are there any programs i can install that has everything preconfigured for me? Like LAMP configures and installs apache with php and mysql?
 
Im going to make a backup of my web files and reinstall the server in a short while and start the mail server setup again to see if i can figure it out

---

### Post by dudumomo on 2010-03-21
I've received several thanks for my tutorials: [http://www.freelydifferent.com/tutorial-selfhosting/](http://www.freelydifferent.com/tutorial-selfhosting/)
May be it can help you !

---

### Post by avisonjohn on 2010-03-21
Cheers, I'll definately be bookmarking that site ;)
 
I think it's all working now but the only problem is If i send email from the new email account, i always get the Relay Access Denied error.
I looked on your pages and it says to set the relay_host to my ISP's SMTP server.
 
Im with Virgin Media and their SMTP address is smtp.virginmedia.com
 
This is a part of whats in my /etc/postfix/main.cf which I have been told are the parts I need to cnocentrate on:
 
```

relayhost = smtp.virginmedia.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

```
 
Any advice on this would be great. Cheers guys.

---

### Post by kewlrichie on 2010-03-22
First off if you don't know already you would need have a hosted MX record  with a hosting provider so your domain (mywebsite.com) knows where to  resolve to your new mail server. Also your ISP has to not have port 25  blocked or you wont be able to receive mail. If your doing this at home  there is work around for ISPs that block 25 port, just do a quick  search on the forums or google and there are services like no-ip.com has  a service called mail reflector [http://www.no-ip.com/services/manage...5_unblock.html]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html")

That being said as for the relay access denied I am guessing here without seeing an output of "postconf -n" first. I believe you need to check your /etc/postfix/main.cf file and look for "mydestination" add your domain there and restart postfix "/etc/init.d/postfix restart" see if that helps the replay access denied problem. the relay host part just leave blank "relayhost ="

Your server denying relay access is a very very good thing. You dont want it doing that unless you know for sure thats what you need and from reading through your post it looks like you dont. The "mynetworks" just tells postfix which networks are allowed to use it. 127.0.0.8 of course being the localhost meaning you would only be able send mail using that machine only. So lets say you have an internal network of 192.168.1.0 with a subnet mask of 255.255.255.0 then you would allow 192.168.1.0/24 to allow computers on your network to use it has a mail server.

you can checkout this site for the postfix basics so you can see what mydestination and mynetworks mean [http://www.postfix.org/basic.html](http://www.postfix.org/basic.html)

Another good tip once you have everything setup is to checkout is [http://mxtoolbox.com/](http://mxtoolbox.com/) you can put your domain name and it will do a MX lookup then you can do a SMTP Test and see if things are correct like making sure its not an open relay, transaction time, if your domain name resolves correctly to your IP address and if your reverse DNS matches your SMTP Banner correctly. All of these things should be good to go for a working mail server.

As for installing a new LAMP server i would highly suggest this site [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp)  they make great tutorials/guides for this kind of stuff. Also they have a iredmail guide for 9.04 at [http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04](http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04) There are also guides on there website also at [http://code.google.com/p/iredmail/wiki/Installation_on_Ubuntu](http://code.google.com/p/iredmail/wiki/Installation_on_Ubuntu)  for ubuntu 8.04 LTS and 9.04 not too sure about 9.10 if thats what your using. by the way this is for a virtual style setup which is pretty nice in case you want to add multiple domains and users. Good luck

---

### Post by avisonjohn on 2010-03-22
Perfect, cheers for that.
is there anyway I can set the 'mynetworks' part to allow anybody to send email as long as they provide the correct login details? I say this because I dont want to be restricted to webmail, i want to be able to send emails from Outlook whilst im at work or elsewhere, but only allow it if I provide the correct login details for my email account.

---

### Post by KB1JWQ on 2010-03-22
Provided you're still using Postfix, permit_sasl_authenticated works.

---

### Post by kewlrichie on 2010-03-25
> **avisonjohn said:**
> Perfect, cheers for that.
is there anyway I can set the 'mynetworks' part to allow anybody to send email as long as they provide the correct login details? I say this because I dont want to be restricted to webmail, i want to be able to send emails from Outlook whilst im at work or elsewhere, but only allow it if I provide the correct login details for my email account.

Well I wouldn't recommend opening up mynetworks to everyone its just not a good idea. Keep it to localhost and your local network. However if you notice in your main.cf you'll see "smtpd_recipient_restrictions =" and it should have "[FONT=monospace][/FONT]permit_mynetworks" which is your local network and also has "[FONT=monospace][/FONT]permit_sasl_authenticated" which is what [KB1JWQ]("http://ubuntuforums.org/member.php?u=1036642") has mentioned for outside of your network SMTP authentication. You can find more info on how to set that up at the link below

 "So let's say your users are going away for holidays but need to use  your mail server to relay mail from outside the organization... Let's  set up  SMTP authentication for the secure port only and allow access to this  from outside your network." 
[http://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only](http://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only)

---

### Post by lisati on 2010-03-25
The main tutorial I used for setting up my email server can be found [here]("https://help.ubuntu.com/community/Postfix"). It covers basic setup, SASL authentication and a few other topics. I'd also suggest looking at [https://help.ubuntu.com/9.04/serverguide/C/mail-filtering.html](https://help.ubuntu.com/9.04/serverguide/C/mail-filtering.html)

---

