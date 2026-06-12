---
title: "Making the plug with KVM"
date: 2016-05-26
forum: Virtualisation
---

### Post by kcallis on 2016-05-26
I installed Ubuntu 16.04 and after working hard to make it work, finally got wireless going. So I am dinking around with command line and while I am no a neophyte to the command line, I figured that life would move a little quicker if I added a desktop component. I initially installed mate, but later inadvertently installed ubuntu-mate-desktop, which wasn't a show stopper, but was not what I really wanted. I am hoping that someone will guide me on how to setup grub so that that the following happens:

The grub menu will look like this:

Mate w/ KVM
Server 16.04 w/ KVM

Basically, I would like from the grub menu the option to allow me to get Desktop or got strictly to command line. I also wish that I could stop both the Mate grub menu and standard grub menu, but I will save that for another forum board. Any pointers would be greatly appreciated, because some times the desktop is nice, but really I would like that to be a failback since I am really trying to get my hands on using KVM and evenually, openvswitch and openstack, so the need for desktop should be nominal.

---

### Post by MAFoElffen on 2016-05-27
??? You have confused me. So now let me get this straight in my own head. (you are talking about your host and not a VM Guest right?)

- You installed 16.04 server edition.
- You installed ubuntu-mate-desktop onto server.

*** Did you install KVM yet?

- You want to configure your grub 2 boot menu to do something with is not really a function of grub 2...

You understand what Grub 2 is right? GNU Grub 2 is your boot manager, which boots installations present on your hardware. In what you describe that you want on your menu, one would think that you had multiple installations under a dual-boot scenario, with one being Mate, and another being Ubuntu Server, with the Grub Menu controlling which installation to boot to... KVM in just a virtualization service. Your post infers that it would be install on both installations. 

***I'm thinking that is not what you meant.

I'm thinking that you are talking about one single installation, with the ability to turn the desktop on and off. Is this what you are referring to? Or do you just want to be able to get to console, without being inside a terminal window?

I've done all that, just to see if I could do it. I can tell you that you have all those capabilities without changing a thing right? Just learning a few key strokes and commands... For instance access to the other virtual console sessions is <Cntrl><Alt><F2>, with F1 thorugh F6 being Virt. Terminal Consoles 1-6 and <Cntrl><Alt><F7> being your graphics console.

Or do you want the capability to not have your X-Window (graphics layer) overhead running all the time?

As for KVM--- If you were thinking about access to an OS, installed and configured, and if you already have KVM installed, then why aren't you using that to do that with? That is where you will save space, time and resources. Virtualization is this section. And that is where you will gain and better utilize your resources in the short time and the long run.

So what do you have? What do you want to do? And how do you want to get there? Those are the questions you need to ask yourself and ask if you need help in getting there. We are here to help you with that. I just want to help guide you n doing that "smartly." (without wasting your time and resources.)

EDIT-- Of course if I took your post as literal, with just one installation present, then just create a single custom menu entry, which would be a copy of your current kernel entry, but with the kernel boot option "text" appended to the end of the boot line, which would boot your Server Edition (with Mate) in text console mode... The drawback to this, would be every time your kernel updated, you would have to manually update that entry to point to the then current kernel.

---

### Post by kcallis on 2016-05-28
> **MAFoElffen said:**
> ??? You have confused me. So now let me get this straight in my own head. (you are talking about your host and not a VM Guest right?)

- You installed 16.04 server edition.
- You installed ubuntu-mate-desktop onto server.

*** Did you install KVM yet?

- You want to configure your grub 2 boot menu to do something with is not really a function of grub 2...

You understand what Grub 2 is right? GNU Grub 2 is your boot manager, which boots installations present on your hardware. In what you describe that you want on your menu, one would think that you had multiple installations under a dual-boot scenario, with one being Mate, and another being Ubuntu Server, with the Grub Menu controlling which installation to boot to... KVM in just a virtualization service. Your post infers that it would be install on both installations. 

***I'm thinking that is not what you meant.

I'm thinking that you are talking about one single installation, with the ability to turn the desktop on and off. Is this what you are referring to? Or do you just want to be able to get to console, without being inside a terminal window?

I've done all that, just to see if I could do it. I can tell you that you have all those capabilities without changing a thing right? Just learning a few key strokes and commands... For instance access to the other virtual console sessions is <Cntrl><Alt><F2>, with F1 thorugh F6 being Virt. Terminal Consoles 1-6 and <Cntrl><Alt><F7> being your graphics console.

Or do you want the capability to not have your X-Window (graphics layer) overhead running all the time?

As for KVM--- If you were thinking about access to an OS, installed and configured, and if you already have KVM installed, then why aren't you using that to do that with? That is where you will save space, time and resources. Virtualization is this section. And that is where you will gain and better utilize your resources in the short time and the long run.

So what do you have? What do you want to do? And how do you want to get there? Those are the questions you need to ask yourself and ask if you need help in getting there. We are here to help you with that. I just want to help guide you n doing that "smartly." (without wasting your time and resources.)

EDIT-- Of course if I took your post as literal, with just one installation present, then just create a single custom menu entry, which would be a copy of your current kernel entry, but with the kernel boot option "text" appended to the end of the boot line, which would boot your Server Edition (with Mate) in text console mode... The drawback to this, would be every time your kernel updated, you would have to manually update that entry to point to the then current kernel.

I know that my posting was very confusing, because I had been awake for over 32 hours, and I am not even sure what direction I was going. 

To be as succinct as possible, I installed US 16.04 and was having an issue with wireless. I decided to install mate desktop so that I could quickly get wifi working with network-manager, as well as be able to get to the browser so that I could bother folk on **Ubuntu Forum** with my question! :P Because I installed ubuntu-mate-desktop, I ended up with the whole sha-bang of needless crap. To add to the problem, is that I can never seem to get straight into command-line when I boot. I was able to figure out how to get command-line boot working somewhat:

```
sudo systemctl set-default multi-user.target
```

Of course, that opened up other issues with wifi and also the fact that startx doesn't work (actually, I try to to **setsid marco**, but that fails as well. But that is another issue all together. Someone did say I should have just worked on getting KVM working, and then install a Desktop image as a guest and go from there, but again, baby set. So yes, I do have KVM working; Yes, unfortunately, I am still booting to a desktop environment, but at least the wifi is working; Yes, I have docker working, but my intention was to have docker working under a server environment as opposed to the overhead of having the desktop environment. Hell, I was even able to create a raw partition and get a CoreOS image running under KVM.

My problem is that although the things are working, it is messy and not something that should be in play. My goal was to create a server, get KVM working, get several guests in play, play with lxc (or I should say lxd), get openvswitch working, and occasionally fire up a desktop for when I need to deal with a GUI. I have been looking for a tutorial to try what I mentioned, but to no avail.

---

### Post by kcallis on 2016-05-28
And with that last post, I think I am going to blow away this machine and armed with the Server Guide and good coffee, I will make this thing work like it suppose to!

---

### Post by houstonbofh on 2016-05-30
The last time I tried this was on 14.04 so I do not know that it works on 16.04.  In installed "ubuntu-desktop" and then removed "lightdm" and it boots to cli.  From cli on the console, startx works.

---

### Post by MAFoElffen on 2016-06-01
(modestly) I am one thought by other's as being one of the Linux Graphic Layer guru's. 

I install minimal X on some of my servers... But I do not do it by installing a "<flavor_name_of>-desktop" package. When you do that, it will inevitably include that flavor's desktop applications and framework onto the Ubuntu core. True, that with the X Session, what links XServer and the Graphical Desktop Environment (DE) to the core at boot is the installation of the Graphical Logon Manager. Removing that will cause is to boot to console, then start with startx, closing back to the console...
"Smarter" is to install just the pieces you need. If you search on my username in the server section, and on minimal X in that section, I believe I have at posts in at least 2 threads, where I posted some minimal X install scripts that you cam modify to your own needs. 

Only additional notes is that the order you load the pieces does matter. Next, install full xserver package now. There is a dependent piece in a change that I haven't found which dependencies that was when they updated one of the iterations of that... I no-longer have the time to track that down myself at the moment.

---

