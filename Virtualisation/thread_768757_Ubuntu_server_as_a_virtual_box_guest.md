---
title: "Ubuntu server as a virtual box guest"
date: 2008-04-26
forum: Virtualisation
---

### Post by hise0001 on 2008-04-26
I'm running a fresh install of Hardy desktop and the Virtualbox OSE from the repositories.

I want to run Hardy server as a guest os in Virtualbox.  The install has completed successfully; but, when I launch the virtual Hardy server, I get the error....

> 
Starting up...
This kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel apprpriate for your CPU.


My host Hardy desktop is 32bit running on an AMD64 and the guest Hardy server is 32bit.

Any help would be greatly appreciated!

---

### Post by alex_f on 2008-04-26
Hi,

I experience the same problem but not on a virtual box. Directly installed on the hardware.

I downloaded the image of Ubuntu server edition 8.04 from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) to install it.

I changed laptop few months ago and I wanted to test Ubuntu server (I want a LAMP Server) in my older laptop before installing into a proper server.

All the installation steps are going ok. Network detected, partitioning ok, package installation ok but when I have to reboot, Grub can't launch the Kernel and I end with this error:

```
the kernel requires the following features not present in the CPU: 0:6
```

I precise that:
[LIST]
[*]I downloaded the x86 version
[*]I my laptop is a Centrino (so a x86 processor)
[*]The laptop was previously running successfully ubuntu (from Breezy to Feisty)
[/LIST]

Thanks for any help.

Cheers

Alex

---

### Post by tighem on 2008-04-27
Check out the following:

[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

Basically the wrong kernel is getting installed. You'll need to rescue a broken system and change it.

---

### Post by dynacrylic on 2008-04-27
> **tighem said:**
> Check out the following:

[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

Basically the wrong kernel is getting installed. You'll need to rescue a broken system and change it.

This resolved my problem, thanks!

> 

[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

 Filipe Bonjour said on 2008-02-06:

Jeronimo, I find that the fix of bug 151942 works here too. You have to boot the server install CD and choose "Rescue a broken system". When you get the prompt, run "apt-get install linux-generic" to install the generic kernel. Reboot and choose the new kernel in GRUB.





I installed Ubuntu 8.04 server on my Leopard MacBook Pro inside virtualbox. Just do as stated:
1) boot to "Rescue a broken system"
2) follow the menu through until you get to something link run a command from shell
3) type "apt-get install linux-generic"
4) after it's done installing reboot
5) while in grub, escape out and select the generic kernel install

It was much easier than I thought.


Thanks for sharing that link!

---

### Post by tnl2k7 on 2008-04-28
dynacrylic thanks,

That's just my saved my rather depressed VirtualBox virtual machine...it wouldn't boot. Some stupid error about a feature called '0:6' not being present on my CPU.

-Luke.

---

### Post by nexxus07 on 2008-04-30
I additionally removed the old kernel server image since it is not needed anymore which frees up around 100MB.

sudo apt-get remove linux-image-<Version>-server
(if you don't know use the keys "tab tab" if you want autocompletion)

I accepted the Grub modification and it booted straight into the now generic kernel. 

I wonder what performance wise the best kernel image is to run in Virtual Box?

---

### Post by It guy on 2008-05-01
I have tried all the methods above i.e the

apt-get install linux-generic

I do this after selecting the dir dir/sva1 or something like that. Then I select run cmommand from dir/sva 1 and type apt-get install linux-gereric.

Then I get:

E: linux-generic not found

What do I do?

---

### Post by nexxus07 on 2008-05-01
I'm confused by the E:. Where does it come from and btw which Version of ubuntu are you trying this on?

does the linux-generic autocomplete with "tab tab"? 
you know you can autocomplete commands in the console with tab tab to prevent typos.

Are you sure you did sudo apt-get update?

apart from that I can only think of a problem with your /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

it should have at least the part above to be able to query the repository


Does this make sense? let us know how you get on.

---

### Post by iClou on 2008-05-02
> **dynacrylic said:**
> This resolved my problem, thanks!





I installed Ubuntu 8.04 server on my Leopard MacBook Pro inside virtualbox. Just do as stated:
1) boot to "Rescue a broken system"
2) follow the menu through until you get to something link run a command from shell
3) type "apt-get install linux-generic"
4) after it's done installing reboot
5) while in grub, escape out and select the generic kernel install

It was much easier than I thought.


Thanks for sharing that link!
I successfully installed linux-generic and I was able to boot this image.
But I do not have network access anymore:
**ping google.com**
...unknown host

eth0 is not configured - how do I have to configure it?

**ifup eth0**
socket: Address family not supported by protocol - make sure CONIFG_PACKET and CONFIG_FILTER are enabled in your kernel configuration.

How can I resolve that?
--
Thanks for any help
Mike

---

### Post by iClou on 2008-05-02
This thread solved my issue!
[http://ubuntuforums.org/showthread.php?t=737305](http://ubuntuforums.org/showthread.php?t=737305)
--
Thanks very much
Mike

---

### Post by It guy on 2008-05-02
I am unsure as to were the E comes from. I am running ubuntu server 8.04. This si the exact message:

reading package lists...DONE
building dependancy tree
building state information...DONE
E: Couldnt find package linux-generic

~~~

If I try sudo apt-get all I get is

SUDO: unable to resolve host ubuntuserver

!!!

---

### Post by It guy on 2008-05-06
finally got the server installed and up and running with a new generic kernel but all i get is a command interface where I log in a and perform tasks. How do I get the G.U.I and desktop etc. 

thanks,

---

### Post by nexxus07 on 2008-05-06
If you want the full desktop experience you might want to consider installing the ubuntu desktop edition in the first place. I think there is also the option to install gnome in the setup menu during the installation on the server edition. 


Personally I have installed fluxbox as a window manager in a second step too because it is one of the smallest windowmanagers around and I need a minimalistic system. The look and feel however might not suit everyone.

To install fluxbox as far as I remember

```
sudo apt-get install fluxbox xorg
```

once you are logged on to the console you can then type 
startx

and fluxbox should start up. 


This might help configuring if you decide to give fluxbox a go too. 
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Alternatively have a look at this thread which deals with installing the default gnome desktop on a server edition.

[http://ubuntuforums.org/showthread.php?t=186298](http://ubuntuforums.org/showthread.php?t=186298)



hope this helps,
Thomas

---

### Post by begemot. on 2008-06-12
I have had the topic-problem too with ...-server-i386.iso


> **tighem said:**
> Check out the following:
[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)
Basically the wrong kernel is getting installed. You'll need to rescue a broken system and change it.

This post solved my deal.
Thank You!

---

### Post by robsearles on 2008-11-12
I too was having problems with Hardy guest on Intrepid host coming up with:

[INDENT]This kernel requires the following features not present on the CPU:
0:6[/INDENT]

Googled the problem and arrived at this thread.
I just wanted to post a quick thanks to dynacrylic, it worked like a charm!

Cheers
Rob

---

### Post by Keneo on 2008-12-21
I wanted to add that the most easy way is to just go to virtualbox: settings, (general) advanced 
and tick the PAE/NX box.

---

### Post by bodhi.zazen on 2008-12-21
> **Keneo said:**
> I wanted to add that the most easy way is to just go to virtualbox: settings, (general) advanced 
and tick the PAE/NX box.

yes, but that only works if you have the correct hardware. If your CPU is not PAE enabled it will not work, in which case you need to install the generic kernel.

---

