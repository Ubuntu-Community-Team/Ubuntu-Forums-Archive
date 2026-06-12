---
title: "Question about sending in laptop for check up"
date: 2007-02-12
forum: The Cafe
---

### Post by PartisanEntity on 2007-02-12
I bought an Asus laptop last year, it came with win xp, since about 4 months now I have been using ubuntu and have removed win xp.

I would like to send in my laptop because the fans are on often and quite loud, I always thought it was normal for the Turion processor, but I met someone with the same laptop recently and theirs was very very quiet. So i would like to send in my laptop to have it checked.

Now, will it matter what OS is installed? Do i need to give Asus technicians access to my OS? Do i have to reinstall win xp?

Anyone have experience with this?

---

### Post by jazzgossen on 2007-02-12
Did the other person also have Ubuntu, or any Linux version, installed? I have read reports that laptops often run hotter (and consequently the fans have to work more) on Linux than on Windows. It has to do with how CPU frequency scaling and undervolting is done. You can try looking at laptop-mode tools (look [here]("http://www.samwel.tk/laptop_mode/index.html"), also in the repo's).

---

### Post by PartisanEntity on 2007-02-12
he had windows, but my laptop does this under both windows and ubuntu.

---

### Post by Fribble on 2007-02-12
It might be worth having a read through the fine print of your warranty, to see if it mentions anything about changing the OS. Many companies still offer no support for Linux, so servicing it may be difficult for them, but I'm fairly sure that your warranty shouldn't be void at least. But... check first, hehe.

---

### Post by mips on 2007-02-12
Some places are full of shite when it comes to linux and will blame it for just about anything.

Create a small partition at the begiining of the drive and restore windows. this way it only boots into windows and they wont see grub or linux. Back up your data and send of the computer.

Or ask them if you can send it in without the hard drive.

---

### Post by Spr0k3t on 2007-02-12
On my lappy the fan was on almost constant with Windows installed and wouldn't last for more than 1.75 hours on battery.  Since Ubuntu, I have yet to hear the fan kick on at all and the system will run for almost 4 hours on battery.  

This is what I would do.  Back up your entire drive to an external drive.  Then do a system restore using the CD or DVD to install a clean copy of XP configured to their specifications.  Order a new laptop drive for your system.  When the lappy comes back, install the new drive, partition it to your liking and restore your files.  Take the original drive and stick it on a shelf somewhere in case you need to send it back in at some point.

---

### Post by PartisanEntity on 2007-02-12
Thanks to all for the advice so far.

> **Spr0k3t said:**
> On my lappy the fan was on almost constant with Windows installed and wouldn't last for more than 1.75 hours on battery.  Since Ubuntu, I have yet to hear the fan kick on at all and the system will run for almost 4 hours on battery.  

This is what I would do.  Back up your entire drive to an external drive.  Then do a system restore using the CD or DVD to install a clean copy of XP configured to their specifications.  Order a new laptop drive for your system.  When the lappy comes back, install the new drive, partition it to your liking and restore your files.  Take the original drive and stick it on a shelf somewhere in case you need to send it back in at some point.

I'm such a thick-head, you just reminded me that I have a spare laptop HDD lying around with a win xp installation on it. Its the actual hdd that came with my laptop when i bought it :)

A new, but related question.

My processor is a **Turion** (not the X2 dual core version) so that's **AMD**. Now I just realised that ever since I installed Dapper I have been using the **386** kernel. I noticed there is a **K7** kernel, but is that compatible with the **Turion**?

Are there any advantages to using the **K7** kernal on a **Turion** based laptop?

As far as I know the **K7** kernel is for **Athlons** only?

Thanks

---

### Post by Spr0k3t on 2007-02-14
> **PartisanEntity said:**
> I'm such a thick-head, you just reminded me that I have a spare laptop HDD lying around with a win xp installation on it. Its the actual hdd that came with my laptop when i bought it :)

HAHAH!  Yeah, I think I've even been there myself.  Whatever happened to the awesome A&W commercials: "It's good to be thick-headed"?  Glad to know that will work for your needs.

> **PartisanEntity said:**
> A new, but related question.

My processor is a **Turion** (not the X2 dual core version) so that's **AMD**. Now I just realised that ever since I installed Dapper I have been using the **386** kernel. I noticed there is a **K7** kernel, but is that compatible with the **Turion**?

Are there any advantages to using the **K7** kernal on a **Turion** based laptop?

As far as I know the **K7** kernel is for **Athlons** only?

Thanks

This depends on whether the turion is 64bit capable or not.  I'm not sure on the turion processors, so you may need to look this up.  I do know that you can pop in the AMD64 live disc and attempt a boot.  If there are any complications it will tell you prior to loading up all the way.  The benefits will not be obvious until you are running at least 1.5GB memory.  At that point, you should see close to 20% speed increase.

---

### Post by FurryNemesis on 2007-02-14
If the fan sounds at all rattle - y you might want to check the fan bay for obstructions or muck. Whatever you find give it a blast of compressed air through the fan vents as it might be a hardware fault  - I have to do this about once every 3 weeks with my lappy to clear out fluff which makes the fan sound like a little jet engine...

---

### Post by PartisanEntity on 2007-02-14
> **Spr0k3t said:**
> This depends on whether the turion is 64bit capable or not.  I'm not sure on the turion processors, so you may need to look this up.  I do know that you can pop in the AMD64 live disc and attempt a boot.  If there are any complications it will tell you prior to loading up all the way.  The benefits will not be obvious until you are running at least 1.5GB memory.  At that point, you should see close to 20% speed increase.

Yes the Turion is 64bit capable. I have 2GB of ram.

Which kernel should I install and how should I install it to prevent anything breaking during updates?

---

### Post by darkhatter on 2007-02-14
I've got a turion64 X2 not really the same chip but this is quite in both windows and Linux

---

### Post by Spr0k3t on 2007-02-14
> **PartisanEntity said:**
> Which kernel should I install and how should I install it to prevent anything breaking during updates?

Your lappy will love the AMD64 version.

---

### Post by PartisanEntity on 2007-02-14
> **Spr0k3t said:**
> Your lappy will love the AMD64 version.

So which package do i need to install or is there more than one?

---

### Post by mips on 2007-02-14
> **PartisanEntity said:**
> So which package do i need to install or is there more than one?

You need to download the 64bit iso, alternate or desktop cd whatever you prefer.

[http://ubuntu.inode.at/cdimage/6.06/](http://ubuntu.inode.at/cdimage/6.06/)
[ubuntu-6.06.1-alternate-amd64.iso]("http://ubuntu.inode.at/cdimage/6.06/ubuntu-6.06.1-alternate-amd64.iso")
or
[ubuntu-6.06.1-desktop-amd64.iso]("http://ubuntu.inode.at/cdimage/6.06/ubuntu-6.06.1-desktop-amd64.iso")

Be warned though, the 64bit version is not as easy to get going as the 32 bit version. i suggest you do some research first and then decide.

---

### Post by FuturePilot on 2007-02-14
> **jazzgossen said:**
> Did the other person also have Ubuntu, or any Linux version, installed? I have read reports that laptops often run hotter (and consequently the fans have to work more) on Linux than on Windows. It has to do with how CPU frequency scaling and undervolting is done. You can try looking at laptop-mode tools (look [here]("http://www.samwel.tk/laptop_mode/index.html"), also in the repo's).

Actually my laptop runs *a lot* cooler with Ubuntu. The fan is like almost always running in Windows.

---

### Post by PartisanEntity on 2007-02-15
> **mips said:**
> You need to download the 64bit iso, alternate or desktop cd whatever you prefer.

[http://ubuntu.inode.at/cdimage/6.06/](http://ubuntu.inode.at/cdimage/6.06/)
[ubuntu-6.06.1-alternate-amd64.iso]("http://ubuntu.inode.at/cdimage/6.06/ubuntu-6.06.1-alternate-amd64.iso")
or
[ubuntu-6.06.1-desktop-amd64.iso]("http://ubuntu.inode.at/cdimage/6.06/ubuntu-6.06.1-desktop-amd64.iso")

Be warned though, the 64bit version is not as easy to get going as the 32 bit version. i suggest you do some research first and then decide.

Im sorry there seems to be a misunderstanding here. I would rather not use 64bit at the moment, also I was actually asking about the kernel version? For example, should I install the k7 image? And if yes, how should I install it, which packages?

---

### Post by Spr0k3t on 2007-02-15
> **PartisanEntity said:**
> Im sorry there seems to be a misunderstanding here. I would rather not use 64bit at the moment, also I was actually asking about the kernel version? For example, should I install the k7 image? And if yes, how should I install it, which packages?

There's a specific K7 kernel package?  Odd, I don't know if you would have any benefit of using the Turion (K8 Core) with the older core.  I'd stick with the one you currently have for now.

The AMD K7 processors were around before the T-Bird chips... That core was stopped around 1.2GHz if I'm not mistaken.

---

### Post by Spr0k3t on 2007-02-15
> **mips said:**
> Be warned though, the 64bit version is not as easy to get going as the 32 bit version. i suggest you do some research first and then decide.

I'm running the AMD64 version on my main computer system.  Getting the system going wasn't the problem; it's watching flash, certain video codecs, and some 3rd party drivers.  But that's a whole different ball of wax.

---

### Post by PartisanEntity on 2007-02-15
okay thanks for the info, i guess in this case im sticking to the 386 image.

---

