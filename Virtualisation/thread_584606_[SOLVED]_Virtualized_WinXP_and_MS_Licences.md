---
title: "[SOLVED] Virtualized WinXP and MS Licences"
date: 2007-10-21
forum: Virtualisation
---

### Post by Alan Stancliff on 2007-10-21
I'm pretty new at this, having had Linux (Ubuntu) for less than 3 weeks. I now have a dual boot machine with Windows XP and Gutsy.

If I want to keep my dual boot, but at the same time install a VM in my Ubuntu and put XP there too, what licensing problems will I have? 

A simple question, no? But wait, it gets more complicated. My Windows XP Pro disk is an upgrade disk. I upgraded from Win 98, which was also an upgrade disk. I upgraded that from a Windows 95 upgrade disk, and my old Win 3.1 disks are probably unreadable, even if I install an old 5.3 drive on my computer, if I am able to find one.

So my question is this, if I attempt to install WinXP on a virtual machine, will the installation see my other installation and say okay? Or will it see the other installation and say I need another license? Or will it not see the other installation and want to see my Win98 disk?

If the latter, when I go to authenticate, I'll have to call Microsoft. Are they going to say I can't install in a virtual machine on the same box without another license? I hear this is the policy for Vista.

Boy is life complicated!

---

### Post by Sef on 2007-10-21
> Are they going to say I can't install in a virtual machine on the same box without another license? I hear this is the policy for Vista.

Yes, they would.  With Vista it is more complicated.  The home basic and the one above can't be virtualized at all.  The others can.

---

### Post by bodhi.zazen on 2007-10-21
You should read the "EULA" or contact Microsoft if you do not understand the terms on the agreement.

---

### Post by Alan Stancliff on 2007-10-21
> **bodhi.zazen said:**
> You should read the "EULA" or contact Microsoft if you do not understand the terms on the agreement.

Good idea about reading the EULA (rtfm). Guess I should break out my trusty dictionary and got to work sounding out those big words :lolflag:
Seriously, though, reading the EULA is  a good idea. 

What I had hoped to do by posting this here is find out what the experience of others had been. How had Microsoft responded to requests to authenticate a second installation on a second partition on the same computer?

For the record, I'm not looking for any illegal hacks or methods to circumvent authentication. I have no illegal software and have not had any illegal software since I owned my first computer back around 1983.

---

### Post by HermanAB on 2007-10-21
Legally, you need a WinXP license for each virtual machine.  With Win2003 Server, you get 5 licenses minimum, so you can legally run 5 VMs.  If you wish to have more, you need to buy more CALs.

In practice, what you do is install Windoze (any flavour) in a VM and register it with MS, then make a tar ball of the VM and install as many copies of the pre-installed and registered VM on as many machines as you want!

If you have to be legal and you are not just playing around at home, see the first paragraph. ;)

Cheers,

Herman

---

### Post by Alan Stancliff on 2007-10-21
> **HermanAB said:**
> Legally, you need a WinXP license for each virtual machine.  With Win2003 Server, you get 5 licenses minimum, so you can legally run 5 VMs.  If you wish to have more, you need to buy more CALs.

In practice, what you do is install Windoze (any flavour) in a VM and register it with MS, then make a tar ball of the VM and install as many copies of the pre-installed and registered VM on as many machines as you want!

If you have to be legal and you are not just playing around at home, see the first paragraph. ;)

Cheers,

Herman
Thanks for the ideas. Although I am just playing around at home, I want to be legal. 

If we expect MS to respect the GPL, then we must respect their EULA. Right now, they must be feeling nervous about the ramifications of the GPL, given their recent deal with Novel. After all, even though Ubuntu and VMWare are free, they are under international copyright protection. It's just the distribution model of Linux that is different, not the copyright protection offered under it. There is speculation about whether Windows infringes on some Linux technology now or will do so in the future.

Having said all that, tt occurs to me just now that I could install the VM and then Windows XP on it and then test it for a few days. If I like the way it works, I could then either uninstall my other installation and get the VM version authenticated, or I could buy another license and keep both installations. At any rate, authentication is not required for 30 days, and so I have a little bit of time to make up my mind and still be legal.

---

### Post by mjwood0 on 2007-10-23
> **Alan Stancliff said:**
> Thanks for the ideas. Although I am just playing around at home, I want to be legal. 

If we expect MS to respect the GPL, then we must respect their EULA. Right now, they must be feeling nervous about the ramifications of the GPL, given their recent deal with Novel. After all, even though Ubuntu and VMWare are free, they are under international copyright protection. It's just the distribution model of Linux that is different, not the copyright protection offered under it. There is speculation about whether Windows infringes on some Linux technology now or will do so in the future.

Having said all that, tt occurs to me just now that I could install the VM and then Windows XP on it and then test it for a few days. If I like the way it works, I could then either uninstall my other installation and get the VM version authenticated, or I could buy another license and keep both installations. At any rate, authentication is not required for 30 days, and so I have a little bit of time to make up my mind and still be legal.

I'm pretty much in the same boat.  

I need XP for work, complete with virus scanner and all so I can VPN into my work.  Unfortunately, it won't work with Linux.

In order to keep things legal, I purchased a copy of XP Home.  I've got it dual booting right now, but I haven't registered the Windows license yet.  I'm hoping to try the VMWare solution or Virtual Box solution and see.  If I can get everything working, I'll probably skip the dual boot as I really hate rebooting that much.  I figure I'll register it once I figure out what I want.

Let me know how it works out!

---

### Post by reiki on 2007-10-23
I've done this. I have installed XP Pro into multiple VMs. I have gotten the little message that I have to call because I've already activated this copy. I call the Microsoft number on the screen. I tell them exactly what I'm doing. "I am setting up Virtual Machines and experimenting with virtualization."

"How many computers are you installing this copy of XP on?"

"I only HAVE one computer, but I am trying virtualization so every time I make a new VM it wants me to re-activate"

"Ok no problem. Here is your new activation code..."

Now I know that there is language in the server licenses that specifically addresses VMs. It's something like... 5 VMs per physical machine in addition to a native install... or something like that. I've asked my licensing department to look at the XP Pro and see what it says about VMs. 

I *believe* that since I called Microsoft and told them exactly what I'm doing, that this isn't an issue. I want to be legit as well. Even if it IS only my home computer. I'll post back when licensing gets back to me.

---

### Post by stuffer007 on 2007-10-23
With XP you are given a little lenience. you can install and reinstall up to the third time before being flagged, then like stated above its no big deal you call in and tell them. but you are aloud to have the same copy of XP on different machines; just as long as only 1 is turned on at a time so if you use your key for dual boot and VM your only going to have one on at a time so you would be safe (so long as your running th VM inside linux, but then why would you want to run windows inside windows...)

---

### Post by Vadi on 2007-10-23
I also have a virtual XP machine, but I never bother to activate it, I just make a snapshot. When the activation time runs out, I just revert to an older snaptshop - I only need the machine for compiling purposes, so it runs max 15 mins a day total.

I don't feel bad at all, since I completely wiped the xp from my laptop when I got it, and boot Ubuntu only. So I think of it as re-locating my xp (until I learn to cross-compile).

---

### Post by reiki on 2007-10-24
What I'm getting back so far from my licensing people is that the XP license, while a little vague in some areas, is intended for a single install on a single machine. And that in order to install it in a VM you are *technically* supposed to have additional licenses. One for each VM. There are certain variables like... what kind of license did you get to begin with? OEM licenses are for one machine and are tied to the machine. NOT the individual. Just because YOU bought it, you do not have the right (technically) to MOVE that license from one machine to another. Other licenses are Microsoft Select (typically found in schools and businesses) and then there are Volume Licenses. 

This changes slightly with Vista.Vista Business and Vista Ultimate have language in their EULA that specifically addresses virtual machines. And Vista Enterprise has even greater abilities as far as installing into VMs. The other (lower) versions of Vista allow for only a single install on a single device. Period. 

So the long and short of it right now, as I understand it, for XP is that in order to be legitimate, you need a license for each VM.

---

### Post by Alan Stancliff on 2007-10-24
> **reiki said:**
> What I'm getting back so far from my licensing people is that the XP license, while a little vague in some areas, is intended for a single install on a single machine. And that in order to install it in a VM you are *technically* supposed to have additional licenses. One for each VM. There are certain variables like... what kind of license did you get to begin with? OEM licenses are for one machine and are tied to the machine. NOT the individual. Just because YOU bought it, you do not have the right (technically) to MOVE that license from one machine to another. Other licenses are Microsoft Select (typically found in schools and businesses) and then there are Volume Licenses. 

This changes slightly with Vista.Vista Business and Vista Ultimate have language in their EULA that specifically addresses virtual machines. And Vista Enterprise has even greater abilities as far as installing into VMs. The other (lower) versions of Vista allow for only a single install on a single device. Period. 

So the long and short of it right now, as I understand it, for XP is that in order to be legitimate, you need a license for each VM.I bought mine at CompUSA seeing as my computer was put together by a technician from parts I bought. 

One of the reasons I don't buy computers with Windows reinstalled is that for 100 bucks more, I get a more transportable Windows disk.

---

### Post by quinnten83 on 2007-10-24
> **reiki said:**
> 

This changes slightly with Vista.Vista Business and Vista Ultimate have language in their EULA that specifically addresses virtual machines. And Vista Enterprise has even greater abilities as far as installing into VMs. The other (lower) versions of Vista allow for only a single install on a single device. Period. 

So the long and short of it right now, as I understand it, for XP is that in order to be legitimate, you need a license for each VM.

How much sense does this make?
The power of virtualisation is portability. 
Which means, I should be able to install a VM and then port it to another computer if needed. That line in the EULA is basically saying that I am not allowed to port my installation from one machine to another. What about servers, then? The whole point of virtualisation becomes moot then.

The way I see it, one virtual machine equals 1 pc, I have one installation of the os on that machine (virtual). The machine is pretty much like a laptop in that I can grab it and take it with me. Sure i need to install software on another PC to see my own machine, but it is still one machine...

can you still follow?
So like someone else said, if you are only playing around, install and validate one virtual machine and copy (or create tarballs) the .vmi and open it on other PC's.

---

### Post by reiki on 2007-10-24
> **quinnten83 said:**
> How much sense does this make?
The power of virtualisation is portability. 
Which means, I should be able to install a VM and then port it to another computer if needed. That line in the EULA is basically saying that I am not allowed to port my installation from one machine to another. What about servers, then? The whole point of virtualisation becomes moot then.

The way I see it, one virtual machine equals 1 pc, I have one installation of the os on that machine (virtual). The machine is pretty much like a laptop in that I can grab it and take it with me. Sure i need to install software on another PC to see my own machine, but it is still one machine...

can you still follow?
So like someone else said, if you are only playing around, install and validate one virtual machine and copy (or create tarballs) the .vmi and open it on other PC's.

Oh! Believe me, I'm not the license police or anything. And I don't disagree with you in principle. I am only trying to provide factual information about the licensing as I understand it. What people actually DO with their installs is totally their own decision. 

And to be honest I, myself, look at this like.... I bought it and as long as I'm not installing it on other people's machines and just installing it once for ME, then whether that machine is virtual (and portable) or not is up to me.

---

### Post by Alan Stancliff on 2007-10-26
> **reiki said:**
> Oh! Believe me, I'm not the license police or anything. And I don't disagree with you in principle. I am only trying to provide factual information about the licensing as I understand it. What people actually DO with their installs is totally their own decision. 

And to be honest I, myself, look at this like.... I bought it and as long as I'm not installing it on other people's machines and just installing it once for ME, then whether that machine is virtual (and portable) or not is up to me.

Hi Reiki,

I appreciated your contribution here very much, and I am with you in that I want to be legal. I appreciate your posting your understanding of your legal department's opinion here. It makes sense to me.

I also appreciate all the feedback I've gotten from the other contributors to this thread. My questions have been answered to my satisfaction. I will mark this thread solved, but of course, if others have things to say, I will read them with interest.

---

