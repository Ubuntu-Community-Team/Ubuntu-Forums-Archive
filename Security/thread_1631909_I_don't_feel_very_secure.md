---
title: "I don't feel very secure"
date: 2010-11-27
forum: Security
---

### Post by reddae on 2010-11-27
I have been off and on with Ubuntu for a few years now. I have again decided to get back to it and I am currently focusing on the security of my system. Going from the tutorials and information on the forums I currently have these installed:

OSSEC
Tiger Security Scanner
ClamAV
PortSentry
LogCheck
chkrootkit

I also have ufw active ang gufw to manage it.

I am concerned though because the output file i got from the tiger scanner is HUGE! It has a lot of  listings such as:

***WARN*** [pass014w]Login (backup) is disabled, but has a valid shell.

and a ton of:

***WARN*** [fsys013w]cannot access /usr/share/omf/office/office-ug.omf is a           dangling symlink.

type entries. The size of that file mixed with my limited knowledge on the use of portsentry and logcheck make me feel a little uneasy about the security of my system.

I used this tutorial to harden the installation once and it just stopped my computer from booting up.
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

---

### Post by halloween2311 on 2010-11-27
Tiger is a great reference tool but it will give you a lot of false positives.

Have you checked out Bhodi.Zazen's intro thread to Ubuntu Security?
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

You may also want to check the tiger man page:
[http://www.penguin-soft.com/penguin/man/8/tiger.html](http://www.penguin-soft.com/penguin/man/8/tiger.html)

When all else fails I recommend following the advice from Hitchikers Guide to the Galaxy - Don't Panic! :-)

---

### Post by reddae on 2010-11-27
Yeah, that is the thread I followed to get ossec. I also used it get get the profiles and activate apparmor. Forgot to list that one though.

I will try not to panic. If someone hacks my computer and steals a copy of college papers I think the world will keep turning.

---

### Post by halloween2311 on 2010-11-27
The advice I received after I first panicked after running tiger was to set aside the WARN messages and concentrate on the FAIL messages.

Do you have many fail messages?

---

### Post by reddae on 2010-11-27
***FAIL*** [lin016f]The system permits source routing from incoming packets

***FAIL*** [dev002f]/dev/fuse has world permissions

***FAIL*** [dev002f]/dev/rfkill has world permissions

***FAIL*** [logf005f]Log file /var/log/btmp permission should be 660 <== Pretty sure I can just chmod this one

***FAIL*** [ssh005w]Cannot find a configuration file for SSH.

***FAIL*** [netw020f]There is no /etc/ftpusers file

---

### Post by halloween2311 on 2010-11-27
OK - first a warning that I am no expert.:-)

What I did with each of my FAIL messages was to copy them into Google and do a search for each one.  I was able to find out tips for each specific FAIL message and how to fix and/or ignore.

It was time consuming but worked fairly well for me when combined with the tiger man page.

Hope this helps!

---

### Post by reddae on 2010-11-27
Yeah I have been googling since I found the "fail" entries. I appreciate the help.

---

### Post by CharlesA on 2010-11-27
Most of those utilities will throw up false positives.

Why do you think you need to run them?

---

### Post by reddae on 2010-11-27
Paranoia is probably a big part of it. I like to feel secure and having several utilites that give me a general sense of well being just makes me feel better. I am sure some of them are redundant since I am not running any servers from my computer and I don't have a lot of heavy traffic coming through it.

---

### Post by OpSecShellshock on 2010-11-27
I have to apologize for the actions of a large number of people in my profession. It's just that there's so much more money to be made engendering the feeling of security than there is in the identification and management of actual risk...

The best thing you can do is to take the time to learn what's normal and expected. There aren't really any shortcuts to that, but if you can do it then anomalies will stand out starkly.

---

### Post by CharlesA on 2010-11-27
If you aren't running any servers, you shouldn't really have to worry about it as there are no services listening on external interfaces by default in Ubuntu.

You can enable Remote Desktop, which uses VNC, but I would suggest not bothering with it and removing it from the start up applications menu.

If you are just browsing the web, look into NoScript and AppArmor.

Also:

> **OpSecShellshock said:**
> The best thing you can do is to take the time to learn what's normal and expected. There aren't really any shortcuts to that, but if you can do it then anomalies will stand out starkly.

Huge +1 to that.

---

### Post by SeijiSensei on 2010-11-29
> **reddae said:**
> ***FAIL*** [lin016f]The system permits source routing from incoming packets

Is the machine exposed to the outside?  Is someone on your local network likely to possess the knowledge to exploit source routing?

> ***FAIL*** [dev002f]/dev/fuse has world permissions

***FAIL*** [dev002f]/dev/rfkill has world permissions

If you care, change the permissions.  Be aware that some things might fail.  However I ran "lsof | grep /dev/fuse" and "lsof | grep /dev/rfkill" and don't see them in use by any processes.

> ***FAIL*** [ssh005w]Cannot find a configuration file for SSH.

I have /etc/ssh/ssh_config on machines with an SSH client, and /etc/ssh/sshd_config on machines with an SSH server.  Both of them are installed by default.  I have no idea what "configuration file" it could be looking for.

> ***FAIL*** [netw020f]There is no /etc/ftpusers file

Are you running an FTP server?

I'm more concerned when an application I'm running throws security errors.  Sendmail, for instance, complains about a variety of things like directory permissions if you're not careful.  Running some "security" scanner that is nothing more than a collection of tests for random potential problems may provide little of relevance to your specific installation but always offers fuel for paranoia.

---

### Post by demarshall on 2011-02-12
> **CharlesA said:**
> If you aren't running any servers, you shouldn't really have to worry about it as there are no services listening on external interfaces by default in Ubuntu.

You can enable Remote Desktop, which uses VNC, but I would suggest not bothering with it and removing it from the start up applications menu.

If you are just browsing the web, look into NoScript and AppArmor.

Also:



Huge +1 to that.



I notice that I have AppArmor installed but it doesn't seem that it's an executable file. How do I use it? I don't see NoScript as being available on the servers.

David

---

### Post by NightwishFan on 2011-02-12
Noscript is a firefox extension.
[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

To enable apparmor:
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Run this from application -> accessories -> terminal:
```
sudo aa-enforce /etc/apparmor.d/*
```

---

### Post by cariboo on 2011-02-12
There are several apparmor profiles loaded by default. in a termianl type:

```
sudo /etc/init.d/apparmor status
```

to see what is loaded.

---

### Post by handy on 2011-02-12
In truth, how many Linux users actually have genuine security issues?

By the nature of its design a desktop Linux system is usually very secure. Ubuntu by default doesn't have any services running that might make it vulnerable.

Really I think that many people come over from the insecure Windows world & have to spend some time adapting to the fact that it is very much different once you get out of there.

---

### Post by rookcifer on 2011-02-13
> **reddae said:**
> I have been off and on with Ubuntu for a few years now. I have again decided to get back to it and I am currently focusing on the security of my system. Going from the tutorials and information on the forums I currently have these installed:

OSSEC

Totally unnecessary on a desktop box.

> Tiger Security Scanner

ditto

> ClamAV

ditto

> PortSentry

ditto

> LogCheck

A useful tool.  I use it.

> chkrootkit

Totally unnecessary

> I also have ufw active ang gufw to manage it.

If you have a router with a firewall, this is unnecessary.  If you don't have a router, then UFW is a good idea.

> I am concerned though because the output file i got from the tiger scanner is HUGE! It has a lot of  listings such as:

***WARN*** [pass014w]Login (backup) is disabled, but has a valid shell.

and a ton of:

***WARN*** [fsys013w]cannot access /usr/share/omf/office/office-ug.omf is a           dangling symlink.

type entries. The size of that file mixed with my limited knowledge on the use of portsentry and logcheck make me feel a little uneasy about the security of my system.

I used this tutorial to harden the installation once and it just stopped my computer from booting up.
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

Dude, you are just paranoid.  Your desktop box is not that important to crackers.  If you run a server open to the world, then I agree that you need to take extra security steps.  Most of those tools you list are only useful on servers.  Your desktop box only needs three things:

1) Only install software from the repos
2) Be sure all ports are closed (default on Ubuntu).
3) Install all security updates promptly

Do this, and there is a 99.9% chance your desktop box will never be cracked.

---

