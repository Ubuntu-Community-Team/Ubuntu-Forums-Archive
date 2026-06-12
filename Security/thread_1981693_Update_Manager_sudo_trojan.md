---
title: "Update Manager sudo trojan"
date: 2012-05-17
forum: Security
---

### Post by AlanQ on 2012-05-17
sudo TWICE in Update Manager?

Last night ~00:00UTC 2012-05-17 I had one item on Update Manager.

I clicked 'Check' just in case there were others. There were. I then absent mindedly clicked 'Install Updates' without checking the list first.

When it had finished, I noticed in the by now greyed-out list, two entries for **sudo**. One had a checkbox, as normal, but one had no checkbox -- ie no option not to choose it. They were:

```

   checkbox  sudo  allow elevation to superuser by user
no checkbox  sudo  allow elevation to superuser by **specranch**

```

I can't remember the usual descriptive wording, but the *specranch* bit is as it was.

Have I somehow allowed in a trojan? Or in some other way been cracked?

Is it ever the case for an item in update to be un-tickable?

Apart from sources and signing keys for Ubuntu Lucid,
my other sources (with signing keys) are:
```
Ubuntu Lucid partner
Virtualbox (Oracle)
Scribus (debian archive)
```

Can anyone put my mind at rest?
Thanks
Alan

---

### Post by 3spartan on 2012-05-17
I arrived on this site doing a search also concerned about an update that referred to SUDO.  Just got my normal periodic update Ubuntu thingy and updated it without thinking twice, noticed the update referred to SUDO then thought "wonder if I've just compromised my system, better check it out."

---

### Post by Delfairen on 2012-05-17
From what I can see this (on Mint mind you not Ubuntu) there is a fix to sudo

[http://packetstormsecurity.org/files/112780/USN-1442-1.txt](http://packetstormsecurity.org/files/112780/USN-1442-1.txt)

---

### Post by AlanQ on 2012-05-17
Thank you, Delfairen

Your link contains a link to a link to here
[Ubuntu Security Notice USN-1442-1]("http://www.ubuntu.com/usn/usn-1442-1/")

That would explain a sudo update last night.

And it's a step towards a positive resolution to this conundrum.

Still doesn't explain why I had TWO entries in the update list for sudo, and the second strange one was un-tickable. Just one, with a tick-box, and I wouldn't be worried.

Maybe the second one was for sudo-ldap ...?

Has anyone else ever noticed an entry in Update Manager with no tick-box, ie no option to un-select it?

---

### Post by 3spartan on 2012-05-17
Found my dpkg.log file, assume what's below to be normal and the update referred to by poster above?

2012-05-17 14:43:14 startup archives unpack
2012-05-17 14:43:22 upgrade sudo 1.7.2p1-1ubuntu5.3 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:22 status half-configured sudo 1.7.2p1-1ubuntu5.3
2012-05-17 14:43:22 status unpacked sudo 1.7.2p1-1ubuntu5.3
2012-05-17 14:43:22 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 14:43:22 status triggers-pending man-db 2.5.7-2ubuntu1
2012-05-17 14:43:22 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 14:43:24 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 14:43:24 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:24 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:25 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2012-05-17 14:43:25 status half-configured man-db 2.5.7-2ubuntu1
2012-05-17 14:43:29 status installed man-db 2.5.7-2ubuntu1
2012-05-17 14:43:30 startup packages configure
2012-05-17 14:43:30 configure sudo 1.7.2p1-1ubuntu5.4 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:30 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:30 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:30 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:30 status half-configured sudo 1.7.2p1-1ubuntu5.4
2012-05-17 14:43:31 status installed sudo 1.7.2p1-1ubuntu5.4

---

### Post by cryptotheslow on 2012-05-17
I'm only seeing one entry for sudo in Update Manager and running a simulated apt-get upgrade only seems to pull down one package.

```
crypto@ubulaptop1204:~$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst sudo [1.8.3p1-1ubuntu3.1] (1.8.3p1-1ubuntu3.2 Ubuntu:12.04/precise-updates [amd64])
Conf sudo (1.8.3p1-1ubuntu3.2 Ubuntu:12.04/precise-updates [amd64])
crypto@ubulaptop1204:~$

```


I'm holding off updating it for now as the changelog is not yet available:
```

crypto@ubulaptop1204:/var/log/apt$ sudo apt-get changelog sudo
Err Changelog for sudo (http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.8.3p1-1ubuntu3.2/changelog)
  404  Not Found
Err Changelog for sudo (http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.8.3p1-1ubuntu3.2.changelog)
  404  Not Found [IP: 91.189.92.176 80]
E: changelog for this version is not (yet) available; try https://launchpad.net/ubuntu/+source/sudo/+changelog

```

---

### Post by AlanQ on 2012-05-17
My dpkg.log for sudo last night is:

```
alan@cube:/var/log$ cat dpkg.log | grep sudo
2012-05-17 01:52:20 upgrade sudo 1.7.2p1-1ubuntu5.3 1.7.2p1-1ubuntu5.4
2012-05-17 01:52:20 status half-configured sudo 1.7.2p1-1ubuntu5.3
2012-05-17 01:52:21 status unpacked sudo 1.7.2p1-1ubuntu5.3
2012-05-17 01:52:21 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 01:52:21 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 01:52:21 status half-installed sudo 1.7.2p1-1ubuntu5.3
2012-05-17 01:52:21 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:52:21 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 configure sudo 1.7.2p1-1ubuntu5.4 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 status unpacked sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 status half-configured sudo 1.7.2p1-1ubuntu5.4
2012-05-17 01:53:14 status installed sudo 1.7.2p1-1ubuntu5.4
alan@cube:/var/log$ 
```

Interestingly, as for 3spartan, there are two sudo:
1.7.2p1-1ubuntu5.3
and
1.7.2p1-1ubuntu5.4

Two updates because 4 followed hot on the heels of 3 and updates must be contiguous?

This would explain version 3 having no check box, as it's essential before version 4.

dpkg.log timestamp is correct.

Of course, if well crafted, a trojan would cover its tracks and delete entries for logs and change timestamps, etc. And I still haven't got to the bottom of  *specranch*. But I'm feeling a bit better. Thanks to all for replies.

---

### Post by wilee-nilee on 2012-05-17
> **AlanQ said:**
> Thank you, Delfairen

Your link contains a link to a link to here
[Ubuntu Security Notice USN-1442-1]("http://www.ubuntu.com/usn/usn-1442-1/")

That would explain a sudo update last night.

And it's a step towards a positive resolution to this conundrum.

Still doesn't explain why I had TWO entries in the update list for sudo, and the second strange one was un-tickable. Just one, with a tick-box, and I wouldn't be worried.

Maybe the second one was for sudo-ldap ...?

Has anyone else ever noticed an entry in Update Manager with no tick-box, ie no option to un-select it?

A untickable in the update manager can mean two things basically, one it is a partial upgrade, which basically should not be run, as it may mean that the repo does not have all the dependencies, they don't all come from the same teams. Or that you just need to run the manager again as a update, to clear out any now available. With a partitial, generally it will get the dependecies so a wait is advised.

The standard ubuntu repositories are very safe, I understand your concern here, but it is from a windows stand point. There are no known trojans on the web for a linux setup.  You are fine in what you saw in the update manager, but it never hurts to want to understand. :smile:

It really also is partially a definition of what a trojan is and rootkits as well and malware, so check out this area of the forums for more information. These definitions are a bit different in how these play out in a windows system compared to  linux, or bsd, or apple setup, apple is basically bsd as well.

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Some of your best protection is strong passwords, and being extremely careful with any third party repos or downloads. Really the same as a widows set up as far as an informed user.

---

### Post by AlanQ on 2012-05-18
Thank you, wilee-nilee

> A untickable in the update manager can mean two things basically, one it is a partial upgrade, which basically should not be run, as it may mean that the repo does not have all the dependencies, they don't all come from the same teams. Or that you just need to run the manager again as a update, to clear out any now available. With a partitial, generally it will get the dependecies so a wait is advised.

But what about the duplication? Why did I have two sudo with slightly different descriptions?

> The standard ubuntu repositories are very safe, I understand your concern here, but it is from a windows stand point. There are no known trojans on the web for a linux setup.

So what would happen if the Ubuntu repositories were cracked and a trojan added for download?

> It really also is partially a definition of what a trojan is and rootkits as well and malware, so check out this area of the forums for more information. These definitions are a bit different in how these play out in a windows system compared to linux, or bsd, or apple setup, apple is basically bsd as well.

As I understand it, a trojan is malicious code that the user puts on his/her computer knowing that it's software, thinking that it's wanted/needed, but not knowing that it's harmful.

> Some of your best protection is strong passwords, and being extremely careful with any third party repos or downloads. Really the same as a widows set up as far as an informed user.

Third party repos are a concern. But I'm hoping Oracle and Scribus are at least the same order of magnitude as safe as Ubuntu...

---

### Post by computeratin on 2012-05-18
> **AlanQ said:**
> ...So what would happen if the Ubuntu repositories were cracked and a trojan added for download?...
 
Hopefully it would be discovered and corrected quickly. But, unfortunately it's not completely outside the realm of possibilty.
 
There was an incident many years ago that occured with the MS driver database.
 
Back in the day of Win95/98 MS maintained a special, seperate database where you could DL ~100k drivers. One of the vendors got hacked and didn't even know it. A trojan was implanted in their driver. They uploaded it to the data base.
 
Fortunately it wasn't one of the big players in the hardware market. But, IIRC ~10k machines were infected before everybody figured out what was going on.

---

### Post by wilee-nilee on 2012-05-18
> But what about the duplication? Why did I have two sudo with slightly different descriptions?Not sure you would have to look up packages of that set up and dependencies I suspect.


> So what would happen if the Ubuntu repositories were cracked and a trojan added for download?Nothing I believe gets put in the repos without being approved. This is with being able to look at all the code, since this is open source, hard to say how much is looked at though I would not know really. Actually the user a IT pro, that runs the IRC freenode channel ##windows in a conversation with me said he thought that the ubuntu repos and the gpt key setup with open source were extremely safe, and wished others would follow this lead.

> As I understand it, a trojan is malicious code that the user puts on his/her computer knowing that it's software, thinking that it's wanted/needed, but not knowing that it's harmful.Certainly possible, but to endanger linux it has to be in a code that runs in it and have root access, I suppose this just part of being safe. The definition of a trojan though is sort of broad, none of this though is an area of expertise for me really. A popup like is seen your infected click here, would nut run in linux unless written for it, and none is known to be on the web.

> Third party repos are a concern. But I'm hoping Oracle and Scribus are at least the same order of magnitude as safe as Ubuntu...I suspect they are oracle has a lot of money, and wants to keep its market hold, letting security be a problem would be a bad business move.

---

### Post by CharlesA on 2012-05-18
The only update to sudo I have had was this one:

```
charles@Thor:/var/log/unattended-upgrades$ cat unattended-upgrades-dpkg_2012-05-17_06\:39\:41.220505.log
(Reading database ... 98896 files and directories currently installed.)
Preparing to replace sudo 1.8.3p1-1ubuntu3.1 (using .../sudo_1.8.3p1-1ubuntu3.2_amd64.deb) ...
Unpacking replacement sudo ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up sudo (1.8.3p1-1ubuntu3.2) ...
```

---

### Post by OpSecShellshock on 2012-05-19
For what it's worth, on the system that I use and update every day I had updates to Sudo two days in a row earlier in the week. However, on the system that I use and update less frequently there was only one. It's possible, though I wasn't really keeping track, that the earlier update addressed one thing but caused unforeseen breakages elsewhere, which were then addressed immediately. That happens from time to time with other packages, and is far, far more likely than the introduction of a trojan package to the repositories.

---

### Post by rookcifer on 2012-05-19
> **AlanQ said:**
> Have I somehow allowed in a trojan? Or in some other way been cracked?

No.  It would be nearly impossible for that to happen since Ubuntu packages are digitally signed.

---

### Post by AlanQ on 2012-05-21
Thanks again, wilee-nilee

> **OpSecShellshock said:**
> For what it's worth, on the system that I use and update every day I had updates to Sudo two days in a row earlier in the week...

That's good to know.

> **rookcifer said:**
> No.  It would be nearly impossible for that to happen since Ubuntu packages are digitally signed.

Ah, yes. I hadn't thought of that. They'd have to crack both the package server and the signature server.

Still nothing relevant when I search on Ubuntu news. So I guess all is well...

Thanks to all who have posted ideas, info, suggestions, answered my questions, etc.

---

### Post by rookcifer on 2012-05-21
> **AlanQ said:**
> Thanks again, wilee-nilee



That's good to know.



Ah, yes. I hadn't thought of that. They'd have to crack both the package server and the signature server.

No, they'd have to go further than that.  They'd have to steal the private key of the Ubuntu maintainers, which would mean hacking their machine and somehow brute-forcing the key's password.  That is, if the Ubuntu developers even keep the key on an Internet connected machine in the first place.

There have been instances where Linux distro repositories have been breached and where rogue packages have been uploaded (it happened to Fedora at least once).  However, those packages were always caught because they failed signature verification.  An attacker would have to actually steal the signing private key to make the attack go unnoticed.  While not impossible, it would be very very difficult if the maintainers were careful about protecting the private key.

So, basically, if the suspicious updates you are talkimg about passed signature verification, they are legit updates.

---

### Post by AlanQ on 2012-05-21
Even better :)

---

### Post by bohemian9485 on 2012-05-22
> **rookcifer said:**
> No, they'd have to go further than that.  They'd have to steal the private key of the Ubuntu maintainers, which would mean hacking their machine and somehow brute-forcing the key's password.  That is, if the Ubuntu developers even keep the key on an Internet connected machine in the first place.

There have been instances where Linux distro repositories have been breached and where rogue packages have been uploaded (it happened to Fedora at least once).  However, those packages were always caught because they failed signature verification.  An attacker would have to actually steal the signing private key to make the attack go unnoticed.  While not impossible, it would be very very difficult if the maintainers were careful about protecting the private key.

So, basically, if the suspicious updates you are talkimg about passed signature verification, they are legit updates.

+1 for Linux :guitar:

---

