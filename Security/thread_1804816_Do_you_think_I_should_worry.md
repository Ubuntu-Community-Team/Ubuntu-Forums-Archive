---
title: "Do you think I should worry?"
date: 2011-07-15
forum: Security
---

### Post by Libertydude on 2011-07-15
Hi, for security reasons I browse the Internet in Virtual Box (guest OS: Ubuntu 11.04 fully patched) on a fully patched Ubuntu 11.04 machine.

Anyway, today I was browsing the web in my guest OS and I clicked a link and it redirected me to an exploit site (mywot said it was, and so did norton safeweb). Anyways, I exited my guest OS and reverted to a snapshot I made of it 5 days ago.

And then I scanned my host OS with clamtk and it found nothing.

So I was wondering, is there anyway malware could infect my host OS from Virtual Box? Perhaps by a vulnerability? Or via my LAN?

Or should I simply not worry?

---

### Post by NERDMAN! on 2011-07-15
not unless you set up a shared folder between guest and host and downloaded a file to it.
you shouldnt have to worry if clamtk found nothing.

---

### Post by Libertydude on 2011-07-15
> **NERDMAN! said:**
> not unless you set up a shared folder between guest and host and downloaded a file to it.
you shouldnt have to worry if clamtk found nothing.
No, but I do have guest addons installed.

---

### Post by Grenage on 2011-07-15
I wouldn't worry.  The chances of a Windows-intended piece of malware (or browser-intended) infecting the host OS from a virtual box, it's not going to happen.

---

### Post by ericrichards420 on 2011-07-15
someone sounds a little paranoid. I have been using linux for a little over 12 years now and I haven't had a single problem getting a virus or spyware or anything else. In ubuntu you have to give admn password in order to install anything. As long as you only install software from trusted places then you will be alright.

---

### Post by haqking on 2011-07-15
> **Grenage said:**
> I wouldn't worry.  The chances of a Windows-intended piece of malware (or browser-intended) infecting the host OS from a virtual box, it's not going to happen.

+1

But just be aware that if you have your Virtual machines setup to share your hosts network and desktop shares etc then there is always a possibility.

The more windows you leave open then the more chances for a burglar to break in ;-)

---

### Post by Libertydude on 2011-07-15
> **haqking said:**
> +1

But just be aware that if you have your Virtual machines setup to share your hosts network and desktop shares etc then there is always a possibility.

The more windows you leave open then the more chances for a burglar to break in ;-)
Sounds reasonable. :) But would clamtk have detected any threats on my computer? Or is there any known Linux malware that disables clamtk?

---

### Post by haqking on 2011-07-15
> **Libertydude said:**
> Sounds reasonable. :) But would clamtk have detected any threats on my computer? Or is there any known Linux malware that disables clamtk?


A windows virus wont effect a linux machine.

And the problem of linux viruses and malware is not a big one.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

The simle story is whatever site you visited in your virtual machine, dont worry about it.

---

### Post by Libertydude on 2011-07-15
> **haqking said:**
> A windows virus wont effect a linux machine.

And the problem of linux viruses and malware is not a big one.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

The simle story is whatever site you visited in your virtual machine, dont worry about it.
This is very reassuring to hear. :D Thanks pal. :)

---

### Post by Libertydude on 2011-07-15
Is there even any malware that currently can even work on a fully patched linux machine?

---

### Post by NERDMAN! on 2011-07-15
there are some scripts people write and put out there that will do evil things to any linux distribution, but as stated before they all require a password to run in ubuntu, and they are usually pretty easy to spot.
if a script is loaded with hex code that usually raises a red flag for me.
but if something ever tries to execute itself on its own and asks for a password, only then should you worry.

if you stick to trusted software sources like sourceforge and the ubuntu repositories, and dont download random scripts from people you dont know, then your laughing. 

theres always a chance but theres just not enough linux malwares out there to be worrying about it. linux doesnt share enough of the market, everyone still uses windows, and because of that all the malware developers target windows users. i cant see you having a malware issue until linux innevitably grows more popular.

---

### Post by Grenage on 2011-07-15
> **Libertydude said:**
> Is there even any malware that currently can even work on a fully patched linux machine?

I've never seen any, or heard of any from a reliable source; some may exist, but not in the wild.  As long as you practice common security sense, you'll be fine.

---

### Post by Libertydude on 2011-07-15
So given my situ I have nothing to worry about?

---

### Post by Grenage on 2011-07-15
In your situation, I would not worry at all.

---

### Post by bodhi.zazen on 2011-07-15
> **Libertydude said:**
> Sounds reasonable. :) But would clamtk have detected any threats on my computer? Or is there any known Linux malware that disables clamtk?

I think you are putting way too much trust in antivirus detection without any understanding of linux security.

There are no known active viruses for Linux, let alone viruses that deactivate things.

I highly suggest you take the time to actually learn something about security, start with the security sticky.

In terms of your browser, use NoScript + apparmor.

If you want to be paranoid to the degree you express in this thread, use Fedora 15, either with the kiosk mode or xguest account. In addition you can use a selinux sandbox for firefox.

[Dan Walsh's Blog - New Kiosk OS posted for Fedora 15]("http://danwalsh.livejournal.com/44398.html") 

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_11_selinux_user_guide/fedora_11_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_11_selinux_user_guide/fedora_11_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

[http://www.linux-magazine.com/Online/News/SELinux-Sandbox-for-Untrusted-Programs](http://www.linux-magazine.com/Online/News/SELinux-Sandbox-for-Untrusted-Programs)

---

### Post by ehode on 2011-07-21
> **Libertydude said:**
> So given my situ I have nothing to worry about?

If I understand.  You have your clean host OS and you run another OS in a VM for browsing.  You are taking way more security than most and should feel good that you've implemented a good amount of layers between your browsing and your host OS.

You reverted to an older snapshot.  You are active in your security model.  

You should sleep well and not worry.

---

### Post by Rasa1111 on 2011-07-21
> **Libertydude said:**
> So given my situ I have nothing to worry about?

Correct. I wouldn't worry at all.

---

### Post by twipley on 2011-07-24
> **Libertydude said:**
> is there anyway malware could infect my host OS from Virtual Box? Perhaps by a vulnerability?
Yes, absolutely. Think of it as holes on an emmental cheese.

> **Libertydude said:**
> Or should I simply not worry?
From what I have read, using AppArmor and NoScript on a freshly installed, and up-to-date Ubuntu distribution renders the best of both worlds, being usability, and security.

---

### Post by amiacamal on 2011-07-25
I thought i read that the only way something could get from an virtual box to the actual OS is if there is a folder shared between the VB and OS? 

Surely thats the point of a Virtual box, another layer of abstraction between the os and the big bad world.

---

### Post by twipley on 2011-07-25
Depends if the developers left a vulnerability in their code, which would allow a virtual-machine attacker to achieve privilege escalation through a VirtualBox vulnerability. Theoretically possible; practically, quite improbable.

---

### Post by Chayak on 2011-07-25
> **Libertydude said:**
> Is there even any malware that currently can even work on a fully patched linux machine?

Yes there is malware that runs on Linux.  Is it practical to worry over, no.

As to something escaping virtualization, relax.  I've seen theoretical attacks to escape virtual machines but none that work real world.  I handle malware in virtual machines on a daily basis and nothing has ever touched the host OS.

---

