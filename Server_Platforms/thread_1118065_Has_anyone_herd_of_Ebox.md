---
title: "Has anyone herd of Ebox"
date: 2009-04-06
forum: Server Platforms
---

### Post by balloooza on 2009-04-06
I am sure the developers at ebox would like more users, so have you herd of ebox, like the quesstion asks.

also try to keep posting, so the thread stays up in the top, if you reply to the poll NO, then ask more about it

A quick description of Ebox.
Ebox is a web administration platform, not utility.
Ebox runs on Ubuntu, it is a package, and is accessed through the repositorys on this page
[http://ebox-platform.com/community/installation-guide/](http://ebox-platform.com/community/installation-guide/)

or, installed using a modified Ubuntu installer, so it is up and running right away.

The great thing about it is that it automagicly configures things, unlike webmin, is that, first the settings are allot more straight forward, and when you want to, lets say setup an email server, you just click what secureity to use, weather pop or imap, and you are done, and all the users are managed through a centeral system so the same login works for a samba file sharing login, and also for a jabber server login.

It also has built in support for egroupware, and uses the same accounts with the rest of the system, egroupware supports a webmail, file uploader, calender and address book, and more (but not that interesting) features

screenshots I made of my server
[http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79](http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79)

web site
[http://ebox-platform.com/](http://ebox-platform.com/)

Sorry for sounding like an annoying geeked up TV shoping add, but I just want to spread the name of Ebox out

---

### Post by kjurkic on 2009-04-06
I have tried a few versions (last autumn) and found myself very frustrated with installation glitches. While ebox purports to be for the inexperienced/newbie admin, trying to perform certain tasks beyond the basics quickly became an exercise in frustration and required command-line magic beyond my skills; I encountered issues with trying to use ebox to act as a central authentication server (with LDAP). I was not attempting anything outside of a vanilla login/Samba server, and could net get a functioning combo. 

There was no easy way (that I could find) to extend the default LDAP schema beyond username/password.

It showed promise, and I may take another run at it if there is a recent update.

regards
Ken

---

### Post by balloooza on 2009-04-06
Yea, Ebox is dumbed down a bit, but if you need an ldap server, look at other tools to work with ebox, because that is not somthing ebox supports.

Try version 1.0 (released about 15 days ago)

---

### Post by Mouth on 2009-04-07
Just finished having to rebuild my server, and in doing so I thought I'd take the opportunity to do it again from scratch and revisit a lot of teh server daemons and management tools I've bene using to see if they are still the best.

I took a look at the eBox website and it looked promising, even if I was slightly confused that it initially appears that it is/was only available as a .ISO.

Went to do an apt-get install to try it, and 'borked' immediately ...the number of packages required was HUUUUUGE, and I certainly don't want postgresql (i want/use mysql). Stopped there and went no further.

Pity, it looked like it had the potential.

---

### Post by ugm6hr on 2009-04-07
I only fiddled with it briefly, but found it was a bit too full-featured (and therefore confusing) for my home server purposes.

It certainly looks like it is useful for enterprise use, and appears to be the Ubuntu equivalent of ClarkConnect.

---

### Post by Iowan on 2009-04-08
The [webmin]("https://help.ubuntu.com/community/WebMin") help page on help.ubuntu.com suggests ebox as a replacement, but the [ebox]("https://help.ubuntu.com/community/eBox") help pages suggest that the *.10 versions were/are broken.

---

### Post by MikeyPooh on 2009-04-08
I Use Ebox to to Admin My Ubuntu server

I Find that if you add the Launchpad repo for intrepid it installs flawlessly.

I Can setup my Dhcp and Samba through Ebox in 5 mins;)

Wouldnt use anything else 

Mike

---

### Post by eseven73 on 2009-04-15
Someone wake me when there's a version 1.0 for Intrepid or Jaunty, according to their site: "You can install the new packages using our stable repository. Note that the new packages are only available for Ubuntu Hardy at the moment. Packages for Intrepid and Jaunty are underway."

Until then, I guess I'll hang with Webmin
:'(

---

### Post by balloooza on 2009-04-15
eseven73, this is not an issue, the "testing" repositorys are quite stable, I would recomend sticking on intrepid for the server, and use the ebox web interface.

---

### Post by lumberjackshaw on 2009-05-06
Having now "played" ebox I feel that is really has a long way to go before it finds itself on one of my servers again. 

The install is smooth.  Each module is self configured.  You will have full server running in no time with the use of ebox.  The admin panel is limited but if you aren't doing anything fancy if works just fine.

On the downside to accomplish all of the above the ebox software re-scripts the processes that it effects.  For example ntp is scripted through ebox to allow ebox control.  Your slapd config is routed through the ebox scripts.  Your current ldap database is backed up and a new one is created for you.  You will not know the admin password(unless you use the password file in the ebox vars), your dc will be ebox.  Without hacking the ebox scripts this is your only option.  There are no attempts be ebox to use your current config.  With all of the mods you pretty much give up your right to administer any server handed over to ebox.

If you install the software a do not decide in its favor uninstall is not clean.  The software removes all of the scripts it put in place without update all of the files that now point to them.  You are left with 2 options: spend hours finding the villainous scripts or start clean.

That being all said I think the ebox module has great potential.  I hope they can continue to develop the project to allow more features and flexibility.  They need to incorporate more of the current config into their changes, otherwise the software will work for new installs only. They need to clean up their changes to the system to make regular system admin more mainstream and create a smoother removal process.

---

### Post by Imortallis on 2009-05-06
I have never heard of Ebox...could it be used as some sort of webserver/http?
 
Although, after reading some of the comments posted, I think that I may stay with Apache...

---

### Post by lavinog on 2009-05-11
I looked but never tried it.
I have used webmin in the past, but I still prefer the to be in control.
My concern is that if I install ebox, I wont be able to manage my system with ssh.
On the other hand, my phone has web support and no ssh. It might be handy to be able to manage my server via cellphone.

---

