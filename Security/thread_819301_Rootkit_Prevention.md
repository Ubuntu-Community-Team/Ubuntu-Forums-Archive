---
title: "Rootkit Prevention"
date: 2008-06-05
forum: Security
---

### Post by tobybaloney on 2008-06-05
Paranoid noobie.

I've come to Ubuntu following severe rootkit trouble on XP (despite being behind firewall router, partner downloaded trojan with a screensaver and tried to install. It infected 4 pcs on our home network, all requiring re-installation).

Im very happy to be here, but how can I guarantee not to pick up a rootkit on Ubuntu Hardy Heron while still using internet?

Rkhunter and chkrootkit only help after the event, and I can't even confidently work out how to configure them - it all seems very complicated. 

Is there a program/patch that installs through synaptic pkg mgr that, once installed, will lock everything down?

I understand that ports are closed, but what if I click a fake link - could that install something?

I've looked at the various "hardening kernal" instructions, grsecurity (maybe not applicable to hardy?), etc. but they're really beyond me. I installed snort and samhain, but can't work out how to use them. I guess they're running in the background somewhere, and may be a security risk themselves.

If we only use non-administrator account online, will that guarantee safety, or could someone "jump in" when I sign in sudo to run system updates? 

I've searched loads of forums, but can't find a simple answer to the question (maybe there isn't one - please say so if that is the case).

I'm really not comfortable with using terminal to configure things without letter by letter instructions. I certainly don;t understand what I'm doing.

I appreciate you may suggest that I should learn how to do it. I've spent hours getting this far, which is really only peeking through a gap in the door.

Any simple advice very gratefully received!

---

### Post by tubbygweilo on 2008-06-05
> partner downloaded trojan with a screensaver and tried to install
If you can educate your partner not to be tricked into downloading and clicking upon links of dubious parentage then well over half the battle has been won and with any luck you machine be it XP or Ubuntu should be a safer place to work.

Setting a strong password on the admin account should help you if by any chance something attempts to gain access by guessing the password also if you respond to the sudo ask password prompt only if you are expecting it eg during updates then you in a good position towards keeping your machine safe. May I suggest that if you are using Mozilla Firefox and have not installed the NoScript, AdBlock Plus and FlashBlock you should consider so doing as they can also mitigate against accidentally allowing nasty things into your machine.

These are the simple practices that I have adopted and for well over a year they have worked, I will let others talk about hardening, root kit detection and other measures to keep thing safe as I do not have too much knowledge on that subject.

---

### Post by erginemr on 2008-06-05
One such preemptive tool is **rkdet**. You may want to check it out:
[http://vancouver-webpages.com/rkdet/](http://vancouver-webpages.com/rkdet/)
[http://www.linuxsecure.de/index.php?action=46](http://www.linuxsecure.de/index.php?action=46)

---

### Post by ordaide on 2008-09-12
For those looking for an easier way into the grsecurity kernel (or 'hardening' without headache) try 

[http://kernelsec.cr0.org/](http://kernelsec.cr0.org/)

Simple yet effective, thanks to the efforts of Julien TINNES.

But indeed.  Heed the above also.


PS  - Easy IP tables generator.

 [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)
*
I have not used it, and cannot verify its ability, but maybe its better than nothing for noobs.

---

### Post by cariboo on 2008-09-12
The only user that gets administration rights is the one that gets setup during installation. You have to specifically make other users members of the administration group. If they try to install programs, they won't be allowed to as they do not have permission to write to any directory but their own. Also as the previous poster stated a little bit of education goes a long way.

Jim

---

### Post by doas777 on 2008-09-12
> **ordaide said:**
> For those looking for an easier way into the grsecurity kernel (or 'hardening' without headache) try 

[http://kernelsec.cr0.org/](http://kernelsec.cr0.org/)

Simple yet effective, thanks to the efforts of Julien TINNES.

But indeed.  Heed the above also.


PS  - Easy IP tables generator.

 [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)
*
I have not used it, and cannot verify its ability, but maybe its better than nothing for noobs.

I was under the impression that I had to mod my kernel to use grsecurity. has it gotten easier?

---

### Post by doas777 on 2008-09-12
usually when i'm hardening a box, I install:

```
sudo apt-get install harden-environment bastille
```

you don;t have to do anything to config the harden package, but you do have to run bastille with 
```
sudo bastille -c
``` and walk through the wizard.

[harden-environment]("http://packages.ubuntu.com/hardy/admin/harden-environment") uses an host intrusion detection system, which should notice an attempt to install most rootkits.

and then there is [this]("http://www.debian.org/doc/manuals/securing-debian-howto/"). get a cup of coffee. you'll be here a while.

Ps: as others have told me, there is very little threat of getting a rootkit from the internet. you have to isntall them, and almost always with sudo or gksu. as such, just don't install software from outside the repositories, and don't add any repositories not cross referenced by cannonical (ubuntu), and you should be fine. 

good luck,
frank

---

### Post by EnGorDiaz on 2008-09-13
harden the enviroment with bastille install a incryption package and back your files with quickstart and put passwords on there archives something semi bind code like 

vah8k8l9i10 theres a password for ya and no one can really crack it

---

