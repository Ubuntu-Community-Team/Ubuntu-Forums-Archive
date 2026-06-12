---
title: "Has anybody installed a recent daily build to VMware Player"
date: 2012-01-16
forum: Virtualisation
---

### Post by mparillo on 2012-01-16
Since I posted this question:
[https://answers.launchpad.net/ubuntu/+source/vmware-player/+question/184650](https://answers.launchpad.net/ubuntu/+source/vmware-player/+question/184650)
I have also tried the 0115 and 0116 daily builds, of both Kubuntu and Ubuntu.
They seem to install cleanly, shut down, and never come up on a re-start.

I am running VMware Player 4.01 on Win7.

Is anybody else successful?

---

### Post by mparillo on 2012-01-17
I was successful on VirtualBox, but not on VMware player.
But I prefer VMware Player, as it seems to 'just work'.
 - Mouse performance seems native.
 - When I maximize my display it feels native on my screen.
 - I did not have to fiddle with mounting and unmounting my ISO, and adding CPU options.

---

### Post by mparillo on 2012-01-18
Work-around:
Instead of pointing VMware Player directly to the ISO and using Easy Install, select the option to Install the Operating System later. With this option, I was able to manually install the 2012.01.18 daily Kubuntu build (the buttons for Ubuntu were outside the VMware window, and I could not scroll).

---

### Post by dcstar on 2012-01-20
> **mparillo said:**
> Work-around:
Instead of pointing VMware Player directly to the ISO and using Easy Install, select the option to Install the Operating System later. With this option, I was able to manually install the 2012.01.18 daily Kubuntu build (the buttons for Ubuntu were outside the VMware window, and I could not scroll).

VMware will not usually function with or support a new Ubuntu client version until **after** it is officially released.

You use development releases like 12.04 at your own peril (unfortunately), too many things seem to radically change in Ubuntu releases these days for third-party platforms to keep up with.

---

### Post by mparillo on 2012-01-20
Thank you David.
I was not really expecting VMware to support a *buntu 12.04 build.
That is why I was posting on this forum rather than on theirs ;-)

I was wondering if anybody was successful with VMware player anyway.
With the VMware Easy Install option, I have found it to be the easiest way to try a variety of distributions.

But if forum etiquette requires me to mark this thread as solved, I understand.

---

### Post by dcstar on 2012-01-23
> **mparillo said:**
> 
...........
With the VMware Easy Install option, I have found it to be the easiest way to try a variety of distributions.

But if forum etiquette requires me to mark this thread as solved, I understand.

The "Easy Install" option is specifically set up for particular releases of supported client OSs - it is the **last** thing you want to use for an unsupported OS.

It is actually fairly useless for supported Ubuntu releases as well, last time I tried to use it the LOCALE setup for the VM was locked at the USA and made the VM useless for me (without a lot of subsequent mucking around).

---

### Post by dcstar on 2012-02-04
> **mparillo said:**
> Since I posted this question:
[https://answers.launchpad.net/ubuntu/+source/vmware-player/+question/184650](https://answers.launchpad.net/ubuntu/+source/vmware-player/+question/184650)
I have also tried the 0115 and 0116 daily builds, of both Kubuntu and Ubuntu.
They seem to install cleanly, shut down, and never come up on a re-start.

I am running VMware Player 4.01 on Win7.

Is anybody else successful?

I have just successfully installed 12.04 Ubuntu 64-bit daily build 4th Feb on VMware Player 4.0.2. This was a manual install using the daily build ISO. VM restarts fine.

The only issue so far is that I cannot install VMware Tools as I get a "Could not find component on update server...." message. This probably indicates that VMware has not yet verified that the Tools works with 12.04.

---

### Post by mparillo on 2012-02-06
Thank you, dcstar. I just installed Kubuntu Alpha 2, and I was forced to manually install also. I assume the reason Easy Install fails is related to your error message on the VMware Tools installation.

---

### Post by dcstar on 2012-02-07
> **mparillo said:**
> Thank you, dcstar. I just installed Kubuntu Alpha 2, and I was forced to manually install also. I assume the reason Easy Install fails is related to your error message on the VMware Tools installation.

Player 4.0.2 is broken, 4.0.1 installs VMware Tools fine.

My Ubuntu 12.04 Alpha was total rubbish using Unity & Compiz - the graphics just doesn't work in the VM properly.

Using Gnome 3 without effects seems to work well, the only issue I have is with logging into HTTPS sites like Launchpad using Firefox 11 - I can't report bugs!!!

---

### Post by mparillo on 2012-03-02
Recently VMware pushed version 4.0.2 of VMware Player.
I was able to point VMware Player directly to the ISO and select Easy Install to install both Kubuntu 12.04 Beta 1 and Ubuntu 12.04 Beta 1 each with VMware Tools.

---

### Post by NOELV on 2012-03-12
What about the login-screen and/of the default back-ground, what are the colors / color depth ?

Are they looking good ? Or do you see a bad color gradient ?


Regards
Noel

---

### Post by mparillo on 2012-03-12
> **NOELV said:**
> What about the login-screen and/of the default back-ground, what are the colors / color depth ?

Are they looking good ? Or do you see a bad color gradient ?


Regards
Noel

I think they look great on Kubuntu 12.04 and Ubuntu 12.04 Beta-1.
The default login screen is a bit smaller than my monitor, but I simply maximize it.
I think the KDE 4.8 wallpaper is less interesting than 4.7, but I have a custom one I use as soon as I login, so that does not matter much to me.
I was pleasantly surprised when Unity changed my login wallpaper before I even logged in.
I will report my color / color depth if I can see it in Unity. KDE seems to bury it in x.conf.

---

