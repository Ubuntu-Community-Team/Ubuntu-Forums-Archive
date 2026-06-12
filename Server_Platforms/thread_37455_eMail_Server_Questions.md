---
title: "eMail Server Questions"
date: 2005-05-27
forum: Server Platforms
---

### Post by orion_114 on 2005-05-27
I am interested in setting up a mail server for my company.
They have been looking into getting MS Exchange and I would prefer to have a OpenSource solution instead.
I have read some of the threads on the site and some tutorials on other sites too.
I am still not clear on some points though:
[list]
[*]Is Postfix purely a SMTP server?
[*]Do I have to use a combination of several applications to have a fully functional mail server, or is there one single solution? (Courier?)
[*]What are the security implications of having this email server? (Will I have to have it in my DMZ?)
[*]What other applications are out there that are pretty easy and if possible have some kind of web interface?
[/list]

---

### Post by deuce868 on 2005-05-27
> Is Postfix purely a SMTP server?
Yes

> Do I have to use a combination of several applications to have a fully functional mail server, or is there one single solution? (Courier?)
You're pretty much going to have to roll it together. 

> What are the security implications of having this email server? (Will I have to have it in my DMZ?
Like any server you're going to have open ports, users connecting with passwords, and more software with potential holes you have to watch for. There will be a lot of check in the setup to make sure you don't get blacklisted and such because you're being used as a spam gateway. 

> What other applications are out there that are pretty easy and if possible have some kind of web interface?
For what? I use a postfix/courier imap/spammassasin/clamav/amavisd-new/squirrelmail setup and it works really well. It definitely took some time and reading to setup, but I prefer it over the exchange box I also run. (I have 10 staff on exchange and 50 students on the linux mail server)

---

### Post by orion_114 on 2005-05-28
hey deuce868,
Thanks for the answers.
I am basically trying to setup a mail server that will handle internal mail and external mail. I want some of my intranet users to have access to internal mail only and other to have access to exteral and internal mail. I have about 50 users that I would like to setup on this system. I also have some other applications that require an smtp server to bounce emails off to other locations.
Would all of this be possible with the programs mentioned and are there releveant resources out there for a noobish administrator ?
Thanks again for the answers !  :grin:

---

### Post by LordHunter317 on 2005-05-28
[QUOTE=deuce868]Yes[/quote]No, postfix is not strictly an SMTP server, not in the sense the OP meant, I think.  Postfix is an MTA which means it handles delievery to the user's mailstore as well.  It does not however, handle delivering to the user.

> There will be a lot of check in the setup to make sure you don't get blacklisted and such because you're being used as a spam gateway. Postfix comes OOB setup not to be a relay and you actually have to try to make it that way.  So this is somewhat difficult to do.

[quote=orion_114]Do I have to use a combination of several applications to have a fully functional mail server, or is there one single solution? (Courier?)[/quote]Courier provides a suite of programs that cover the whole job, but their still seperate applications.  And I can only vouch for their IMAP and POP3 servers, not their MTA.

> What are the security implications of having this email server? (Will I have to have it in my DMZ?)Yes, it belongs in your DMZ (it serves the Internet, right?  Therefore, it goes in the DMZ).  If the mail being delievered is solely for internal users and they only need internal access, you could setup a relay box in the DMZ that does spam/anti-virus processing and gets mail to/from the Internet.  You could than have the delievery server (running POP3/IMAP) inside your LAN.  You configure the relay box to deliever to the delivery server.

This is of course, if you don't need/want your users to have Internet access to their mail.

> I am basically trying to setup a mail server that will handle internal mail and external mail. I want some of my intranet users to have access to internal mail onlyMeaning what?  They can only send to users on your domain?  Or meaning they don't have an Internet-accessible account?  I believe this is possible, but it'll take some work.

> I also have some other applications that require an smtp server to bounce emails off to other locations.Postfix can do this.

---

### Post by orion_114 on 2005-05-31
hey guys,
I have been reading up quite a bit and I have decided apon using the courier suite of apps. 
I have managed to install and configure it. (oh so easy with the webadmin component)
My problem now is the user setup. I am not sure how to go about this.
I have created a test account on the mail server (using the Ubuntu users and groups dialog from the administration menu) and I have edited the /etc/aliases file adding the following:
```
testuser: testuser@mydomain.com
```
I have tried to access the email account from my Windows machine with outlook, but the pop3 authentication seems to fail.
I am using the username and password I created on the mail server as a local user for the login details to my pop3 server.
Can somebody please help me out ? I am sure I am doing something horribly wrong  ](*,)

---

### Post by orion_114 on 2005-05-31
I found out what was wrong. I used telnet on port 110 to try and log in to the pop3 server manually. 
It threw an error about the Maildir, which was missing. 
All I needed to do was create a directory structure ~/Maildir/cur for each user in order for them to login.  \\:D/

---

