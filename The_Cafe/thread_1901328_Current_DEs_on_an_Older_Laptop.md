---
title: "Current DEs on an Older Laptop"
date: 2011-12-28
forum: The Cafe
---

### Post by neu5eeCh on 2011-12-28
Half question. Half discussion.

In terms of environments - how do Lubuntu, Xubuntu, Gnome Classic (effects & no effects), and Unity 2D compare? I've been reading different opinions as to whether there's any significant differences between Unity 2D, LXDE or Gnome Classic (no effects). Do any of you happen to be using these environments? Seems like both Gnome and Unity have created their own "lightweight" alternatives. What's your memory usage like, and speed? I'm wondering what to recommend to a friend with an older laptop (4 years old, I think). He's a very non-technical user.

I seriously hesitate to recommend Xubuntu (or XFCE) because of the XFWM4 bug (no windows borders). I would consider Lubuntu, but whether it's LXDE or their implementation, the DE strikes me as amateurish (deservedly or not), what with system tray icons moving around and colliding (at least in my experience). On the other hand, I've been impressed by the seeming rock, solid finish of Gnome Classic. He's the kind of user who doesn't customize. He could care less - just wants his browser to work, but loves the speed of Linux (compared to VISTA on the same computer).

I guess I'm deciding between Mint Linux 12 (Gnome Classic) or Ubuntu 11.10 Unity 2D? -- but open to other experiences & suggestions.

---

### Post by Dragonbite on 2011-12-28
Unity / Unity 2D are not too bad once you get used to them.  My systems all revert to Unity 2D except for my wife's new computer which I am experimenting on.

What about KDE?  Especially with Kubuntu's "lite" version which turns off a number of resource hogs.  I've been impressed with how much faster it feels even though the eye candy is turned off.

The laptop I test these on is a Dell D400 Pentium M @ 1.6 GHz with 1GB of Ram, if that provides any sort of reference.

I am actually using openSUSE's KDE installation (because it gives me desktop effects) which is slower but very usable.  When I've fooled around with Kubuntu on it, I don't get the desktop effects but everything feels very snappy.

---

### Post by stalkingwolf on 2011-12-28
Ive tried several.  one to look at is zorin.  It aside from its "new user" usibility has a feature that i found nice. it is called look changer.  it changes the desk top look , has Gnome, windows, and a third that i dont remember.  i installed it on my desktop ( older than 4 yrs) and two Hp laptops (6-7 yrs old) and it ran fine.

---

### Post by neu5eeCh on 2011-12-28
Thanks Dragonbite. I'll consider that. My only thought is that if and when he calls me up, it helps if I'm familiar with the DE. (I don't use KDE on any of my own systems.) The other problem with KDE is that (when I **have** used it) I've never, not once (in all seriousness), had a good experience with its wireless network manager. However, given that your system is similar to his, I won't be close minded about it. 

Thanks again for responding. :-)

---

### Post by keithpeter on 2011-12-28
Hello All

Unity 2d/11.10 works acceptably to me on a Dell D610 laptop (P3 coppermine 850MHz with 512Mb ram, 2001 vintage). I wrote most of the Unity 2d tutorial on that machine, including using shotwell for screen grabs. Using LibreOffice, Firefox and Shotwell had me into swap, but apart from the paging delay when switching application it seemed quite responsive.

I have a Thinkpad T60 (dual core with 1Gb ram, 2006/7 vintage) - no problems with Unity 2d or 3d on that machine, everything just works, responsive, can run LibreOffice, Firefox, GIMP, Gedit no issues. I think classic on that would be fine. That dual boots with Windows 7 which jogs, ok, more sort of walks :twisted:

---

### Post by neu5eeCh on 2011-12-28
> **stalkingwolf said:**
> Ive tried several.  one to look at is zorin.  It aside from its "new user" usibility has a feature that i found nice. it is called look changer.  it changes the desk top look , has Gnome, windows, and a third that i dont remember.  i installed it on my desktop ( older than 4 yrs) and two Hp laptops (6-7 yrs old) and it ran fine.

Hey, that's an interesting possibility I hadn't thought of. I'm going to download it and try it in VB - looks like it uses Gnome 2.X?

---

### Post by neu5eeCh on 2011-12-28
> **keithpeter said:**
> Unity 2d/11.10 works acceptably to me on a Dell D610 laptop (P3 coppermine 850MHz with 512Mb ram, 2001 vintage). 

Thanks, that's good to know. If 2D works on an old system like that, then it would certainly work on my friend's.

Out of curiosity, if you're not running any other software, what do you get when you type [free -m] at the command prompt?

---

### Post by lykwydchykyn on 2011-12-28
A four year old laptop is not what I would consider "older" -- at least not in the sense that it would immediately drive me to use an alternative DE.  I just got a couple of 4-5 yr old desktop systems for my kids -- one is running Unity and the other KDE, neither with any problems to speak of.  

Obviously, it all comes down to specs and video driver support, but until you get into pre-Vista hardware I don't think there's a need to look past mainstream environments (unless you're like me and you just enjoy it).

---

### Post by neu5eeCh on 2011-12-28
> **lykwydchykyn said:**
> A four year old laptop is not what I would consider "older" -- at least not in the sense that it would immediately drive me to use an alternative DE.

His laptop runs VISTA s-l-o-w-l-y. He bought a stripped down "business" laptop to begin with. What he likes most about Linux is how snappy and quick it is. I don't want to disappoint him. I'm obviously going to be turning off all compositing and "effects" when I upgrade/replace his current installation. Eye-candy means nothing to him. When he runs VISTA, he likes the Win2000 "look".

---

### Post by keithpeter on 2011-12-28
> **VTPoet said:**
> Thanks, that's good to know. If 2D works on an old system like that, then it would certainly work on my friend's.

Out of curiosity, if you're not running any other software, what do you get when you type [free -m] at the command prompt?

Below from 11.10 in Unity 2, haven't tried the fallback session.

```
keith@C610:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           496        488          8          0         16        232
-/+ buffers/cache:        238        257
Swap:         1905         26       1879
```

Above with default vm.swappiness settings and no software running except terminal.

```
keith@C610:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           496        487          8          0         12        174
-/+ buffers/cache:        300        195
Swap:         1905         72       1833
```

Above logged in here using Firefox and the update notification dialogue box has just joined the party.

Youtube is *basic*, stick to non hd and don't try full screening and they play but the frame rate is low.

A centrino based laptop with plenty of ram should be noticeably better than this old clunker.

---

### Post by lykwydchykyn on 2011-12-28
> **VTPoet said:**
> His laptop runs VISTA s-l-o-w-l-y. He bought a stripped down "business" laptop to begin with. What he likes most about Linux is how snappy and quick it is. I don't want to disappoint him. I'm obviously going to be turning off all compositing and "effects" when I upgrade/replace his current installation. Eye-candy means nothing to him. When he runs VISTA, he likes the Win2000 "look".

That makes more sense then; just saying I wouldn't go there based on the *hardware*.  If the user wants simple and conservative, then I'd steer clear of Unity/GNOME3/KDE4.  

Personally I've always thought LXDE reminded me of the simplicity of windows 2000, but you've already said you don't care for it.  I'd hesitate to go with anything GNOME 2 at this point, because sooner or later it's going to have to go to GNOME 3 or something else.

I don't know what XFCE bug you're talking about, but I've always found it to be pretty stable and (for better or worse) boring.

---

### Post by neu5eeCh on 2011-12-28
//If the user wants simple and conservative, then I'd steer clear of Unity/GNOME3/KDE4.  //

Yes, but I was wondering about Unity 2D & Gnome Classic. I'm running Xubuntu right now and love it, but every so often it will start up without window borders and you have to find a way to kick start the window manager. I don't want to have to field that phone call. It's a PITA. It's been mentioned at Distrowatch and [here]("http://ubuntuforums.org/showthread.php?t=1846266"). The Xubuntu debs think they'll have it fixed in 12.04.

Looking at Keithpeter's memory usage with Unity 2D, it doesn't seem all that much more than LXDE. I'll have to look up how much memory Gnome Classic, without effects, uses. He's already fairly comfortable in Gnome2, so Gnome Classic might feel familiar.

---

### Post by keithpeter on 2011-12-29
Hello All

Windows 2000 eh?

Below on the P3, I just installed gnome-shell which adds the gnome-fallback stuff and gives me Gnome Classic (no effects) in the log-in session menu.

I deleted the top panel, added indicators, clock, main menu, and a few launchers to the bottom panel. Used spacers between the launchers as you don't seem to be able to move the panel items to random positions.

Seems solid enough, but I'm sure I'll find a way of breaking it :twisted:

---

### Post by neu5eeCh on 2011-12-29
> **keithpeter said:**
> I deleted the top panel, added indicators, clock, main menu, and a few launchers to the bottom panel. Used spacers between the launchers as you don't seem to be able to move the panel items to random positions.

Hey, I'd like to delete the top panel in the same fashion, and add the menu the bottom. That's what he's used to. Did you ALT-RIGHT CLICK to make those modifications? Can you point me in a useful direction?

**Edit:** Just answered my own question: [Classic Gnome Guide]("http://mandriver.users.sourceforge.net/classic-gnome-guide.html")

---

### Post by neu5eeCh on 2011-12-29
Another question: I've been reading up on Gnome Fallback. My understanding was that this was Gnome Shell's version of Unity 2D, but some sites imply that Gnome Fallback is a temporary, *to be discontinued*, DE?

---

### Post by lykwydchykyn on 2011-12-29
> **VTPoet said:**
> Another question: I've been reading up on Gnome Fallback. My understanding was that this was Gnome Shell's version of Unity 2D, but some sites imply that Gnome Fallback is a temporary, *to be discontinued*, DE?

That's my understanding of it, which is why I'd recommend steering clear of it.  New wine for new wineskins and all that.

There's also [cinnamon](http://cinnamon.linuxmint.com/), maybe that fits the bill.

---

### Post by neu5eeCh on 2011-12-29
> **lykwydchykyn said:**
> That's my understanding of it, which is why I'd recommend steering clear of it.  New wine for new wineskins and all that.

There's also [cinnamon]("http://cinnamon.linuxmint.com/"), maybe that fits the bill.

So is Gnome going to have an option for older systems? - are they going to come out with something like Gnome Shell 2D? Or have they written off older systems?

---

### Post by Dragonbite on 2011-12-29
> **VTPoet said:**
> Another question: I've been reading up on Gnome Fallback. My understanding was that this was Gnome Shell's version of Unity 2D, but some sites imply that Gnome Fallback is a temporary, *to be discontinued*, DE?

I think what they mean is the "fallback" mode is going to be akin to Unity 2D, where it runs without requiring the desktop effects/hardware acceleration but otherwise looks similar.

If the system can handle it, it goes into full glory Gnome-shell/Unity mode. Otherwise it goes to Gnome-shell-2D/Unity 2D (the Gnome-shell-2D is just a guess ).

That's my guess but I don't have any citations or reference that says exactly that, just that the fallback mode (as we know it now) is being eliminated.  

Keep an eye on Fedora 17 (due out in April or May), as that is supposed to be the first with this Gnome version available.

---

### Post by neu5eeCh on 2011-12-29
> **Dragonbite said:**
> I think what they mean is the "fallback" mode is going to be akin to Unity 2D, where it runs without requiring the desktop effects/hardware acceleration but otherwise looks similar 

Got it. So it will use something like Metacity, like Unity 2D maybe.... or nothing at all. That's too bad. Gnome Classic, while it lacks the customization of Gnome 2.x, seemed like a good option for a user like my friend; but then I don't know what their Gnome Shell 2D will look like. The advantage to Gnome Classic was that it came with or without effects. The disadvantage to a Gnome Shell 2D (I'm guessing) will be that compositing won't be available (at all). Now I'm thinking that the Mint Cinnamon Session might be the best option for him. That, at least, has a future. Cinnamon is probably familiar enough that he won't have to relearn the ins and outs of Unity. I just don't want to have to field frustrated phone calls about Gnome Shell or Unity. If he wants to try them, he can, but the idea is that he'll have a familiar option.

Here is mem usage for Gnome Shell on Mint Linux 12:
> 
                                           total       used       free     shared    buffers     cached
Mem:                       3016       1289       1726          0        156        887
-/+ buffers/cache:          245       2771
Swap:           5859          0       5859Here is Cinnamon, same machine:

>              total       used       free     shared    buffers     cached
Mem:          3016       1227       1788          0        157        867
-/+ buffers/cache:        203       2813
Swap:         5859          0       5859Here is MATE with no effects:

> 
             total       used       free     shared    buffers     cached
Mem:          3016       1218       1797          0        158        858
-/+ buffers/cache:        201       2814
Swap:         5859          0       5859Gnome Classic with Effects (Compiz)
>              total       used       free     shared    buffers     cached
Mem:          3016       1268       1748          0        159        906
-/+ buffers/cache:        202       2814
Swap:         5859          0       5859Gnome Classic without Effects
>              total       used       free     shared    buffers     cached
Mem:          3016       1231       1785          0        159        870
-/+ buffers/cache:        200       2816
Swap:         5859          0       5859
And Unity 3D
>              total       used       free     shared    buffers     cached
Mem:          3016       1441       1575          0        169       1027
-/+ buffers/cache:        244       2771
Swap:         5859          0       5859

So... don't know if this is useful to anybody at all, but there it is.

---

### Post by ssam on 2011-12-29
There is also the [Mate]("http://mate-desktop.org/") project if you want to keep using gnome2.

---

### Post by keithpeter on 2011-12-29
Hello All

[http://askubuntu.com/questions/83334/will-12-04-default-into-unity-the-way-11-10-did](http://askubuntu.com/questions/83334/will-12-04-default-into-unity-the-way-11-10-did)

Good chance the gnome-fallback-session will be around for the next LTS cycle. There is a Gnome Classic mega thread in Ubuntu + 1

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

Fallback customising: I just used the ALT-right click to customise the bottom panel after deleting the top one (ALT-right click delete panel). Added indicators, main menu and the launchers. Looks a bit clunky but it works.

P3 Dell does *not* like Cinnamon. It was fine and customisable to one panel easily when I tried it on the desktop the other day. 

@VTPoet: I bet you an Ubuntu sticker that your friend goes out and buys an iPad before LTS 14.04. 'Ordinary' people I know are doing this over here.

---

### Post by doorknob60 on 2011-12-29
I'd just go with XFCE. Not necessarily Xubuntu either, Debian or Arch with XFCE, if set up properly, is a very quick, light, and stable option (much lighter than Xubuntu). Xubuntu would be fine too though (or maybe something like Mint XFCE?).

---

### Post by mamamia88 on 2011-12-29
> **doorknob60 said:**
> I'd just go with XFCE. Not necessarily Xubuntu either, Debian or Arch with XFCE, if set up properly, is a very quick, light, and stable option (much lighter than Xubuntu). Xubuntu would be fine too though (or maybe something like Mint XFCE?).
Using xubuntu 11.10 right now on my 3-4 year old netbook and it feels brand new.    Don't know how much difference arch or debian would make.

---

### Post by neu5eeCh on 2011-12-29
> **keithpeter said:**
> Good chance the gnome-fallback-session will be around for the next LTS cycle. There is a Gnome Classic mega thread in Ubuntu + 1

That's good to hear. Once I started experimenting with Gnome Fallback, I decided it wasn't quite as bad as it was made out to be.

[URL="http://ubuntuforums.org/showthread.php?t=1873765"]> **keithpeter said:**
> [/URL]@VTPoet: I bet you an Ubuntu sticker that your friend goes out and buys an iPad before LTS 14.04. 'Ordinary' people I know are doing this over here.

Well, I would accept your bet but that would be like taking candy from a baby. My friend is a flinty New Englander as tight as bark on a tree. 

I, however, was just gifted two first generation IPod touches. I didn't realize how useful they were until I started using them. I can download podcasts straight to the IPod. That's kinda' cool. But that's about the only thing they're really useful for (as far as **my** needs go).

---

### Post by neu5eeCh on 2011-12-29
> **doorknob60 said:**
> I'd just go with XFCE. Not necessarily Xubuntu either, Debian or Arch with XFCE, if set up properly, is a very quick, light, and stable option (much lighter than Xubuntu). Xubuntu would be fine too though (or maybe something like Mint XFCE?).

Yeah. That'll be the day. ;) He only just barely knows how to turn his computer on and off. Like I'm really going to give him an Arch or Debian install! Ha! But I hear you. For someone a little more knowledgeable, your recommendation is a good one.

---

### Post by Dragonbite on 2011-12-30
> **VTPoet said:**
> My friend is a flinty New Englander as tight as bark on a tree.

Ha!  I'll have to remember that description, it's so apt!  I take it he was raised up there as well?

---

### Post by neu5eeCh on 2011-12-30
> **Dragonbite said:**
> Ha!  I'll have to remember that description, it's so apt!  I take it he was raised up there as well?

Aye-up, he was raised up here. An IPad with him would be a ten dollar hat on a ten cent head (as we like to say up here).

---

### Post by mips on 2011-12-30
> **mamamia88 said:**
> Don't know how much difference arch or debian would make.

Well Crunchbang XFCE (Debian 6) is way faster than Xubuntu. I'm using Xubuntu at the moment.

---

### Post by stalkingwolf on 2012-01-01
> **VTPoet said:**
> Hey, that's an interesting possibility I hadn't thought of. I'm going to download it and try it in VB - looks like it uses Gnome 2.X?

yes gnome 2 is one of the choices.

---

### Post by neu5eeCh on 2012-01-01
> **stalkingwolf said:**
> yes gnome 2 is one of the choices.

Well... I downloaded and tried out Zorin. For some reason, they felt it necessary to enable a variety of compiz special effects, like wobbly windows. :rolleyes: I guess it's easy enough to disable these, but what a bother. The interface only marginally imitates Win 7. I wanted to try the Zorin "Look Changer", but in the live session I had to log out and log back in. Naturally, none of these distros tell you what the password is. Bother.

Although I swore off KDE, I tried Netrunner 4 (just released) and was impressed with it. Everything worked. One minor glitch (which wouldn't affect *him*) is that deleting the Firefox text Menu doesn't produce a Firefox Button. I might try it on his laptop just because it's the most like Windows (Vista/7). If it lags, I'll try something different.

I keep coming back to Xubuntu with Docky (despite the XFMW4 bug), Gnome Classic or Unity 2D.

---

### Post by BrokenKingpin on 2012-01-02
> **VTPoet said:**
> 
I seriously hesitate to recommend Xubuntu (or XFCE) because of the XFWM4 bug (no windows borders). 
I have never seen this and I have been running Xfce for years? Is it only in certain weird configurations?

Xubuntu is my distro of choice right now, it is a perfect balance between functionality and lightweight. It runs great on my old slow netbook, and also looks very nice on my main desktop with desktop effects and transparency turned on. Highly recommended.

---

### Post by neu5eeCh on 2012-01-02
> **BrokenKingpin said:**
> I have never seen this and I have been running Xfce for years? Is it only in certain weird configurations?

Xubuntu is my distro of choice right now, it is a perfect balance between functionality and lightweight. It runs great on my old slow netbook, and also looks very nice on my main desktop with desktop effects and transparency turned on. Highly recommended.

Can't explain it, but under "Desktop Environments" (here in the forums) there have already been several users affected by it and it was discussed at Distrowatch when 11.04 was reviewed. Anyway, you can read all about it here: [Bug 495361]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361").

But, I set him up tonight. After all the hemming and hawing about which DE I should use, I went with Unity 11.10. :biggrin:

Lubuntu -- Didn't like that it didn't come with Ubuntu Software Center (though that's easy to remedy). Don't like PCMan. Turning off touchpad tap (and other missing little refinements) was going to be a PITA. Don't like how some apps don't initially fit within the allotted screen space (as also described by Dedoimedo). Feels too rough & basic for someone I'm trying to impress.

Xubuntu-- I use Xubuntu, but the bug mentioned above is a deal breaker for a newbie. It also takes more tweaking (than I was willing to invest), to make it as fluid as I like: like making Xubuntu Window List Menu  accessible from at all times, turning off the touchpad tap, installing docky or AWN.

Zorin -- Didn't like that it was built on Gnome 2. Time to move on...

Linux Mint 12 -- I like Mint but Cinnamon is still alpha, Gnome Classic is OK but I didn't like the "no compositing" bug, and the Gnome 3 extensions still aren't enough, in my view, to save the DE. It still doesn't feel very flexible. Also seems like there's just too much fiddle faddle, mousing and keystrokes to do what used to be done much more easily. 

DreamLinux -- Just released, based on Debian Testing, XFCE, docky read to go, wine, Softmaker and other goodies. Based on my experience with LMDE, Debian testing can be rough around the edges. I tried installing it in VB, but it hung. That was enough to make me steer clear of it (for him). I myself might try it again.

Netrunner 4 -- Wow. I *really* like this Distro's implementation of KDE. Wine, Codecs, VLC... everything is ready to go. I would have considered installing this for him except that KDE can be heavy, convoluted to configure, and I just don't like Muon for a new user. From what I've read, it seems unstable and fitful; and it's def. not as new-user friendly as Ubuntu's software center. As for me? I'm going to install this over my Linux Mint 12 partition and start using it.

Ubuntu 11.10 -- Easy to turn off Touchpad tap. Installed the [Classic Menu Indicator]("http://www.omgubuntu.co.uk/2011/06/classicmenu-indicator-puts-old-school-gnome-menus-in-unity/") so he wouldn't have to search, and search, and search through those &%#$! lenses. Installed Ubuntu Tweak, Codecs, Compiz Config Settings Manager, Grub Customizer (so the Grub Menu looks swanky), Synapse, wine and he's good to go. His computer seems happy in terms of speed. His 3-1 printer, scanner, & fax machine now works. He's in clover.

---

### Post by stalkingwolf on 2012-01-07
I have never had to use a password in a zorin live session.   hmmmmmmmm

---

### Post by neu5eeCh on 2012-01-07
> **stalkingwolf said:**
> I have never had to use a password in a zorin live session.   hmmmmmmmm

Have you ever tried to log out and back in during a live session?

---

### Post by stalkingwolf on 2012-01-10
Yes.   ill have to play with it some more.

---

### Post by neu5eeCh on 2012-01-10
The installation is a success. 

My friend seems thrilled with Ubuntu but, so far, he has two complaints. First, he doesn't like how the launcher frequently pops up when he moves his mouse leftward to click on the browser's "back button". (I would move the launcher to the bottom but...) Secondly, he wanted a windows style task bar. I had him install the xfce4-panel and moved it to the bottom. No more complaints for now.

---

### Post by Dragonbite on 2012-01-10
> **VTPoet said:**
> The installation is a success. 

My friend seems thrilled with Ubuntu but, so far, he has two complaints. First, he doesn't like how the launcher frequently pops up when he moves his mouse leftward to click on the browser's "back button". (I would move the launcher to the bottom but...) Secondly, he wanted a windows style task bar. I had him install the xfce4-panel and moved it to the bottom. No more complaints for now.

It's supposed to be easy to move the launcher to the bottom.  There's even a PPA for that.

Assuming you are referring to Unity's launcher.

---

### Post by stalkingwolf on 2012-01-11
> **stalkingwolf said:**
> Yes.   ill have to play with it some more.

i played with it some yesterday and got the result you did. Ill see if i can find an answer.

---

### Post by neu5eeCh on 2012-01-11
> **Dragonbite said:**
> It's supposed to be easy to move the launcher to the bottom.  There's even a PPA for that.

Assuming you are referring to Unity's launcher.

Yes, but the unity launcher doesn't allow him to minimize, for instance, a window the way the xfrce4 panel does (or Windows). There are some other niceties absent from the launcher that I can't think of now because I don't use it often enough. The first thing he told me was that he missed "the windows in the bar that tell you what programs are running" - or something like that. I don't want to turn this into a bash Unity thread because Unity is growing on me, but the launcher is still fairly primitive and limited. So... I put xfce4-panel at the bottom of the screen. This meant I couldn't put the launcher there. You see the dilemma? I wish it were possible to move the launcher to the right or simply turn it off. It really doesn't do Unity any favors. At this stage of its development, there are much, much better options.

---

### Post by neu5eeCh on 2012-01-11
> **stalkingwolf said:**
> i played with it some yesterday and got the result you did. Ill see if i can find an answer.

You'd think they would provide that information somewhere - especially since a key feature involves logging out and back in. A remember a year or so ago there were some distros that required me to log in during a live session -- half of them didn't tell me what username or password I should use!

---

