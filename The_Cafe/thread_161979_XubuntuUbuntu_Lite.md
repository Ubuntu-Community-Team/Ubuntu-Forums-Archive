---
title: "Xubuntu/Ubuntu Lite"
date: 2006-04-18
forum: The Cafe
---

### Post by catlett on 2006-04-18
Please excuse my ignorance but I just wanted to clarify something I am unsure of and get your advice. Is the difference between Xububtu and Ubuntu Lite(I'm going by the wiki called Ubuntu Lite) the fact that Xubuntu uses Xfce as a window manager and Ubuntu Lite uses Icewm?
What is some of your opinions for a light working Ubuntu desktop? I'm salvaging a P2 laptop (Toshiba 3110CT). It's specs are low and I wanted to install Xubuntu or U Lite. The specs are 64mb Ram, P2 300mhz and 6gb hard drive. It runs Win 98 but that's about to turn into a bunch of zeroes:twisted: .
I was originally thinking of a minimilist specific distro. But the more I thought the more I wanted to stay where I'm comfortable and happy i.e. Ubuntu. I knew of Xubuntu and started looking into it and I came across the directions for Ubuntu Lite. And the obvious next step is to post and get advice.
I'm looking for the computer to do basic ofice work. I'll be taking it to construction sites and setting up in make shift offices. I'll need a word processor, basic browser and a spreadsheet would be nice but I don't know if there is something lite.  
Thanks in advance. I'm off to work and won't be able to reply until tonight. Always a pleasure being connected to Ubuntu forums. Regards,  Catlett

---

### Post by Sef on 2006-04-18
There is also fluxbox; it's the lightest of the window managers.

---

### Post by Stone123 on 2006-04-18
Well if i was going to use light installation then i would use something like:
[https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)
//or was it other methods of installation ? i dont remember. 
I only used netboot or bootiso that is in debian. Install base system (auto) and then : 
x-window-system-core , xserver-xorg (xfree86 in debian )and fluxbox.
Some lightweight filemanager and eterm and some internet browser.

I like fluxbox but i think blackbox (fluxbox is based on it), takes the credit for lightest that i know , something like 4 mb of RAM for running it.
 //i have blackbox on my pictureframe computer that was and old 486 laptop with 8 MB ram.

---

### Post by localzuk on 2006-04-18
I would suggest, due to the ram, that you use Ubuntu Lite - as ICEWM is lighter than xfce. If you could get another 64M ram then XFCE would run superbly, as that laptop would be the same spec as one of mine.

For word processing, I suggest either AbiWord or FLWriter (the latter is lighter than the prior).

For spreadsheet, something like Siag ([http://siag.nu/siag/](http://siag.nu/siag/)) would be good. (I don't know if there is an ubuntu package yet though).

For web browsing, something like Epiphany would be faster than Firefox or the like.

---

### Post by localzuk on 2006-04-18
I would suggest taking a look at the 'Damn Small Linux' distro ([http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)) if you want to take a look at a complete, ultra light fluxbox based distro.

---

### Post by 3rdalbum on 2006-04-18
Yes, definately look at DSL.

Epiphany uses GNOME dependancies and requires Firefox to be installed, so that's probably not such a great choice for a lightweight browser running on IceWM or Xfce.

If you don't mind having GNOME dependancies installed, then for your spreadsheet I would recommend Gnumeric. It's 33 megs installed, but it has excellent MS Office compatibility, will get OpenDocument compatibility soon, and runs like a dream.

---

### Post by Iandefor on 2006-04-18
[quote=Sef]There is also fluxbox; it's the lightest of the window managers.[/quote] Having personally used a huge variety of WM's, I think I can safely refute this as bull. Try ratpoison for a seriously lite WM. But if you want something approaching usable, try Enlightenment DR16.

---

### Post by catlett on 2006-04-18
This is why I want to stay within Ubuntu. You can always get good, prompt and knowledgable advice. 
I think I'm going to go down to the local computer shop, get a pulled 64 ram and try xfce.  Then I'll start experimenting  with the different word processors and spreadsheets mentioned.
 My thinking is that  xfce is  easier to work with(I may be wrong). I'm going to be introducing Linux to a whole group of guys that never even heard of Linux through this little laptop, and I'd like to get them working with it. They are good candidates actually. They don't have any computer experience. So they haven't been indoctrinated into any particular way to interface with a computer.  
Just one more related question before I say thanks.. Would it be better to get an older version of a  mozilla/opera for this older system or to get a modern epiphany/dillo (actually I shouldn't say dillo, that's too light for me) browser? Basically do I look for apps from when my machine was new or look for light modern apps?
 Once again thank you to all who took time to give me advice. Regards.

---

### Post by John.Michael.Kane on 2006-04-18
@Iandefor looking at the info on the ratpoison web site i must say your damn right it's light. to the OP more info on it here [http://www.nongnu.org/ratpoison/](http://www.nongnu.org/ratpoison/)

---

### Post by catlett on 2006-04-19
Just thought I'd drop by and post from within Xubuntu. I have to say every one of my Ubuntu installs went great. Well thanks for the advice. For now it's xfce and I saw abiword was the default. Off to browse in the new ride.:D

---

### Post by graabein on 2006-04-19
Good to hear it's working out. 

I'm relatively new to GNU/Linux and I've mainly used Ubuntu thus far with a testdrive of Knoppix and DSL. On two old computers I did the server install and added X and openbox/fluxbox with pypanel. I've also played with Window Manager and tried a live-cd of Enlightenment. 

The Ubuntu base install with openbox and pypanel works allright for me. It's a big plus salvaging old computers and getting them to be productive with Linux.

---

### Post by Buffalo Soldier on 2006-04-19
[QUOTE=catlett]Just thought I'd drop by and post from within Xubuntu. I have to say every one of my Ubuntu installs went great. Well thanks for the advice. For now it's xfce and I saw abiword was the default. Off to browse in the new ride.:D[/QUOTE]
Out of curiosity which install method did you use?[list]
[*] [https://wiki.ubuntu.com/XubuntuReleases](https://wiki.ubuntu.com/XubuntuReleases)
[*] [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)
[/list]

How's the performance?

---

### Post by catlett on 2006-04-20
I was lucky and the laptop came with an adapter that had an ethernet connector. Plus I found out the laptop had hotkeys which enabled me to boot from an external cd drive. Because I had both of those I did a download and burn of the Xubuntu daily build. Then just did a normal boot to the install. The install process of Ubuntu has always been great for me. I just chose for the install to resize the partition and to . I  kept the Win98 on 1.5 gb of the 6gb drive. Not that I like 98, it's just that I feel more comfortable with a dual boot when it comes to being protected against data lost. The dual boot makes me think I can always access the hard drive.  I didn't get the memory yet but Xubuntu is running well on just the 64. Regards

---

