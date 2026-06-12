---
title: "Unity 5.2 PPA Testing"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-01-31
It's that time again everyone. Please see my post for info on how to get the latest version of unity, what's new, and how to test. Feel free to post here if you run into trouble. I'm checking out the multi-monitor support myself. Thanks for testing!

[Unity 5.2: What's new, and a call for testing]("http://www.theorangenotebook.com/2012/01/unity-52-whats-new-and-call-for-testing.html")
[B]
EDIT:It's important enough to note that anyone here who is testing HUD will have to purge the ppa (and thus lose HUD for now) in order to test this. I give instructions in my post in case you need them.[/B]

---

### Post by zika on 2012-01-31
> **guitara said:**
> It's that time again everyone. Please see my post for info on how to get the latest version of unity, what's new, and how to test. Feel free to post here if you run into trouble. I'm checking out the multi-monitor support myself. Thanks for testing!

[Unity 5.2: What's new, and a call for testing]("http://www.theorangenotebook.com/2012/01/unity-52-whats-new-and-call-for-testing.html")
[B]
EDIT:It's important enough to note that anyone here who is testing HUD will have to purge the ppa (and thus lose HUD for now) in order to test this. I give instructions in my post in case you need them.[/B]Before I've noticed Your warning I did all upgrades (with both HUD and Unity PPA active) and all work... Should I fear of doom?

---

### Post by balloons on 2012-01-31
> **zika said:**
> Before I've noticed Your warning I did all upgrades (with both HUD and Unity PPA active) and all work... Should I fear of doom?

zika, I tried this first myself but found I didn't have the latest version of unity afterwards.. some bits of it were runing the old versions. Like you unity did come up and I could use it, but the new features weren't working properly. It would be best to rollback one or the other for now.

---

### Post by zika on 2012-01-31
> **guitara said:**
> zika, I tried this first myself but found I didn't have the latest version of unity afterwards.. some bits of it were runing the old versions. Like you unity did come up and I could use it, but the new features weren't working properly. It would be best to rollback one or the other for now.I did *ppa--purge ppa:unity-team/hud* already. Thank You... ;)
(It did not make any progress, but...)

---

### Post by kaldor on 2012-01-31
Got a bit of a problem with the launcher colour. If I change the colour of the launcher in CCSM it seems that the icons change as well. See attachment.

---

### Post by go7Ul1ai on 2012-01-31
So is the HUD going to be incorporated into Unity in a later release or has something changed?

---

### Post by mc4man on 2012-01-31
> **kaldor said:**
> Got a bit of a problem with the launcher colour. If I change the colour of the launcher in CCSM it seems that the icons change as well. See attachment.

Was also previously using custom Dash color. same deal
Also a transparent panel is semi broken, a black global/app menu shows when not displaying a window's app menu

The reveal feels clunky, interesting that  these setting's make the new one in "user interface" worthless

Took 14 months but the restricting of the launcher icon's  l. click spread to only open windows on the current workspace has happened, I'm sure some will love it, certainly not here.

---

### Post by balloons on 2012-01-31
> **lee.jarratt said:**
> So is the HUD going to be incorporated into Unity in a later release or has something changed?

Precise is an LTS, and HUD has to be able to pass the acceptability criteria in order to make it into precise. We hope this will happen, and with enough testing and good development it will :-) But it's not there yet.

---

### Post by xyzzyman on 2012-01-31
With my synaptic touchpad, 'pushing' the edge is taking a few tries (3-4) to get the launcher to appear. Even when I try to not think about it and let it occur naturally, it seems to take even more tries (5-6). Anyone else experiencing this?

---

### Post by PaulW2U on 2012-01-31
> **xyzzyman said:**
> With my synaptic touchpad, 'pushing' the edge is taking a few tries (3-4) to get the launcher to appear. Even when I try to not think about it and let it occur naturally, it seems to take even more tries (5-6). Anyone else experiencing this?

It's not much easier with a mouse. ](*,)

---

### Post by effenberg0x0 on 2012-01-31
It clearly runs smoother with NVidia 290.10 than previous releases here. 

About Auto-hide: It doesn't feel smooth using a Logitech trackball mouse. I have to roll the trackball left to touch the screen limit and then roll it up or down for a while to make it show.

I get an error when running dist-upgrade regarding **libfreerdp1 10.0-0git1** not being found. It's the old "Trying to overwrite" which is properly described [here]("https://wiki.ubuntu.com/UsingDevelopmentReleases/FixingProblems#Uninstallable_packages"). After restarting the session, if I attempt to run Unity Test I also get a dialog about this package (see screenshot).
[ATTACH]211756[/ATTACH]

Of course a manual install fails too:
```

[10:01 PM][ahsl:AL-DESK:~]
$ sudo apt-get install libfreerdp1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfreerdp
The following NEW packages will be installed:
  libfreerdp1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
69 not fully installed or removed.
Need to get 0 B/253 kB of archives.
After this operation, 745 kB of additional disk space will be used.
(Reading database ... 227105 files and directories currently installed.)
Unpacking libfreerdp1 (from .../libfreerdp1_1.0.0-0git1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libfreerdp1_1.0.0-0git1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/freerdp/keymaps/xfree86', which is also in package libfreerdp0 0.8.2-2build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libfreerdp1_1.0.0-0git1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```And then  a dpkg -i --force-all sort of fixes it :)
```

sudo dpkg -i --force-all /var/cache/apt/archives/libfreerdp1_1.0.0-0git1_amd64.deb
(Reading database ... 227105 files and directories currently installed.)
Unpacking libfreerdp1 (from .../libfreerdp1_1.0.0-0git1_amd64.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/xfree86', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/empty', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/ibm', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/xfree98', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/sun', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/aliases', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/ataritt', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/evdev', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/digital_vndr/lk', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/digital_vndr/pc', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/hp', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/sony', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/fujitsu', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/sgi_vndr/indy', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/sgi_vndr/indigo', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/sgi_vndr/iris', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/amiga', which is also in package libfreerdp0 0.8.2-2build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/freerdp/keymaps/macintosh', which is also in package libfreerdp0 0.8.2-2build1
Setting up libfreerdp1 (1.0.0-0git1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```Also, just a note on a secondary visual glitch: Setting the launcher to 0% opacity and a dark wallpaper, I can see a white triangle in each of the corners of every launcher icon. Purging the PPA and going back to repos version, this doesn't show and icons look normal (see the screenshot):
[ATTACH]211755[/ATTACH]

Regards,
Effenberg

---

### Post by mc4man on 2012-01-31
> **xyzzyman said:**
> With my synaptic touchpad, 'pushing' the edge is taking a few tries (3-4) to get the launcher to appear. Even when I try to not think about it and let it occur naturally, it seems to take even more tries (5-6). Anyone else experiencing this?
See the same unless I reduce the reveal pressure considerably - the available scale for that is a bit absurd - the higher numbers may take a truck instead of a mouse

Anything from 15 - default seems to take at least 2 tries, below 15 usually just 1
10 is alright here

---

### Post by mc4man on 2012-01-31
The 2 minor bugs seen here so far
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586)

---

### Post by xyzzyman on 2012-01-31
So we've already established this is hard to use with touchpads, mice and trackballs... Anyone having issues with head tracking? :P I couldn't identify how it was making me feel at first, and it finally dawned on me, even with the touchpad it feels like trying to use a mouse with a ton of hair and dirty and grime up all on the ball and the rollers. It's been a long time since most of us have had to deal with that. We take optical mice for granted. But trying to get the launcher to reveal gave me that same feeling! Ah. Memories.

@effenberg: I've had those white corners for a week now at least on a mid-range opacity, not just today.  Thought it may have just been an odd design choice.

---

### Post by mc4man on 2012-01-31
Actually think here the reveal issue was me not quite understanding it - thought it was pressure (force) of the **initial bump** up against. That doesn't matter, it's the secondary push. In that case the the default of 20 is ok, though some of the higher values are of no use

---

### Post by effenberg0x0 on 2012-01-31
> **xyzzyman said:**
> So we've already established this is hard to use with touchpads, mice and trackballs... Anyone having issues with head tracking? :P I couldn't identify how it was making me feel at first, and it finally dawned on me, even with the touchpad it feels like trying to use a mouse with a ton of hair and dirty and grime up all on the ball and the rollers. It's been a long time since most of us have had to deal with that. We take optical mice for granted. But trying to get the launcher to reveal gave me that same feeling! Ah. Memories.

I can try a touchscreen monitor tomorrow at work, but I have a feeling I'll probably break either the monitor or my finger.

@effenberg: I've had those white corners for a week now at least on a mid-range opacity, not just today.  Thought it may have just been an odd design choice.

Thanks for confirming Xyzzyman. I have captured and zoomed it on gimp. What we're seeing are the parts of the icons that shouldn't be rendered (so that icons would seem to have round corners). As they are being wrongly rendered now, icons look squared and with these white corners. It can be made more visible by applying a strong dark color like a dark green or brown in CCSM/UbuntuPlugin/Experimental/BackgroungColor.

**EDIT: **A new finding: I can only see this effect if launcher icons are == 32. If i size them to 33, I can see round borders and no white thing, as expected.

---

### Post by xyzzyman on 2012-01-31
> **effenberg0x0 said:**
> Thanks for confirming Xyzzyman. I have captured and zoomed it on gimp. What we're seeing are the parts of the icons that shouldn't be rendered (so that icons would seem to have round corners). As they are being wrongly rendered now, icons look squared and with these white corners. It can be made more visible by applying a strong dark color like a dark green or brown in CCSM/UbuntuPlugin/Experimental/BackgroungColor.

**EDIT: **A new finding: I can only see this effect if launcher icons are == 32. If i size them to 33, I can see round borders and no white thing, as expected.

Yup. Resizing to 32 is the first thing I do on a fresh install. I've got work going on in 11.10 so if you submit a bug report before I do post the link and I'll add myself.

@mc4man I'll have to play with the settings next time I boot into PP. Are they in CCSM Unity plugin?

---

### Post by mc4man on 2012-01-31
> **xyzzyman said:**
> .

@mc4man I'll have to play with the settings next time I boot into PP. Are they in CCSM Unity plugin?
Yeah, under the experimental tab or in gconf in the unityshell options

---

### Post by MacUntu on 2012-01-31
Did the multi-monitor tests run for you? It went straight to the result page after finishing the window manager tests.

---

### Post by mc4man on 2012-02-01
This would only be a bug if there is no way to change & there is any expectation users could change. 
Regarding light-themes - 
Until 5.2 all of the unity panel dropdown menus, (appmenu, indicators), would use the defined 'selected_bg_color' &  'selected_fg_color', whether set globally in /usr/share/themes/Ambiance/... or locally in gsettings/dconf-editor (org.gnome.desktop.interface gtk-color-scheme

As of the current 5.2 they will use the defined 'selected_bg_color' but not the 'selected_fg_color', that stays the white or slightly off-white color
Probably will file a bug even though it's a non-standard use case, if it doesn't change would certainly limit modding the light-themes as to chosen 'selected_bg_color'

for the heck of it 
[https://bugs.launchpad.net/unity/+bug/924893](https://bugs.launchpad.net/unity/+bug/924893)

---

### Post by philinux on 2012-02-01
The test crashed at the end with a invalid email. Can I recover it and send the report.

---

### Post by candtalan on 2012-02-01
I have spent the best part of today carefully going through the recent unity testing app. On completion I see a report is available and is readable, but 'there are some invalid...'
I sign into launchpad
and them the report is not sent, all my results are lost.

Sorry. I do not have (another day!) to repeat this. I am not impressed.
Just as well I am not getting paid. 
:-|

---

### Post by ronacc on 2012-02-01
This is exactly what TESTING is for . Finding and reporting bugs is why we are here .

---

### Post by t1497f35 on 2012-02-01
> **ronacc said:**
> This is exactly what TESTING is for . Finding and reporting bugs is why we are here .
I think he means he couldn't send a testing report, imo one should reasonably expect that at least the sending report/bug system should work since these aren't sophisticated programs on the user-side and are central to actually reporting a problem.

---

### Post by zika on 2012-02-01
Shouldn't this be discussed in [http://ubuntuforums.org/showthread.php?t=1918193](http://ubuntuforums.org/showthread.php?t=1918193) or in [http://ubuntuforums.org/showthread.php?t=1905631](http://ubuntuforums.org/showthread.php?t=1905631) ...?

---

### Post by candtalan on 2012-02-01
> **t1497f35 said:**
> I think he means he couldn't send a testing report, imo one should reasonably expect that at least the sending report/bug system should work since these aren't sophisticated programs on the user-side and are central to actually reporting a problem.

Yes! or if an invalid report is a possibility then a robust method of not wasting my whole day. I love Ubuntu and want to continue helping but even my resources are limited.

---

### Post by philinux on 2012-02-01
Merged. Agreed. Not much point testing if the report is lost at the end.

---

### Post by balloons on 2012-02-01
Can you expand on what is happening when you try and submit? What are the exact errors you are receiving? Your report should still be around on your hard drive -- look for a submission.xml file in the ~/.checkbox folder. In addition there is a log in there that may tell what's going on. When you restart unity testing does it prompt you to recover your testing?

---

### Post by philinux on 2012-02-01
> **guitara said:**
> Can you expand on what is happening when you try and submit? What are the exact errors you are receiving? IYour report should still be around on your hard drive -- look for a submission.xml file in the ~/.checkbox folder. In addition there is a log in there that may tell what's going on. When you restart unity testing does it prompt you to recover your testing?

I'm not at my pc. But it just said invalid email. It had not asked me for one either. Then the test aborted. I'll try your suggestions when I'm home.

---

### Post by fluteflute on 2012-02-01
> **MacUntu said:**
> Did the multi-monitor tests run for you? It went straight to the result page after finishing the window manager tests.Snap.

[https://bugs.launchpad.net/unity/+bug/925030](https://bugs.launchpad.net/unity/+bug/925030)

---

### Post by fluteflute on 2012-02-01
I have to say that I am not currently too keen on the new launcher reveal, or the implications of this on multimonitors. 

However, it's early days, and I can see myself getting used to it.

---

### Post by mc4man on 2012-02-01
The unity checkbox package is no longer in the staging repo, if it ever was there for Precise don't know. *saw previously an Oneiric version

If it's anything like the current checkbox-gtk then it's pretty much not able to send a report or even view from checkbox ("unable to open web browser"

Basic error would be something like
> $  checkbox-gtk
Expecting an element hal, got nothing
Invalid sequence in interleave
Invalid sequence in interleave
Element hardware failed to validate content
/usr/bin/checkbox-gtk: line 18:  4875 I/O possible            python $CHECKBOX_SHARE/run "$@" $CHECKBOX_SHARE/configs/$(basename $0).ini

Making an assumption? that if checkbox (System Testing) fails to send ect.,  then the unity one will also

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/925157](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/925157)

---

### Post by philinux on 2012-02-02
> **guitara said:**
> Can you expand on what is happening when you try and submit? What are the exact errors you are receiving? Your report should still be around on your hard drive -- look for a submission.xml file in the ~/.checkbox folder. In addition there is a log in there that may tell what's going on. When you restart unity testing does it prompt you to recover your testing?

Ok all the files are there in the checkbox folder. It performed a recover but refused to send again saying no email provided.

---

### Post by mc4man on 2012-02-02
> **philinux said:**
> Ok all the files are there in the checkbox folder. It performed a recover but refused to send again saying no email provided.

In the bug report I linked previous post - comment 10 - while I' not too sure he paid any attention to the gist of the report or ANY of the attachments there is mention that on the "View Report" option of a field to enter email, whatever

In the context of that report it's a moot point, the 'View Report' option fails also... (As I believe I clearly mentioned & provided a screen of

---

### Post by grahammechanical on 2012-02-02
I have twice run the Unity test (5.0 & now 5.2) and twice I was caught out with the no email message. There is an invisible panel at the bottom to put our Launchpad log-in email address.

I also do not like the fact that the person writing the instructions doesn't understand that "Launcher Hide" and "Launcher Reveal" are familiar terms to me, at least. The terms "slide in" and "slide out" were being used with the opposite meanings as far as I was concerned. Because of this misunderstanding I was marking some of the test as impossible to work.

Such is life in Ubuntu +1

Regards.

---

### Post by philinux on 2012-02-02
> **grahammechanical said:**
> I have twice run the Unity test (5.0 & now 5.2) and twice I was caught out with the no email message. There is an invisible panel at the bottom to put our Launchpad log-in email address.

I also do not like the fact that the person writing the instructions doesn't understand that "Launcher Hide" and "Launcher Reveal" are familiar terms to me, at least. The terms "slide in" and "slide out" were being used with the opposite meanings as far as I was concerned. Because of this misunderstanding I was marking some of the test as impossible to work.

Such is life in Ubuntu +1

Regards.

Invisible Panel. Great. ](*,)

---

### Post by MacUntu on 2012-02-02
What invisible panel? It's a text field at the bottom of the last screen.

---

### Post by philinux on 2012-02-02
> **MacUntu said:**
> What invisible panel? It's a text field at the bottom of the last screen.

IIRC it doesnt say insert email here. I did not even see the field. I'll have another go when I next reboot.

---

### Post by MacUntu on 2012-02-02
[IMG]http://img.xrmb2.net/images/591739.png[/IMG]

---

### Post by philinux on 2012-02-02
It's easy to see there. But not obvious at the time. I think it's caught a few out too. 

I was expecting it to ask for my email on the next screen etc. Should have gone to Specsavers.

---

### Post by MacUntu on 2012-02-02
There's certainly room for improvement - throughout the whole application. ;)

---

### Post by philinux on 2012-02-02
> **MacUntu said:**
> There's certainly room for improvement - throughout the whole application. ;)

Sorted now. I reckon it needs splitting into two tests. It's too long at one sitting.

---

### Post by balloons on 2012-02-02
Good to hear you've sorted things out.. BTW, you can file bugs against checkbox too. I would recommend filing one to make that entry form a BIT more obvious! :-) You can file it against unity, tag 5.2rc-1 as usual.

---

### Post by Yokohama50 on 2012-02-08
Looks like HUD is out of stock at the moment:) I could get it working with downgrade but that word isnt in my dictionary:)

---

### Post by cariboo on 2012-02-08
> **Yokohama50 said:**
> Looks like HUD is out of stock at the moment:) I could get it working with downgrade but that word isnt in my dictionary:)

See [this]("http://ubuntuforums.org/showthread.php?t=1921310") thread

---

### Post by mc4man on 2012-02-10
Is there any point/need to report against the current unity/staging builds & if so what is the tag?
(see an interesting effect on non-favorite/device icons in the launcher. While not bad on some backgrounds such as screen, on others not so

---

