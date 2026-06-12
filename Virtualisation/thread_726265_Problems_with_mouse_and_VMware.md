---
title: "Problems with mouse and VMware"
date: 2008-03-16
forum: Virtualisation
---

### Post by kk0sse54 on 2008-03-16
This is my first post and i just started using ubuntu so please bear with me. I run windows xp and use ubuntu through VM player which works perfectly for me until i try running it in full screen mode. What happens is that my mouse starts acting weird and starts freezing up or will not allow my to move the pointer over certain areas of the screen. Instead it forces me to run it as a window in xp.I would really like to be able to get this to work  so that i can run it in full screen mode so that it feels like a real desktop environment. If anybody knows how to fix this problem I would greatly appreciate it.Thnks

---

### Post by fjgaude on 2008-03-16
Okay, in vmware go to Edit/Preferences/Display and check both items. Changing the size of windows should be automatic then.

Let us know if it works.

---

### Post by kk0sse54 on 2008-03-16
okay so i found preferences and went in there but there is no display tab or any options regarding the display. Is this an option only found in VMware workstation because i am using VMware player and there really isn't many options for anything.

---

### Post by fjgaude on 2008-03-16
Oh, I'm only using vmware server. I have never used player.

---

### Post by kk0sse54 on 2008-03-16
aye that explains. I think that i am going to try and use an old mouse from my older computer and see if anything is different. I will post the results as soon as i can.

---

### Post by kk0sse54 on 2008-03-16
Plugged in a new mouse and installed it but i am getting the same problem. The mouse works fine on XP but not on vm player. Both are just Logitech mouses nothing special. I am really at loss at what to do please if anybody has experienced problems similar to these using VM player please respond as i would really like to run Linux in a normal desktop environment.

---

### Post by fjgaude on 2008-03-16
Is there an option to Install VM Tools in player?

I find such under the VM tab menu on my server.

---

### Post by kk0sse54 on 2008-03-16
Yes i have them, they appear on my linux desktop and there are four tabs: options, Devices, scripts, and shrinks. I can't access Scripts and shrinks because it says that i don't have vm tools as  root. Options and devices i have already explored and they don't do anything to help me either.

---

### Post by dpj23 on 2008-03-17
1. check that vmtools are installed..

2. in quest you may have to accelerate the mouse to improve performance....

---

### Post by kk0sse54 on 2008-03-17
they are installed but they don't do much for me because i don't know how to establish them as root whatever that means. Plus Vm player on a whole  just  doesn't seem to have a lot of options as i have tried looking around. I want to upgrade it to vmware workstation or something better but i don't have the money to spend unfortunately.

---

### Post by fjgaude on 2008-03-17
VMware server is free, from their web site: vmware.com... the key is free and never has to be renewed.

Give it a look-see.

---

### Post by kk0sse54 on 2008-03-18
aye vmware server and player are free but workstation isn't.  Just one quick question though whats the difference between vmplayer and vmserver?

---

### Post by fjgaude on 2008-03-18
VMware player does just that, it plays VMs created by another program, like VMware server or workstation.

---

### Post by kk0sse54 on 2008-03-18
Okay so if i download VM server how can that help me with my mouse and isn't that for running another OS on servers and will i be able to transfer my current files and settings from ubuntu on vm player to vm server?

---

### Post by fjgaude on 2008-03-18
Vmware server is not for running on other servers, no. It is a server itself, and others can use it on the local network, if you have a network.

It has what is called VMware Tools that you install and makes the video and mouse work as if you were on your main host.

I'm not sure what you mean by transfering your settings and files from Ubuntu to  VMware server from player.

You mean you are running your player from Windows or from Ubuntu presently?

I run Ubuntu as my main OS, called the host for VMware server. On that server I have installed Windows. What is it you wish to do?

---

### Post by kk0sse54 on 2008-03-18
sorry for the confusion but i run VMplayer on windows XP using that as my main OS because i seemed like an easier alternative than partitioning my drive. I run Ubuntu 7.10  on VMplayer and i have been running it for a few weeks now so i was wondering if i download and install VM server and ran Ubuntu on that if i would be able to transfer all my settings, files, applications etc etc. from player to server. Also i went into ubuntu settings changed the mouse acceleration from there but the same problem still continues.

---

### Post by fjgaude on 2008-03-18
Likely not, but it is possible... if you got the guest vmx file from the vmware.com web site it likely only runs on the player. That's been my experience.

---

### Post by kk0sse54 on 2008-03-19
The problem has gotten worse now where i can't run VMware in a larger window than 4 in. x 4 in. without the mouse freezing. I think that i will give up on this virtualisation software and just partition my HD and run it as a dual boot. Thank you so much for the time you spent to try to help me and i really appreciate it .

---

### Post by fjgaude on 2008-03-19
> **C!oud said:**
> The problem has gotten worse now where i can't run VMware in a larger window than 4 in. x 4 in. without the mouse freezing. I think that i will give up on this virtualisation software and just partition my HD and run it as a dual boot. Thank you so much for the time you spent to try to help me and i really appreciate it .

I would look into the rest of the system for some issue that has brought this situation about...

Good luck at whatever you do.

---

### Post by aimaz on 2009-11-26
I am also having this problem under Karmic Koala. I'm using a laptop with an external mouse, both show the same problem. It only happens in an my XP VM, works fine when I run a linux VM. It used to work ok... I've noticed that when the problem is happening the message flickers between the "press Ctrl+Alt..." and "press ctrl+g" messages.

Reinstalling the VMware mouse driver had no effect.

The problem also happens on a backup copy of the VM that I made before the problem started.

---

### Post by roxy2 on 2010-01-09
> **C!oud said:**
> The problem has gotten worse now where i can't run VMware in a larger window than 4 in. x 4 in. without the mouse freezing

I have the same problem in ubuntu 9.10. I used [this]("http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html") instructions to install vmware server 2.0.2 and omit some problems with 2.6.31 kernel.

---

### Post by deakblue on 2010-01-11
Same problem

Host: Karmic Koala 64
Guest: WinXP 32
Within: vmware workstation

Had the same setup issue-free running Ubuntu 8.10 a few weeks ago.

When the guest desktop is spread beyond about 800x600 it renders fine, but the mouse cursor gets 'hung-up' along that 800x600 edge.  In other words, the regions to the right and below that edge are unclickable in the guest and seem to belong to the host.

I'll cross post a link to this thread in the vmware forum.

---

### Post by deakblue on 2010-01-11
SOLVED POSSIBLY

A full system (aka HOST aka Ubuntu) restart and the problem is gone for me at least.  Maybe other posters had a similar experience.

If you find yourself here, give a system restart a try.

---

