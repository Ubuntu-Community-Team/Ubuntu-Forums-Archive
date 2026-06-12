---
title: "Call for testing Compiz 0.9.7.0-beta1"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-02-10
Hello everyone. I wanted to inform you of another testing opportunity! 

The ubuntu desktop team has packaged up a new version of compiz and is looking for people to help test for breakage before releasing into the archive. 

The changes in this new version of compiz are better performance and stability, but this needs testing to verify that is the case.

Please see this post for more details:
[http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html](http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html)

Please help test - and feel free to post any questions about doing so here. The testing goes on through this weekend with a goal of pushing this to precise next week. Thanks!

Nicholas

---

### Post by lucazade on 2012-02-10
any further info besides "The changes in this new version of compiz are better performance and stability" that means everything and nothing? :)

the only thing I've found are the latest commits in the trunk branch but no milestone or other info:
[https://code.launchpad.net/~compiz/compiz/ubuntu](https://code.launchpad.net/~compiz/compiz/ubuntu)

---

### Post by balloons on 2012-02-10
> **lucazade said:**
> any further info besides "The changes in this new version of compiz are better performance and stability" that means everything and nothing? :)

the only thing I've found are the latest commits in the trunk branch but no milestone or other info:
[https://code.launchpad.net/~compiz/compiz/ubuntu](https://code.launchpad.net/~compiz/compiz/ubuntu)

Yep, really generic :-) However if your curious for specifics, check out the commit log on bugs this is attempting to correct:

[Commit Log for Compiz0.9.7]("https://code.launchpad.net/~didrocks/unity/ubuntu-compiz0.9.7")

---

### Post by ventrical on 2012-02-10
> **guitara said:**
> Hello everyone. I wanted to inform you of another testing opportunity! 

The ubuntu desktop team has packaged up a new version of compiz and is looking for people to help test for breakage before releasing into the archive. 

The changes in this new version of compiz are better performance and stability, but this needs testing to verify that is the case.

Please see this post for more details:
[http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html](http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html)

Please help test - and feel free to post any questions about doing so here. The testing goes on through this weekend with a goal of pushing this to precise next week. Thanks!

Nicholas


Thanks Nick.. thats the best news Iv'e heard yet ! :)

 I'm in!

---

### Post by effenberg0x0 on 2012-02-10
In [https://code.launchpad.net/~didrocks/unity/ubuntu-compiz0.9.7](https://code.launchpad.net/~didrocks/unity/ubuntu-compiz0.9.7) we can the revisions. Not a proper changelog, but gives us an idea of the LP bugs fixed in each revision for this branch.

Regards,
Effenberg

---

### Post by lucazade on 2012-02-10
> **guitara said:**
> Yep, really generic :-) However if your curious for specifics, check out the commit log on bugs this is attempting to correct:

[Commit Log for Compiz0.9.7]("https://code.launchpad.net/~didrocks/unity/ubuntu-compiz0.9.7")

ah great, thanks!

Devil is in the details :)

---

### Post by prusswan on 2012-02-10
is this still a certified Unity killer?

edit: nvm I read the blog post

---

### Post by mc4man on 2012-02-10
Just to note - atm this ppa & unity staging are not compatible, so if using the staging one would need to remove/revert before testing compiz

---

### Post by ventrical on 2012-02-10
Works just beautiful on my Nvidia!!

  Nice work so far.

```
camel2@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
camel2@ubuntu:~$ 

```

---

### Post by ventrical on 2012-02-10
The menu title border on windows (firefox) and the raster tear that used to be there between the main window and the menu border is practically non existent when using (wobbly windows)! :)

 nice work ..

---

### Post by ventrical on 2012-02-10
First crash bug ..
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/930336](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/930336)

---

### Post by cariboo on 2012-02-10
I saw this in my email this morning:

> Hello everyone. I wanted to inform you of another testing opportunity!

The ubuntu desktop team has packaged up a new version of compiz and is looking for people to help test for breakage before releasing into the archive.

The changes in this new version of compiz are better performance and stability, but this needs testing to verify that is the case.

Please see this post for more details:
[http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html](http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html)

Please help test - and feel free to post any questions about doing so here. The testing goes on through this weekend with a goal of pushing this to precise next week. Thanks!

Nicholas

**Edit** I did it again, I'm going to have to stop posting until at least my second cup of coffee in the morning. :)

---

### Post by balloons on 2012-02-10
> **ventrical said:**
> First crash bug ..
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/930336](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/930336)

I edited your report to add the "0.9.7.0-beta1".. we're working on a way to automagically have these attached to bug reports, but for now it's really important you include it so this report gets seen and queued properly :-) Thanks for reporting the issue!

---

### Post by ventrical on 2012-02-10
> **guitara said:**
> I edited your report to add the "0.9.7.0-beta1".. we're working on a way to automagically have these attached to bug reports, but for now it's really important you include it so this report gets seen and queued properly :-) Thanks for reporting the issue!

A hh .. yes ... I am just trying to get active with testing and forgot the order in which way we are to report on these bugs.

 Thanks so very much ,regards, Ventrical

---

### Post by mc4man on 2012-02-10
A quick look suggests not so great atm - will have to explore further, just looked at viewports
At least here
[Desktop-based viewport switching broken]("https://bugs.launchpad.net/bugs/930427")
No scale binding can be set whether initiated straight up or thru dbus, possibly something upcoming as the 1 current one is broken? (Shift+Alt+up 
Keyboard viewport switching, (Wall), is graphically poor ( may be corner case hardware, don't know yet, edit - not hardware based, just poor compared to 0.9.6+

---

### Post by Vaun on 2012-02-10
Much much slower than compiz in the archive for Precise on intel graphics.  Slow scrolling, laggy animations, slow fading windows.  Purged.

---

### Post by ventrical on 2012-02-10
Will not allow for some bug report because compiz-core is third party app.

---

### Post by cariboo on 2012-02-10
Are you doing what it suggests here?

> Filing Bugs
If you find something is broken, please let the developers know. Please file bugs against the compiz-core package in launchpad ([https://bugs.launchpad.net/compiz-core/+filebug](https://bugs.launchpad.net/compiz-core/+filebug)). Make sure when filing to tag it "0.9.7.0-beta1". This will make sure your issue is seen by the developers and they will know it is in relation to this new package.

---

### Post by ventrical on 2012-02-10
It's a lot snappier and has this new function  (when you hover over layered windows they will come up).

  Looking good so far.

  It doesn't crash  as bad as it used to as during the beta testing during Oneiric. 
  It will freeze up  when making changes in CCSM, ie; like Ring Switcher... and there  is a conflict with the <super> key and Shortcuts window.

[http://www.youtube.com/watch?v=BdQgBJVFneU](http://www.youtube.com/watch?v=BdQgBJVFneU)

---

### Post by redcylon on 2012-02-10
> **mc4man said:**
> A quick look suggests not so great atm - will have to explore further, just looked at viewports
At least here
[Desktop-based viewport switching broken]("https://bugs.launchpad.net/bugs/930427")
No scale binding can be set whether initiated straight up or thru dbus, possibly something upcoming as the 1 current one is broken? (Shift+Alt+up 
Keyboard viewport switching, (Wall), is graphically poor ( may be corner case hardware, don't know yet, edit - not hardware based, just poor compared to 0.9.6+

Yeap..just filed a bug for scale binding not working when initiated via mouse. Shift+Alt+up works though.

---

### Post by ventrical on 2012-02-10
> **cariboo907 said:**
> Are you doing what it suggests here?

Thanks for the reminder.

---

### Post by ventrical on 2012-02-10
> **redcylon said:**
> Yeap..just filed a bug for scale binding not working when initiated via mouse. Shift+Alt+up works though.

Shift+alt+up working here too.

---

### Post by mc4man on 2012-02-10
> **redcylon said:**
> Yeap..just filed a bug for scale binding not working when initiated via mouse. Shift+Alt+up works though.

Working here now - may have been something related to purging the unity/staging & upgrading from the compiz ppa.

(have you ever tried to set a binding for window group or initiate all? could get it in 0.9.6 but in 0.9.7 doesn't work

Edit; as far as scroll on desktop - took a bit to realize what was happening, it stops if the Ws has no open windows

---

### Post by kaldor on 2012-02-10
I'm noticing absolutely no difference between this PPA and stock after a reboot on my secondary machine. I guess this is a good thing.

---

### Post by geojorg on 2012-02-11
> **mc4man said:**
> Working here now - may have been something related to purging the unity/staging & upgrading from the compiz ppa.

(have you ever tried to set a binding for window group or initiate all? could get it in 0.9.6 but in 0.9.7 doesn't work

Edit; as far as scroll on desktop - took a bit to realize what was happening, it stops if the Ws has no open windows

Could you point me to your bug report, I don't have scale for all windows in all workspaces neither hot corner or Shift+alt+up. 
The same thing for expo plugin

---

### Post by geojorg on 2012-02-11
I just reported this one [https://bugs.launchpad.net/unity/+bug/930629](https://bugs.launchpad.net/unity/+bug/930629)

---

### Post by mc4man on 2012-02-11
> **geojorg said:**
> Could you point me to your bug report, I don't have scale for all windows in all workspaces neither hot corner or Shift+alt+up. 
The same thing for expo plugin

I don't believe initiate_all is working in 0.9.7, likely this is already known - filed anyway
[https://bugs.launchpad.net/compiz-core/+bug/930514](https://bugs.launchpad.net/compiz-core/+bug/930514)

---

### Post by rbrick49 on 2012-02-12
> **guitara said:**
> Hello everyone. I wanted to inform you of another testing opportunity! 

The ubuntu desktop team has packaged up a new version of compiz and is looking for people to help test for breakage before releasing into the archive. 

The changes in this new version of compiz are better performance and stability, but this needs testing to verify that is the case.

Please see this post for more details:
[http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html](http://www.theorangenotebook.com/2012/02/call-for-testing-compiz-0970-beta1.html)

Please help test - and feel free to post any questions about doing so here. The testing goes on through this weekend with a goal of pushing this to precise next week. 

Nicholasseems to be working ok here 64 bit system

---

### Post by VinDSL on 2012-02-12
Heh!  Late to the party, again...  :D

I have a bad habit of only reading the 1st page in the +1 Forum -- glad somebody bumped this!

Anyway, I've been onboard for... let's see... the past 17 minutes.  LoL!

So far, so good!

---

### Post by rbrick49 on 2012-02-12
> **VinDSL said:**
> Heh!  Late to the party, again...  :D

I have a bad habit of only reading the 1st page in the +1 Forum -- glad somebody bumped this!

Anyway, I've been onboard for... let's see... the past 17 minutes.  LoL!

So far, so good!hello vin I just installed  the new compiz seems ok wobbly windows the best I have seen since 11.10 my daughter just loves it it comes up minimized then jups to full screen firefox and chrome that is
its getting late in the night here excuse my backwards forward

---

### Post by ventrical on 2012-02-12
enable shelf causes crash. reset and wierd Unity launcher activity. Although  it will scale down, other open windows have to be minimized to be able to scale up the scaled down window, otherwise it remians blurred in scale down.

[https://bugs.launchpad.net/compiz-core/+bug/931081](https://bugs.launchpad.net/compiz-core/+bug/931081)

---

### Post by mc4man on 2012-02-12
> **ventrical said:**
> enable shelf causes crash. reset and wierd Unity launcher activity. Although  it will scale down, other open windows have to be minimized to be able to scale up the scaled down window, toherwise it remians blurred in scale down.

[https://bugs.launchpad.net/compiz-core/+bug/931081](https://bugs.launchpad.net/compiz-core/+bug/931081)

Well good luck there - will be interested to see if you get any support on 

That plugin would be a 2 strike plugin, 1 it's in Universe, 2 it's not default provided.

From what I see even  plugins **that are in Main but not in the 'default' packages** won't see significant bug support (official) during dev or ever

So these would be the "supported" plugins, the rest seem to be considered "unsupported"
> 
animation
ezoom
move
staticswitcher
bailer 
fade
opengl
unityshell
gnomecompat
place
vpswitch
compiztoolbox
grid
regex
wall
composite
gtkloader
resize
workarounds
decor
imgpng
scale
detection
session
expo
mousepoll
snap

---

### Post by ventrical on 2012-02-12
> **mc4man said:**
> Well good luck there - will be interested to see if you get any support on 

That plugin would be a 2 strike plugin, 1 it's in Universe, 2 it's not default provided.

From what I see even  plugins **that are in Main but not in the 'default' packages** won't see significant bug support (official) during dev or ever

So these would be the "supported" plugins, the rest seem to be considered "unsupported"


  I thought the call  for compiz testing dealt with the whole lot of CCSM plugins.

oh well.. we'll see..

 thanks for your veiws

  saves lots of work :)

---

### Post by mc4man on 2012-02-12
> **ventrical said:**
> I thought the call  for compiz testing dealt with the whole lot of CCSM plugins.

oh well.. we'll see..

 thanks for your views

  saves lots of work :)
Don't take what I said as 'fact', it's just an observation
(one example of a broken plugin in Main that likely will not be fixed is here though the bug report has recently gotten well out of hand

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

---

### Post by ventrical on 2012-02-12
> **mc4man said:**
> Don't take what I said as 'fact', it's just an observation
(one example of a broken plugin in Main that likely will not be fixed is here though the bug report has recently gotten well out of hand

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)


 Interesting for sure. It is very fast. I tried some experiments with Enable Rotate Cube , Additional settings , but no luck. It just appears to me that the screen is bootstraping itself after the mouse binding has been let go of.  I think there is a conflict with another plug in that may be doing this.  But I think also that  the problem may be deeper. It is a program workaround that may be doing this A patch that they had to insert to satisfy Unity depends. So it appears that  the devs  took a short cut here and this bug may be a result of a simple reset of a process in the loop - so it will  _pop_ a hole in the subroutine, set up a traffic cop, reset the cube_screen_current , pull the traffic cop, then _put_ the segment back in the loop and the result is that flicker. ( assumedly) :)


 Just amazing..

---

### Post by ventrical on 2012-02-12
I was just experimenting with 3d Windows option and  disabled '3D only on Mouse rotate' and it appeared to  improve it ..  at least  it looks so .. but no fix for sure..

---

### Post by ventrical on 2012-02-12
Unchecking option: Grid>Edges>Snap Windows back to Original Size, will wipe out all CCSM settings a default to Unity 2D with all setting (including Unity Plugin) unchecked.

I'll report this ... in a bit..

---

### Post by ventrical on 2012-02-12
> **ventrical said:**
> Unchecking option: Grid>Edges>Snap Windows back to Original Size, will wipe out all CCSM settings a default to Unity 2D with all setting (including Unity Plugin) unchecked.

I'll report this ... in a bit..


edit:

  This bug is a real hazard!!!  It has wiped out all my Unity 3D DE across 7 admin users.

edit:

[https://bugs.launchpad.net/compiz-core/+bug/931173](https://bugs.launchpad.net/compiz-core/+bug/931173)

---

### Post by ventrical on 2012-02-12
Desktops restored by logging on to Unity 2D, tic Unity-Plugins.

---

### Post by mc4man on 2012-02-12
> **ventrical said:**
> edit:

  This bug is a real hazard!!!  It has wiped out all my Unity 3D DE across 7 admin users.

edit:

[https://bugs.launchpad.net/compiz-core/+bug/931173](https://bugs.launchpad.net/compiz-core/+bug/931173)

Do see the option as an issue if changed though not affecting other accounts & _not a ccsm issue_, same occurs with gconf

What happens is this is one of those settings changes where compiz 'resets' except in this case the option prevents that from completing and compiz can't start. Same occurs on a re-login

Can be seen here - 
> blah, blah
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Skipping upgrade com.canonical.unity.unity.03.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing snap options...done
Initializing wall options...done
Initializing vpswitch options...done
Initializing gnomecompat options...done
Initializing resize options...done
[COLOR="Blue"]Initializing grid options...done
compiz (core) - Warn: Value type is not yet set[/COLOR]
gnome-session[12831]: WARNING: App 'compiz.desktop' respawning too quickly
[COLOR="Red"]gnome-session[12831]: WARNING: Application 'compiz.desktop' killed by signal[/COLOR]
gnome-session[12831]: WARNING: App 'compiz.desktop' respawning too quickly

As far as recovery - nautilus should of still be up - you could navigate to either where the option is set, open in gedit & change, (screen) or go to /usr/share/applications, open ccsm & change or open a  terminal & change the option back.

If you want to try again this will set the bad option & opposite will restore
```

gconftool-2 -s -t bool /apps/compiz-1/plugins/grid/screen0/options/snapback_windows false
```

---

### Post by ventrical on 2012-02-12
Mabey I am getting old , but, back in my day they would set a traffic_cop and wait for a value to be set. I see it as  the programmers are trying to expedite a quick and efficient program but getting all these side by sides in the process.

  Good too see that it is not ccsm related. In fact I think too many bugs are flagged to ccsm when they are most likely generated elsewhere.

  I may try your method later but Ctrl+Alt+F1, sudo reboot, log on to Unity 2D and  reset the Unity Plugin worked great.

 Overall ccsm/compiz is working great from the ppa. Guess we will just have to keep brainstorming to find some fixes. ... what .. less than 60 days for stable 12.04 release?

---

### Post by BwackNinja on 2012-02-13
> **mc4man said:**
> Don't take what I said as 'fact', it's just an observation
(one example of a broken plugin in Main that likely will not be fixed is here though the bug report has recently gotten well out of hand

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

I've got a hack that I'm using right now that makes the issue go away, but its just a hack. At best it shows that there is some miscommunication between rotate and cube plugins, or just the repainting. Through some debugging I've found that multiple threads are in PrivateCubeScreen::glPaintTransformedOutput at the same time, which updates some variables used to calculate how far the cube has been rotated. Something caused it to stop being thread-safe or is causing too many repaints.

---

### Post by mc4man on 2012-02-13
> **BwackNinja said:**
> I've got a hack that I'm using right now that makes the issue go away, but its just a hack. At best it shows that there is some miscommunication between rotate and cube plugins, or just the repainting. Through some debugging I've found that multiple threads are in PrivateCubeScreen::glPaintTransformedOutput at the same time, which updates some variables used to calculate how far the cube has been rotated. Something caused it to stop being thread-safe or is causing too many repaints.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14)

I'd think 'officially' this is something (fixing), that will fall by the wayside, at least for the foreseeable future
If some community fix happens that would be great, if not then wall is ok 

(i used rotate over wall not for any of the so called 'eye candy', just think its simpler & quicker as is unfold over expo

---

### Post by ventrical on 2012-02-13
> **BwackNinja said:**
> I've got a hack that I'm using right now that makes the issue go away, but its just a hack. At best it shows that there is some miscommunication between rotate and cube plugins, or just the repainting. Through some debugging I've found that multiple threads are in PrivateCubeScreen::glPaintTransformedOutput at the same time, which updates some variables used to calculate how far the cube has been rotated. Something caused it to stop being thread-safe or is causing too many repaints.


Would like to try that hack :)

---

### Post by ventrical on 2012-02-13
Big update in the stack !

---

### Post by dino99 on 2012-02-13
> **ventrical said:**
> Big update in the stack !

not fully installable due to plugin

---

### Post by balloons on 2012-02-13
> **ventrical said:**
> Will not allow for some bug report because compiz-core is third party app.

Yes, this is on my list to get it working properly with the crash handler.. ATM, it's important to tag the bug properly and manually file. I *hope* the next calls for testing will do this automagically for you :-)

---

### Post by ventrical on 2012-02-13
> **guitara said:**
> Yes, this is on my list to get it working properly with the crash handler.. ATM, it's important to tag the bug properly and manually file. I *hope* the next calls for testing will do this automagically for you :-)

Thanks .. great work so far.!!

---

### Post by ventrical on 2012-02-13
> **dino99 said:**
> not fully installable due to plugin

could you elaborate ?

which plugin?

thanks

---

### Post by ventrical on 2012-02-13
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14)

I'd think 'officially' this is something (fixing), that will fall by the wayside, at least for the foreseeable future
If some community fix happens that would be great, if not then wall is ok 

(i used rotate over wall not for any of the so called 'eye candy', just think its simpler & quicker as is unfold over expo

  It only happens when a window is opened on the cube. If you do not open any windows then the cube will rotate with no flicker - so there must be something redrawing after a window is opened- it is trying to resize or reset the window after the macro-binding is let go of.  Mabey this is a clue.

---

### Post by dino99 on 2012-02-13
> **ventrical said:**
> could you elaborate ?

which plugin?

thanks

Now its ok :)

---

### Post by mc4man on 2012-02-13
> **ventrical said:**
> could you elaborate ?

which plugin?

thanks
You'll need a new unity, i386 is done, others building
Have installed all here, ssdd

---

### Post by ventrical on 2012-02-13
> **dino99 said:**
> Now its ok :)

Yeah .. I seen that the core is now realigned to the inlay bridge. ;)

---

### Post by ventrical on 2012-02-13
> **mc4man said:**
> You'll need a new unity, i386 is done, others building
Have installed all here, ssdd

Never thought that possible , but looks like it stacked nicely.

---

### Post by mc4man on 2012-02-13
In addition the 2 previous breaks that continue - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)
[https://bugs.launchpad.net/compiz-plugins-main/+bug/930427](https://bugs.launchpad.net/compiz-plugins-main/+bug/930427) 

Now see 'prev window flashing' in expo when clicking from a WS with an open window to another WS with an open window (staying in expo, just highlighting another WS

Edit: weird thing on the expo flashing - if running a Desktop recorder (recordmydesktop) then there is no flashing

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)

---

### Post by ventrical on 2012-02-13
> **mc4man said:**
> In addition the 2 previous breaks that continue - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)
[https://bugs.launchpad.net/compiz-plugins-main/+bug/930427](https://bugs.launchpad.net/compiz-plugins-main/+bug/930427) 

Now see 'prev window flashing' in expo when clicking from a WS with an open window to another WS with an open window (staying in expo, just highlighting another WS

Edit: weird thing on the expo flashing - if running a Desktop recorder (recordmydesktop) then there is no flashing

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)


 I have a video comming. Just that shotwell and USB transfer has a major bug <I'll keep that for later>.

---

### Post by ventrical on 2012-02-13
> **mc4man said:**
> In addition the 2 previous breaks that continue - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)
[https://bugs.launchpad.net/compiz-plugins-main/+bug/930427](https://bugs.launchpad.net/compiz-plugins-main/+bug/930427) 

Now see 'prev window flashing' in expo when clicking from a WS with an open window to another WS with an open window (staying in expo, just highlighting another WS

Edit: weird thing on the expo flashing - if running a Desktop recorder (recordmydesktop) then there is no flashing

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)

Feel free to attach this.


[http://www.youtube.com/watch?v=bkD6O5Q7-js](http://www.youtube.com/watch?v=bkD6O5Q7-js)

---

### Post by mc4man on 2012-02-13
> **ventrical said:**
> Feel free to attach this.


[http://www.youtube.com/watch?v=bkD6O5Q7-js](http://www.youtube.com/watch?v=bkD6O5Q7-js)

Well if your seeing this (appears so) you should go to the bug, mark as affected/confirm & if you wish post link

---

### Post by ventrical on 2012-02-13
> **mc4man said:**
> Well if your seeing this (appears so) you should go to the bug, mark as affected/confirm & if you wish post link

done..

---

### Post by mc4man on 2012-02-13
> **ventrical said:**
> done..

+1

Figured out how to stop Desktop recorder from 'fixing' expo. It has a default option to outline the capture area on the screen (draw a frame).
Disabling this 'unfixed' expo

---

### Post by kyleabaker on 2012-02-13
> **ventrical said:**
> The menu title border on windows (firefox) and the raster tear that used to be there between the main window and the menu border is practically non existent when using (wobbly windows)! :)

 nice work ..

You're right! I haven't used wobbly windows in years, but it looks much better now!

---

### Post by VinDSL on 2012-02-14
> **kyleabaker said:**
> You're right! I haven't used wobbly windows in years, but it looks much better now!
Dittos!

I was bored, tried it... and left it enabled.  LoL!  :D

---

### Post by ventrical on 2012-02-14
> **VinDSL said:**
> Dittos!

I was bored, tried it... and left it enabled.  LoL!  :D

  I use it as a benchmark. I just give it a wobble now and again to make sure  everything is working :)

---

### Post by TerryNewton on 2012-02-14
Hi testers,

The new compiz 0.9.7 is installed in my VirtualBox test system, but I'm having some issues that I'd like to see if others are getting. This is with a Gnome Classic session without the unity plugin enabled (additional profile) and without the indicator-appmenu packages installed (shouldn't have any effect in gnome-panel).

When opening a text file in gedit, leafpad, etc, the modified indicator (the *) in the window title does not reflect the modification status, unless the window is minimized and restored. Mod status is ok in the panel window list.

The window control colors and title bar text do not change when the windows are
focused and unfocused. In metacity, mutter, etc they dim when unfocused.

When windows are minimized and restored, they first restore to the top left corner then jump to the restored position. Sometimes the previous vertical location is not restored, especially when effects enabled (wobbly, animations and fade).

VirtualBox isn't fully compatible with 3D stuff (and not appropriate for official bug reporting imo, I use it so I can figure out the new stuff and plan my future upgrade strategy) so I'm curious if anyone else is seeing these effects on real hardware. Thanks.

---

### Post by ventrical on 2012-02-14
> **guitara said:**
> Yes, this is on my list to get it working properly with the crash handler.. ATM, it's important to tag the bug properly and manually file. I *hope* the next calls for testing will do this automagically for you :-)

Bingo !! It worked! :)


[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/932200](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/932200)

---

### Post by ventrical on 2012-02-14
> **TerryNewton said:**
> Hi testers,

The new compiz 0.9.7 is installed in my VirtualBox test system, but I'm having some issues that I'd like to see if others are getting. This is with a Gnome Classic session without the unity plugin enabled (additional profile) and without the indicator-appmenu packages installed (shouldn't have any effect in gnome-panel).

When opening a text file in gedit, leafpad, etc, the modified indicator (the *) in the window title does not reflect the modification status, unless the window is minimized and restored. Mod status is ok in the panel window list.

The window control colors and title bar text do not change when the windows are
focused and unfocused. In metacity, mutter, etc they dim when unfocused.

When windows are minimized and restored, they first restore to the top left corner then jump to the restored position. Sometimes the previous vertical location is not restored, especially when effects enabled (wobbly, animations and fade).

VirtualBox isn't fully compatible with 3D stuff (and not appropriate for official bug reporting imo, I use it so I can figure out the new stuff and plan my future upgrade strategy) so I'm curious if anyone else is seeing these effects on real hardware. Thanks.


 I can't replicate this bug on a hard install. Works well.

---

### Post by TerryNewton on 2012-02-14
> **ventrical said:**
> I can't replicate this bug on a hard install. Works well.

Very good, that's what I wanted to hear :-) Thanks for checking.

---

### Post by quequotion on 2012-02-15
First, an oddity:

Between lightdm and loading the desktop, a few scrambled screens flicker (one to three).

At first I thought it was just junk, but I noticed it contained partial images from a web page I was looking at just before the previous shutdown.

Whatever was on the screen or perhaps in the framebuffer just before shutdown is getting splattered on the screen at the next login.

Second, a bug:

I was trying to reproduce a bug from [this post](http://ubuntuforums.org/showpost.php?p=11685626&postcount=17) but ran into another.
When I attempted to minimise a maximised window, then re-maximise it, it came up completely blank.

Re-maximised windows are completely white sheets of nothingness.

---

### Post by ventrical on 2012-02-15
> **quequotion said:**
> First, an oddity:

Between lightdm and loading the desktop, a few scrambled screens flicker (one to three).

At first I thought it was just junk, but I noticed it contained partial images from a web page I was looking at just before the previous shutdown.

Whatever was on the screen or perhaps in the framebuffer just before shutdown is getting splattered on the screen at the next login.

Second, a bug:

I was trying to reproduce a bug from [this post]("http://ubuntuforums.org/showpost.php?p=11685626&postcount=17") but ran into another.
When I attempted to minimise a maximised window, then re-maximise it, it came up completely blank.

Re-maximised windows are completely white sheets of nothingness.


Yes.. I can confirm this on one user but not others.

---

### Post by redcylon on 2012-02-15
Is it just me that "Show Desktop Icon in the Launcher" when invoke puts the icon on top, above the Dash icon.

---

### Post by quequotion on 2012-02-15
A few more:

1. Alt+Tab / Alt+Shift+Tab to switch windows doesn't seem to be working with any of the switchers, not even Unity's native switcher.

This was working before updating to Unity wih HUD...

2. Setting or Unsetting plugins that require a compiz restart tends to fully lock up compiz. Luckily, it's still possible to switch to a terminal (Ctrl+Alt+F1) and restart the session (sudo /etc/init.d/lightdm restart).

Not sure when this started.

---

### Post by ventrical on 2012-02-15
> **mc4man said:**
> In addition the 2 previous breaks that continue - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)
[https://bugs.launchpad.net/compiz-plugins-main/+bug/930427](https://bugs.launchpad.net/compiz-plugins-main/+bug/930427) 

Now see 'prev window flashing' in expo when clicking from a WS with an open window to another WS with an open window (staying in expo, just highlighting another WS

Edit: weird thing on the expo flashing - if running a Desktop recorder (recordmydesktop) then there is no flashing

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)


More pronounced than ever since latest update..

[http://www.youtube.com/watch?v=wAACli_m7Hk](http://www.youtube.com/watch?v=wAACli_m7Hk)

---

### Post by prusswan on 2012-02-15
This beta is more like an alpha, I am resorting to locking compiz-plugins-main for now

---

### Post by ventrical on 2012-02-15
Are we suppossed to remove the ppas now ?

:)

---

### Post by ventrical on 2012-02-19
> **mc4man said:**
> 

Edit: weird thing on the expo flashing - if running a Desktop recorder (recordmydesktop) then there is no flashing

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)

This bug non-existant with:

```

dale@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
dale@ventrical-P4M266A-8237:~$ 

```

---

### Post by balloons on 2012-02-21
> **ventrical said:**
> Are we suppossed to remove the ppas now ?

:)

This version is now in precise, but it should update to the archive version even with the ppa installed. However, yes you can remove the ppa ;-) Thanks for testing everyone!

---

### Post by BwackNinja on 2012-02-27
Here's the hack I currently have in place. It is a patch against current bzr. I can't give you any expectations of it working for you other than it has worked for me and won't cause any extra crashes. It is really a miserable hack though.

to test:

```
sudo apt-get build-dep compiz
bzr branch lp:compiz-core
cd compiz-core
patch -Np0 -i ../cuberotate-hack.patch.txt
mkdir build
cd build
cmake ..
make

# now either do
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
#or
sudo make install


#and restart compiz (I like to double fork it)
bash -c 'compiz --replace ccp &'
```

I recommend just copying libcube.so, which should be ABI compatible because its less invasive and easy to get a clean system again. (just 'sudo mv /usr/lib/compiz/libcube.so{-bak,}' )

---

### Post by ventrical on 2012-02-27
> **BwackNinja said:**
> Here's the hack I currently have in place. It is a patch against current bzr. I can't give you any expectations of it working for you other than it has worked for me and won't cause any extra crashes. It is really a miserable hack though.

to test:

```
sudo apt-get build-dep compiz
bzr lp:compiz-core
cd compiz-core
patch -Np0 -i ../cuberotate-hack.patch.txt
mkdir build
cd build
cmake ..
make

# now either do
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
#or
sudo make install


#and restart compiz (I like to double fork it)
bash -c 'compiz --replace ccp &'
```I recommend just copying libcube.so, which should be ABI compatible because its less invasive and easy to get a clean system again. (just 'sudo mv /usr/lib/compiz/libcube.so{-bak,}' )


 I  entered your code , it downloaded a humungus amount of files and then:

user@user:~$ bzr lp:compiz-core
The program 'bzr' is currently not installed.  You can install it by typing:
sudo apt-get install bzr
dale@dale:~$ sudo apt-get brz
E: Invalid operation brz
dale@dale:~$ sudo apt-get install brz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brz

---

### Post by ventrical on 2012-02-27
> **BwackNinja said:**
> Here's the hack I currently have in place. It is a patch against current bzr. I can't give you any expectations of it working for you other than it has worked for me and won't cause any extra crashes. It is really a miserable hack though.

to test:

```
sudo apt-get build-dep compiz
bzr lp:compiz-core
cd compiz-core
patch -Np0 -i ../cuberotate-hack.patch.txt
mkdir build
cd build
cmake ..
make

# now either do
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
#or
sudo make install


#and restart compiz (I like to double fork it)
bash -c 'compiz --replace ccp &'
```I recommend just copying libcube.so, which should be ABI compatible because its less invasive and easy to get a clean system again. (just 'sudo mv /usr/lib/compiz/libcube.so{-bak,}' )

What do we do with the .txt file ?? Rename it ?

---

### Post by ventrical on 2012-02-27
sorry .. 'bzr'   

brain fart.. :)

---

### Post by BwackNinja on 2012-02-27
You misspelled 'bzr'

Its a patch, so its a text file anyway. I reference it with the *.txt extension anyway. Instructions show that it needs to be in the same directory as the compiz-core folder is when you run bzr.

---

### Post by ventrical on 2012-02-27
sheesh..

```

Unpacking bzr (from .../bzr_2.5.0-1ubuntu1_all.deb) ...
Selecting previously unselected package python-paramiko.
Unpacking python-paramiko (from .../python-paramiko_1.7.7.1-2_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python-configobj (4.7.2+ds-3build1) ...
Setting up python-bzrlib (2.5.0-1ubuntu1) ...
Setting up bzr (2.5.0-1ubuntu1) ...
Setting up python-paramiko (1.7.7.1-2) ...
dale@dale:~$ bzr lp:compiz-core
bzr: ERROR: unknown command "lp:compiz-core"

```

---

### Post by ventrical on 2012-02-27
> **BwackNinja said:**
> You misspelled 'bzr'

Its a patch, so its a text file anyway. I reference it with the *.txt extension anyway. Instructions show that it needs to be in the same directory as the compiz-core folder is when you run bzr.

 If I knew where compiz-core was I  would be off an running eh ! :)

thanks anyways

---

### Post by rburkartjo on 2012-02-28
nice to reable to have some desktop effects. works decently with my radeon driver. i can only get to desktops but can rotate them and all the effects work.

---

### Post by BwackNinja on 2012-02-28
> **ventrical said:**
> sheesh..

```

Unpacking bzr (from .../bzr_2.5.0-1ubuntu1_all.deb) ...
Selecting previously unselected package python-paramiko.
Unpacking python-paramiko (from .../python-paramiko_1.7.7.1-2_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python-configobj (4.7.2+ds-3build1) ...
Setting up python-bzrlib (2.5.0-1ubuntu1) ...
Setting up bzr (2.5.0-1ubuntu1) ...
Setting up python-paramiko (1.7.7.1-2) ...
dale@dale:~$ bzr lp:compiz-core
bzr: ERROR: unknown command "lp:compiz-core"

```

bzr branch lp:compiz-core

oops, I just wrote that command from memory. Everything else should be fine. Edited my post.

---

### Post by mc4man on 2012-02-28
> **BwackNinja said:**
> Here's the hack I currently have in place. It is a patch against current bzr. I can't give you any expectations of it working for you other than it has worked for me and won't cause any extra crashes. It is really a miserable hack though.


Big Thanks - 
Works fine here in a short test on 8400m..
As far as "miserable hack", well anything is better than the big NO that is atm, & that descript isn't all that far off for compiz in general

Anyway real happy be be rid of wall, (at least for the moment), scroll on Desktop has always been better with rotate

Took a bit here to get Ctrl+Alt+ L or R to work correctly, initially was going 2 WS's at a time (offshoot of the [current silly binding change]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/940085")

Hopefully the patch or similar will survive the next few months or so.(12.04 + maybe 1 SRU

Edit: there used to be an 'erroneous' conflict between 'flip left' & reveal, cursor grab & cursor are 2 different things, now it seems 'flip left' is outright killed off when the launcher is 'always shown', flip left works when the launcher is hidden

unfold is a bit of a session killer here, otherwise all good - Edit: - the issue here with unfold is not related to these patches, existed prior to - tested on other install

---

### Post by BwackNinja on 2012-02-29
If nothing else, this is an easy patch to maintain, especially because this code hasn't been touched in a while. I remember seeing that same issue with unfold, but I forget what got rid of it.

I'm glad it works for you. My real hope is for the issue to get looked into by more capable people, this hack was basically as far as I could go.

---

### Post by mc4man on 2012-02-29
> **BwackNinja said:**
> .
I'm glad it works for you. My real hope is for the issue to get looked into by more capable people, this hack was basically as far as I could go.
The one response out of over 100 comments on the 2 bug reports that was 'relevant' was by Sam Spilsbury  back on Oct. 19th - 
> Actually, the fix for this was insanely complicated.

I've done it but it requires a bit more testing because its a big
change to the way we do rendering.

So atm it's really nowhere, maybe down the road, one way or the other?

I do remember having an issue in 11.10 with unfold & got it to go away, don't quite remember how, hadn't used rotate since this began till seeing your post yesterday ( & use more the scroll on desktop & the typical crtl+alt+arrow, like an old friend has returned...

---

### Post by ventrical on 2012-02-29
> **BwackNinja said:**
> bzr branch lp:compiz-core

oops, I just wrote that command from memory. Everything else should be fine. Edited my post.

 I did everything and now ....


dale@dale:~/compiz-core$ patch -Np0 -i ../cuberotate-hack.patch.txt
patch: **** Can't open patch file ../cuberotate-hack.patch.txt : No such file or directory


 what am I doing wrong ..?

---

### Post by mc4man on 2012-02-29
> **ventrical said:**
> I did everything and now ....


dale@dale:~/compiz-core$ patch -Np0 -i ../cuberotate-hack.patch.txt
patch: **** Can't open patch file ../cuberotate-hack.patch.txt : No such file or directory


 what am I doing wrong ..?
The patch (cuberotate-hack.patch.txt) that you downloaded from his post, (you did grab it?),  needs to be in the same directory as compiz-core, that's what the ../ is  saying

see screen, I generally create a dir. to hold indiv. builds, though you could just have compiz-core & the patch in your home folder

(also suggest you do the mv & cp instead of a make install, if coping those commands do so from the compiz-core/build$  prompt

---

### Post by ventrical on 2012-02-29
> **mc4man said:**
> The patch (cuberotate-hack.patch.txt) that you downloaded from his post, (you did grab it?),  needs to be in the same directory as compiz-core, that's what the ../ is  saying

see screen, I generally create a dir. to hold indiv. builds, though you could just have compiz-core & the patch in your home folder

(also suggest you do the mv & cp instead of a make install, if coping those commands do so from the compiz-core/build$  prompt

Yes .. it's there for sure.. (I did grab it ). But no go.
```



dale@dale:~$ cd compiz-core
dale@dale:~/compiz-core$ dir
AUTHORS          COPYING             gtk        metadata   src
ChangeLog      COPYING.GPL             images        NEWS       tests
cmake          COPYING.LGPL             include        plugins    TODO
CMakeLists.txt      COPYING.MIT             INSTALL        po           VERSION
compiz.pc.in      cuberotate-hack.patch.txt  kde        README     xslt
config.h.core.in  Doxyfile             libdecoration  RELEASING
dale@dale:~/compiz-core$ 

```


guess I'll try a reboot.

---

### Post by mc4man on 2012-02-29
> **ventrical said:**
> Yes .. it's there for sure.. (I did grab it ). But no go.
```



dale@dale:~$ cd compiz-core
dale@dale:~/compiz-core$ dir
AUTHORS          COPYING             gtk        metadata   src
ChangeLog      COPYING.GPL             images        NEWS       tests
cmake          COPYING.LGPL             include        plugins    TODO
CMakeLists.txt      COPYING.MIT             INSTALL        po           VERSION
compiz.pc.in      cuberotate-hack.patch.txt  kde        README     xslt
config.h.core.in  Doxyfile             libdecoration  RELEASING
dale@dale:~/compiz-core$ 

```


guess I'll try a reboot.
Did you look at the screenshot I provided - with that command the patch **is not inside** the compiz-core folder, **it's in the same directory** (folder ) as compiz-core

Edit: if you wanted to place the patch directly in the compiz-core folder then just remove a . (dot) from the command, as in - 
patch -Np0 -i ./cuberotate-hack.patch.txt

---

### Post by ventrical on 2012-02-29
Amazing hack indeed, but there are some errors..with the restart code:

```

Setting Update "icon_size"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x36000d8

WARN  2012-02-29 14:09:13 unity.iconloader IconLoader.cpp:536 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-29 14:09:13 unity.iconloader IconLoader.cpp:536 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg at size 24: Error opening file: No such file or directory


```

---

### Post by ventrical on 2012-02-29
> **mc4man said:**
> Did you look at the screenshot I provided - with that command the patch **is not inside** the compiz-core folder, **it's in the same directory** (folder ) as compiz-core

Edit: if you wanted to place the patch directly in the compiz-core folder then just remove a . (dot) from the command, as in - 
patch -Np0 -i ./cuberotate-hack.patch.txt

  Thanks  very much mac4man. That did the trick.  I have been doing msdos directory for almost a quater of a century and so  it is difficult  at times to think *linux* without thinking *msdos*.

---

### Post by ventrical on 2012-02-29
> **BwackNinja said:**
> Here's the hack I currently have in place. It is a patch against current bzr. I can't give you any expectations of it working for you other than it has worked for me and won't cause any extra crashes. It is really a miserable hack though.

to test:

```
sudo apt-get build-dep compiz
bzr branch lp:compiz-core
cd compiz-core
patch -Np0 -i ../cuberotate-hack.patch.txt
mkdir build
cd build
cmake ..
make

# now either do
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
#or
sudo make install


#and restart compiz (I like to double fork it)
bash -c 'compiz --replace ccp &'
```I recommend just copying libcube.so, which should be ABI compatible because its less invasive and easy to get a clean system again. (just 'sudo mv /usr/lib/compiz/libcube.so{-bak,}' )


 Really smart workaround bwackninja!! compiz_flicker_be_gone_! :)

 Thanks a lot and thanks to :
@mac4man for walking me through the directory structure.

  I am just curious as to why they just don't replace that *.so file.


[http://www.youtube.com/watch?v=69fqw7_n_3I](http://www.youtube.com/watch?v=69fqw7_n_3I)

---

### Post by balloons on 2012-02-29
Have you spoken with the compiz-core devs about this? I know they are working on a cube fix as we speak...

> **ventrical said:**
> Really smart workaround bwackninja!! compiz_flicker_be_gone_! :)

 Thanks a lot and thanks to :
@mac4man for walking me through the directory structure.

  I am just curious as to why they just don't replace that *.so file.


[http://www.youtube.com/watch?v=69fqw7_n_3I](http://www.youtube.com/watch?v=69fqw7_n_3I)

---

### Post by ventrical on 2012-03-01
> **guitara said:**
> Have you spoken with the compiz-core devs about this? I know they are working on a cube fix as we speak...


Bravo! .. I knew it :)

---

### Post by quequotion on 2012-03-01
Ran into a huge problem with compiz in the unity team PPAs.

The "shift switcher" plugin is causing compiz to crash immediately if a right-click occurs anywhere.

I've been using this switcher for a long time.
I hope it can be updated and tested against recent changes.

I don't like Unity's iconic switcher.
It takes a moment to think about what an icon represents.

With the thumbnail-based switchers in compiz, I can see the actual window content and make a quick decision if it's the window I need.

---

### Post by ventrical on 2012-03-01
Not here. I use it all the time and it is working great. It even works through  the <Shift+Super+s> binding with no prob. Keyboard shortcuts show up, Unity laucher markers and then  it will shift - smooth.

---

### Post by ventrical on 2012-03-01
> **guitara said:**
> Have you spoken with the compiz-core devs about this? I know they are working on a cube fix as we speak...

The Unity ppa testing completely destroyed bwackNinjas' workaround for the cube .. the flicker is back!

---

### Post by BwackNinja on 2012-03-01
> **ventrical said:**
> The Unity ppa testing completely destroyed bwackNinjas' workaround for the cube .. the flicker is back!

It has a version of compiz newer than the one in the repos, just re-copy the libcube.so file.

---

### Post by ventrical on 2012-03-01
> **BwackNinja said:**
> It has a version of compiz newer than the one in the repos, just re-copy the libcube.so file.

OK.. worked well .. but I had to manually enter the code because if I tired to left click to copy, it would then crash compiz and  subsequently the whole system. Definitely major bugs with new Unity ppa.

---

### Post by quequotion on 2012-03-02
> **ventrical said:**
> Not here. I use it all the time and it is working great. It even works through  the <Shift+Super+s> binding with no prob. Keyboard shortcuts show up, Unity laucher markers and then  it will shift - smooth.

That's not what I meant.

The switcher itself works just fine!

As long as I have it enabled however, right-clicking anywhere crashes compiz.

This is happening all the time, not just when switching applications.

If I disable the plugin, I have no problems.

Perhaps this is caused by Shift Switcher in concert with another plugin?

I tested by individually enabling and disabling each plug in, but I stopped at Shift Switcher and I didn't test things in combination.

---

### Post by quequotion on 2012-03-02
> **quequotion said:**
> Between lightdm and loading the desktop, a few scrambled screens flicker...
At first I thought it was just junk, but I noticed it contained partial images from a web page I was looking at just before the previous shutdown.
Whatever was on the screen or perhaps in the framebuffer just before shutdown is getting splattered on the screen at the next login.

I don't think this is a compiz problem.

I get the same semi-random splatter of the last session's screen with XFWM.

It is also noticeably less scrambled when the previous session was XFWM.
I think this has to do with how XFWM is buffering the graphics.

If the previous session crashed, the screen is *completely* scrambled and looks like colorful static.
Maybe this means the buffer was damaged, destroyed or empty.

---

### Post by ventrical on 2012-03-02
> **quequotion said:**
> That's not what I meant.

The switcher itself works just fine!

As long as I have it enabled however, right-clicking anywhere crashes compiz.

This is happening all the time, not just when switching applications.

If I disable the plugin, I have no problems.

Perhaps this is caused by Shift Switcher in concert with another plugin?

I tested by individually enabling and disabling each plug in, but I stopped at Shift Switcher and I didn't test things in combination.


ahh yes.. thanks for the clairification. I have the exact same bug on one install so that is a confirm ! with the exception that my system totally crashes! I'll try your workaround.

EDIT: Button 3 <right click> ? Terminate Switcher. So looks like there is a binding conflict I presume.

---

### Post by ventrical on 2012-03-02
> **quequotion said:**
> I don't think this is a compiz problem.

I get the same semi-random splatter of the last session's screen with XFWM.

It is also noticeably less scrambled when the previous session was XFWM.
I think this has to do with how XFWM is buffering the graphics.

If the previous session crashed, the screen is *completely* scrambled and looks like colorful static.
Maybe this means the buffer was damaged, destroyed or empty.

 More and more , that opening screen after logon makes me think my computer is stoned ! :)

---

### Post by quequotion on 2012-03-03
> **ventrical said:**
> More and more , that opening screen after logon makes me think my computer is stoned ! :)

Haha, maybe lightdm's been smoking the framebuffer.

---

### Post by ventrical on 2012-03-05
> **BwackNinja said:**
> It has a version of compiz newer than the one in the repos, just re-copy the libcube.so file.


Just a note .. the latest upgrade of compiz un-did your workaround again. :(

---

### Post by bartq1989 on 2012-03-05
sorry for being such a noob, but i tried this beta version and I don't know how to return to older one:/ 
is there any solution step by step?

---

### Post by ventrical on 2012-03-05
> **bartq1989 said:**
> sorry for being such a noob, but i tried this beta version and I don't know how to return to older one:/ 
is there any solution step by step?

  Oh .. do you mean to remove the ppa from the sources list ?

---

### Post by ventrical on 2012-03-05
> **quequotion said:**
> Haha, maybe lightdm's been smoking the framebuffer.


  I think it is something like that for sure. :)

---

### Post by bartq1989 on 2012-03-05
> **ventrical said:**
> Oh .. do you mean to remove the ppa from the sources list ?
I actually removed it but i don't know if it is equivalent with downgradeing:/ i have problem with opening new windows - they appear in random parts of desktop:/

---

### Post by ScislaC on 2012-03-05
> **bartq1989 said:**
> I actually removed it but i don't know if it is equivalent with downgradeing:/ i have problem with opening new windows - they appear in random parts of desktop:/

It's not the same. You actually would want to use ppa-purge to do the disabling of the PPA and downgrading packages.

---

### Post by ventrical on 2012-03-05
> **bartq1989 said:**
> I actually removed it but i don't know if it is equivalent with downgradeing:/ i have problem with opening new windows - they appear in random parts of desktop:/



 Here is what effenberg posted in another thread about this :

[COLOR=Blue]13.[/COLOR]Do  not rely on any inaccurate information  from the user as to whether he   has (or not) added PPAs to his install.  We just get the PPAs and read   them. Then we parse the PPAs (from  ppa-file-name.list to PPA:razz:paname/package  format - which is the format required by the command ppa-purge)     ```


     **if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; **for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi

```

---

### Post by quequotion on 2012-03-08
> **ventrical said:**
> ahh yes.. thanks for the clairification. I have the exact same bug on one install so that is a confirm ! with the exception that my system totally crashes! I'll try your workaround.

EDIT: Button 3 <right click> ? Terminate Switcher. So looks like there is a binding conflict I presume.

I think you're right.

I found "Button 3" as a *default* binding in at least three different extensions: Expo (exit expo), Shift Switcher (terminate), and Scale Add-ons (zoom window).

Theoretically, if the binding were only valid while each plugin is active (in use) then there shouldn't only be any conflict unless they were activated simultaneously (ie: start Expo with Scale on each viewport and Scale Add-ons should display a conflict between Expo and Scale Addons).

It's likely that CCSM asked me to resolve these conflicts, but not understanding how they could affect compiz even when the plugins are inactive, I chose to ignore those conflicts.

Honestly I don't remember well as I have been through three or four full purges and re-installations of compiz since upgrading to 12.04.

It really does seem buggy to me that the bindings should affect anything else when a particular plugin is not active.

I've disabled all of those bindings and now I can use compiz with Shift Switcher and have no problems with right-click.

---

### Post by ventrical on 2012-03-08
During  compiz beta testing I chose to resolve or fix any conflicts. I found that ignoring them only led to trouble. In fact that is another unique aspect about the ccsm in that  it reports macro conflicts!! This would also then be a good model overall for developers to build a Unity macro-binding detector for the desktop because  there are also very many binding conflicts with screenshot, dash and etc...so if an end_user were to install other helpers and MyUnity helpers and HUD and HID helpers .. etc.. then there should be some sort of handshaking between ccsm not just from the compiz side , but from the Unity side.  As highly developed as compiz is I thought that Unity would either match it or surpass it in the field of settings. Don't get me wrong.. I am not saying that Unity is badly written or that compiz is perfect. CCSM still needs a lot of work and tweaking. Unity needs to dig deeper into the workings of CCSM and try to work with it.  Unity should behave more like a child process with CCSM as the parent (figuratively and conceptually speaking). The evidence of this can be referred and documented as to how well CCSM worked with GNOME with releases like Lucid and Maveric, 10.04&10.10.  There was none of the bugs that we are seeing now. It was an enthusiastic desktop to work with. Natty&Unity did swell also with the Edubuntu releases so it is perplexing as to why a lot of  graphical bugs are not getting much attention.

 I admire the work that the compiz & ccsm developers are doing (and have done recently) and I thought the way Unity worked with Precise alpha 1 was just bonus.. but now they have neutered the Unity Launcher bouncey dodger and that just totally  is a royal pain the the ar$e and whoever thought to employ that should be put in the stocks  or sent to the Tower! :)

---

### Post by quequotion on 2012-03-12
> **ventrical said:**
> During  compiz beta testing I chose to resolve or fix any conflicts. I found that ignoring them only led to trouble. In fact that is another unique aspect about the ccsm in that  it reports macro conflicts!! This would also then be a good model overall for developers to build a Unity macro-binding detector for the desktop because  there are also very many binding conflicts with screenshot, dash and etc...so if an end_user were to install other helpers and MyUnity helpers and HUD and HID helpers .. etc.. then there should be some sort of handshaking between ccsm not just from the compiz side , but from the Unity side.  As highly developed as compiz is I thought that Unity would either match it or surpass it in the field of settings. Don't get me wrong.. I am not saying that Unity is badly written or that compiz is perfect. CCSM still needs a lot of work and tweaking. Unity needs to dig deeper into the workings of CCSM and try to work with it.  Unity should behave more like a child process with CCSM as the parent (figuratively and conceptually speaking). The evidence of this can be referred and documented as to how well CCSM worked with GNOME with releases like Lucid and Maveric, 10.04&10.10.  There was none of the bugs that we are seeing now. It was an enthusiastic desktop to work with. Natty&Unity did swell also with the Edubuntu releases so it is perplexing as to why a lot of  graphical bugs are not getting much attention.

 I admire the work that the compiz & ccsm developers are doing (and have done recently) and I thought the way Unity worked with Precise alpha 1 was just bonus.. but now they have neutered the Unity Launcher bouncey dodger and that just totally  is a royal pain the the ar$e and whoever thought to employ that should be put in the stocks  or sent to the Tower! :)

Customizations for unity. <--This is a really good idea.

Especially because all of the other compiz plugins *work just like that* and unity is the only plugin to have it's own external configuration.

It's also the only plugin to have it's own independent diagnostic tool and it's own restart command *that restarts compiz as well*.

Take a look at [this](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html). There was actually a debate over whether or not to support CCSM in Ubuntu due to *perceived* conflicts with Unity.

The proposed solutions include:

-Complete expungance from the Ubuntu repository with future PPA packaging to include "Conflicts with: unity" so users may only install it with **sudo dpkg -i --force-conflicts compizconfig-settings-manager**.

---

### Post by ventrical on 2012-03-12
Currently a huge omnibus update underway with compiz, lightdm and unity-greeter included.

I'll be back for a comment on this.

*edit*

ok .. that update was  relatively usless as far as any fixes for compiz *blink* bug.

---

### Post by alphacrucis2 on 2012-03-12
Just noticed after the latest updates that compiz-plugins-extra can be installed again. My windows are burning :p

---

### Post by ventrical on 2012-03-12
Yep .. fire!  :)

---

### Post by Tovi on 2012-03-15
When (if ever) will compiz 0.9.7 make it to ubuntu 11.10? I want to refrain building from source, cause I'm not such an advanced user, but I also want some of the fixes mentioned in the release notes.

---

### Post by TerminX on 2012-03-17
Does anyone know when the alt+tab problems with compiz 0.9.7.0 will be fixed?  Using the proprietary NVIDIA driver with a 9800 GTX+ and any time I alt+tab I get rather strange results.  Either compiz will freeze up until I switch to a VT and back, or the window thumbnails will be all white, or the window decorations will be mis-textured with what should have been the window thumbnails.  Usually, all three occur.

I have verified that it's not caused by a driver update (tried all driver versions going back to the last ABI change) and downgrading to the last upload of compiz 0.9.6 fixes it.

I've attached my 0.9.6 settings exported from ccsm in case anyone wants to try and reproduce it.

---

### Post by TerminX on 2012-03-23
Ah, my issue was fixed in 0.9.7.2-0ubuntu1.

---

