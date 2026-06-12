---
title: "SSH via the web"
date: 2005-04-11
forum: The Cafe
---

### Post by earobinson on 2005-04-11
is there any website that will let me ssh connect to my computer? i want to be able to get on any windows box go to a site and ssh onto my computer without installing any softwair.

Thanks

earobinson

---

### Post by Nis on 2005-04-11
[QUOTE=earobinson]is there any website that will let me ssh connect to my computer? i want to be able to get on any windows box go to a site and ssh onto my computer without installing any softwair.

Thanks

earobinson[/QUOTE]
 [This](http://www.oit.duke.edu/sa/security/ssh.html) is exactly what you're looking for.  Java ssh client that runs over the web. :)

---

### Post by heimo on 2005-04-11
Putty
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
doesn't need to be installed. At ~400KB it's also easy to download when needed (or put it on floppy/USB memory stick).

---

### Post by earobinson on 2005-04-11
[QUOTE=Nis][This](http://www.oit.duke.edu/sa/security/ssh.html) is exactly what you're looking for.  Java ssh client that runs over the web. :)[/QUOTE]
 this dont seem to work, i try connecting to my computer the way i would in ssh and it wont connect, did it work for u? do you do anyhting diferent? and i want to be able to use this at the libary and such where i cant put a disk in. thanks.

---

### Post by earobinson on 2005-04-13
no one has an answer to this?

---

### Post by heimo on 2005-04-13
I haven't tried, but there's SSH Login module for Webmin, requires Java on client side.

---

### Post by earobinson on 2005-04-14
[QUOTE=heimo]I haven't tried, but there's SSH Login module for Webmin, requires Java on client side.[/QUOTE]
 what website?

---

### Post by heimo on 2005-04-14
It's not a website - so it's probably not what you're looking for. But it's a module that can be used with webmin (which is available in Ubuntu) and it can be used to create web-based ssh connection to your server. Idea is that you install the webmin with this module to the server you want to control and use web browser to connect (easier to get around firewalls and makes it possible to administer server without having to install ssh on client side).

[http://www.webmin.com/]("http://www.webmin.com/")

---

### Post by earobinson on 2005-04-16
[QUOTE=heimo]It's not a website - so it's probably not what you're looking for. But it's a module that can be used with webmin (which is available in Ubuntu) and it can be used to create web-based ssh connection to your server. Idea is that you install the webmin with this module to the server you want to control and use web browser to connect (easier to get around firewalls and makes it possible to administer server without having to install ssh on client side).

[http://www.webmin.com/]("http://www.webmin.com/")[/QUOTE]
 no not what im looking for, i want to be able to use a windows box with IE and without downloading a thing be able to ssh to my computer, some one has to have this. I have the webspace so if u write it ill host it.

---

### Post by jdong on 2005-04-16
If you search "Mindterm" on google, you can find *plenty* of sites that offer this applet without a download.


---A paranoid view---

 But, however, would you *trust* them? Even if someone here offers to host the applet, how do you know he's not logging everyone's logins/passwords? When you're dealing with an open-source Java applet, that's quite easy to do!


You're better off getting a Putty client wherever you go, since that way you have a bit more assurance it's legit.

---

### Post by earobinson on 2005-04-17
[QUOTE=jdong]If you search "Mindterm" on google, you can find *plenty* of sites that offer this applet without a download.


---A paranoid view---

 But, however, would you *trust* them? Even if someone here offers to host the applet, how do you know he's not logging everyone's logins/passwords? When you're dealing with an open-source Java applet, that's quite easy to do!


You're better off getting a Putty client wherever you go, since that way you have a bit more assurance it's legit.[/QUOTE]
 cant find one that works at all :(

---

### Post by jdong on 2005-04-17
Mindterm simply sucks with SSH2. Don't use it :)

---

### Post by earobinson on 2005-04-19
[QUOTE=jdong]If you search "Mindterm" on google, you can find *plenty* of sites that offer this applet without a download.


---A paranoid view---

 But, however, would you *trust* them? Even if someone here offers to host the applet, how do you know he's not logging everyone's logins/passwords? When you're dealing with an open-source Java applet, that's quite easy to do!


You're better off getting a Putty client wherever you go, since that way you have a bit more assurance it's legit.[/QUOTE]
 i have tried a few and got nothing maybe im doing it wrong, but if to ssh into my computer i use the command ssh [email]earobinson@computername.com[/email] then in mindterm shouldent i just use [email]earobinson@computername.com[/email], cuz thats not working at all.

---

### Post by jdong on 2005-04-19
No, just computer hostname. It prompts for a username later on.

---

### Post by earobinson on 2005-04-20
[QUOTE=jdong]No, just computer hostname. It prompts for a username later on.[/QUOTE]
 still habing lots of problems any idea when i can get a tutorial on it?

---

### Post by speedman on 2005-04-20
This applet works well (we have it on several systems) even though it is a little bloated:

[http://prdownloads.sourceforge.net/sshtools/SSHTerm-0.2.2-applet-signed.tar.gz?download](http://prdownloads.sourceforge.net/sshtools/SSHTerm-0.2.2-applet-signed.tar.gz?download)


Regards,

SM

---

### Post by thoms on 2005-04-20
This is something I've been interested in for awhile now too, espescially as I'm often at college where I can't download, install or even run programs and often need to SSH from windows to Linux. 

If we can compile a decent amount of info in here, I'm willing to build a HOWTO/wiki thing.

---

### Post by earobinson on 2005-04-23
[QUOTE=thoms]This is something I've been interested in for awhile now too, espescially as I'm often at college where I can't download, install or even run programs and often need to SSH from windows to Linux. 

If we can compile a decent amount of info in here, I'm willing to build a HOWTO/wiki thing.[/QUOTE]
 that would be perfect

---

