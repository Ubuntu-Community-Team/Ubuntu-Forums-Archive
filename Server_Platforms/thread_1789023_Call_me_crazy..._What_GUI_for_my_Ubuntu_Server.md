---
title: "Call me crazy... What GUI for my Ubuntu Server???"
date: 2011-06-23
forum: Server Platforms
---

### Post by Sorky on 2011-06-23
Yes I know - Ubuntu Server doesn't have a GUI for a reason, it's a server! I hear you, but I think I need it so I'll explain what I'm hoping to achieve and you can tell me I'm crazy or what would work the best.

My aim...

A) Each member of the household has a VM (or more) for their everyday use
 * Quickly & easily backed-up and restored (read as fixed/replaced)
 * Easy to have several for different purposes (keeping each light-weight)
 * Can run several at the same time (but with obvious performance loss)
 * Same VM is able to be accessed from multiple locations (even remotely)

B) Server...
 * Nice quad core with 32GB RAM [basic graphics, sound, etc]
 * Would remain on with a UPS and easy to do backups centrally & regularly
 * Acts as a domain controller, file & print server & hosts VMs
 * It would normally simply not have anyone logged in
 * I would load the gui to access my VM & basic stuff (eg: file copy) 
 * I could still use the shell to do other things

C) Other PCs in the house...
 * Can be very basic - Just need to do RDP - recommendations?
 * Could potentially be hosted on non-pc devices 
 * The clients can be boxes others would throw away! 

So... Am I crazy or are there some suggestions or alternatives? 

PS: My initial experimentation has been with xubuntu-desktop on Ubuntu Server and now that I've got the domain, file, print & VM serving sorted, I'm ready to start again with a minimalist approach. My initial ideas is "awesome" or "xmonad" or possibly "Fluxbox" or "Openbox" - Anyone done similar? Any traps?

PPS: I'm NOT an expert, but I'm learning FAST ;-)

---

### Post by collisionystm on 2011-06-23
I know you insist on using the GUI, but you can load VM's and manage them from another Ubuntu Machine without ever touching the Ubuntu Server. You can use Hypervisor and the Remote management tool that you can get from the software Center. 

I think you have a lovely idea that will be fun to try out..

May I suggest you use Zentyal for your server? [www.zentyal.com](www.zentyal.com)

It already comes with a gui and a web interface to manager it.  It makes setting up a PDC, mail server, VPN etc... SO EASYY!!!!!!!! Load it up and install virtualbox to host your VM's. 

Try it out, You wont be dissapointed.

---

### Post by collisionystm on 2011-06-23
Oh and its based on Ubuntu 10.04 LTS

---

### Post by snowpine on 2011-06-23
Xubuntu is a fine choice. I doubt you'll see much performance benefit switching to openbox/awesome/etc. on a 32gb ram quad-core.

---

### Post by Maheriano on 2011-06-23
I fail to see anywhere in your post where you require a GUI.

---

### Post by kgatan on 2011-06-23
Im quite inexperienced with VMs but have been trying out Virtualbox on ubuntu and everything works great so far and it wasnt hard to setup.

Virtualbox isnt in the repository but there is a debian package from their website and lots of guides.

For GUI i use PHPVirtualbox which is a web-based gui for virtualbox.
Im not sure if it has all the functionality that you need but basic managment of vms is realy easy.

---

### Post by lykwydchykyn on 2011-06-23
Have you looked at setting up LTSP and booting your clients over the network?  That looks suspiciously like what you're trying to accomplish.

---

### Post by arrrghhh on 2011-06-23
> **Maheriano said:**
> I fail to see anywhere in your post where you require a GUI.

Agreed.

Based on your first post, all the VM's will have a GUI - I assume you'll be running a mix of Win&Lin VM's?  If so, just use VRDP that comes with VirutalBox and VBoxHeadless.  Works great, I do this and use a WinXP VM to get into my work remotely...  (Yes, they **require** Windows for this.  Don't ask.)

---

### Post by Grenage on 2011-06-23
> **lykwydchykyn said:**
> Have you looked at setting up LTSP and booting your clients over the network?  That looks suspiciously like what you're trying to accomplish.

I second this, you can have some dinky thin clients connected up.  I've never set one up before, but it's on the list.

---

### Post by CharlesA on 2011-06-23
I didn't see anywhere that said that VM software you were using. I've been using VirtualBox headless for a while (managing it via CLI then from phpvirtualbox cuz I'm lazy :p)

Shouldn't really have a reason to run a GUI as there are web frontends you can use. :)

---

### Post by Demented ZA on 2011-06-23
> **CharlesA said:**
> I didn't see anywhere that said that VM software you were using. I've been using VirtualBox headless for a while (managing it via CLI then from phpvirtualbox cuz I'm lazy :p)

Shouldn't really have a reason to run a GUI as there are web frontends you can use. :)

+1

I'm running the same setup. I specifically wanted to run a strictly no-gui setup. works beautifully! Also wrote a script to pause my VMs upon restarting the system and starting certain VMs persistently. No Gui means less user interaction =  reducing the single biggest IT problem: the user :tongue:

---

### Post by CharlesA on 2011-06-23
> **Demented ZA said:**
> +1

I'm running the same setup. I specifically wanted to run a strictly no-gui setup. works beautifully! Also wrote a script to pause my VMs upon restarting the system and starting certain VMs persistently. No Gui means less user interaction =  reducing the single biggest IT problem: the user :tongue:

Yep. I have similar scripts too. Works wonderfully.

Plus you don't run into problems with the GUI not starting up for whatever reason (graphics drivers after a kernel update, for instance).

---

### Post by Demented ZA on 2011-06-23
> **CharlesA said:**
> Yep. I have similar scripts too. Works wonderfully.

Plus you don't run into problems with the GUI not starting up for whatever reason (graphics drivers after a kernel update, for instance).

Exactly!

Only problem I have is that my VMs actually slow down and stutter if I install guest additions. Without them things run super smooth. Seems to be something with timing or interrupts. problem escalates using Firefox on the VM. Running on a second generation Quad Core i5 2500k, not overclocked (yet :-)  ) Ubuntu 64-bit 11.04.

Its not bothering me, and I'm not trying to hijack the thread, just saying I'm all for gui-less like the rest :-)

---

### Post by CharlesA on 2011-06-23
> **Demented ZA said:**
> Exactly!

Only problem I have is that my VMs actually slow down and stutter if I install guest additions. Without them things run super smooth. Seems to be something with timing or interrupts. problem escalates using Firefox on the VM. Running on a second generation Quad Core i5 2500k, not overclocked (yet :-)  ) Ubuntu 64-bit 11.04.

Its not bothering me, and I'm not trying to hijack the thread, just saying I'm all for gui-less like the rest :-)

Curious, but are you just using VRDP or another method of accessing the guest VM?

I've been using Windows Remote Desktop for windows guests (since I don't have any "home" versions running, and NXserver from nomachine.com for Linux guests. Haven't noticed any problems (and I haven't had to install the guest additions either).

---

### Post by Sorky on 2011-06-23
Thanks for the responses so far!
 
> **Maheriano said:**
> I fail to see anywhere in your post where you require a GUI.
 
The reason I assume I need a GUI is > **Sorky said:**
> * I would load the gui to access my VM & basic stuff (eg: file copy)  I'm assuming I need a GUI (window manager) to hold the window that will open when I want to view MY VM while sitting AT the Server. I expect to run all VMs (except mine) headless on the server. 
 
When at the server I would run with a head, when away from the server I'd use SSH to start it headless and then RDP in.
 
PS: Yes, I intend to use VirtuaBox (I've got this part all sorted nicely).

---

### Post by Sorky on 2011-06-23
> **lykwydchykyn said:**
> Have you looked at setting up LTSP and booting your clients over the network? That looks suspiciously like what you're trying to accomplish.
 
Hadn't heard of it, but that is exactly the sort of thing what I want for my clients - Thanks! 
 
If I follow correctly, 
1) I need to install an LTSP server component in my Ubuntu Server 
2) The computers around the house can simply be built as LTSP clients!
3) I could even dual-boot these computers should they have to have their own OS ;-)
 
PS: Following on from the GUI for the Server question, if the VM can run VISIBLE on the server without a window manager, then I definitely can drop the GUI :-D

---

### Post by arrrghhh on 2011-06-24
> **Sorky said:**
> Hadn't heard of it, but that is exactly the sort of thing what I want for my clients - Thanks! 
 
If I follow correctly, 
1) I need to install an LTSP server component in my Ubuntu Server 
2) The computers around the house can simply be built as LTSP clients!
3) I could even dual-boot these computers should they have to have their own OS ;-)
 
PS: Following on from the GUI for the Server question, if the VM can run VISIBLE on the server without a window manager, then I definitely can drop the GUI :-D

1) Yes
2) Yes
3) Yes!  ;)

On your PS - that is interesting, I guess I always ssh to my server.  Even when I'm at home, I just ssh with a laptop or RDP to the VM that's running... I don't really want the overhead on my server, and with my particular setup it's kinda awkward to directly connect a monitor & actually "work" on the server.  I assume your setup is not awkward for this type of work... and I guess you can install gnome-core (so you don't get all the ubuntu-desktop stuff!) and work that way.  Just start gdm manually when you need it, and shut it down when you're done... There's a thread on it somehweres, I'll try to find it for ya.

Edit - 
So install with ```
sudo apt-get install gnome-core gdm xinit
```

Also, not the best example, but [this thread](http://ubuntuforums.org/showthread.php?t=1774280) goes thru what you would need for starting/stopping it...

---

### Post by lykwydchykyn on 2011-06-24
> **Sorky said:**
> Hadn't heard of it, but that is exactly the sort of thing what I want for my clients - Thanks! 
 
If I follow correctly, 
1) I need to install an LTSP server component in my Ubuntu Server 
2) The computers around the house can simply be built as LTSP clients!
3) I could even dual-boot these computers should they have to have their own OS ;-)
 
Yep, you just need to make sure they can boot to PXE -- most network cards from the last 5 years or so can.  With older ones it depends on the brand.

LTSP takes a bit of time and study to set up, but it works pretty well, and you can set up the clients to connect to RDP if that's what you need.  I've run an LTSP network for many years at work and it's reasonably reliable (though I've had a lot more trouble with Lucid Lynx, for some reason).


> 
PS: Following on from the GUI for the Server question, if the VM can run VISIBLE on the server without a window manager, then I definitely can drop the GUI :-D

Well, you'd at least need X11 and you'd probably want a WM.  I wouldn't waste resources with GNOME or any convential DE, you might just want to create ~/.xinitrc with something like this in it:
```

VBoxManage startvm "my_vm_name"

```

There may be a way to force it to fullscreen, not sure.  You may have trouble getting it to go fullscreen or deal with dialog boxes without a window manager running; if so use something light such as openbox or matchbox-window-manager.

---

### Post by Gyokuro on 2011-06-24
Just found this thread but I would suggest (as already other do) go with a non-GUI Ubuntu LTS Server and KVM (for VM's)- all headless, save CPU cycles, more secure (as it is less software on your system), easier to administer from a remote location,...

---

### Post by Sorky on 2011-06-25
> **Gyokuro said:**
> Just found this thread but I would suggest (as already other do) go with a non-GUI Ubuntu LTS Server and KVM (for VM's)- all headless, save CPU cycles, more secure (as it is less software on your system), easier to administer from a remote location,...

Like I said before - I'm happy to be called crazy if someone can tell me I can VIEW MY VM **ON** on the server without a GUI [ If all the other VMs suffer. bad luck - it's my server ;-) ]. Otherwise, I'm looking for the lightest weight GUI that I can load/stop as required.

---

### Post by Gyokuro on 2011-06-25
No - that want work and you need for your crazy idea :) a display manager - so you will need a minimal X window system and maybe as window manager twm - maybe somebody knows a smaller setup.

---

### Post by Sorky on 2011-06-26
> **Gyokuro said:**
> No - that want work and you need for your crazy idea :) a display manager - so you will need a minimal X window system and maybe as window manager twm - maybe somebody knows a smaller setup.

Been playing and fairly happy with the results so far... Pretty much covered my needs with "xinit" + "awesome" + "xfe" + "hplip" + "virtualbox-ose-qt" and "firefox" [so I can search for much needed assistance ;-) ]

Login and run xinit which loads awesome and then quit that back to the shell.

---

### Post by Sorky on 2011-07-22
Final update... 
 
I was happy with my prototype and I've now completed my new system. A few minor things to complete, but I'm pretty happy so far...
 
System
[LIST]
[*]QuadCore i7
[*]16Gb of RAM,
[*]500Mb SATA /// HD for the main disk
[*]1T SATA /// HD as a file share
[*]Networked printer
[*]UPS
[/LIST]Setup
[LIST]
[*]Ubuntu Server 64 [with SSH Server + PRINT + SAMBA]
[*]xinit + awesome + virtualbox + xfe + firefox
[/LIST]Usage
[LIST]
[*]Normally sitting at the console login
[*]File & Print sharing + Domain controller
[*]Virtual Machine Host
[LIST]
[*]When I want to use a PC,
[LIST]
[*]I login
[*]Load awesome (xinit)
[*]Run my virtual PC
[/LIST]
[*]Wife & Kids virtual PCs start "headless"
[LIST]
[*]They remotely access their running PC from any "box" around the house
[/LIST]
[/LIST]
[/LIST]I now have half a dozen PCs all running in the one system :)
 
:guitar:
 
PS: My thanks to those answers in here as well as the many other contributors posting in these forums!

---

