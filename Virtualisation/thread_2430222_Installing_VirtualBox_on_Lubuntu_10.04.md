---
title: "Installing VirtualBox on Lubuntu 10.04"
date: 2019-10-29
forum: Virtualisation
---

### Post by lasdude on 2019-10-29
[I][B]Hi there, guys!
[/B][/I]
I've got a question on _Lubuntu 10.04_: 
[B]How on the Earth can I install any version of Oracle VirtualBox on it?
[/B]This line in Terminal doesn't work: [I]sudo apt-get install virtualbox

[/I]So could you help me?

---

### Post by uRock on 2019-10-29
10.04 has not been supported for more than 5 years. Please try 18.04, which is LTS, or 19.10.

---

### Post by guiverc on 2019-10-29
fyi: the 10.04 means it was the 2010-April release of Lubuntu (ie. releases are *yy.mm* in format ).  Where as Ubuntu 10.04 LTS came with 5 years of supported life, Lubuntu was a flavor and only had 3 years of supported life, release-upgrading to 12.04 LTS (also EOL) then 14.04 LTS (also EOL), then 16.04 LTS (Lubuntu 16.04 is EOL, but Ubuntu 16.04 is still supported), then 18.04 LTS.

---

### Post by lasdude on 2019-10-29
Can 16.04 LTS or 18.04 LTS be installed on a computer with 64 or 128 MiB of RAM? I need an Ubuntu version that could do this! Do you know one? Please, I really need it.

---

### Post by uRock on 2019-10-29
Go with Lubuntu 18.04.

---

### Post by uRock on 2019-10-29
You want to install a virtual machine on a system running such little RAM?

---

### Post by lasdude on 2019-10-29
Officials write about [COLOR=#444444][FONT=&quot]lubuntu 18.04 Bionic Beaver:
[/FONT][/COLOR]
[LIST]
[*][SIZE=2]Memory (RAM): for advanced internet services like Google+, YouTube, Google Drive, and Facebook, your computer needs at least 1 GB of RAM. For local programs like LibreOffice and simple browsing habits, your computer needs at least 512 MB of RAM.[/SIZE]
[*][SIZE=2]Processor (CPU): the minimum specification for CPU is Pentium 4 or Pentium M or AMD K8. Older processors are too slow and the AMD K7 has problems with Flash video.[/SIZE]
[/LIST]

---

### Post by lasdude on 2019-10-29
Yeah, I want this. Will I face a problem doing this?

---

### Post by guiverc on 2019-10-29
I never tested Lubuntu 18.04 (or 18.10/19.04) on any machine with less than 1gb of RAM (1.5gb for 19.10).  The alternate-installer should be used on machines with low-ram (ie. 700MB or less) but the smallest RAM for any semi-recent Ubuntu is Ubuntu Server (minimal; [https://help.ubuntu.com/lts/serverguide/preparing-to-install.html#system-requirements](https://help.ubuntu.com/lts/serverguide/preparing-to-install.html#system-requirements)) being 384MB of RAM, as no machine made in years has less than 1gb. 

Lubuntu no longer provides a minimum amount of RAM ([https://lubuntu.me/taking-a-new-direction/](https://lubuntu.me/taking-a-new-direction/)), even the alternate installer hasn't been updated since early 2018 (ie. no 18.04.3 or more recent builds), but lower than 1gb of RAM really applies to x86 ([https://lubuntu.me/sunsetting-i386/](https://lubuntu.me/sunsetting-i386/)) with builds stopping Dec-2018.  I doubt any Ubuntu outside of server would be usable in 64MB/128MB of RAM - myself I'd use PuppyWary, DSL or something else (and the Puppy I'm mentioning is not the Ubuntu based version).

---

### Post by uRock on 2019-10-29
You may be able to get a host running on it, but getting a VM installed within the host with that little RAM isn't going to work out.

---

### Post by guiverc on 2019-10-29
VirtualBox requires 512MB as a minimum, and I suspect that's beyond what the OS has available, it recommends 2GB as the minimum for windows. [https://www.virtualbox.org/wiki/End-user_documentation](https://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by lasdude on 2019-10-29
> **guiverc said:**
>  I doubt any Ubuntu outside of server would be usable in 64MB/128MB of RAM - myself I'd use PuppyWary, DSL or something else (and the Puppy I'm mentioning is not the Ubuntu based version).

Where can I find it? Does it still support VirtualBox?

---

### Post by guiverc on 2019-10-29
> **lasdude said:**
> Where can I find it? Does it still support VirtualBox?

Ubuntu Server - [https://ubuntu.com/download/server](https://ubuntu.com/download/server)

DSL: [https://distrowatch.com/table.php?distribution=damnsmall](https://distrowatch.com/table.php?distribution=damnsmall)
Puppy : [http://puppylinux.com/](http://puppylinux.com/)

(I mentioned PuppyWary; I only see Slacko now; I've run Wary on 64MB laptops but not Slacko).

I suspect none of them will run VirtualBox; but I doubt VirtualBox would run in 128MB of RAM when it states its own doco states 512MB is needed to run it + whatever you want a client OS to use + host OS.  (okay Ubuntu Server will, but it'll cause itself to be changed into a desktop version & I doubt it'll be usable on 128MB of RAM for VirtualBox)

---

### Post by lasdude on 2019-10-29
> **guiverc said:**
>  I suspect none of them will run VirtualBox; but I doubt VirtualBox would run in 128MB of RAM when it states its own doco states 512MB is needed to run it + whatever you want a client OS to use + host OS.  (okay Ubuntu Server will, but it'll cause itself to be changed into a desktop version & I doubt it'll be usable on 128MB of RAM for VirtualBox)

I'll try on a strong PC first. Thanks for links, I'll try them too. Could you help me with the way how to install VirtualBox on Lubuntu 10.04 - I tried [https://www.virtualbox.org/wiki/Download_Old_Builds](https://www.virtualbox.org/wiki/Download_Old_Builds) but [VirtualBox 4.0]("https://www.virtualbox.org/wiki/Download_Old_Builds_4_0") couldn't launch that. That was version for Ubuntu 10.04...

---

### Post by uRock on 2019-10-29
> **lasdude said:**
> I'll try on a strong PC first. Thanks for links, I'll try them too. Could you help me with the way how to install VirtualBox on Lubuntu 10.04 - I tried [https://www.virtualbox.org/wiki/Download_Old_Builds](https://www.virtualbox.org/wiki/Download_Old_Builds) but [VirtualBox 4.0]("https://www.virtualbox.org/wiki/Download_Old_Builds_4_0") couldn't launch that. That was version for Ubuntu 10.04...

Try a supported version. You're not going to find anything that will install on 10.04.

---

### Post by crip720 on 2019-10-29
Even if you could get virtualbox to install, it will take at least half of your ram to run.  You would be left with frozen/crash system.  I would not try a VM with less than 4GBs, and if I want it to run well, at least 2x more ram.

---

### Post by guiverc on 2019-10-29
> **lasdude said:**
> I'll try on a strong PC first. Thanks for links, I'll try them too. Could you help me with the way how to install VirtualBox on Lubuntu 10.04 - I tried [https://www.virtualbox.org/wiki/Download_Old_Builds](https://www.virtualbox.org/wiki/Download_Old_Builds) but [VirtualBox 4.0]("https://www.virtualbox.org/wiki/Download_Old_Builds_4_0") couldn't launch that. That was version for Ubuntu 10.04...

I'm the primary Lubuntu team member allocated to this site, however Lubuntu has a 3 year LTS support life - so 10.04 support ended in 2013-April.  The oldest supported Lubuntu is 18.04 LTS, so sorry no.  The exception to this (EOL rule) is help is provided moving you to a supported release if required.

---

