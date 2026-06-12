---
title: "Darter U3 graphics driver"
date: 2008-12-29
forum: System76 Support
---

### Post by EnderEcho on 2008-12-29
So I'm trying to install WoW on my DU3 and I've got everything working except for super jumbled graphics. It seems a lot of people are suggesting installing graphics drivers.

Are the system76 drivers sufficient?

Could someone direct me to where i can install intel 4500HD drivers?

---

### Post by Guille Damke on 2008-12-29
Hi,
At least in a Pangolin using nVidia graphic cards, we have to go to System>Administration>"Hardware Drivers" and click on the "activate" button that appears there related to the graphic card. Probably that also works for you. Then, this hardware manager downloads and installs the proprietary driver by itself, you just have to reboot your machine and that's all.
God luck!
Guille.

---

### Post by thomasaaron on 2008-12-29
I don't know much about WoW, but we don't add anything for the 4500 chipset. It is supported by xserver-xorg-video-intel out of the box with Ubuntu.

---

### Post by EnderEcho on 2008-12-29
Thanks! I'll try that when I get back from work tonight.

---

### Post by EnderEcho on 2008-12-29
There are no options for me to chose from when I go to hardware drivers. All fields are blank so there is nothing for me to enable.

---

### Post by thomasaaron on 2008-12-29
That's because the driver is already enabled. That's what I meant when I said we don't add anything for the 4500 chipset. It is supported by xserver-xorg-video-intel out of the box with Ubuntu.

---

### Post by EnderEcho on 2008-12-29
O ok. I didn't understand that. Thanks for the help thomas aaron. So now I'll try and fix it from a different angle.

---

### Post by MorphWVUtuba on 2008-12-29
I had similar problems when I tried to install KOTOR on my old Gazelle, which had an older Intel card.  I just gave up & just played Windows games on my Windows box.

One does not have to install the Windows version of the video driver under Wine, right?  Or is that what others are referring to when they say you need to install the video driver?

---

### Post by Murrquan on 2008-12-30
I have been having these same problems on my new Darter Ultra 3: [LINK]("http://ubuntuforums.org/showthread.php?t=1021629")

And yes, I enabled the System76 drivers.

What can I do to solve this? Does anyone have any ideas?

---

### Post by EnderEcho on 2009-01-02
I've been reading through a lot of forums trying to understand this whole open driver thing for Intel cards. I always had nvidia before I got my darter so I guess I never really had the need to learn about the importance of graphics cards and 3d games.

I heard 3D games wont run that great on Intel cards. Is there any place I can get a different driver for my intel card or is what I have out of the box my only option?

Thanks.

---

### Post by Spr0k3t on 2009-01-02
> **EnderEcho said:**
> I've been reading through a lot of forums trying to understand this whole open driver thing for Intel cards. I always had nvidia before I got my darter so I guess I never really had the need to learn about the importance of graphics cards and 3d games.

I heard 3D games wont run that great on Intel cards. Is there any place I can get a different driver for my intel card or is what I have out of the box my only option?

Thanks.

Yeah, 3D games won't run that great by comparison to the extreme bleeding edge of a dedicated graphics card.  However, running games like UrbanTerror at full screen with all the settings at full quality and still getting an average of 80+ fps is nothing to be upset with.

---

### Post by Murrquan on 2009-01-02
> **EnderEcho said:**
> I've been reading through a lot of forums trying to understand this whole open driver thing for Intel cards. I always had nvidia before I got my darter so I guess I never really had the need to learn about the importance of graphics cards and 3d games.

I heard 3D games wont run that great on Intel cards.

[The Phoronix benchmarks]("http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1") suggest that as far as integrated processors go, we've got a good one. But I'm having trouble getting it to run anything, even [Runescape]("http://www.runescape.com"). Planet Penguin Racer and Compiz work fine, but Java and Wine apps are either broken or slow.

I think the issue is related to driver support ... at least, [this thread]("http://ubuntuforums.org/showthread.php?t=889323") suggests as much. The most recent poster [expresses his hopes]("http://ubuntuforums.org/showpost.php?p=6466940&postcount=170") that it'll be solved by the time Jaunty comes out, but if there's anything we can do to fix it before then, there'll be a lot of happy DARU3 owners out there. Including me!

Let's keep digging and see what we can come up with. WoW and FFXI players unite!

---

### Post by Murrquan on 2009-01-03
**UPDATE:** There was an update to wine and wine-gecko this morning, so I decided to give Steam and the POL Viewer a shot. This time Steam loaded and was stable, although some of the text was a little fuzzy. Starting Portal, though, caused the whole system to crash and revert to the login prompt. Same thing with the POL Viewer, after a minute, which still just displayed a black screen.

The terminal output showed a lot of "Can't translate this" strings in relation to some Wine Direct3d / DirectDraw function.

---

### Post by Murrquan on 2009-01-03
**UPDATE:** I just attempted to use Wine to install Sonic R, an old Win98 game that ran well on my old Thinkpad and that has [a Silver rating]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5962") on WineHQ.org. Terminal output says things like "Bad Pixmap" and backtraces to things like "X11DRV_GetBitmapBits."

I'm still not sure what all of this means. But taken together, it's starting to look like Windows games just don't run on a DARU3 running Ubuntu, period.

---

### Post by Spr0k3t on 2009-01-03
Verified Portal crashes X with the DARU3.  I'm testing WINE with the latest build (1.1.12).

---

### Post by EnderEcho on 2009-01-03
I downloaded the wine 1.1.12 patch this morning and although things are still scrambled its running smoother. The sound is better and the graphics are not jumpy. 

Unfortunately it didn't fix my scrambled problem, but things are improving. I can run fallout 1 and 2 on my computer so its not to say that all windows games dont run. It just takes a little work. So just keep putting the effort and we'll get there.

Just wish I could find out why the graphics would be jumbled the way they are. I'll try again in D3D modes witht he new patch when I get home tonight and post results.

---

### Post by Murrquan on 2009-01-03
**PROGRESS:** I tried installing Sonic R again, this time with Compiz turned off. This time, it worked! It crashed when I went to run the game, but I got the following output in the terminal:

```
Unhandled exception: divide by zero in 32-bit code (0x004801d9).
```

That got me thinking. Maybe we're having these problems because we're trying to run 32-bit Windows apps with the 64-bit version of Wine, on 64-bit Ubuntu? I don't know much about this kind of thing, but [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) says

> If you're running a 64 bit version of your distro, building Wine the usual way yields... 64 bit wine! This usually isn't what you want. Building a 32 bit Wine on a 64 bit system requires a few extra steps.

They give instructions for building 32-bit Wine "The easy way," which is only supported on Ubuntu 8.10 out of all the distros of Linux right now. Lucky us! Unfortunately, I ran their instructions and got

```
install-wine-deps.sh: 2: Syntax error: newline unexpected
```

A bit of examination revealed why. The install-wine-deps.sh file that's retrieved using their command is an HTML file from Google Code! Talk about your mix-ups. But Google came through to help me find what we're *really* looking for, here: [http://www.nabble.com/install-wine-deps.sh-can-now-handle-32-bit-wine-on-64-bit-systems-td21260595.html](http://www.nabble.com/install-wine-deps.sh-can-now-handle-32-bit-wine-on-64-bit-systems-td21260595.html)

I clicked on the link that they gave there, [http://code.google.com/p/winezeug/source/browse/trunk/install-wine-deps.sh](http://code.google.com/p/winezeug/source/browse/trunk/install-wine-deps.sh), and got -- sure enough -- a Google Code page. The code was there, though, and this time I just copied and pasted it into Gedit, and saved over the old file. Then I typed

```
sudo sh install-wine-deps.sh
```

as WineHQ recommended in [the link that I gave earlier](http://wiki.winehq.org/WineOn64bit), and it worked! It pulled down all the necessary files and installed them.

Unfortunately, I'm stuck on the next part, where *they* say to type

```
./configure 
make
```

and the guy on Nabble says to type

```
./configure --target=i686-unknown-gnu-linux
make
```

because typing ./configure just gives me

```
bash: ./configure: No such file or directory
```

Is there something I'm missing here? What can I do to get it to work? And does this sound like a good idea to investigate?

**Incidentally**, I think the problem with Runescape that I mentioned might be because I was trying to run it in IcedTea. Unfortunately, there isn't a 64-bit version of Sun Java in the repositories. There was a thread somewhere on the forums that explained how to install 64-bit Sun Java, but I tried it and couldn't get it to work. Maybe I did something wrong? I'll try to dig that thread up later on.

---

### Post by EnderEcho on 2009-01-03
Running a 32-bit version might be worth investigating. I have a few games that are currently working so I'm a little hesitant to reinstall wine and potentially be left with nothing.

Keep me posted on building a 32 bit and maybe if I get fed up with seemingly dead end I'll give it a whirl.

---

### Post by Spr0k3t on 2009-01-03
> **Murrquan said:**
> **Incidentally**, I think the problem with Runescape that I mentioned might be because I was trying to run it in IcedTea. Unfortunately, there isn't a 64-bit version of Sun Java in the repositories. There was a thread somewhere on the forums that explained how to install 64-bit Sun Java, but I tried it and couldn't get it to work. Maybe I did something wrong? I'll try to dig that thread up later on.

I can rule out Runescape.  It works perfectly on 64bit with the Sun Java plugin (Follow this thread for install instructions [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)).  I was even able to log into the game using fullscreen (hide advertising element then F11 to fullscreen firefox) with no problems.

In the repos using the wineteam PPA, the 64bit package of WINE is compiled already for 32bit.  Also, I can run Portal on the other computer systems in my network without problems.  Only one system is not running 64bit due to processor limitations.

---

### Post by Murrquan on 2009-01-03
> **EnderEcho said:**
> Running a 32-bit version might be worth investigating. I have a few games that are currently working so I'm a little hesitant to reinstall wine and potentially be left with nothing.

Keep me posted on building a 32 bit and maybe if I get fed up with seemingly dead end I'll give it a whirl.

I will if I can find out how!

What games are you running? And are you just using the standard Wine install from Add/Remove Programs?

---

### Post by EnderEcho on 2009-01-03
Well that rules that out. I wish I had my box in front of me to try out the D3D results. Is there any other way I can run it in direct X mode other than changing the wtf config file?

---

### Post by darkknight045 on 2009-01-05
> **EnderEcho said:**
> Well that rules that out. I wish I had my box in front of me to try out the D3D results. Is there any other way I can run it in direct X mode other than changing the wtf config file?

Absolutely, simply run the game with the following command in Terminal:
(You may need to adjust the path if you don't have it installed to the default directory.)
```
wine "C:\Program Files\World of Warcraft\Wow.exe" -d3d
```

If this doesn't do too well then try:

```
wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```

I've heard accounts of WoW performing better in D3D mode when running on Intel Cards.

---

### Post by Modax42 on 2009-01-06
Some windows games do work.  I am running Baldur's Gate, Baldur's Gate II, and Deus Ex on my Darter Ultra 3 without issues.  Performance in Deus Ex leaves something to be desired though.

---

### Post by EnderEcho on 2009-01-07
So I run WoW in the terminal after a reinstall. Everything is still jumbled. 

Heres the ouput:

user@ubuntu:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374026a4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20028, 0x13c8d0): stub
user@ubuntu:~$ 



Can anyone give me some tips on whats going on here?


Also i just got a new update that said something about Nvidia, but I'm confused since I have an intel card.

---

### Post by EnderEcho on 2009-01-07
Everytime I run in D3D mode it crashes. Where can I find the output from the terminal after my system reboots?

---

### Post by EnderEcho on 2009-01-14
Im running it effectively in D3D mode. Im running wine in windows 98 mode with pixel shader turned off. 

Anyone know how i can get more FPS?

---

### Post by EnderEcho on 2009-01-17
I've been looking at different intel drivers and I'm familiar with downloading drivers on ubuntu.

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

I'm not very familiar with the language either, but it seems that this might be a great option for driver that supports OpenGL direct rendering.

I need some opnions and guidance before I check this out though

---

### Post by Murrquan on 2009-01-19
EnderEcho, here's what I've dug up. Apparently there's an epic thread going on about it here: [http://ubuntuforums.org/showthread.php?t=963386](http://ubuntuforums.org/showthread.php?t=963386)

[This post]("http://ubuntuforums.org/showpost.php?p=6333299&postcount=27") and [this post]("http://ubuntuforums.org/showpost.php?p=6386402&postcount=31") seem to confirm my suspicions: There's a good deal of CPU emulation going on here. We aren't seeing hardware acceleration at all. People say that the next version of the Linux kernel may have the support that we need ... and [this guy]("http://ubuntuforums.org/showpost.php?p=6461619&postcount=47") seems to suggest that nothing else will work, and that only the next release of Ubuntu will help.

Some people are reporting that Fedora 10 works too, but I think the reports conflict, and Fedora doesn't have the System76 drivers anyway. Plus, it's not as cool as Ubuntu.

---

### Post by Murrquan on 2009-01-20
'Nother update: [This guy]("http://ubuntuforums.org/showthread.php?t=1010805") said last month that our 3d acceleration still isn't working in Jaunty. Someone replied to him, though, saying that the problem would be fixed soon. Looks like there's nothing for it but to sit tight and wait.

---

### Post by EnderEcho on 2009-01-20
Thanks for the heads up Murr!

---

### Post by Modax42 on 2009-01-20
[QUOTE=Murrquan] This post and this post seem to confirm my suspicions: There's a good deal of CPU emulation going on here. We aren't seeing hardware acceleration at all. People say that the next version of the Linux kernel may have the support that we need ... and this guy seems to suggest that nothing else will work, and that only the next release of Ubuntu will help.[/QUOTE]

CPU emulation?  Do you mean that the CPU is being forced to do the job of the graphics chip in games?  That would explain why CPU usage in Baldur's Gate is a constant 60% even though the system requirements are so minimal.  In Deus Ex (which is Open GL, by the way) CPU usage is like 90%.

I truly hope that the x4500 gets fully supported by Jaunty.  My Daru3 will be six months old by then!

---

### Post by Murrquan on 2009-01-20
> **Modax42 said:**
> CPU emulation?  Do you mean that the CPU is being forced to do the job of the graphics chip in games?

Yes, that's what I mean. At least, that's the way that it seems that it is.

D'you suppose there's some way to give potential System76 customers a heads-up, or something? It probably wouldn't have changed my decision (since they're going to fix it soon), but it might be important for someone else to know.

---

### Post by Murrquan on 2009-04-18
UPDATE: Graphics performance on the DARU3 Darter Ultra drops dramatically in Jaunty. It's not just games this time; Frame rate on Docky and Compiz is extremely choppy, even with the backported drivers from the Intel PPA. ([LINK]("https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa"))

I'm emailing System76 support, and hoping they don't tell me the problem is I bought too cheap of a computer. Like they did last time. ^.^; They probably don't support Jaunty yet, but as least I can let them know that it's an issue. Hopefully you people won't have to go through this with the official release.

[http://ubuntuforums.org/showpost.php?p=7089002&postcount=143](http://ubuntuforums.org/showpost.php?p=7089002&postcount=143)

---

