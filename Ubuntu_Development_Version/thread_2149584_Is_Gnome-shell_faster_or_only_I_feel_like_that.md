---
title: "Is Gnome-shell faster or only I feel like that?"
date: 2013-05-29
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-05-29
I have installed Gnome 3.8 to Ubuntu, and I find Gnome-shell responds faster than Unity. Is it only I feel that way, or do others too?:)

---

### Post by VinDSL on 2013-05-29
> **Chanath said:**
> I have installed Gnome 3.8 to Ubuntu, and I find Gnome-shell responds faster than Unity. Is it only I feel that way, or do others too?:)
On this GS 3.9.1 install, I don't see an ounce_of_difference between Gnome-Shell and Unity -- which is a good thing.

IMO, GS used to be a kludge.  The only reason I kept it around was out of idle curiosity, and for a fallback DE, when Unity would break.

These days, I consider Gnome-Shell to be equal to Unity in every respect, including performance.  ;)

That said, I judge that ppl are really missing out, if they haven't tried the lastest Gnome-Shell.  They've definitely made many, many improvements to it, over the past few months.  And, there are more changes coming almost daily.  Gnome is on a roll, right now.

If someone hasn't used Gnome-Shell since (say) 3.2, I think they will be shocked at the difference(s).

---

### Post by sgage on 2013-05-29
> **VinDSL said:**
> On this GS 3.9.1 install, I don't see an ounce_of_difference between Gnome-Shell and Unity -- which is a good thing.

IMO, GS used to be a kludge.  The only reason I kept it around was out of idle curiosity, and for a fallback DE, when Unity would break.

These days, I consider Gnome-Shell to be equal to Unity in every respect, including performance.  ;)

That said, I judge that ppl are really missing out, if they haven't tried the lastest Gnome-Shell.  They've definitely made many, many improvements to it, over the past few months.  And, there are more changes coming almost daily.  Gnome is on a roll, right now.

If someone hasn't used Gnome-Shell since (say) 3.2, I think they will be shocked at the difference(s).

Is 3.9.1 the current version in ricotz/testing? I can't even get any version of GS to work in saucy these days. I might just go for broke and try 3.9.1.

---

### Post by Harry33 on 2013-05-29
> **sgage said:**
> Is 3.9.1 the current version in ricotz/testing? I can't even get any version of GS to work in saucy these days. I might just go for broke and try 3.9.1.

Gnome-shell has been very troublesome in saucy for a while.
Today with all the updates from saucy-proposed it will not run nor even start.
You need to downgrade clutter-1.0 first, then it is OK.
The vte3 issue has been solved for now.
However, enabling the Gnome3 PPA (raring branch) into the saucy, Gs will work better (and with the newest clutter-1.0).
The Gs will work well even after you enable both Gnome3 PPA (raring branch) and Gnome3 Staging PPA (raring branch).

Anyways, keep in mind that using Ricotz Gnome Testing PPA is recommended only by enabling the Gnome3 PPA and Gnome3 Staging PPA too.

---

### Post by Chanath on 2013-05-29
Themes work better on Gnome 3, than on Unity. No idea why, though. I still find Gnome 3.8 responding faster than Unity. There is one minus in Gnome-shell, i.e, there is no way to have a icon to change keyboard layouts, which in Unity just a click away. Do you know how to do that in Gnome 3.8?

---

### Post by zika on 2013-05-29
> **Harry33 said:**
> Gnome-shell has been very troublesome in saucy for a while.
Today with all the updates from saucy-proposed it will not run nor even start.
You need to downgrade clutter-1.0 first, then it is OK.
The vte3 issue has been solved for now.
However, enabling the Gnome3 PPA (raring branch) into the saucy, Gs will work better (and with the newest clutter-1.0).
The Gs will work well even after you enable both Gnome3 PPA (raring branch) and Gnome3 Staging PPA (raring branch).

**Anyways, keep in mind that using Ricotz Gnome Testing PPA is recommended only by enabling the Gnome3 PPA and Gnome3 Staging PPA too.**Even though there is no Saucy branch of these two PPAs...? Usage of Raring branch is recommended? If the answer is &#8222;yes&#8220; I'm on the right track even though I thought that I'm way off the right path... ;)

---

### Post by sgage on 2013-05-29
> **Harry33 said:**
> Gnome-shell has been very troublesome in saucy for a while.
Today with all the updates from saucy-proposed it will not run nor even start.
You need to downgrade clutter-1.0 first, then it is OK.
The vte3 issue has been solved for now.
However, enabling the Gnome3 PPA (raring branch) into the saucy, Gs will work better (and with the newest clutter-1.0).
The Gs will work well even after you enable both Gnome3 PPA (raring branch) and Gnome3 Staging PPA (raring branch).

Anyways, keep in mind that using Ricotz Gnome Testing PPA is recommended only by enabling the Gnome3 PPA and Gnome3 Staging PPA too.

Of course, the old 'clutter' problem - I had thought it was fixed by now, so I didn't think to downgrade clutter. But in any case, I am now successfully running GS 3.8.2 from the gnome3 PPA - I thought I was before, but I had forgotten to change 'saucy' to 'raring' in the sources :-)  

However GDM 3.8.0 is not working. I get the gray screen and the top panel, but no greeter at all - just a blank gray screen.

---

### Post by VinDSL on 2013-05-29
> **sgage said:**
> Is 3.9.1 the current version in ricotz/testing?

> **Harry33 said:**
> [...] keep in mind that using Ricotz Gnome Testing PPA is recommended only by enabling the Gnome3 PPA and Gnome3 Staging PPA too.
Correct.

[LIST=1]
[*]Ricotz Gnome Testing PPA
[*]Gnome3 Staging PPA
[*]Gnome3 PPA
[/LIST]

Be V careful using "Proposed", as always.  It's fun to poke bears with sticks, but...  ;)

---

### Post by Chanath on 2013-05-29
> **VinDSL said:**
> Correct.

[LIST=1]
[*]Ricotz Gnome Testing PPA 
[*]Gnome3 Staging PPA 
[*]Gnome3 PPA 
[/LIST]

Be V careful using "Proposed", as always.  It's fun to poke bears with sticks, but...  ;)

I had used #2 & #3, but not Ricotz Gnome Testing PPA. I'm using GS 3.8.2. I'm not sure, if there are enough extensions yet for Gnome 3.9.1. 

Whether it is Unity or GS, all I want is it to help me in finding applications/files faster, and to stay away from my screen. Both of them do that quite nicely. GS has an extension for minimizing, maximizing windows, which Unity doesn't have. Unity has keyboard changer, while GS doesn't. 

I'm going to use GS & Unity half the time for a week, to find out which one would stay with me. I still look forward for Unity Next, though.:)

---

### Post by VinDSL on 2013-05-29
> **Harry33 said:**
> You need to downgrade clutter-1.0 first, then it is OK.
Interesting! 

```
vindsl@Zuul:~$ apt-cache policy clutter-1.

gir1.2-clutter-1.0:
  Installed: 1.14.4-1
  Candidate: 1.14.4-1
  Version table:
 *** 1.14.4-1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.14.4-1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.14.4-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages

libclutter-1.0-0:
  Installed: 1.14.4-1
  Candidate: 1.14.4-1
  Version table:
 *** 1.14.4-1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.14.4-1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.14.4-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages

libclutter-1.0-common:
  Installed: 1.14.4-1
  Candidate: 1.14.4-1
  Version table:
 *** 1.14.4-1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.14.4-1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.14.4-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages

```

Are these the versions you're running, too?

Everything is working fine, here...

---

### Post by sgage on 2013-05-29
I just wanted to add an update...

I applied the gnome3-staging PPA, and it bumped GDM from 3.8.0 to 3.8.1, and it now works well. I now have a fully functional GDM/GS system in Saucy for the first time in a while...

---

### Post by VinDSL on 2013-05-29
> **sgage said:**
> I applied the gnome3-staging PPA, and it bumped GDM from 3.8.0 to 3.8.1, and it now works well. I now have a fully functional GDM/GS system in Saucy for the first time in a while...
Sweet!  :)

If you decide to try 3.9.1 -- as Harry said -- there have been some teething problems in Saucy.

Heads up...

One of the manifestations has been, GDM quits working (has happened to me twice in the past week).

If GDM quits working, because of this_or_that upgrade, switching to LightDM will allow you to login, and fix the problem(s).

```
sudo dpkg-reconfigure gdm
```

Currently, GDM/GS is working fine for me, but that doesn't guarantee it will work tomorrow, you know? ;)

---

### Post by markbl on 2013-05-29
> **VinDSL said:**
> 
That said, I judge that ppl are really missing out, if they haven't tried the lastest Gnome-Shell.  They've definitely made many, many improvements to it, over the past few months.
I respectfully disagree. I use GS 3.8 all day every day on Ubuntu 13.04 + GNOME 3 ppa and GS 3.4 on another stock Ubuntu 12.04 box and they are fundamentally the same. GS has always been good! I think the changes to the messaging menu in GS 3.8 are a step backwards because now you don't see "everything" when you press the super key. The new message tray is too big and clumsy to use. I prefer the tray in GS 3.4 - although the larger and proportionally scaled windows in the GS 3.8 are a definite improvement. I don't really see much point in the new GDM slide shade.

Regarding performance, I have always found that GS performs well on all the boxes I have installed it. Unity used to have some performance issues but recent versions are fine, same as GS. I like Unity but have no need for all that scope stuff which Unity emphasises. I just want the simple launcher as in GS and I love the GS overview for window selection/management. There's beauty in the simple elegant GS design (although the new message tray breaks that elegance somewhat IMHO).

---

### Post by sgage on 2013-05-29
> **VinDSL said:**
> Sweet!  :)

If you decide to try 3.9.1 -- as Harry said -- there have been some teething problems in Saucy.

Heads up...

One of the manifestations has been, GDM quits working (has happened to me twice in the past week).

If GDM quits working, because of this_or_that upgrade, switching to LightDM will allow you to login, and fix the problem(s).

```
sudo dpkg-reconfigure gdm
```

Currently, GDM/GS is working fine for me, but that doesn't guarantee it will work tomorrow, you know? ;)

I've gotten very familiar with that command over the past few weeks ;-)

You don't even have to switch to lightdm... when gdm fails, just ctl-alt-Fx to a VT and you can run the command there. Maybe first do

 ```
service gdm stop
``` 

and then 

```
service gdm start
```

afterwards. Or just reboot. No guarantees in this business, indeed!

---

### Post by Chanath on 2013-05-29
> VinDSL Are these the versions you're running, too?

Everything is working fine, here...

gir1.2-clutter-1.0 is 1.14.4-1

Are you using GS 3.9.1?
If so, do you have enough extensions?

---

### Post by VinDSL on 2013-05-29
> **markbl said:**
> I respectfully disagree.[...]
That's fine...

I should have used another word.  "Improvements" is a highly subjective term, isn't it?

The jury is out, on whether or not the "changes" are actually "improvements".  ;)

---

### Post by VinDSL on 2013-05-29
> **sgage said:**
> You don't even have to switch to lightdm... when gdm fails, just ctl-alt-Fx to a VT and you can run the command there.[...]
True!

My problem was... GDM was hard-locking my machine at some guttural/hardware  level -- keyboard went dormant, and so forth, and so on.

Only way I could boot was to go into recovery mode, switch DMs, and reboot.  ;)

---

### Post by dino99 on 2013-05-29
> **Chanath said:**
> gir1.2-clutter-1.0 is 1.14.4-1

Are you using GS 3.9.1?
If so, do you have enough extensions?

GS 3.8/3.9 are quite the same, BUT the extensions are not available for 3.9  :mad: (except 2 that i does not care)
Quickly said, 3.9 is missing the topicon & appindicator extensions right now. Thats too bad.

---

### Post by Chanath on 2013-05-29
> **dino99 said:**
> GS 3.8/3.9 are quite the same, BUT the extensions are not available for 3.9  :mad: (except 2 that i does not care)
Quickly said, 3.9 is missing the topicon & appindicator extensions right now. Thats too bad.

Installed GS 3.9, but came back to GS 3.8.2, as I need some extensions. Next change would be, when extensions are there, most probably GS 3.10...

---

### Post by Harry33 on 2013-05-30
> **VinDSL said:**
> Interesting! 

...

Are these the versions you're running, too?

Everything is working fine, here...

Yes they are, and they do work fine.
The new clutter-1.0_1.14 branch clutter can only be used with gnome 3.8 branch, not with the 3.6 branch, which we still have in saucy.
In other words, if you use Gnome3 PPA (and even Gnome3 Staging), then clutter-1.0_1.14.4-1 is just fine.

---

### Post by Harry33 on 2013-05-30
> **zika said:**
> Even though there is no Saucy branch of these two PPAs...? Usage of Raring branch is recommended? If the answer is „yes“ I'm on the right track even though I thought that I'm way off the right path... ;)

Yes, when you use saucy with gdm, you need to enable Gnome3 PPA (raring branch) and you can very well enable Gnome3 Staging PPA (raring branch) as well. These do work well ATM.
Then, if you need to do more testing and if you need to be in trouble more frequently :guitar:, enable the saucy-proposed too.
This is where you get the dependency issues every now and then, with the PPA's I mentioned.

I do all this. But I do not use the Gnome Testing PPA.

---

### Post by zika on 2013-05-30
> **Harry33 said:**
> Yes, when you use saucy with gdm, you need to enable Gnome3 PPA (raring branch) and you can very well enable Gnome3 Staging PPA (raring branch) as well. These do work well ATM.
Then, if you need to do more testing and if you need to be in trouble more frequently :guitar:, enable the saucy-proposed too.
This is where you get the dependency issues every now and then, with the PPA's I mentioned.

I do all this. But I do not use the Gnome Testing PPA.
Not using saucy-proposed, I've trained myself to wait at least for that repository... I see it as a sandbox as it is supposed to be treated... ;)
When are we to expect a proper Saucy branch for these two PPAs...?

---

### Post by dino99 on 2013-05-30
> **zika said:**
> Not using saucy-proposed, I've trained myself to wait at least for that repository... I see it as a sandbox as it is supposed to be treated... ;)
When are we to expect a proper Saucy branch for these two PPAs...?

Hopes to see them with the coming gnome 3.10 (aka 3.9.x as found inside testing)

---

### Post by VinDSL on 2013-05-30
> **Chanath said:**
> Installed GS 3.9, but came back to GS 3.8.2, as I need some extensions. Next change would be, when extensions are there, most probably GS 3.10...
I hacked the json file, on the ones I *need*.  They seem to be working fine...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-may-2013-1.png")

*Experimental "Light Dubstep" Station -- Icecast Radio.  Mock Graphic. Full listing available soon. [/INDENT]

---

### Post by VinDSL on 2013-05-30
Sorry in advance, zika.  LoL!  :D

---

### Post by Chanath on 2013-05-30
> **VinDSL said:**
> I hacked the json file, on the ones I *need*.  They seem to be working fine...

How do you hack the json file? How to do that?

---

### Post by zika on 2013-05-30
The only extension I'd like to have (HideTopBar) does not work with just changing .json... ;(

---

### Post by sgage on 2013-05-30
> **Chanath said:**
> How do you hack the json file? How to do that?

Each extension has, in its folder (in ~/.local/share/gnome-shell/extensions) a metadata.json file. In that file, you will see the versions of Gnome Shell for which that extension is supposedly designed. Sometimes (not always), if you just add the version number of the newer version to the list, it will work just fine. Sometimes it still won't work, if there's something coded into that extension that actually requires some feature that has changed or is handled differently now.

When editing metadata.json, be sure to put the desired version number in "", and put a comma in between entries (but not after the last entry). After editing, do a reset of gnome-shell (Alt-F2, r), and then bring up the tweak tool and look under extensions - you'll see if your extension has been enabled.

I've been lucky - all the extensions I consider must-have work using this technique. If your desired extension still doesn't work, go to the extensions website, click on 'installed extensions', and sometimes you'll see there's an update that will get it going...

---

### Post by VinDSL on 2013-05-30
Yeppers!

Actually, you only *need* the version you're running.

EXAMPLE:  Icon Hider

```
{
  "_generated": "Generated by SweetTooth, do not edit, unless you want to", 
  "description": "Show/Hide icons from top panel", 
  "gettext-domain": "org.gnome.shell.extensions.icon-hider", 
  "name": "Icon Hider", 
  "settings-schema": "org.gnome.shell.extensions.icon-hider", 
  **[COLOR="#0000CD"]"shell-version": ["3.9.1"], [/COLOR]**
  "url": "https://github.com/ikalnitsky/gnome-shell-extension-icon-hider", 
  "uuid": "icon-hider@kalnitsky.org", 
  "version": 8
}
```

---

### Post by VinDSL on 2013-05-30
w00t!  New version.  Released 2 days ago. 

Thanks, for reminding me to check!  :D

New json hack...

```
{
    **[COLOR="#0000CD"]"shell-version": ["3.9.1"],[/COLOR]**
    "uuid": "icon-hider@kalnitsky.org",
    "name": "Icon Hider",
    "description": "Show/Hide icons from top panel",
    "url": "https://github.com/ikalnitsky/gnome-shell-extension-icon-hider",
    "settings-schema": "org.gnome.shell.extensions.icon-hider",
    "gettext-domain": "org.gnome.shell.extensions.icon-hider",
    "version": "9"
}
```

[INDENT][ATTACH=CONFIG]243314[/ATTACH][/INDENT]

Anyway, that's all there is to it...  ;)

---

### Post by dino99 on 2013-05-31
3.9.2 is out : major upgrade with lot of fixes (testing ppa)

---

### Post by Chanath on 2013-05-31
Thanks guys!:)

I have Gnome 3.8.2 yet. I have a little problem with backgrounds wallpaper after upgrading yesterday. It is in both Unity & Gnome-shell. Does anyone know how to correct that. Appearance in missing in the system-settings in Unity, but backgrounds are there in the Gnome-shell, but the wallpaper won't come.

---

### Post by dino99 on 2013-05-31
> **Chanath said:**
> Thanks guys!:)

I have Gnome 3.8.2 yet. I have a little problem with backgrounds wallpaper after upgrading yesterday. It is in both Unity & Gnome-shell. Does anyone know how to correct that. Appearance in missing in the system-settings in Unity, but backgrounds are there in the Gnome-shell, but the wallpaper won't come.

The rule here is to not hijack a thread  with something that already have been posted on an other thread. If you have updated your system, that background issue should be now gone.
[http://ubuntuforums.org/showthread.php?t=2149864](http://ubuntuforums.org/showthread.php?t=2149864)

---

### Post by Chanath on 2013-05-31
QUOTE=dino99;12671127]The rule here is to not hijack a thread  with something that already have been posted on an other thread. If you have updated your system, that background issue should be now gone.
[http://ubuntuforums.org/showthread.php?t=2149864](http://ubuntuforums.org/showthread.php?t=2149864)[/QUOTE]

Its me asking the same question, Dino. I didn't get a reply there. I started both these threads. 
 While, I was upgrading, I lost my "Appearance" in the System Settings. Lot of people replied here, so I asked that again. By the way.
 if you how to, do please let me know, in this thread or in the other one. Thanks!

---

### Post by VinDSL on 2013-05-31
> **dino99 said:**
> 3.9.2 is out : major upgrade with lot of fixes (testing ppa)
Interesting!

GS 3.9.2 wouldn't boot under Linux 3.10-rc3 via GDM nor LightDM.  Kept tossing me back to the login screen.  Lubuntu worked.

Restarted under Linux 3.9.4, and logged into GS 3.9.2 just fine.

Had to hack my json files again, of course, to get some extensions working.

Oh, what a tangled web we weave...  LoL!  :D

---

### Post by Chanath on 2013-05-31
> **VinDSL said:**
> Interesting!

GS 3.9.2 wouldn't boot under Linux 3.10-rc3 via GDM nor LightDM.  Kept tossing me back to the login screen.  Lubuntu worked.

Restarted under Linux 3.9.4, and logged into GS 3.9.2 just fine.

Had to hack my json files again, of course, to get some extensions working.

Oh, what a tangled web we weave...  LoL!  :D

Do you find GS 3.9.2 better than 3.8.2? Could you get the top bar to hide?

---

