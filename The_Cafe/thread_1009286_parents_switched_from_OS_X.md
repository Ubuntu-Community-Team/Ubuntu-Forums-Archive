---
title: "parents switched from OS X"
date: 2008-12-12
forum: The Cafe
---

### Post by wvmac on 2008-12-12
Over the summer my dad decided it was time for a new computer. He was using my old ibook with tiger running on it. He liked OS X but the laptop had become too slow when browsing flash and video pages. He used iphoto and itunes, safari and one of the word processors, I think it was bean. He was going to need to use windows occasionally but there was no way he was going to use windows as his primary OS, he is afraid of the security. So I told him that it would be possible to run windows occasionally with both a linux machine and a new mac. 

He had used linux in the past before switching to the ibook and decided that he didn't want to spend the money for a mac and went with a Dell with ubuntu. 
Dad set the pc up his self and I went home later and set up a dual boot and installed a few more apps for them to use in linux; picasa, google earth, vlc and a few others. 

I didn't receive many calls when he was running OS X and guess what, I still don't receive pc related calls. It just works for my parents.  
They like the speed and security; dad really likes the simplicity. He says that linux just stays out of his way. 

It has been almost 6 months and he doesn't even miss OS X. He has nothing against OS X, but he prefers ubuntu linux now.  

I switched from OS X several years ago as well, so once you go mac you never go back to windows but you just might move on to linux. 
Now I'm going to work on converting my sisters since they are having a good experience when using my parents pc. My wife, who is still a mac fan, is even considering linux because of certain irritations and restrictions with leopard on her macbook.

---

### Post by SunnyRabbiera on 2008-12-12
Well I can bet for most the switch from apple to linux will be quite easy as linux and apple are both unix like and have similarities like the filesystem, plus gnome has sort of a mac like layout.

---

### Post by mips on 2008-12-13
> **wvmac said:**
> 
Dad set the pc up his self and I went home later and set up a dual boot and installed a few more apps for them to use in linux; picasa, google earth, vlc and a few others.  

Instead of dual booting you should have installed XP in Virtualbox. No need for dualbootiing then and you can run your windows apps while linux is running.

---

### Post by I-75 on 2008-12-13
Good story...maybe this belongs in testimonials.

---

### Post by blippy on 2008-12-13
> **wvmac said:**
> It has been almost 6 months and he doesn't even miss OS X. He has nothing against OS X, but he prefers ubuntu linux now.  

I just got my iMac back from the repairers - the DVD drive was faulty. It took them about a month (!) to sort the problem out. Fortunately, I had a spare PC: Dell running Ubuntu. I had an old 17" CRT monitor, making Ubuntu look fairly clunky. I have installed Ibex back on my iMac now - and it looks a lot better.

I really like Macs because of their hardware - it's also their greatest weakness. If one bit goes wrong, then what you've got is a very beautiful doorstop.

In an OS X versus Ubuntu debate, there's so many pros and cons that it's difficult to announce a true winner. Perhaps we should call it a stalemate. OS X has good looks, vendor lock-in, great commercial apps. Ubuntu has a vast selection of free software.

Ubuntu is getting better - I'm looking at the fonts and thinking that they're actually quite good. OS X seems to give me more screen real-estate, though. Apple really know how to add polish to their products.

At the moment, I have XP working in VirtualBox - so I'm very happy with that!

---

### Post by MikeTheC on 2008-12-13
(Oddly enough, I'm typing this post on my PowerBook G4...)

Fonts and font rendering have long been an issue for me with Linux, no matter the distribution. While I'm certain there's any number of people out there who really don't care how fonts look on the screen -- apart from them being readable in a text editor or terminal window or something -- I actually do care very much about it. It has been during this latest "go-around" with running Linux that I've learned a LOT about how this is controlled in Linux, and what to do about it.

There's basically been three things I've needed to do to make Gnome render fonts decently.

Step 1: Enable full auto-hinting

Now, I can't speak to other distros, but in Ubuntu 8.04 and 8.10, it seems like they've forgotten about fonts. So, use your favorite text editor (I like GEdit myself) and create a new configuration file, titled ".fonts.conf" (the leading "." is deliberate, since this is supposed to be a hidden file.) in your user folder (i.e.: [font="Courier New"]~/.fonts.conf[/font] ). In this file, place the following data:

```
<?xml version="1.0&#8243; ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
   <match target="font">
      <edit name="autohint" mode="assign">
         <bool>true</bool>
      </edit>
   </match>
</fontconfig>
```


Step 2: Set rendering/hinting for Gnome

Again, it may seem like I am carping, but why in the world does Ubuntu -- given Mark Shuttleworth's mandate -- leave such trivial-to-fix gaping holes go unfixed, but nevertheless for some reason Gnome's appearance settings for fonts is not optimal for a smooth appearance. So...

System > Settings > Appearance > [Fonts tab]

Under the "Rendering" section, select "Subpixel smoothing (LCDs)".
Click the "Details" button.
Ensure your screen's DPI is set correctly (defaults to 96 dpi, but my screen is approximately 98 dpi)
Under the section "Smoothing", make sure "Subpixel (LCD)" is chosen.
Under the section "Hinting", make sure "Slight" is chosen.


Step 3: Create the user's Fonts folder

There are two ways to do this. The first way, which is "safe" and is what I used to do, is simply to create a new folder in your user folder called ".fonts" (again, the leading "." is intentional, since this is supposed to be a hidden folder.)

*[**Disclaimer:** The following method involves changing permissions on a central system resource which could, in theory, have the potential for security exploitation. It is put forth as an example of how this user does things on his computer, and does not reflect the advice or opinions of UbuntuForums, Canonical, or anyone else.]*

The second way, which is what I use now, is to:

[list=1][*] Generate a root-privileged Nautilus session (that is, Applications > Accessories > Terminal; "[font="Courier New"]sudo nautilus[/font]" );
[*] Navigate using this new Nautilus window to the central system "fonts" folder, located at [font="Courier New"]/usr/share/fonts[/font] ;
[*] Create several additional sub-folders for organizational purposes;
[*] Change the privileges of this folder and it's contents to "read-write" for my normal user account;
[*] Close that Nautilus window out;
[*] Navigate back to [font="Courier New"]/usr/share/fonts[/font] in Nautilus under my own natural privileges;
[*] Create a symlink (that is, a "shortcut" or "alias") to it in my own user folder;
[*] Rename the symlink to ".fonts" (the leading "." being intentional, of course)[/list]

Now, I really don't like having to do all this, but I feel it's necessary because of what I view as a major oversight on the part of the Ubuntu maintainers. I mean, [font="Courier New"]~/.fonts[/font] is specified in other system-supplied configuration files, so why the heck doesn't the folder exist from initial setup? I understand the whole "let's tinker with things under-the-hood" mentality of Linux, and I don't object to it per-se, but when you consider: 1. You can't "technically" even add fonts to your system on an ad-hoc basis from install; 2. Mark Shuttleworth's mandate that the Linux experience by polished and sanitized; and 3. This whole structure is defined by Gnome, is established and "known", clearly it's an issue which shouldn't even now need to be corrected, but obviously "now" should be.

Anyhow, that's what I do (well, apart from my own choice of adding fonts to my system) to finish off the rough edges of Ubuntu where fonts are concerned.

I'd get into my selection of themes, icons and the like, but this is a long-enough post as it is.

---

### Post by wvmac on 2008-12-13
I wanted to use virtual box but my dad was worried that the software would not work that way. The company is really concerned about security when working from home so I wasn't sure if a problem would arise from using virtualbox and I am not at home often enough to fix problems fast. So I just played it safe. 

So does the virtualized OS appear to be a normal pc to a remote pc?

---

### Post by mips on 2008-12-13
> **wvmac said:**
> I wanted to use virtual box but my dad was worried that the software would not work that way. The company is really concerned about security when working from home so I wasn't sure if a problem would arise from using virtualbox and I am not at home often enough to fix problems fast. So I just played it safe. 

So does the virtualized OS appear to be a normal pc to a remote pc?

Running XP in a VM to me seems to add an additional layer of protection if you use NAT.

For all intense purposes I would say Yes.

---

### Post by handy on 2008-12-13
My ISP runs all their servers in virtual machines on top of Gentoo.

---

### Post by squeabs on 2008-12-13
I have an old PowerPc G4 running OS X. It's a little slow, but I mostly use it for dnd game planning, writing, and photo editing. It seems to work well for the simple things. I've become a little attached to Mac; I had an iBook G4 before. I also have a much more powerful machine running Ubuntu 8.04 and Vista Ultimate. I've become attached to Ubuntu also.
I have to say I can't really decide between the two, which is why I use both. There just seems to be some kind of simple elegance to unix vs windows.

---

### Post by aschwerin.moses on 2008-12-14
> **MikeTheC said:**
> (Oddly enough, I'm typing this post on my PowerBook G4...)

Fonts and font rendering have long been an issue for me with Linux, no matter the distribution. While I'm certain there's any number of people out there who really don't care how fonts look on the screen -- apart from them being readable in a text editor or terminal window or something -- I actually do care very much about it. It has been during this latest "go-around" with running Linux that I've learned a LOT about how this is controlled in Linux, and what to do about it.

There's basically been three things I've needed to do to make Gnome render fonts decently.

Step 1: Enable full auto-hinting

Now, I can't speak to other distros, but in Ubuntu 8.04 and 8.10, it seems like they've forgotten about fonts. So, use your favorite text editor (I like GEdit myself) and create a new configuration file, titled ".fonts.conf" (the leading "." is deliberate, since this is supposed to be a hidden file.) in your user folder (i.e.: [font="Courier New"]~/.fonts.conf[/font] ). In this file, place the following data:

```
<?xml version="1.0&#8243; ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
   <match target="font">
      <edit name="autohint" mode="assign">
         <bool>true</bool>
      </edit>
   </match>
</fontconfig>
```


Step 2: Set rendering/hinting for Gnome

Again, it may seem like I am carping, but why in the world does Ubuntu -- given Mark Shuttleworth's mandate -- leave such trivial-to-fix gaping holes go unfixed, but nevertheless for some reason Gnome's appearance settings for fonts is not optimal for a smooth appearance. So...

System > Settings > Appearance > [Fonts tab]

Under the "Rendering" section, select "Subpixel smoothing (LCDs)".
Click the "Details" button.
Ensure your screen's DPI is set correctly (defaults to 96 dpi, but my screen is approximately 98 dpi)
Under the section "Smoothing", make sure "Subpixel (LCD)" is chosen.
Under the section "Hinting", make sure "Slight" is chosen.


Step 3: Create the user's Fonts folder

There are two ways to do this. The first way, which is "safe" and is what I used to do, is simply to create a new folder in your user folder called ".fonts" (again, the leading "." is intentional, since this is supposed to be a hidden folder.)

*[**Disclaimer:** The following method involves changing permissions on a central system resource which could, in theory, have the potential for security exploitation. It is put forth as an example of how this user does things on his computer, and does not reflect the advice or opinions of UbuntuForums, Canonical, or anyone else.]*

The second way, which is what I use now, is to:

[list=1][*] Generate a root-privileged Nautilus session (that is, Applications > Accessories > Terminal; "[font="Courier New"]sudo nautilus[/font]" );
[*] Navigate using this new Nautilus window to the central system "fonts" folder, located at [font="Courier New"]/usr/share/fonts[/font] ;
[*] Create several additional sub-folders for organizational purposes;
[*] Change the privileges of this folder and it's contents to "read-write" for my normal user account;
[*] Close that Nautilus window out;
[*] Navigate back to [font="Courier New"]/usr/share/fonts[/font] in Nautilus under my own natural privileges;
[*] Create a symlink (that is, a "shortcut" or "alias") to it in my own user folder;
[*] Rename the symlink to ".fonts" (the leading "." being intentional, of course)[/list]

Now, I really don't like having to do all this, but I feel it's necessary because of what I view as a major oversight on the part of the Ubuntu maintainers. I mean, [font="Courier New"]~/.fonts[/font] is specified in other system-supplied configuration files, so why the heck doesn't the folder exist from initial setup? I understand the whole "let's tinker with things under-the-hood" mentality of Linux, and I don't object to it per-se, but when you consider: 1. You can't "technically" even add fonts to your system on an ad-hoc basis from install; 2. Mark Shuttleworth's mandate that the Linux experience by polished and sanitized; and 3. This whole structure is defined by Gnome, is established and "known", clearly it's an issue which shouldn't even now need to be corrected, but obviously "now" should be.

Anyhow, that's what I do (well, apart from my own choice of adding fonts to my system) to finish off the rough edges of Ubuntu where fonts are concerned.

I'd get into my selection of themes, icons and the like, but this is a long-enough post as it is.
Well buddy.. thanks a ton.. i like like like it :)

---

