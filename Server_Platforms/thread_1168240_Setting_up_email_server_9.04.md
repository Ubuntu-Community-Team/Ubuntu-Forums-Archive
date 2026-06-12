---
title: "Setting up email server 9.04"
date: 2009-05-23
forum: Server Platforms
---

### Post by deekthesqueak on 2009-05-23
I recently decided that my needs on a shared hosting services were not met and was ready to take the step up to a VPS solution.  I found a host and got Ubuntu 9.04 server setup and running fine.  I have SSH working a created a non root user to do all the administartion and disabled old root out for security.

I have worked with linux for awhile and know my way around a command line with no problems but I have run into a road block setting up something I have taken granted for in the past, email.

After many days of searching I have found lots of conflicting information and I have decided it is time to ask some clarifying questions. First let me lay out how I would like things to function and then what I have tired doing so far.

I will be hosting a few different domains, some are my own personal and one is for a friends startup.  I have envisioned that each domain will have its own directory in /home that is tied to a user who can SSH in but only have access to their own domain.  The web serving part of this I am able to do no problem. 

As far as email I would like that user, essentially the domain admin to be able to add email accounts on as add needed basis with no need to bother the overall server admin (me).

I have looked around and I have seen good amount of talk on turnkey solutions.  One of the reasons I am hesitant to this is I like to know exactly what is going on and have control over that.  Plus the more I work on a setup myself the more I will learn about it's function.

I have looked long and hard at the Ubuntu server guide and documentation related to it and decided postfix looks like the best solution.  Now I'm not sure which to choose when it comes to my IMAP/POP3 server.  I see there is dovecot and courier, does anyone have any feedback on which is the best to use?  It looks like what want to do is called "virtual users" where different emails can be added to domains without creating users in the system, this seems to be mostly done with a database (MySQL is my preference).  Does this narrow my choice for IMAP/POP3 servers?

I have a full three day weekend, a case of Mountain Dew, and and itch to get a working email server up and running.  Any help on moving forward would be most helpful. I know there are some guides out there but I would like to know what I want to do before I go searching for a guide then find out one thing is different from what I'm looking for and I just wasted 10 hours trying to get something to work that simply can't be done.

---

### Post by windependence on 2009-05-23
So you wanna do it the hard way? No problem. Here are some resources to get you started:

[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)   (this is a list of How Tos, not the actual docs)

[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)   (virtual domains with postfix)

[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)  (from the Ubuntu docs)

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)  (more from Ubuntu)

If you get frustrated because you are up against a time limit, you can always fall back on Zimbra or Citadel as a complete 30 minute solution.

Good luck!

-Tim

---

### Post by deekthesqueak on 2009-05-23
> **windependence said:**
> So you wanna do it the hard way?
Always :)

> **windependence said:**
> 
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)


I had actually come across this in my pre-post searches. [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10)

Do you know the difference between courier and dovecot? Dovecot is listed in the Ubuntu Server guide and from what I can tell at a quick glance it is a bit simpler.  Any thoughts?

---

### Post by Xipher on 2009-05-23
I haven't tried Courier, but I do use Dovecot and it's been a great program to work with so far. It also integrates well with Postfix and Postfix can even use Dovecot to handle authentication so you don't have to worry about keeping their data in sync for authentication purposes.

---

### Post by deekthesqueak on 2009-05-23
@Xipher
Did you set up your own certificate authority (CA) to do IMAPS/POP3S or do you even use those protocols?

---

### Post by Xipher on 2009-05-23
No, I've been using [http://www.startssl.com/](http://www.startssl.com/) for certificates. Free and Mozilla includes them as a trusted CA so Firefox and Thunderbird don't throw warnings.

---

### Post by deekthesqueak on 2009-05-23
@Xipher
Cool site, doesn't seem to like Chrome or Firefox 3.5 right now. Are you using MySQL with your setup that you have right now?

---

### Post by Xipher on 2009-05-24
Yes I am, Postfix, Dovecot, Mysql backend with Postfixadmin handling web based administration, and I'm using roundcube for webmail. Virtualhost setup but it's also all hosted on OpenBSD, not Ubuntu.

---

### Post by ian dobson on 2009-05-24
Hi,

Maybe have a look at xmail ([http://www.xmailserver.org](http://www.xmailserver.org)). Simple to setup using configuration files. Adding scripts for email scanning is also really easy.

I've been running it on my backend server for about a year without any problems. You might need to manually compile/install it as the ubuntu package was broken the last time I looked at it.

Regards
Ian Dobson

---

### Post by salim.madni on 2009-05-24
dear

try to use AXIGEN MAIL SERVER, alternate of MS-EXCHANGE, it called like EXCHANGE FOR LINUX. looks no further. 5 user office edition free for life

also you need hardware,os ubuntu, and axigen...no effort...everthing is inside single package bundle. 

you wil never disapoint using axigen, and free support is great response in time. try to send email [email]support@axigen.com[/email]

also have download start free trial full edition 30 days also, 

if you need any assistance let us know. one of isp level portal using 5MILLION 5,000,000 mailboxes on single axigen box server. just imagine how strong it will be similar to QMAIL.

regards
salim

---

### Post by kustomjs on 2009-05-24
I am using dovecot/postfix/mysql/roundcube for my email server.

---

### Post by windependence on 2009-05-24
Truth be told, in the real world I don't have time to set up mail from scratch. All my commercial clients get Zimbra unless they want something else and then it's usually Citadel. I know how to set them up from scratch but you can't beat Zimbra's integration of Postfix, Clam, Spamassassin, LDAP, and other packages all in one install. I can have one running in less than 30 minutes. In my business I need the speed.

-Tim

---

### Post by kustomjs on 2009-05-24
I had more problems with Citadel in 9.04 then what setup I have now. if anybody wants a working copy of my email server files let me know.

---

### Post by deekthesqueak on 2009-05-24
> **Xipher said:**
> Yes I am, Postfix, Dovecot, Mysql backend with Postfixadmin handling web based administration, and I'm using roundcube for webmail. Virtualhost setup but it's also all hosted on OpenBSD, not Ubuntu.

Do you have a guide you used?

---

### Post by kustomjs on 2009-05-24
I dont use postfixadmin but I got a code/script that was custom build for my setup and it does same thing as postfixadmin but much easier to use.

but I am looking to get a how to guide done soon for how my system was setup.

---

### Post by deekthesqueak on 2009-05-25
> **windependence said:**
> Truth be told, in the real world I don't have time to set up mail from scratch. All my commercial clients get Zimbra unless they want something else and then it's usually Citadel. I know how to set them up from scratch but you can't beat Zimbra's integration of Postfix, Clam, Spamassassin, LDAP, and other packages all in one install. I can have one running in less than 30 minutes. In my business I need the speed.

-Tim
I took a look at the feature list and Zimbra does have a great many features but anything that is for domain specific administartion (what I am looking to do) isn't in the open source edition :(

---

### Post by albinootje on 2009-05-25
> **deekthesqueak said:**
> 
As far as email I would like that user, essentially the domain admin to be able to add email accounts on as add needed basis with no need to bother the overall server admin (me).


Imho you really should go for Dovecot + Postfix.

And you're saying you want full control over what happens, that would sound like you want to do everything manually, but you also want to have some easy delegation of tasks.
I think postfixadmin would be perfect. I'm using it on a few mailservers since years, and i'm very happy with it.
You can have email-admins per domain, and you can let all users change their passwords, change their forward.

The one thing I had problems with in the past was the vacation (auto-reply) option in Postfixadmin, in the end I decided to go for the Sieve vacation option from Dovecot, which means that users are dependent on me to have a vacation message activated or 
disabled. See here : [http://wiki.dovecot.org/LDA/Sieve](http://wiki.dovecot.org/LDA/Sieve)
It is possible that the vacation troubles I had with Postfixadmin are fixed in the meantime, it was a while ago, and development of Postfixadmin is not that slow at all. (They also provide deb packages now).

I have used this howto for the installation of Postfixadmin/Dovecot :
[http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)

That howto is not written for Ubuntu or Debian, but it is simply a matter of installing the relevant packages (Postfix, Postfixadmin, MySQL, Dovecot, php, Apache), and then change the GID for the "mail" group, which is "12" in CentOS, but "8" in Debian and Ubuntu.
```

grep mail /etc/group

```

Another nice thing about Dovecot is that it can do authenticated  smtp (SASL) for you (without having to bother with the more difficult Cyrus SASL), and.. you don't need to punish yourself with Courier Maildrop for local mailfiltering, because Dovecot has a LDA itself.

---

### Post by LepeKaname on 2009-05-26
If you are interested, I made a script to install Postfix/Dovecot with SASL and TSL which I use in 4 servers... 

Also I explain in detail how to set up it manually...

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

I hope it is useful.

---

### Post by deekthesqueak on 2009-05-29
I think I have things all set up but using so many different guides I am not sure how to check that everything is working.  I am not able to to login to any account from Thunderbird tho it does get the certificate I have.

My postfixadmin webpage is working but whenever I add an account the webpage will never resolve.  Can someone who has a Postfix/Dovecot/MySQL setup give me a couple of suggestions on how to test each different part to make sure everything is working?

For reference here is the output of ufw status just in case I might have a firewall problem:

```
Status: active

To                         Action  From
--                         ------  ----
Apache                     ALLOW   Anywhere
OpenSSH                    ALLOW   Anywhere
Dovecot IMAP               ALLOW   Anywhere
Dovecot POP3               ALLOW   Anywhere
Dovecot Secure IMAP        ALLOW   Anywhere
Dovecot Secure POP3        ALLOW   Anywhere
```

---

### Post by windependence on 2009-05-29
> **deekthesqueak said:**
> I took a look at the feature list and Zimbra does have a great many features but anything that is for domain specific administartion (what I am looking to do) isn't in the open source edition :(

That's not true. I have several running with more than one domain.

-Tim

---

### Post by albinootje on 2009-05-29
> **deekthesqueak said:**
> Can someone who has a Postfix/Dovecot/MySQL setup give me a couple of suggestions on how to test each different part to make sure everything is working?

Testing Dovecot : [http://wiki.dovecot.org/TestInstallation](http://wiki.dovecot.org/TestInstallation)
For the rest, check your log files, and also, for Dovecot you can even have a delivery log file.

---

### Post by deekthesqueak on 2009-05-29
> **windependence said:**
> That's not true. I have several running with more than one domain.

-Tim
Odd not the impression that I got. Either way I am moving forward with the Postfix/Dovecot/MySQL solution.

---

### Post by windependence on 2009-05-31
It would be a good idea if you have time to do the setup as you are planning, so that you understand how it all works. Then, if you need to deploy a mail server fast, give Zimbra a try and you will be familiar with the underlying components. I think it's very beneficial to do what you are doing so that you can see all that is involved in getting mail working. You will be better able to troubleshoot mail even in packages such as Zimbra.

-Tim

---

### Post by deekthesqueak on 2009-06-01
Has anyone setup this mail server using packages?  It seems lots of the configuration can be doing during setup or with a dpkg-reconfigure after install.  Plus there is now a .deb package for postfixadmin that seems to do all the database creation for you.  Has anyone played with this?  

I have that package (postfixadmin 2.3_rc5) installed on my server and my only question is what do I do from here as far as configuration to get virtual domains? If anyone has set up their server from packages instead of source I'd like to hear from them :)  If not it looks like it is my duty to get this working and write a guide!

---

### Post by Cheesemill on 2009-06-01
I've successfully used this guide

[http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)

To install a mail server hosting multiple domains on a Ubuntu Server 8.04 JeOS install (even though the guide is meant for Debian, it worked for me without any modifications).

Cheesemill


PS - But I substitute squirrelmail for roundcube, it's far better IMHO

PPS - I'm planning to rebuild my mail server on a Debian Lenny VM when the tutorial above is updated.

---

### Post by deekthesqueak on 2009-06-05
> **kustomjs said:**
> I am using dovecot/postfix/mysql/roundcube for my email server.

Did you use postfixadmin as well?  I have my postfix/dovecot/mysql/postfixadmin/spamassassin/clamav set up working great but I want to integrate roundcube into it now.  The patchset that postfixadmin points to is version 1.0.5 and works with and older version of roundcube (0.2) anyone know if it works on the latest version of roundcube (0.2.2)?

---

### Post by albinootje on 2009-06-05
> **Cheesemill said:**
>  PS - But I substitute squirrelmail for roundcube, it's far better IMHO

Why ? For what features is that ?
... Last time I tried RoundCube (0.1.x I think) I found it a pain to set up, but much more important : there was no next button and no email-window within or next to the inbox-tree window, you had to close down the popup email window before being able to -read- the next email. Pretty unusable behavior to give that to my users.

Back then I assumed that people only liked RoundCube for the eyecandy.. [..]

I just noticed that Jaunty has 0.2.1.x in the repositories (unfortunately it's not in Debian Etch or Debian Lenny), I'll give it a try again.
> 
PPS - I'm planning to rebuild my mail server on a Debian Lenny VM when the tutorial above is updated.

1) That howto is at least 1 year old, .. and why wait for an update ?
2) What would be so different between Etch and Lenny that you can't use the same howto ? I know that there's some important differences between various Dovecot versions, but that's all I can think of.

---

### Post by kustomjs on 2009-06-05
I did have postfixadmin but I have something different that manages my email server that can add,edit,delete email addresses (custom script) and I just got done setting up a custom script for email forwarding. and how I got roundcube on my mail server was: sudo apt-get install roundcube.

> **deekthesqueak said:**
> Did you use postfixadmin as well?  I have my postfix/dovecot/mysql/postfixadmin/spamassassin/clamav set up working great but I want to integrate roundcube into it now.  The patchset that postfixadmin points to is version 1.0.5 and works with and older version of roundcube (0.2) anyone know if it works on the latest version of roundcube (0.2.2)?

---

