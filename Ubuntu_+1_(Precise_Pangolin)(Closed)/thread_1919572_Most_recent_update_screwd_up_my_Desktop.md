---
title: "Most recent update screwd up my Desktop"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-03
Hi all

I've installed the reported updates last night, and then after a restart my GUI is having issues. Menus and windows have an awful light grey background, my password prompt fields (including on login) became narrow so I can't even see if I'm typing, some icons got changed too. But the worst thing is that my Skype installation was removed for some reason, and I can't even re-install it:

Cannot install ia32-libs.

When I try to install ia32-libs through Synaptic, it wants to uninstall 20 other rhings, among which Unity, Unity-2D, VLC etc.

What's going on?

---

### Post by bmbaker on 2012-02-03
well i don't have the skype or .la issues but the themes are all off somehow! the only theme wks properly is the gnome-shell default!!

---

### Post by dino99 on 2012-02-03
> **bmbaker said:**
> well i don't have the skype or .la issues but the themes are all off somehow! the only theme wks properly is the gnome-shell default!!

Sorry but gnome-classic have no trouble at all (i386)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-03
I don't have Gnome installed, so can't test Gnome Themes, unfortunately.

---

### Post by xyzzyman on 2012-02-03
Did you do a 'partial update'? That's the only way it would have uninstalled Skype and it would have asked you. You're going to have to wait until the dependancies are all resolved so keep checkin' the repo's for updates.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-03
I giess that's what I did, although I can't recall. How long do you think it should take to resolve dependancies, if there's any guessing?

---

### Post by xyzzyman on 2012-02-03
Hard to know. Also depends on when your mirror gets updated. It wouldn't have updated you to unity 5.0 unless you added a PPA that has unity 5.0 in it. It was pulled for precise from the unity-team staging PPA so not sure what PPA you've added

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-03
Thanks for the help. I have Unity 5.1 installed. I guess I'll have to wait some more. But the newest update is actually trying to uninstall ubuntu-desktop and unity(?!?!) Nonsense.

---

### Post by xyzzyman on 2012-02-03
No, it's not nonsense. It happens during alpha and beta testing. Please read the following sticky: [http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

If this isn't acceptable then you may be happier dropping back to the current LTS (10.04) or 11.10 if you want the closest to what 12.04 will be.

---

### Post by mc4man on 2012-02-03
> **&#1058 said:**
> Hi all

I've installed the reported updates last night, and then after a restart my GUI is having issues. Menus and windows have an awful light grey background, 

What's going on?

There was an upgrade to gtk* that required some light-theme fixes. The new light-theme is still a bit broken but - 
There is some suggestion in the bug report that there has been a design change to use light background, dark text on context menus.
If so I dislike & will change locally, time will tell on that I suppose

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

The latest update revrts some gtk2 changes that messed up messaging menu - the light bg, dark on context menu windows stands - seems wrong, but if not changed shouldn't be hard to revert

---

### Post by Quackers on 2012-02-03
I'm currently holding back on the libxcb updates as they want to remove all kinds of things ( google-earth, gstreamer blah, blah, blah).

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-03
I'm fully aware of risks involved when using pre-stable releases. And probably my reaction was too harsh, given that it's still far from the finished product. But this regression took me by surprise - my 12.04 pre-alpha actually seemed more stable than 12.04 alpha 2.

Not that I'm mad about current look & feel of Ambience theme, but mixing background colours like it happened on my platform is really a less optimal solution.

---

### Post by xyzzyman on 2012-02-03
> **&#1058 said:**
> I'm fully aware of risks involved when using pre-stable releases. And probably my reaction was too harsh, given that it's still far from the finished product. But this regression took me by surprise - my 12.04 pre-alpha actually seemed more stable than 12.04 alpha 2.

Not that I'm mad about current look & feel of Ambience theme, but mixing background colours like it happened on my platform is really a less optimal solution.

Pre alpha or alpha 2 is meaningless as that was just a snapshot of where it was that day. On a developers machine somewheres where they updated a package things are probably working fine. It's when you do a partial upgrade and things aren't all synced yet that things will really break and then you can't blame it on anyone but yourself. When they regress during normal upgrades then you can go submitting bug reports.

---

### Post by 57990166419925142424 on 2012-02-03
The update uninstalled ubuntu-desktop and unity. 

I cannot reinstall them since libnux-abiversion-20111214 is not available. Any idea on how to fix this?

---

### Post by xyzzyman on 2012-02-03
> **57990166419925142424 said:**
> The update uninstalled ubuntu-desktop and unity. 

I cannot reinstall them since libnux-abiversion-20111214 is not available. Any idea on how to fix this?

You'll have to wait until the update is available.

---

### Post by ranch hand on 2012-02-04
I my experience with testing Ubuntu A2 is where the real fun begins.

Before that you have a modification of the last release.

After that you have the raw new release.  A2 is when grub2 was dropped into 9.10-testing.  A2 was when Plymouth was dropped into 10.04-testing.

This is when the FUN begins.  Ought to get back to stable sometime around the 10.04.4 ISO release or shortly after.

---

### Post by keithpeter on 2012-02-04
> **ranch hand said:**
> This is when the FUN begins.  Ought to get back to stable sometime around the 10.04.4 ISO release or shortly after.

OK, pre-flight checklist

[LIST]
[*]Separate home partition [ check ]
[*]Rsync backup of home drive to external hard drive daily [ check ]
[*]Small partition with CentOS 6.2 install with own home drive that can mount main home drive [ check ]
[*]Tin hat [ check ]
[*]Change of under clothing [ check ]
[/LIST]

Bring it on :twisted:

---

### Post by kevpan815 on 2012-02-04
There were some 20 updates that were originally held back yesterday, that you would have noticed if you had used sudo apt-get update and sudo apt-get upgrade, one of them was an update for Unity. Just FYI.

---

### Post by VinDSL on 2012-02-05
> **mc4man said:**
> There was an upgrade to gtk* that required some light-theme fixes. The new light-theme is still a bit broken but - 
There is some suggestion in the bug report that there has been a design change to use light background, dark text on context menus.
If so I dislike & will change locally, time will tell on that I suppose

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

The latest update revrts some gtk2 changes that messed up messaging menu - the light bg, dark on context menu windows stands - seems wrong, but if not changed shouldn't be hard to revert
Latest updates seem to have taken care of the problem(s) for me.

I run an odd mixture of light/dark themes and icons sets, and my desktop looked like garbage for the past couple of weeks.

After today's updates, Unity 3D is good again...


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-5-feb-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-feb-2012-1.png")[/INDENT]

---

