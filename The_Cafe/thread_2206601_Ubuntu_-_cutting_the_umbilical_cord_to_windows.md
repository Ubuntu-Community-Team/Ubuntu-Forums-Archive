---
title: "Ubuntu - cutting the umbilical cord to windows"
date: 2014-02-19
forum: The Cafe
---

### Post by rachel-g41 on 2014-02-19
Ubuntu - cutting the umbilical cord to windows

As some of you might know, over Christmas I installed lubuntu on a netbook. (The netbook had been running ok, but then the HD got damaged and replacing it seemed like a good opportunity to give linux a go.)

I like lubuntu, it's quick and easy and so far there's nothing I've found that I could do with windows that I can't do with lubuntu.

So now I'm thinking of installing it on my other laptop. It's an Acer aspire 5535 for what it's worth. It came with Vista home premium and a partitioned disk. It's now full and runs slowly - the netbook is far better for speed, I notice the difference and particularly with skype and streaming. I'm pretty sure that installing lubuntu will make it far more efficient and easier to use. However, this will leave me with no windows machine which makes me a bit nervous despite everything. 

What I would like to know is: Is there anything I should know/do before I make the switch? I will, of course, back up my own files, but should I make any system disks just in case? Really  I think (and hope) the answer is no but I need a bit of reassurance. 

And a second question, I am now used to and happy with lubuntu. Would there be any advantage in moving to the full-fat Ubuntu, or any disadvantage in sticking to lubuntu? I did have a quick look at Ubuntu while playing with distros but it was different enough to lubuntu to disorient me a bit. 

Any advice or reassurance will be much appreciated.


[I]edited to add: For clarification, I don't intend to install linux alongside Windows, I intend to format and start again.



[/I]Mods feel free to move this to Absolute Beginners or Installation if appropriate.

---

### Post by Psil0cybin on 2014-02-19
> **rachel-g41 said:**
> Ubuntu - cutting the umbilical cord to windows

As some of you might know, over Christmas I installed lubuntu on a netbook. (The netbook had been running ok, but then the HD got damaged and replacing it seemed like a good opportunity to give linux a go.)

I like lubuntu, it's quick and easy and so far there's nothing I've found that I could do with windows that I can't do with lubuntu.

So now I'm thinking of installing it on my other laptop. It's an Acer aspire 5535 for what it's worth. It came with Vista home premium and a partitioned disk. It's now full and runs slowly - the netbook is far better for speed, I notice the difference and particularly with skype and streaming. I'm pretty sure that installing lubuntu will make it far more efficient and easier to use. However, this will leave me with no windows machine which makes me a bit nervous despite everything. 

What I would like to know is: Is there anything I should know/do before I make the switch? I will, of course, back up my own files, but should I make any system disks just in case? Really  I think (and hope) the answer is no but I need a bit of reassurance. 

And a second question, I am now used to and happy with lubuntu. Would there be any advantage in moving to the full-fat Ubuntu, or any disadvantage in sticking to lubuntu? I did have a quick look at Ubuntu while playing with distros but it was different enough to lubuntu to disorient me a bit. 

Any advice or reassurance will be much appreciated.


[I]edited to add: For clarification, I don't intend to install linux alongside Windows, I intend to format and start again.



[/I]Mods feel free to move this to Absolute Beginners or Installation if appropriate.

Okay well the fact that you are a little disoriented with Ubuntu vs Lubuntu is normal because it is a GUI Change, but 90% of the system will be the same (in terms of the back end)

If you are using CLI or the Terminal you will notice, everything is the same..only thing you will need to get used too is the graphical user interface, and perhaps Ubuntu eats more ram/uses more resources than Lubuntu, take that into consideration! (if you are using older hardware)

Words of encouragement/reassurance?

I went from using windows 7 to Xubuntu two years ago, and love it since do not have any windows partitions on my computers. (if you are nervous about being without a window machine, I suggest keeping a small partition for windows as a back up - but if you really do not want to do that and want to jump fully into Linux, you can always use WINE to emulate/run certain windows applications you may not be able to live without!)

_When it comes to backing up information, etc please wait for someone with more information to reply_ I personally nuke all my hard drives, and just install Xubuntu/Ubuntu (fresh)
Linux takes time and patients, if you have that than you will love it...I for one sometimes do get frustrated with my machine, but at the end of the day I love linux!

, hope I helped.

---

### Post by andrew.46 on 2014-02-19
> **rachel-g41 said:**
> And a second question, I am now used to and happy with lubuntu. Would there be any advantage in moving to the full-fat Ubuntu, or any disadvantage in sticking to lubuntu? I did have a quick look at Ubuntu while playing with distros but it was different enough to lubuntu to disorient me a bit.

Unity is definitely an *acquired* taste, it would not take you all that long to adapt to it. But if you are happy with lubuntu I would recommend that you just stay there.

---

### Post by Daliz on 2014-02-20
One downside of Lubuntu is that it isn't LTS. So if you're looking to install stuff and use it for a long time then look into something that's LTS: Ubuntu, Xubuntu, Kubuntu. All of those are more heavy on the resources than Lubuntu though, XFCE-variant being the most lightweight and also a "traditional" desktop.

---

### Post by Bucky Ball on 2014-02-20
*Thread moved to **The Cafe**.*

Not a support request so here it is.

You can run Windows as a virtual machine using [Virtualbox]("https://www.virtualbox.org/") on any host machine, any time and at the same time as you're running just about anything else as the host operating system, including Lubuntu. Virtualbox is in the repositories. ;)

PS: Your first question, was that about the machine you are going to install Linux to? Well, if you are eradicating Windows from it, no, you won't need system or backup disks of anything but your personal data ... unless you intend installing Windows on it again someday. Otherwise, wipe and start again by booting from Lubuntu live install media, format as you will (but good idea to make a partitioning plan before jumping in unless you're going to let the installer make that decision for you 'automagically').

---

### Post by monkeybrain20122 on 2014-02-20
> **Daliz said:**
> One downside of Lubuntu is that it isn't LTS. So if you're looking to install stuff and use it for a long time then look into something that's LTS: Ubuntu, Xubuntu, Kubuntu. All of those are more heavy on the resources than Lubuntu though, XFCE-variant being the most lightweight and also a "traditional" desktop.

You can consider [http://lxle.net/](http://lxle.net/) It is basically lubuntu 12.04 but with long term support.

Since lubuntu uses all of Ubuntu's repository most things in lubuntu 12.04 would be supported for as long as Ubuntu 12.04. I think you would get same lts support as lxle if you install lubuntu12.04 and add the lxle ppa.[https://launchpad.net/~lxle/+archive/stable](https://launchpad.net/~lxle/+archive/stable) 

If you start with lubuntu 12.04  I believe you can use the LTS enablement stack and get upgraded along with the Ubuntu 12.04 point releases too.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) I have not tried it but can't see why it wouldn't work.

---

### Post by mips on 2014-02-20
You can resize your windows partition and dual-boot.
You can wipe the entire HDD, install linux and run windows in a VM
I would recommend Xubuntu for that laptop as it has the power to run it.

---

### Post by rachel-g41 on 2014-02-20
Many thanks for all the replies. 

I will have a go tomorrow, Friday and let you know how it goes. Meanwhile I will read a bit about the differences between the different varieties of ubuntu.

---

### Post by Don_Stahl on 2014-02-20
I believe you've got a single-core CPU, maybe 1.6 GHz? And 3 GB of RAM? 

I think -- and others will correct me I hope, 'cos I'm no expert -- I *think* that you'll be good on RAM with whatever distro you choose. Your CPU may be the bottleneck -- it may hit a wall sometimes. Infrequently, though, unless you're applying graphic effects to large images or something. 

With a 160 GB hard drive (yes?) you can do as mips suggests. Half of it, 80 GB, is plenty for Linux. Or if you decide to wipe the hard drive, you might make sure you have a Windows recovery disk for Vista. Just for that sudden realization -- "Wait, I can't run SomeUniqueProgram.exe now, so that one project is dead..."

Just some early-morning musings, and pretty much off-the-cuff. Must have coffee now... O:)

---

### Post by rachel-g41 on 2014-02-20
Thanks, it's 320GB HD I think but the rest sounds right (not at home to check right now). 

I dont do much which is heavy on graphics - just basic photo editing and video streaming. 

As for windows, I already have wine installed on the netbook because despite all the alternatives, I still find irfanview the best and quickest for simple image editing (cropping, rotating to correct wonky horizons, resizing, contrast & gamma adjusts).

---

### Post by ronniew on 2014-02-20
> **monkeybrain20122 said:**
> Since lubuntu uses all of Ubuntu's repository most things in lubuntu 12.04 would be supported for as long as Ubuntu 12.04. I think you would get same lts support as lxle if you install lubuntu12.04 and add the lxle ppa.[https://launchpad.net/~lxle/+archive/stable](https://launchpad.net/~lxle/+archive/stable) 

I told you before that this is not the case. LXLE is more than just a repository or PPA.

---

### Post by Don_Stahl on 2014-02-20
> ....[COLOR=#000000]I still find irfanview the best and quickest for simple image editing...[/COLOR]

Yes indeed. Irfan Skiljan is, in my book, maximum good.

---

### Post by lykwydchykyn on 2014-02-20
I agree, it's good to have something in the house that can boot to Windows if required.  You just never know when you'll run into some website, device, or application that you have to run that requires it.   I've been on Linux primarily for 10 years, but once in a blue moon we have to boot a system up to windows to accomodate some lazy programmer somewhere. :P

---

### Post by craig10x on 2014-02-20
Regular Ubuntu with Unity desktop is very nice if you don't mind using a dock type of launcher (which is what unity really is) such as like you would see on a mac (except Unity is fixed to the left side of the screen, but can be auto-hidden of course...easiest way to use it is to put favorites and most used apps on the unity launcher ( for quick 1 click access) and use the "dash search" for less used apps...you can also make the pixel size of the icons smaller in the settings (which is very handy if you are putting a lot of apps on the launcher dock)...With the "global menu" top panel it has,  it all feels very "mac-like" if you don't mind that....i don't and i enjoy unity desktop very much, myself :D

Give it a try for awhile and see how you like it! ;)

---

### Post by Don_Stahl on 2014-02-20
...and, if you like the idea of having a Gnome 2-style menuing app as well, you can install ClassicMenu:

```
sudo apt-add-repository ppa:diesch/testing

sudo apt-get update && sudo apt-get install classicmenu-indicator
```

I kind of like having a few different options, and I use classic menu quite often.

---

### Post by Old_Grey_Wolf on 2014-02-20
> **rachel-g41 said:**
> I will, of course, back up my own files, but should I make any system disks just in case? Really  I think (and hope) the answer is no but I need a bit of reassurance.

CDs and DVDs are inexpensive. It wouldn't be much time or money involved in making system disks. Just knowing they are available may be worth it.

> **rachel-g41 said:**
> And a second question, I am now used to and happy with lubuntu. Would there be any advantage in moving to the full-fat Ubuntu, or any disadvantage in sticking to lubuntu? 

You may want to use Xubuntu instead of Lubuntu as Xubuntu 12.04 and soon to be released Xubuntu 14.04 are LTS.

Edit: it is planned that the Lubuntu 14.04 release be an LTS; however, it will be 2 months before it comes out.

---

### Post by lykwydchykyn on 2014-02-20
> **Old_Grey_Wolf said:**
> 
You may want to use Xubuntu instead of Lubuntu as Xubuntu 12.04 and soon to be released Xubuntu 14.04 are LTS.


I can't see this being that big of a deal.  The only parts of Lubuntu that aren't getting LTS are the parts unique to it.  The core OS and any applications or libraries used in other LTS flavors are still getting support.

I'd say pick the desktop environment you like the best and use that, LTS or not.

---

### Post by rachel-g41 on 2014-02-23
So far so good :)

The delay was down to getting hold of some DVDs to make the back up disks just in case. 

IN the end I decided to stick with lubuntu for now, it's what I'm familiar with and if I decide to change later it won't be as traumatic.

It has only just finished instaling and updating, but it  seems to be working fine. I haven't yet started with the extras and add-ons, that can wait at least until tomorrow. 
 
Really, I had nothing to lose - the laptop was so slow as to be almost unusable.

Thanks for all the comments and moral support.

---

### Post by rachel-g41 on 2014-02-24
Unfortunately after that last post I had problems with the laptop shutting down. I suspect overheating and there are various threads online referring to problems with machines of this series (most of these threads are very old, I've had the machine for a good few years). The problem seems to be that the fan is controlled by Acer energy management which of course is included in the original WInVista install but which does not come with linux. There are workarounds offered but they all look horribly complicated for someone new to linux. 

Right now I'm not sure what to do next, whether to try to find a solution or revert to windows in the meantime - or to just give it a good clean inside and see if that helps.

---

### Post by Bucky Ball on 2014-02-24
Can of compressed air might help.

---

### Post by rachel-g41 on 2014-02-24
Yes, if I can get that locally today I will - otherwise it'll be tomorrow after work.

I may also try reinstalling windows and running lubuntu from flash to compare the performance - to see if it really is that the fan is not properly managed under linux.

---

### Post by Bucky Ball on 2014-02-24
If the compressed air doesn't make any difference, this is an old fix, but you never know. You need to:

```
sudo apt-get install smartmontools
```

... then check the load-cycle-count with:

```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

... from [THIS]("http://www.viboon.org/tag/load-cycle-count/") page. Replace /sda with the drive you're testing. There is also a fix there, but scant explanation of whether you need one. Then have a look [HERE]("https://wiki.ubuntu.com/DanielHahler/Bug59695").

It fixed an HP I used to have, but that was in 7.04 from memory! You should be able to find more about it with a search on 'load cycle count ubuntu' + whatever release you're using.

---

### Post by rachel-g41 on 2014-02-24
Since my questions are now more specific re fan control and overheating I've started a new thread [http://ubuntuforums.org/showthread.php?t=2207627](http://ubuntuforums.org/showthread.php?t=2207627)

Thanks to all who've answered so far.

---

