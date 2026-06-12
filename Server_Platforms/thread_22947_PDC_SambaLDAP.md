---
title: "PDC Samba/LDAP"
date: 2005-03-30
forum: Server Platforms
---

### Post by nixn00b on 2005-03-30
Does anyone feel like posting up some sortof HowTo on setting up Ubuntu as a Windows PDC, using Samba and Ldap, it seems fairly simple to get it working with the straightforward Samba NT4 emulation, but as soon as the LDAP side kicks in, things get a little too crazy for my liking.

I've been trying to follow a few guides, such as idealx, and compiling all the apps from source, as could not seem to find equivalents in ubuntu repos, managed to compile LDAP, but unsure if the switches were correct, but after that, tried compiling APache, and things seemed to go wrong when applying the ldap switches in apache compilation.

Perhaps I'd be better off downloading the RPM's, and alien(ing) them, and follow the howto exactly?


Perhaps this is the wrong forum, but between the sticky here, and the sticky in the howtos section, both seem to say the same thing, 'post questions elsewhere'

---

### Post by garyng on 2005-03-30
you don't need to compile anything, they are in universe/multiverse if you cannot find in main.

However, Samba + LDAP is not an easy stuff, lots of things to setup and think about. The main advantage of Samba + LDAP is the backend replication of LDAP database which is needed for a large complex network. 

For small single server(or even a few local servers on the same LAN), I don't think the complexity pay.

There is a howto floating around, try samba's main site or google. I briefly tried it and the most difficult thing to me back then is the user/group management for LDAP(through samba).

---

### Post by [flax] on 2005-04-13
[QUOTE=garyng]
....
However, Samba + LDAP is not an easy stuff, lots of things to setup and think about. The main advantage of Samba + LDAP is the backend replication of LDAP database which is needed for a large complex network. 
....
[/QUOTE]
I am currently working on bashscript which -should- do this whole process for you on a ubuntu hoary system based upon a few basic questions (and a lot of pre-defined assumptions)

It is quite a mess at this moment, with some help, we could give it a new start
with the [Old Materials *caution not working*](http://nergens.org/projects/samba/) i crafted earlier.

Personally i think it would be great to offer a tool to configure Ubuntu in such a way that it can replace a NT 4 server with a few click, since the support is no longer provided on those servers

---

### Post by dorris on 2005-04-15
That would be real great to have, I gave the config a break, got busy wih the rest of life, hope to get back into resolving this matter soon, Am currently in a situation where I've had enough of useless payouts to microsoft, and uncompatible licenses, that I just want to throw everything onto Linux. But  there is just so many little quirks, and you really seem to have to have a solid knowledge, not only of SAMBA/Ldap, but also of windows networking.

Look forward to see the work, I stopped last week, after making some bum change that hung the whole system every time I got to the bringingup network section of Bootup.
Windows mentality started coming back to me at that point, so...
 I ended up mounting the drive in winbloze and editing the rcS to skip networking, once I managed to get back into Ubuntu, I then uninstalled everything to do with samba/ldap/nss, have to start over soon!

---

### Post by dataw0lf on 2005-04-15
[QUOTE='[flax]']I am currently working on bashscript which -should- do this whole process for you on a ubuntu hoary system based upon a few basic questions (and a lot of pre-defined assumptions)

It is quite a mess at this moment, with some help, we could give it a new start
with the [Old Materials *caution not working*](http://nergens.org/projects/samba/) i crafted earlier.

Personally i think it would be great to offer a tool to configure Ubuntu in such a way that it can replace a NT 4 server with a few click, since the support is no longer provided on those servers[/QUOTE]


This sounds like a good idea, but I hope you know the work involved (generating specific LDIF files, synchronization, etc).

---

### Post by adeh on 2005-04-20
Does anyone here have experience with just the PDC part? I ahve been looking for info about Samba PDC Samba 3.0.10 + WinXP SP 2 and the knowledge out there seems a little thin. We got one computer to join the domain, all the rest fail...

Just wondering what kind of success other people have had.

---

### Post by [flax] on 2005-04-20
[QUOTE=adeh]Does anyone here have experience with just the PDC part? I ahve been looking for info about Samba PDC Samba 3.0.10 + WinXP SP 2 and the knowledge out there seems a little thin. We got one computer to join the domain, all the rest fail...

Just wondering what kind of success other people have had.[/QUOTE]
The following url should tell you all steps:[http://samba.idealx.org/index.en.html](http://samba.idealx.org/index.en.html). 

You have to keep in mind that within Ubuntu can be a little bit different, but overall i think that you could use this document.

---

### Post by [flax] on 2005-07-01
Currently i have a new document (in dutch), with information about configurating hoary with samba and ldap: [http://nergens.org/projects/samba/Ubuntu%20Samba%20Server%20v.01.pdf](http://nergens.org/projects/samba/Ubuntu%20Samba%20Server%20v.01.pdf) (created by our training period cursor)
It misses the import of an existing windows domain server and the smb.conf settings (but they can be found looking in the information provided by idealx)

I hope that the document will be finished next week and that people can use the information(feedback is welcome :D )

---

### Post by tumma72 on 2006-03-06
I have followed carefully what is written in this small tutorial [http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap) and I got Breezy Badger working as a PDC (Active Directory) with Windows XP SP2 clients and Linux and MacOSX clients as well. All password including Linux and MacOSX are synchronized using OpenLDAP :-)

But you are absolutely right saying is not an easy staff ;-)

Ciao
Tumma

---

### Post by arkopII on 2006-05-03
[QUOTE=tumma72]I have followed carefully what is written in this small tutorial [http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap) and I got Breezy Badger working as a PDC (Active Directory) with Windows XP SP2 clients and Linux and MacOSX clients as well. All password including Linux and MacOSX are synchronized using OpenLDAP :-)

But you are absolutely right saying is not an easy staff ;-)

Ciao
Tumma[/QUOTE]

Hi, I have followed this tutorial and after the step when "fred" user is created I try to test it and get this failure.
```

root@localhost:/# smbclient -L localhost --user fred
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```

Did this happen to you? May you share a basic smb.conf?

Thank you very much.

---

### Post by sus on 2006-05-06
I have also followed that tutorial with limited luck - i can login from a client using ssh but when i try and login via GDM i get "cannot set your user group; you will not be able to login".   Any ideas?

---

### Post by sus on 2006-05-06
[QUOTE=sus]I have also followed that tutorial with limited luck - i can login from a client using ssh but when i try and login via GDM i get "cannot set your user group; you will not be able to login".   Any ideas?[/QUOTE]

opps - sorted. Just needed to restart GDM.  :oops:

---

### Post by jferrando on 2006-05-11
Hi,
I have this setup running in a Debian/etch box some time ago. You can see my notes in:

[]("http://http://www.intransys.com/linux/Debian/ldap_samba/ldap.odt")

Also there is a lot of ours in my personal experience running a linux server in a small firm in

[http://www.intransys.com/linux]("http://www.intransys.com/linux")

I have pasted the documents from my server. Please mail me if you see any security concern for my server in this notes, I have not browsed through them, so maybe I should remove something.

Good luck.

---

### Post by jferrando on 2006-05-11
Sorry for the link,
[]("http://www.intransys.com/linux/Debian/ldap_samba/ldap.odt")

---

### Post by lramos85 on 2006-10-15
I am working on this HowTo, It is still not finished as of Oct 15 2006, but here it is for when it is finished. It works perfectly for our network and it currently manages around 40 Accounts. We haven't tested it for a bigger number. But it works great with our Raid Servers with Ubuntu and everything. Hope it helps.:D 

[https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29)

---

### Post by cajetanus on 2006-10-17
I have tried to use this tutorial:

[https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29)

However, I can never get the LDAP database to actually import the data. The server works, I can connect to it, even do a ldapsearch, but can't add anything to it. Server refuses to add records, or tells me that the container doesn't yet exist (and phpldapadmin can't even create it). I've tried to modify the ACL so that all could write, no go. LDAP is probably the most obtuse piece of software that I have ever seen.

Searching the ldapguru forums didn't help much, except for consoling me with the fact that many others are having exactly the same problems with no solutions.

LDAP is an absolute PITA. Certainly there must be some other way to do this than using LDAP.

Can this be done just using the /etc/passwd file? But how can PAM authenticate against the passwd file on another computer? I would like the users to have all their settings and their home folder on the server.

LDAP would be nice if it only worked. But even getting it to work doesn't guarantee that it will actually store any data (so far it won't accept anything).

signed,
=== one frustrated administrator ====

---

### Post by Chayak on 2006-10-18
There has to be a better way than slugging though all of the configs.  I have to support quite a few servers and even for setup things need to be as streamlined as possible because time adds up and manhours spent on problems and setup needs to be minimized.  It would REALLY be nice if there was an install option for a domain controller similar to what they have setup for LAMP.

---

### Post by bluefrog on 2006-10-19
I have been faced to the same problem some time ago.

After numerous manual installs, I have written a menu driven bash script that automates most of the samba-ldap setup.

I will make it available on my website in a few days.

**There will be warnings in big this script is not for unexperienced user and to be run ONLY on a fresh install.**

I know what needs to be changed, no need to tell me.

What I would like ppl to tell me is HOW to change it as my scripting knowledge is far from being good.

The ideal thing would be to have a knowledgable guy/girl willing to transform it in a meta-package for example...

James

---

### Post by hortimech on 2006-10-24
I dont know how tell you this but, you are reinventing the wheel here, try googling on smbldap-installer, fresh install to pdc server in about 5mins:)

---

### Post by bluefrog on 2006-10-25
Far from me to argue forever about scripts and so on but...
I made my script quite sometimes ago (beginning of breezy) for myself as I was not pleased with things I could find.
My script enables me to semi automate/automate samba-ldap, bind, ltsp, postfix/clamav/spamassin/quota and more (on Dapper only, I don't care about other distro).

Difference with what I read from the smbldap-installer you recommend:
I only use deb files from ubuntu repository (main/universe and maybe multiverse for 1 or 2 files). So there is no fiddling with perl -MCPAN -e –shell and smbldap-tools is coming from the repo as well (well yes I will not have the latest but I don't care).

Regarding smbldap-tools, by default the first added smbldap user (root/administrator) will have uid=1000 BUT Ubuntu is setting the install created user with 1000 as well, the interaction of both gives some strange results. The problem doesn't exist on FC as the first user has a UID < 1000 (if I remember well).
So, to get rid of that annoyance my script change the uid=1000 to uid=3000 in the smbldap.pm file.(why 3000? well, why not...)
this is coming from 2 * $uid + 1000 (if not mistaken) in smbldap_tools.pm

I do not recommend anyone to use any script (and so far I still wonder if I am going to put mine online even if I can get some time to do so..) especially if they haven't done anything work by hand themselves before.

In my mind, using no cost softwares shouldn't let people think they don't need to pay IT specialists to set up/maintain their network (am talking mainly about small companies here of course not about user lambda who is playing at home with his favorites linux distribution).

James

---

### Post by hortimech on 2006-10-25
> **bluefrog said:**
> Far from me to argue forever about scripts and so on but...

Difference with what I read from the smbldap-installer you recommend:
I only use deb files from ubuntu repository (main/universe and maybe multiverse for 1 or 2 files). So there is no fiddling with perl -MCPAN -e –shell and smbldap-tools is coming from the repo as well (well yes I will not have the latest but I don't care).


The main problem with setting up LDAP/SAMBA is getting all the software required, running the smbldap-installer script automates this.

> **bluefrog said:**
> 
Regarding smbldap-tools, by default the first added smbldap user (root/administrator) will have uid=1000 BUT Ubuntu is setting the install created user with 1000 as well, the interaction of both gives some strange results. The problem doesn't exist on FC as the first user has a UID < 1000 (if I remember well).
So, to get rid of that annoyance my script change the uid=1000 to uid=3000 in the smbldap.pm file.(why 3000? well, why not...)
this is coming from 2 * $uid + 1000 (if not mistaken) in smbldap_tools.pm


I used the script on the server version which I installed as an expert purely to get root to log in, but I take your point and will check the UID of root.

> **bluefrog said:**
> 
I do not recommend anyone to use any script (and so far I still wonder if I am going to put mine online even if I can get some time to do so..) especially if they haven't done anything work by hand themselves before.


If like me, you tried to setup to ldap/samba by following various howto's and googling the net, you learn how to do it, but it is quicker just to run the script.
 
> **bluefrog said:**
> 
In my mind, using no cost softwares shouldn't let people think they don't need to pay IT specialists to set up/maintain their network (am talking mainly about small companies here of course not about user lambda who is playing at home with his favorites linux distribution).

James

some people cannot afford to pay IT costs and yet still need to use IT.

---

### Post by lonetree on 2006-11-03
> **'[flax] said:**
> Currently i have a new document (in dutch), with information about configurating hoary with samba and ldap: [http://nergens.org/projects/samba/Ubuntu%20Samba%20Server%20v.01.pdf](http://nergens.org/projects/samba/Ubuntu%20Samba%20Server%20v.01.pdf) (created by our training period cursor)
It misses the import of an existing windows domain server and the smb.conf settings (but they can be found looking in the information provided by idealx)

I hope that the document will be finished next week and that people can use the information(feedback is welcome :D )

Is there an english version for this tutorial?

---

