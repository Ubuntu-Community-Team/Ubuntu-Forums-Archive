---
title: "Need help setting up a email server."
date: 2009-05-05
forum: Server Platforms
---

### Post by kustomjs on 2009-05-05
Hi Guys
I am just wondering if anybody could help me setup a email server. what I am looking to do is use webmail with mysql with virtual hosted domain name.

---

### Post by windependence on 2009-05-05
Well if it were me, I would use something like Zimbra or Citadel instead of building your mail server from scratch. To build a full mail server, you would need at least postfix, dovecot or Courier Imap, maybe MySQL for the back end, Spamassassin, ClamAV, etc. These packages have all that stuff already integrated in one package.

Here are some useful links:

[http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide](http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide)

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://postfixmail.com/blog/?p=345](http://postfixmail.com/blog/?p=345)

[http://www.citadel.org/doku.php/installation:start](http://www.citadel.org/doku.php/installation:start)

-Tim

---

### Post by ejschaefer on 2009-05-05
Here is a great article to get you started with Postfix and Courier with a MySQL backend

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10)


I've been running a similar setup for a number of years without any problems. Its a lot less resource hungry than Zimbra too, not that Zimbra isn't a great product.

Running through this tutorial would be an excellent learning experience. If you poke around the HowtoForge site, you'll come across a plethora of additional articles detailing Postfix virtual hosting with various combinations of Courier, Dovecot, LDAP, MySQL, SpamAssassin, ClamAV, Squirrel, Horde, Roundcube and DKIM/DK-Milter.

Have fun! Let me know if you have any problems or questions.

---

### Post by jperez3 on 2009-05-06
I have ran through the process of setting up virtual mailboxes with Postfix/Dovecot 

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

and it worked like a charm.  However I needed some help refining a shell script I made that incorporates the commands to add users and restarting dovecot.

Here's my shell:
[html]
#!/bin/bash
clear
echo "enter email address:"
read fname
adddovecotuser $fname;
echo "enter email password:"
read upass
mkdovecotpasswd $fname $upass;
/etc/init.d/dovecot restart;
chmod 755 -R /home/vmail;
chown -R vmail:vmail /home/vmail;
exit[/html]The problem I have is that when users are added the accounts are not readable by default so the above shell makes them readable so they can be used.  

What I would like is to make this script process a command and halt if there is an error.  Currently it just keeps going until the script has ran it's course.  Can anyone help?

Thanks again

---

### Post by kustomjs on 2009-05-06
I tried to setup citadel and I cant even login to the web gui to it.


> **windependence said:**
> Well if it were me, I would use something like Zimbra or Citadel instead of building your mail server from scratch. To build a full mail server, you would need at least postfix, dovecot or Courier Imap, maybe MySQL for the back end, Spamassassin, ClamAV, etc. These packages have all that stuff already integrated in one package.

Here are some useful links:

[http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide](http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide)

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://postfixmail.com/blog/?p=345](http://postfixmail.com/blog/?p=345)

[http://www.citadel.org/doku.php/installation:start](http://www.citadel.org/doku.php/installation:start)

-Tim

---

### Post by windependence on 2009-05-07
What address are you using to access it? Are you trying to access it locally or remotely?

-Tim

---

### Post by kustomjs on 2009-05-07
well I am trying to access it by my internal ip address.

---

### Post by HermanAB on 2009-05-07
Well, since you are use virtualization already, just download the Citadel VM and be on your way in a few minutes.  It is pre-installed with everything including RBLs, SpamAssassin and ClamAV:
[http://www.citadel.org/doku.php/installation:appliance](http://www.citadel.org/doku.php/installation:appliance)

---

### Post by kustomjs on 2009-05-07
I dont have a virtual server on my server I am using virtual hosting. what I am going to do is im going try that how to guide on howtoforge. then Citadel will be my last option.

---

### Post by nquinnathome1 on 2009-05-08
See here if you're running 9.04:

[http://packages.ubuntu.com/uk/jaunty/dovecot-postfix](http://packages.ubuntu.com/uk/jaunty/dovecot-postfix)

---

### Post by kustomjs on 2009-05-09
Thanks To Ed aka ejschaefer for taking his busy schedule to help me setup my email server and got to work but I still cant receive emails.  

so if anybody needs help setting email server up talk to Ed aka ejschaefer to see if he is willing to help you out or you can talk to me and get my configure settings from my email server.

---

### Post by pmla on 2009-05-10
Can't login to citadel webgui "webcit"? that's strange.

To be honest with you, I'm have medium knowledge of linux or maybe I'm just a newbie. I have tried them all:
- Postfix (complex)
- Qmail (complex)
- Sendmail (complex)
- Zimbra (medium easy but not ubuntu 8.10 server ready)
and finally citadel... that's what I'm running now with ubuntu 8.10, and it's dam easy to install and use.

About your citadel problem... check out their website and documentation page also check their support page:
[http://uncensored.citadel.org:8080/]("http://uncensored.citadel.org:8080/")
Just login using any "user" any "password"

See if the default webgui 2000 port is not in use by something else.
Use the reconfigure command for citadel if you want to change your custom installation data like admin user, domain, etc.
You can also use the:
#dpkg-reconfigure citadel-webcit
to reconfigure webcit, you can change port here.

---

