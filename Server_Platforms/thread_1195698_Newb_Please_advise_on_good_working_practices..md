---
title: "Newb: Please advise on good working practices."
date: 2009-06-24
forum: Server Platforms
---

### Post by Smartin on 2009-06-24
Hi,

The more time I spend on my Ubuntu 8.04 LTS + ISPConfig3 server, the more petrified I become of screwing something up, not being able to clear up the mess and having to start all over again.

Can you help me establish some sensible working practices?

1) How do you set up test sites/sandboxes where you can mess about until things work and then efficiently move your work to the 'production' side?

2) What is the best way to take a snapshot of my server so I can 'roll back' to a previous state if I make a screwup?

3) Does it make sense to 'hard link' my config files and php.ini files to a separate folder and make regular backups of this folder? Which files are the crucial ones on a mail/web server? (LAMP, Postfix, Courier)

Any other basics I should know on this topic?

Appreciate your advice :-)

Simon

---

### Post by antikristian on 2009-06-26
seems to me like you should be testing in a virtual environment.
Try installing in virtualbox or vmware, test, tweak, take snapshots, revert, then either do it for real on the proper hardware later, or copy the config files from the virtual servers.

---

### Post by Smartin on 2009-06-26
> **antikristian said:**
> seems to me like you should be testing in a virtual environment.
Try installing in virtualbox or vmware, test, tweak, take snapshots, revert, then either do it for real on the proper hardware later, or copy the config files from the virtual servers.

antikristian,

Thanks for your comment...

Is installing vmware something a newb can easily get to grips with?

My brain hurts bad enough as it is...

Is doing regular backups not an easier approach? Then roll back if disaster strikes?

Simon

---

### Post by antikristian on 2009-06-26
If you run it in a virtual environment you'll get these great buttons to start, stop, pause, create snapshots and revert to earlier snapshots. It makes it so much easier to experiment without fearing you have to reinstall or start a hefty recovery solution.

virtualbox and vmware are really easy to install and run, and they both come with a graphical user interface.

There are three versions I'd recommend for newer users, each with their own pros and cons, try them out either on a ubuntu desktop or windows computer since at least Virtualbox and VMWare Workstation works best in a desktop environment.

**Virtualbox **
Pros:
Easy to install, on ubuntu you run ```
sudo apt-get install virtualbox-ose
```
Easy to configure. 
Free, Open source
Cons:
No USB support on the version that's included with Ubuntu, possible to download a closed source version with usb support

**VMWare Workstation**
Pros:
Really Kick-***:D
USB support
Easy to configure
Possible to connect to it with a remote console
Can store several snapshots of each virtual machine
Cons: 
A bit pricey, but it might be worth it
May require a few tweeks to install and run on ubuntu

**VMWare Server 2.0**
Pros:
Server grade virtualization
Can run on a headless server easily
Free
USB support
Cons:
Crappy web interface with crappy bugs in it
Really crappy web interface
Did I tell you about the web interface??
May require a few tweeks to install and run on ubuntu


I'd go with Virtualbox if I were you, but VMWare Workstation is also a really nice product

---

### Post by windependence on 2009-06-26
You left out VMware ESXi. No OS needed, great web interface, more robust than Server. Cons: Picky about storage. 

-Tim

---

### Post by Kareeser on 2009-06-26
I also think using a VM is a good idea. You can muck it up real bad, and then just start over at the click of a button (more or less).

It's true that there's a feeling of "I don't want to mess it up" when you're working with your server, but in the end - even if you screw up, what you've learned while setting up your server will help you to re-setup your server much quicker than before.

It took me weeks of tweaking to get my server set up properly, and when I had a catastrophic hard drive failure, I had the server back up and running in less than a day.

---

### Post by cariboo on 2009-06-27
The main thing I would suggest is to make a backup of the file you are about to edit, before doing anything else.

---

### Post by Smartin on 2009-06-27
Guys,

Really appreciate all the responses.

Sounds like virtualbox is the way I should go, if only I had a spare desktop computer :D

What do you recommend as a way to make incremental backups so that I could make a backup just before trying something out and then roll back to a previous state if I mess up too badly?

Or is that not a viable way to work...?

Simon

---

### Post by Smartin on 2009-06-27
> **windependence said:**
> You left out VMware ESXi. No OS needed, great web interface, more robust than Server. Cons: Picky about storage. 

-Tim

Tim,

This looks interesting but I'm guessing I can't retro-fit it to my server? Doesn't it have to be the first thing installed?

I need a spare box...

S

---

### Post by Smartin on 2009-06-27
> **cariboo907 said:**
> The main thing I would suggest is to make a backup of the file you are about to edit, before doing anything else.

cariboo907,

I'm going to get into the habit of this for sure :-)

S

---

### Post by windependence on 2009-06-27
> **Smartin said:**
> Tim,

This looks interesting but I'm guessing I can't retro-fit it to my server? Doesn't it have to be the first thing installed?

I need a spare box...

S

You could do it, but you'd have to  convert your physical machine to a VM using the free VMware converter, and then save the VM somewhere until you get ESXi loaded. Then you can just import the VM and fire it up. After all that you can ust keep creating new VMs to your heart's content.

-Tim

---

### Post by Smartin on 2009-06-27
> **windependence said:**
> You could do it, but you'd have to  convert your physical machine to a VM using the free VMware converter, and then save the VM somewhere until you get ESXi loaded. Then you can just import the VM and fire it up. After all that you can ust keep creating new VMs to your heart's content.

-Tim

Tim,

Seems to me I need to lay my hands on another box to play with this stuff on.

That would be best. Yes?

Thanks for your help though!

S

---

### Post by antikristian on 2009-06-27
> **windependence said:**
> You left out VMware ESXi. No OS needed, great web interface, more robust than Server. Cons: Picky about storage. 

-Tim

I have been wanting to try out ESXi for some time, but isn't it also picky about the hardware? I read on their site a while ago, that you had to run it on servers that they have tested it on, like specific dell servers etc. Can it run on older hardware?

---

