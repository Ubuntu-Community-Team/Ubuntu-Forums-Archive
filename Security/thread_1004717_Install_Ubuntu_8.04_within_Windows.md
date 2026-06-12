---
title: "Install Ubuntu 8.04 within Windows"
date: 2008-12-07
forum: Security
---

### Post by David4 on 2008-12-07
Hi
I have the CD to install v 8.04
this question is about protecting the integrity of the Whole hard drive.
If I install it using the "Install Inside Windows" option, and after having the two OS I reboot using the Ubuntu OS option, while working on the web I get a virus, trojan,etc  or a hacker intrusion, will that event also corrupt/affect my Microsoft Windows OS and all programs installed under that OS as well?.
David

Moved Posting to Security Discussions

---

### Post by David4 on 2008-12-07
After posting under General Discussion I realize this forum may be more appropriate, sorry about double posting.

Hi
I have the CD to install v 8.04
this question is about protecting the integrity of the Whole hard drive.
If I install it using the "Install Inside Windows" option, and after having the two OS I reboot using the Ubuntu OS option, while working on the web I get a virus, trojan,etc or a hacker intrusion, will that event also corrupt/affect my Microsoft Windows OS and all programs installed under that OS as well?.
David

---

### Post by 2hot6ft2 on 2008-12-07
If it's installed inside windows, and windows gets messed up then I would imagine that you wouldn't be able to get into it if you can't get into windows to get in it.

---

### Post by jmoorse on 2008-12-07
David,

First off, it is my understanding you are installing _from within windows_, not installing Ubuntu _into windows_.  This will create two distinct partitions and a boot menu (grub) that comes up following boot and POST.

Interactions between both partitions (Linux and Win) could theoretically pass viral content (e.g.: downloading files to your Windows partition) although I would highly doubt this would ever happen.

If you are concerned about system integrity and malware you can also make use of some of the great open source antivirus and firewall apps available in the Ubuntu repositories.

Be sure you are also running adequate malware/firewall protection on the windows side just to be safe.

Corially,
Jeff Moorse

---

### Post by David4 on 2008-12-07
Jeff and 2hot6ft2
thank you for your replies.
I thought that will be the case.
I am trying to setup this desktop to enable my kids the use of web browsing without having to worry about my  windows installed programs that I cannot install under Ubuntu.
Looks like the only way to do that will be either partition the HD and use a different partition or use a second HD to install Ubuntu.
thank you both for your response.
David

---

### Post by cariboo on 2008-12-07
If you get a Windows virus in Windows you should already be protected. If you get a Windows virus in Ubuntu, you shouldn't have to worry as Windows executables don't work with linux. You have to boot into each operating system separately so the only way a virus will affect you Windows installation, is if you copy the virus to your Windows partition.

Jim

---

### Post by David4 on 2008-12-07
thank you for your response,now, if Ubuntu is installed under Windows environment then Windows could be affected also as is in the same partition??

David

---

### Post by Kinstonian on 2008-12-07
It's unlikely a virus would be cross-platform and able to infect Windows from Linux or vice versa.  However, if Ubuntu gets compromised by an actual attacker, then whether your Windows partition gets compromised as well depends mostly on the skill of the attacker and his motivation.

---

### Post by David4 on 2008-12-07
Kinstonian
that is an interesting view, perhaps the question should be, when installing Ubuntu within Windows are they in different partitions or is Ubuntu really "another" program under Windows?
David

---

### Post by aysiu on 2008-12-07
The *install inside Windows* option (otherwise known as Wubi) actually creates a large dynamically-sized file inside Windows that acts a virtual partition for Ubuntu and then tells the Windows boot loader (boot.ini) to look for the operating system in that file.

So, as far as the Ubuntu session goes, there's absolutely no way to access Windows when you're in the session.

However, if Windows gets compromised, since Ubuntu just lives as a file within Windows, you won't be able to boot into Ubuntu necessarily either.

If you're concerned about security, your best bet is to have Ubuntu be your main OS and then install Windows as a virtual operating system (using something like VirtualBox) inside Ubuntu.

---

### Post by Kinstonian on 2008-12-07
> **David4 said:**
> Kinstonian
that is an interesting view, perhaps the question should be, when installing Ubuntu within Windows are they in different partitions or is Ubuntu really "another" program under Windows?
David

Disregard what I said... I thought when in Ubuntu the attacker would be able to see your Windows partition, but according to aysiu, that's not the case.  You learn something everyday. :)

---

### Post by David4 on 2008-12-07
thank you aysiu
that answers my concern, very helpful
Will go ahead and install it since now I understand how it will work
take care
David

---

