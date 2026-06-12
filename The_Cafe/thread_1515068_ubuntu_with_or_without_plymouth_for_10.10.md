---
title: "ubuntu with or without plymouth for 10.10"
date: 2010-06-21
forum: The Cafe
---

### Post by 5dolla on 2010-06-21
I was wondering how many people actually want this piece o crap in the future of 
Ubuntu.

---

### Post by Dustin2128 on 2010-06-21
Plymouth in ubuntu 10.10 or not? It's open source; you decide.

---

### Post by 5dolla on 2010-06-21
interesting. I think the idea of Plymouth is genuine. but ready for a distro as widely used as Ubuntu hardly.

---

### Post by Bachstelze on 2010-06-21
Haters are hating, good enough reason to keep it.

---

### Post by Simian Man on 2010-06-21
They're surely not going to remove it after putting it into the long term release version, so you can forget about that.

---

### Post by RiceMonster on 2010-06-21
"Yes Please keep Plymouth it rock even tho most of us can't use it"

Such an unbiased poll. No loaded options here.

---

### Post by SilverDragon on 2010-06-21
> **RiceMonster said:**
> "Yes Please keep Plymouth it rock even tho most of us can't use it"

Such an unbiased poll. No loaded options here.

I was thinking the same exact thing.

Plymouth works fine for me.

---

### Post by FuturePilot on 2010-06-21
Biased poll is biased.

---

### Post by 5dolla on 2010-06-21
no its not i use arch form my main os  haha i just hate to see Ubuntu users suffer.

---

### Post by Bachstelze on 2010-06-21
> **5dolla said:**
> no its not i use arch form my main os  haha i just hate to see Ubuntu users suffer.

Dear Arch user, please go back to the Arch community. We appreciate your empathy, but rest assured we will be just fine without you.

Thanks

The Ubuntu users

---

### Post by V for Vincent on 2010-06-22
> **5dolla said:**
> no its not i use arch form my main os  haha i just hate to see Ubuntu users suffer.

God. Biased polls *and* Arch snobbery?

---

### Post by betrunkenaffe on 2010-06-22
Nothing to see here.

/thread

---

### Post by Paqman on 2010-06-22
> **5dolla said:**
> no its not i use arch form my main os  haha i just hate to see Ubuntu users suffer.

-5 knowing-what-you're-talking-about points then.

---

### Post by Legendary_Bibo on 2010-06-22
What's plymouth? Isn't that the thing that has the purple screen that says "Ubuntu" and the five orange dots that turn white?

---

### Post by ad_267 on 2010-06-22
For those of us that have no problem with Plymouth can you explain what's wrong with it?

>  but ready for a distro as widely used as Ubuntu hardly.

Heard of a distro called Fedora? Seems pretty widely used to me...

---

### Post by bruno9779 on 2010-06-22
> **Bachstelze said:**
> Dear Arch user, please go back to the Arch community. We appreciate your empathy, but rest assured we will be just fine without you.

Thanks

The Ubuntu users

It is the 3rd hateful or about haters post I see from you today.

Are you doing fine Bachstelze?

By the way, aren't you an UF staff member anymore?

---

### Post by bryncoles on 2010-06-22
For those who *don't* know what he's talking about, you can check Plymouth's website [here](http://www.visitplymouth.co.uk/), and (of course) gather more accurate (as in additional information which happens to be accurate, not information of an increased accuracy) from [ol' reliable](http://en.wikipedia.org/wiki/Plymouth).

---

### Post by bruno9779 on 2010-06-22
And, Plymouth sucks.

If I want plymouth to work properly I have to give up 3D acceleration.

If I want 3D acceleration my boot is uglier and buggier than it was in 6.10 and my TTYs have huge hugly fonts

The only workaround I found, using VESA, gives me a nice boot, 3D acceleration, but no TTYs!!!

This aren't choices an user should be forced to make.

Especially when Nvidia (probably the most used GPU in linux) said explicitly that they are never gonna support the modules required for plymouth to work properly.

EDIT: oh, I almost forgot, my boot times have more than doubled. Canonical is better come up with something, I am getting increasingly frustrated and, as many others, I am thinking to change to some other distro. (Arch?)

---

### Post by betrunkenaffe on 2010-06-22
> **bruno9779 said:**
> Canonical is better come up with something

Oooo, I swear I just heard the entirety of canonical drop their lunch plates and run to fix that with the provided solution.

Other than the "installed nvidia drivers and now looks huge" bug (which is fixable, found solution online with complete step by step), it does it's job and my computer starts.

Oh, and since that walkthrough to fix the poor resolution, my boot up looks even better than ever.

---

### Post by Simian Man on 2010-06-22
> **bruno9779 said:**
> If I want plymouth to work properly I have to give up 3D acceleration.

If I want 3D acceleration my boot is uglier and buggier than it was in 6.10 and my TTYs have huge hugly fonts

The only workaround I found, using VESA, gives me a nice boot, 3D acceleration, but no TTYs!!!

This aren't choices an user should be forced to make.

Especially when Nvidia (probably the most used GPU in linux) said explicitly that they are never gonna support the modules required for plymouth to work properly.

Here's how plymouth + Nvidia work for me (on Fedora):

If I use the open source Nouveau driver I get a great looking boot screen, good TTYs and basic 3D support - fast enough to run compiz but not 3D games.

If I install the Nvidia driver, and add 0x318 to my boot parameters then I get good looking boot screen, good TTYs and great 3D support.  I have no idea why you would have no TTYs at all; I'd file a bug with Ubuntu.

BTW I fully expect the Nouveau and Gallium projects to improve quickly.  I expect we will no longer need Nvidia drivers for a great gaming experience on Linux.  Until Linux gets some better games that is :).

---

### Post by MadCookie on 2010-06-22
If they can make plymouth work properly, I thikn they should keep it :P

---

### Post by cbrunhaver on 2010-06-22
time for burg + plymouth?

---

### Post by samjh on 2010-06-22
Plymouth works for me also. Even when it didn't work, it didn't stop the computer from booting, so I don't why it should be dumped.

---

### Post by RiceMonster on 2010-06-22
> **Simian Man said:**
> If I install the Nvidia driver, and add 0x318 to my boot parameters then I get good looking boot screen, good TTYs and great 3D support..

Cool, haven't heard of that boot parameter. I'll have to try that. The VGA fall back on Fedora doesn't look great, but I actually don't mind it.

---

### Post by Simian Man on 2010-06-23
> **RiceMonster said:**
> Cool, haven't heard of that boot parameter. I'll have to try that. The VGA fall back on Fedora doesn't look great, but I actually don't mind it.

You actually have to put "vga=0x318" and the number could differ depending on the resolution you want/your setup supports.  You can see a chart [here]("http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html").  0x318 is 1024x768 with 24 bit colors which should work pretty much everywhere.  This just forces vga to use a certain screen resolution which not only improves the fallback boot graphics, but also increases the screen resolution on your virtual terminals.

---

### Post by kevdog on 2010-06-23
Where do you add these parameters to? xorg.conf?

---

### Post by FuturePilot on 2010-06-23
> **RiceMonster said:**
> Cool, haven't heard of that boot parameter. I'll have to try that. The VGA fall back on Fedora doesn't look great, but I actually don't mind it.

> **Simian Man said:**
> You actually have to put "vga=0x318" and the number could differ depending on the resolution you want/your setup supports.  You can see a chart [here]("http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html").  0x318 is 1024x768 with 24 bit colors which should work pretty much everywhere.  This just forces vga to use a certain screen resolution which not only improves the fallback boot graphics, but also increases the screen resolution on your virtual terminals.


VGA= is deprecated in Grub2. You have to use GRUB_GFXMODE=WxH in combination with GRUB_GFXPAYLOAD=WxH or in some cases only GRUB_GFXPAYLOAD_LINUX=WxHxD. (GRUB_GFXMODE and GRUB_GFXPAYLOAD did not work for me, but GRUB_GFXPAYLOAD_LINUX did.)

---

### Post by Simian Man on 2010-06-23
> **kevdog said:**
> Where do you add these parameters to? xorg.conf?

No, they're boot parameters so they must be given to the kernel at boot-time by your bootloader.  For grub1, which is used with Fedora, you just append them to the kernel line in /boot/grub/grub.conf.  I have no idea what grub2 uses since I haven't used it before.


[quote=FuturePilot]
VGA= is deprecated in Grub2. You have to use GRUB_GFXMODE=WxH in combination with GRUB_GFXPAYLOAD=WxH or in some cases only GRUB_GFXPAYLOAD_LINUX=WxHxD. (GRUB_GFXMODE and GRUB_GFXPAYLOAD did not work for me, but GRUB_GFXPAYLOAD_LINUX did.)[/quote]
OK, like I said I haven't used grub2.  I wasn't trying to provide support, but to explain how Plymouth works for me.  So Ubuntu users don't try what I said!

---

### Post by RiceMonster on 2010-06-23
> **Simian Man said:**
> You actually have to put "vga=0x318" and the number could differ depending on the resolution you want/your setup supports.  You can see a chart [here]("http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html").  0x318 is 1024x768 with 24 bit colors which should work pretty much everywhere.  This just forces vga to use a certain screen resolution which not only improves the fallback boot graphics, but also increases the screen resolution on your virtual terminals.

Oh right, I have used that before. Don't know why I don't think to use it with plymouth.

---

### Post by FuturePilot on 2010-06-23
> **Simian Man said:**
> 

OK, like I said I haven't used grub2.  I wasn't trying to provide support, but to explain how Plymouth works for me.  So Ubuntu users don't try what I said!

Oh I must have missed that part. Anyways just a little FYI. ;)

---

### Post by Lucradia on 2010-06-23
> **Dustin2128 said:**
> Plymouth in ubuntu 10.10 or not? It's open source; you decide.

You can't remove plymouth in ubuntu. Doing so causes your system not to boot.

Plymouth is even installed via mini.iso.

---

### Post by FuturePilot on 2010-06-23
It's funny how people were practically begging for Plymouth a few releases ago and now OMG IT'S TEH EVILS!!!. Same with Grub2 but that's a different thread.

---

### Post by bondo101 on 2010-06-23
Plymouth was a car not a splash screen , it had its own splash called the road runner and it went beep beep . The splash screen is butt ugly . How bout a picture of the Meercat holding a Tux. Or have a design contest to see Whoooo could come up with a better splash screen. When the Meercat comes out in Oct.
                just my 2 cents worth.:lolflag:):P

---

### Post by MichealH on 2010-06-23
Although this thread may of caused offence.I have to have my say: I dont like plymouth because, well I have to echo blacklist vgas and all that nosence and it still wont show me that sexy ubuntu logo.

---

### Post by NightwishFan on 2010-06-23
Plymouth has more advantages than just a boot theme. I believe it takes advantage of KMS which within the year should be nearly universal.

---

### Post by MichealH on 2010-06-23
> **NightwishFan said:**
> Plymouth has more advantages than just a boot theme. I believe it takes advantage of KMS which within the year should be nearly universal.

One issue, IN ONE YEAR? Why impliment it now than in 1 year? If I needed to reinstall ubuntu 1 hour is made od me having to rebuild initramfs and xorg just to get a ok ish resolution and a plymouth screen worth dying i mean running away for.

---

### Post by NightwishFan on 2010-06-23
Not sure I follow you. Even now the git intel drivers require kernel mode setting. Flicker free boot and animations it also uses DRM. Hopefully we can get it sorted out its a welcome innovation.

---

### Post by Legendary_Bibo on 2010-06-23
The only problem I have with plymouth is that it's always stuck in a low resolution (not my desktop screen, it's normal). I used "start-up manager" to fix it but it didn't do anything. Oh well I only see it for a few seconds on bootup and shutdown.

Also I would like to ask a question to the guys talking about boot parameters and stuff like that.

How the hell do you guys know that stuff?!\\:D/

---

### Post by NightwishFan on 2010-06-23
This solves the "no or brief splash" problem for me. First run:
```
sudo su
```
Then:
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
```
Finally this and reboot.
```
update-initramfs -u
```

Works like a charm, though I am on an intel chip.

---

### Post by Perfect Storm on 2010-06-23
I fixed plymouth to look grerat with my nvidia card + restricted driver with this guide (for nvidia and ATI restricted drivers): [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Spr0k3t on 2010-06-24
I vote to take the path of the fastest possible boot time.  Whichever route that may be.  Also, remove the hard dependancy of mountall so plymouth can be removed without ramifications.

---

### Post by Breambutt on 2010-06-24
Never seen the splash, not even after a "fix" which managed to temporarily break my display doodie even further. Sometimes it even hangs during boot time for some reason.

Oh well, couldn't really care less. Natural curiosity factor just kicked in.

---

### Post by bruno9779 on 2010-06-27
> **Artificial Intelligence said:**
> I fixed plymouth to look grerat with my nvidia card + restricted driver with this guide (for nvidia and ATI restricted drivers): [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Great!! Everything works now, TTYs included.

I wonder why these operations aren't made by the Hardware Driver install process just after installing the proprietary drivers

---

