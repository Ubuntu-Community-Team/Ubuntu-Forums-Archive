---
title: "Saucy gnome fallback top and bottom panel color"
date: 2013-06-12
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-06-12
Every time I boot into Saucy the middle section of the top and bottom panels are a light color close to white.
I have found that if I hold ALT+Super+right click the mouse on each panel, go to properties, click background, 
change it to solid color and then back to none (use system theme) then it straightens out and the color matches the rest of the panels.

I have to do this once per login on each panel. 

Any ideas? Or is this perhaps just a phase?

---

### Post by tista on 2013-06-13
Hi Cavsfan,

I didn't have such issue on my saucy... :(
And I suppose you mean the area "Center pack" of gnome-panel couldn't apply the correct theming appearance, right?

So, which gtk3 theme do you use? or I hope you'd already checked any contents packed in center-pack via dconf-editor... ;)

Usually such bugs might be caused by some types of gtk theming instead of the codes in gnome-panel, donf/gconf backends, and so...

Best Regards,
Tista

---

### Post by Cavsfan on 2013-06-13
> **tista said:**
> Hi Cavsfan,

I didn't have such issue on my saucy... :(
And I suppose you mean the area "Center pack" of gnome-panel couldn't apply the correct theming appearance, right?

So, which gtk3 theme do you use? or I hope you'd already checked any contents packed in center-pack via dconf-editor... ;)

Usually such bugs might be caused by some types of gtk theming instead of the codes in gnome-panel, donf/gconf backends, and so...

Best Regards,
Tista

Thanks for the post but, I was hoping to hear from someone with the same problem. I have not touched anything in donf/gconf and if I change anything 
as far as the panel colors go in gnome-tweak-tool it gets much, much worse than it already is. ;)

[IMG]http://i.imgur.com/RK6CpNx.jpg[/IMG]

This is what it looks like when I initially login before being "touched up".
It isn't anything I have done as far as I can tell. I am noticing that the menus in Applications in the top left have gone weird. Many things are duplicated while 
others are in places I haven't seen before. I guess I'll have to try to touch them up. ;)

I'm sure I could just install from a fresh iso and most probably this problem would go away but, I am not about to do that right now.
The panel colors aren't a deal breaker, just thought I'd throw this out there and see if any one else has the same issue.

---

### Post by muktupavels on 2013-06-13
I have same problem...

---

### Post by Cavsfan on 2013-06-13
> **albertsmuktupavels said:**
> I have same problem...

Great! I don't mean that in a bad way. :) I just meant that it's good to know I am not the only one who has this problem.
Thanks for posting! :)

I mentioned the work around in the first post but, you have to do it every time you login.

[ATTACH=CONFIG]243782[/ATTACH]

I am also getting this in Firefox when I click on different links. I have NoScript addon but, 
I have never seen that before on any of the other 5 Linux systems installed on this box.

---

### Post by muktupavels on 2013-06-13
> **Cavsfan said:**
> I mentioned the work around in the first post but, you have to do it every time you login.
Workaround is not solution to me. I don't want do it for 6 panels every time I login. Furthermore after some time white colour comes back for some panels.

---

### Post by Cavsfan on 2013-06-14
> **albertsmuktupavels said:**
> Workaround is not solution to me. I don't want do it for 6 panels every time I login. Furthermore after some time white colour comes back for some panels.

I agree. Something you have to do like that every time you login is definitely not a workaround.
I just wanted to mention what I had found to get rid of the white parts. Remember this is a developmental release and things are going to break.
In today's updates one was for the gnome-shell which I had hoped fixed this problem but, upon reboot the problem is still there.

I thought I seen the bottom panel change back to white yesterday but, wasn't sure.
Right now the menus at the top left when you click on Applications are so messed up it is hard to find things and many things are duplicated.

---

### Post by Cavsfan on 2013-06-14
I think I found what caused it and the solution as well. Time will tell but, upon reboot it looks normal. 
As far as what caused it: I am pretty sure I installed the gnome-shell via **sudo apt-get gnome-shell**. I believe that was when the fun began.

The solution was to remove **gnome-shell** and **gnome-shell-extentions** via Synaptic and leave anything else **gnome-shell*** alone.
It also removed **gdm** but that did not matter to me as I use **lightdm**.

If you enter in terminal **sudo apt-get purge gnome-shell**, it will take **gnome-session-fallback** with it which is the reason a lot of us are here.  :)

So, be sure and use SPM.

---

### Post by Cavsfan on 2013-06-14
Pretty sure that also fixed the java error popup window I was getting too every time I clicked on certain things. :)

Haven't had it happen since I purged gnome-shell.

It also straightened out my Application menu. I don't have duplication any more and everything looks like it is back to normal. :)

---

### Post by Cavsfan on 2013-06-14
Well it is back sort of. The top panel is white and some apps in the bottom panel are white. 
I just removed **gnome-shell-common** which was the last remaining gnome* version 3.8.2 thing I had installed.
Removed it via SPM also and it took **gnome-tweak-tool** with it.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-panel
gnome-panel:
  Installed: 1:3.6.2-0ubuntu4
  Candidate: 1:3.6.2-0ubuntu4
  Version table:
 *** 1:3.6.2-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Not sure what to make of it now. I'll reboot and see. :-s

---

### Post by Cavsfan on 2013-06-14
Yup it's back but, only the top panel and apps that do not have the focus in the bottom panel are also too light white to read. 
It's a shot in the right direction but...
:neutral:

Found out the bottom panel was set to "solid color" in properties and changing it back to none (use system theme) fixed the bottom panel.

---

### Post by Cavsfan on 2013-06-14
Now it's back just like it was. Both middle sections are white.

---

### Post by Cavsfan on 2013-06-16
I wonder why the versions are mixed. :confused:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-session-fallback
gnome-session-fallback:
  Installed: 3.6.2-0ubuntu7
  Candidate: 3.6.2-0ubuntu7
  Version table:
 *** 3.6.2-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: (none)
  Candidate: 3.8.2-1ubuntu2
  Version table:
     3.8.2-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
```

I currently do not have gnome-shell or any of it's associated files installed and I would have to manually install them any way which is puzzling by itself.

With or without gnome-shell installed I still have the white middle section of both panels upon boot. :o

---

### Post by muktupavels on 2013-06-16
Panels are normal if running Gnome Fallback (No Effects). So maybe there is problem with compiz?

---

### Post by Cavsfan on 2013-06-16
> **albertsmuktupavels said:**
> Panels are normal if running Gnome Fallback (No Effects). So maybe there is problem with compiz?

You are probably right. Compiz is being very finicky. Let's hope they fix it at some point. :)

---

### Post by racb on 2013-06-21
I may have the same problem. I've been killing and restarting gnome-panel, which seems to fix it for me. Does this work for you too? If so, it may be some kind of race condition.

---

### Post by dino99 on 2013-06-21
fallback is replaced by flashback (glance at synaptic's package details)

---

### Post by Cavsfan on 2013-06-24
> **dino99 said:**
> fallback is replaced by flashback (glance at synaptic's package details)

I did notice that. Not sure what I need to do as I still have the same problem with the white middle of both panels as in the picture on page 1 of this thread.
The reason I say I am not sure what to do is the versions are all mixed up:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-panel
gnome-panel:
  Installed: 1:3.6.2-0ubuntu11
  Candidate: [COLOR=#ff0000]1:3.6.2-0[/COLOR]ubuntu11
  Version table:
 *** 1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```


```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: (none)
  Candidate: [COLOR=#ff0000]3.8.3-1[/COLOR]ubuntu1
  Version table:
     3.8.3-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages

```

Do I install gnome-shell? I am not installing the Gnome 3 PPA; not really interested.

---

### Post by Cavsfan on 2013-06-24
> **albertsmuktupavels said:**
> Panels are normal if running Gnome Fallback (No Effects). So maybe there is problem with compiz?

Running what is now "Gnome Flashback (No Effects)" produces the exact same white panels that "Gnome Flashback" does for me.

---

### Post by zika on 2013-06-24
```
:~$ apt-cache policy gnome-panelgnome-panel:
  Installed: 1:3.6.2-0ubuntu11
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
 *** 1:3.6.2-0ubuntu11 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
     1:3.6.2-0ubuntu4~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main amd64 Packages
:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.9.3+git20130618.580bd672-0ubuntu1~13.10~ricotz0
  Candidate: 3.9.3+git20130618.580bd672-0ubuntu1~13.10~ricotz0
  Version table:
 *** 3.9.3+git20130618.580bd672-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
     3.8.3-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
     3.8.3-0ubuntu1~raring1.1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main amd64 Packages
     3.8.2-1ubuntu2~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main amd64 Packages
```
No ill-effects You mention...
Update&#8321;: To clarify: no ill-effects in flashback sessions... In GnomeClassic I do have panels of different color (not by my choice)... Not been there lately...

---

### Post by Cavsfan on 2013-06-24
> **zika said:**
> No ill-effects You mention...
Update&#8321;: To clarify: no ill-effects in flashback sessions... In GnomeClassic I do have panels of different color (not by my choice)... Not been there lately...

All I have is Gnome Flashback and the problem is there. I no longer have Gnome Classic as an option.
Don't you have the Gnome 3 PPA and the ricotz testing PPA installed? I have neither.

---

### Post by zika on 2013-06-24
> **Cavsfan said:**
> All I have is Gnome Flashback and the problem is there. I no longer have Gnome Classic as an option.
Don't you have the Gnome 3 PPA and the ricotz testing PPA installed? I have neither.Both G3 and all ricotz that are applicable...

---

### Post by Cavsfan on 2013-06-27
I am pretty amazed. ):P I just downloaded the daily iso and installed a fresh copy of Saucy. I got everything all setup. Installed gnome-flashback and viola the white on the middle of the panels are back just like before. #-o
I'm not touching the gnome 3 ppa or any of that other stuff that is not included with generic Ubuntu through normal updates etc.
This is why I like LTS versions but, I am trying really hard to play along... ;-)

---

### Post by Cavsfan on 2013-06-29
What a difference a few hours can make. I doanloaded the iso on the morning of June 27th USA ET and it was the same but, I noticed the alpha had been released and was produced later on the 27th.
Just installed it with Gnome and no more white panels. Guess this problem is resolved. ;)

---

### Post by gexpower on 2013-06-30
The Bug is Reported in Launchpad

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1196177](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1196177)

If anyone has time, please report.

---

### Post by Cavsfan on 2013-06-30
I signed onto that bug and it is back on the regular iso. I just installed it over the gnome version.

---

### Post by Cavsfan on 2013-07-01
Yup this is a real problem. It has occurred on each Saucy generic install I have done. It can be readily repeated.
I urge everyone who is getting this on gnome fallback/flashback (whichever) to add your name to the bug mentioned above.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1196177](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1196177)

That is the bug **gexpower** mentioned and there are only 3 people on that bug. There should many more than that.

---

### Post by gexpower on 2013-07-02
IMPORTANT!!


Since Ubuntu 13.04 gnome-session-fallback has become buggly. We need you support registering in the follow URL (Bug Record) your comments about it, of course, if you're affected.

[https://bugs.launchpad.net/compiz-core/+bug/1196177](https://bugs.launchpad.net/compiz-core/+bug/1196177)


As Cavsfan Says, we need more people join us on this bug report. 

¡ Thank you for bring us your help !

---

### Post by Cavsfan on 2013-07-03
> **gexpower said:**
> IMPORTANT!!


Since Ubuntu 13.04 gnome-session-fallback has become buggly. We need you support registering in the follow URL (Bug Record) your comments about it, of course, if you're affected.

[https://bugs.launchpad.net/compiz-core/+bug/1196177](https://bugs.launchpad.net/compiz-core/+bug/1196177)


As Cavsfan Says, we need more people join us on this bug report. 

¡ Thank you for bring us your help !

That is the bug about the white section of the top and bottom panels in Saucy gnome flashback. It still says it only affects 3 people. Although anyone who installs Saucy and uses gnome flashback/fallback (whatever it's called) will get this every time. I have installed it at least three times and it never fails.

This bug is the one that started in Raring 13.04 and continues into Saucy 13.10 where after you maximize any window, the three buttons at the top of the window become unclickable. You cannot minimize, close, etc. that window. It would be nice to see this fixed as it is more problematic than just the white color which is just annoying. But, both are annoying.

[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

---

### Post by zika on 2013-07-03
> **Cavsfan said:**
> That is the bug about the white section of the top and bottom panels in Saucy gnome flashback. It still says it only affects 3 people. **Although anyone who installs Saucy and uses gnome flashback/fallback (whatever it's called) will get this every time. I have installed it at least three times and it never fails.**

This bug is the one that started in Raring 13.04 and continues into Saucy 13.10 where after you maximize any window, the three buttons at the top of the window become unclickable. You cannot minimize, close, etc. that window. It would be nice to see this fixed as it is more problematic than just the white color which is just annoying. But, both are annoying.

[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)
I can not reproduce problem either with the color or with Max/Restore/...
I do have 13.10 and do have all GS and Ricotz (with a bunch of others) PPAs turned on...
Hencw, I, for example, can not sign those bugs...
Do not be so exclusive...

---

### Post by muktupavels on 2013-07-03
> **zika said:**
> I can not reproduce problem either with the color or with Max/Restore/...
I do have 13.10 and do have all GS and Ricotz (with a bunch of others) PPAs turned on...
Hencw, I, for example, can not sign those bugs...
Do not be so exclusive...

Do you use Gnome Flashback (gnome-session-flashback)?

---

### Post by zika on 2013-07-03
> **albertsmuktupavels said:**
> Do you use Gnome Flashback (gnome-session-flashback)?
Yes, I was/am writting all these messages from it. Do You think I would write the stuff what I have written and not use it...?
I, simply, do not write about stuff I do not use...
Yes, I have several other environments, that is the point of Testing, isn't it?

---

### Post by zika on 2013-07-03
> **albertsmuktupavels said:**
> Do you use Gnome Flashback (gnome-session-flashback)?
Yes, Iwas writting all these messages from it. I do use both of flashback flavours... (compiz and no-effects)... Do You think I would write the stuff what I have written and not use it...? I, simply, do not write about stuff I do not use... Yes, I have several other environments, that is the point of Testing, isn't it?

---

### Post by muktupavels on 2013-07-03
> **zika said:**
> 
No ill-effects You mention...
Update&#8321;: To clarify: no ill-effects in flashback sessions... In  GnomeClassic I do have panels of different color (not by my choice)...  Not been there lately...

Here you write that you have no problem in Gnome Classic. I think that Gnome Flashback != Gnome Classic. Or am I wrong?

---

### Post by muktupavels on 2013-07-03
Can you test if you have same problem on clean install?

Just installed clean install on virtualbox, and i have same problems. 

Maybe you can list things you have installed?

---

### Post by zika on 2013-07-04
> **albertsmuktupavels said:**
> Here you write that you have no problem in Gnome Classic. I think that Gnome Flashback != Gnome Classic. Or am I wrong?
I might made a typo, (update: no, I have not, see below...) I'm not going to track all my messages about this...

Situation is, to repat and repeat...:

1. Gnome-Flashback (both Compiz and NoEffects, no difference) are working OK. Min/Max/ working fine... No clock... No any trouble with menus...
2. Gnome-Classic is working OK except for some coloring issues, I'd have to log-in back into it (I'm in Flashback now) to refresh my memory about that...

I think You've misunderstood some of my messages or did not read them carefully, or I was totally unclear, which is probably the case...

Over&Out...

You're right one thing: GnomeFlashBack(former FallBack)(either one) is not GnomeClassic...

Update&#8321;: You do quote my message:
> **zika said:**
> Update&#8321;: To clarify: no ill-effects in flashback sessions... In GnomeClassic I do have panels of different color (not by my choice)... Not been there lately...
in which I write just the same thing I wrote above and the same thing You try to read in complete negation...???

No ill-effects in nomeFlashBack...
Errors in GnomeClassic (GS!=GFB)
I've not been in GC lately...

What is going on?

---

### Post by Cavsfan on 2013-07-04
> **zika said:**
> I can not reproduce problem either with the color or with Max/Restore/...
I do have 13.10 and do have all GS and Ricotz (with a bunch of others) PPAs turned on...
Hencw, I, for example, can not sign those bugs...
Do not be so exclusive...

I meant if you do not install the GS, Ricotz, etc. PPAs... If you do not install those you will get the same results I have EVERY TIME which is the white... ;)

---

### Post by zika on 2013-07-04
> **Cavsfan said:**
> I meant if you do not install the GS, Ricotz, etc. PPAs... If you do not install those you will get the same results I have EVERY TIME which is the white... ;)That is the beauty of our diversity... It helps us decide where is the culprit and, more important, if solution is already on the way... ;)

---

### Post by Cavsfan on 2013-07-04
> **zika said:**
> I can not reproduce problem either with the color or with Max/Restore/...
I do have 13.10 and do have all GS and Ricotz (with a bunch of others) PPAs turned on...
Hencw, I, for example, can not sign those bugs...
[COLOR=#ff0000]Do not be so exclusive...[/COLOR]

> **zika said:**
> That is the beauty of our diversity... It helps us decide where is the culprit and, more important, if solution is already on the way... ;)

I had already mentioned that I did not install any GS, Ricotz or any other special PPA. I had also already mentioned that [U]anyone that installs Saucy plain vanilla and installs 
gnome flashback or whatever it is called will get this every time and that this can be repeated over and over again[/U].
 Not everyone installs the special ppas and loves breakage. I tried it a few times and ended up unable to boot into it. So, It's sort of like fool me once...

When I said > I [COLOR=#ff0000]meant[/COLOR] if you do not install the GS, Ricotz, etc. PPAs...

I should not have said "meant" as I did say that I did not install those special PPAs more than once already.
Maybe you should read the thread more before you get all belligerent. ;)

---

### Post by zika on 2013-07-04
> **Cavsfan said:**
> I had already mentioned that I did not install any GS, Ricotz or any other special PPA. I had also already mentioned that [U]anyone that installs Saucy plain vanilla and installs 
gnome flashback or whatever it is called will get this every time and that this can be repeated over and over again[/U].
 Not everyone installs the special ppas and loves breakage. I tried it a few times and ended up unable to boot into it. So, It's sort of like fool me once...

When I said 

I should not have said "meant" as I did say that I did not install those special PPAs more than once already.
Maybe you should read the thread more before you get all belligerent. ;)I am the least belligerent of all... ;) Trust me... :P
Just because I did read the thread more (than once) I did conclude (judging for example from my experience, and judging from the fact that PPA stuff will evenutlly get into vanilla) that solution for Your problem is already there... That's all I had to write... :P Belligerent or not...

---

### Post by Cavsfan on 2013-07-04
> **zika said:**
> I am the least belligerent of all... ;) Trust me... :P
Just because I did read the thread more (than once) I did conclude (judging for example from my experience, and judging from the fact that PPA stuff will evenutlly get into vanilla) that solution for Your problem is already there... That's all I had to write... :P Belligerent or not...

I'll take your word for it. :p

What I am saying is the fix for this whatever that may be will have to be in the normal updates before it ever gets to me... ;)

---

### Post by zika on 2013-07-04
> **Cavsfan said:**
> I'll take your word for it. :p

What I am saying is the fix for this whatever that may be will have to be in the normal updates before it ever gets to me... ;)No power in my old body to give a word... I can just suppose and You can wait for it in proposed... :P

---

### Post by muktupavels on 2013-07-04
Witch PPAs i need to add? I will add and install all updates on virtualbox.

---

### Post by Cavsfan on 2013-07-04
> **zika said:**
> No power in my old body to give a word... I can just suppose and You can wait for it in proposed... :P

I suppose you can suppose whatever you wish... :P Regardless I am not holding my breath. I have other things to do.

> **albertsmuktupavels said:**
> Which PPAs i need to add? I will add and install all updates on virtualbox.

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) is one of them. 

I suppose zika can provide you with the rest.

---

### Post by muktupavels on 2013-07-04
> **Cavsfan said:**
> [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) is one of them. 

Added this ppa, updated and upgraded. Still white panel, still apps opened in full screen cannot be closed, minimized, maximized with title bar buttons. :(

---

### Post by mc4man on 2013-07-04
The light color in the panels is likely from your theme, whether light-themes behaves better in gnome-flashback w/compiz down the road , no idea. (when Ubuntu eventually drops compiz then again no idea whether it will be usable in any way.
If you were to switch all or part (gtk+), to adwaita then it should  act better, while the default adwaita isn't pleasing to many it can be manipulated in various ways. (or test some other gtk+3 themes.

Additionally here it seems to use some things like background with a  solid color gradient I needed to enable the gnome-settings-daemon "background" plugin.
(- for that did manually or in a unity session  as the gnome version of the Appearance panel has got to be the lowest rent panel I've ever seen, or at least as presented in Ubuntu












0

---

### Post by Cavsfan on 2013-07-05
> **mc4man said:**
> The light color in the panels is likely from your theme, whether light-themes behaves better in gnome-flashback w/compiz down the road , no idea. (when Ubuntu eventually drops compiz then again no idea whether it will be usable in any way.
If you were to switch all or part (gtk+), to adwaita then it should  act better, while the default adwaita isn't pleasing to many it can be manipulated in various ways. (or test some other gtk+3 themes.

Additionally here it seems to use some things like background with a  solid color gradient I needed to enable the gnome-settings-daemon "background" plugin.
(- for that did manually or in a unity session  as the gnome version of the Appearance panel has got to be the lowest rent panel I've ever seen, or at least as presented in Ubuntu.

You may be right. I logged into Unity which is fine and then back into fallback. Changed the theming as shown. Although it did some wierd things like at first the two panels disappeared and I had to logout and back in more than once and then I restarted the PC and it is still the same as the picture.
Although CCSM was totally reset and had the checkmark warning me about changing settings like it does initially. Compiz also crashed and sent a bug report.

It is almost too dark to read the font on the windows.
Time will tell if this is permanent or not...

[ATTACH=CONFIG]244427[/ATTACH]

















0

---

### Post by Cavsfan on 2013-07-06
So far so good. And all I had to do was change in gnome tweak tool under theme is set GTK+ theme from Ambiance to Adwaita (default). 
That is bizzare. =P~ But, I guess running compiz, CCSM and various other settings can make a huge difference.

Does that solve your problem as well albertsmuktupavels?

Edit: My appologies zika. I should not have used the word belligerent.

---

### Post by zika on 2013-07-06
> **Cavsfan said:**
> Edit: My appologies zika. I should not have used the word belligerent.Why apologies? I found it quite appropriate and also joke-provoking so I took that opportunity and laughed while answering... Really, no reason for any kind of apologies... To the contrary... ;)
My avatar looks belligerent, I do admit... ;)

---

### Post by Cavsfan on 2013-07-07
> **zika said:**
> Why apologies? I found it quite appropriate and also joke-provoking so I took that opportunity and laughed while answering... Really, no reason for any kind of apologies... To the contrary... ;)
My avatar looks belligerent, I do admit... ;)

All right then! ;) lol

I think I am going to mark this thread as solved as I no longer have the white panels any more with the simple change in gnome tweak tool.
Everything is pretty dark but, I can live with it.

---

### Post by zika on 2013-07-07
> **Cavsfan said:**
> All right then! ;) lol

I think I am going to mark this thread as solved as I no longer have the white panels any more with the simple change in gnome tweak tool.
Everything is pretty dark but, I can live with it.
On log-out just minutes ago I've lost FlashBack sessions (both)... ;)
Classic and GS are working...

---

### Post by Cavsfan on 2013-07-07
> **zika said:**
> On log-out just minutes ago I've lost FlashBack sessions (both)... ;)
Classic and GS are working...

I tried to remove gnome-screensaver and it wanted to remove gnome-fallback-session and gnome-flashback-session.
So, I said "no". lol

So I cannot get a screensaver working unless I manually click on screensaver and it kills gnome-screensaver and xscreensaver takes over. ;)

---

### Post by zika on 2013-07-07
> **Cavsfan said:**
> I tried to remove gnome-screensaver and it wanted to remove gnome-fallback-session and gnome-flashback-session.
So, I said "no". lol

So I cannot get a screensaver working unless I manually click on screensaver and it kills gnome-screensaver and xscreensaver takes over. ;)No, I did not loose them as unistalled, they just refuse to work properly... I'll see to that tomorrow...

---

### Post by Cavsfan on 2013-07-07
> **zika said:**
> No, I did not loose them as unistalled, they just refuse to work properly... I'll see to that tomorrow...

I just tried all of my login options. It's weird but Gnome (which I guess you are referring to as GS)  and Gnome (no effects) seem to be the same. They both allow rotation of the cube.
The same as Classic except no top or bottom panels.
Then I tried Ubuntu (default) with Unity and had no rotating cube. Oddly I had Gnome Classic and Gnome Fallback both. They appeared to function the same but, the icon for selecting Classic had the gnome icon and Fallback just had a round circle with no icon. :???:
So I am back on Gnome fallback and all works except the screensaver and no clock or calendar in the top right panel. :)

---

### Post by zika on 2013-07-08
> **Cavsfan said:**
> I just tried all of my login options. It's weird but Gnome (which I guess you are referring to as GS)  and Gnome (no effects) seem to be the same. They both allow rotation of the cube.
The same as Classic except no top or bottom panels.
Then I tried Ubuntu (default) with Unity and had no rotating cube. Oddly I had Gnome Classic and Gnome Fallback both. They appeared to function the same but, the icon for selecting Classic had the gnome icon and Fallback just had a round circle with no icon. :???:
So I am back on Gnome fallback and all works except the screensaver and no clock or calendar in the top right panel. :)
It seems strange to me how sessions are behaving at Your place...
At my place I have:
Gnome (GnomeShell proper)
Gnome Classic (very much alike GS but static, two panels, upper and lower)
Gnome FlashBack (no effects) with metacity (different from GSC) visualy same as GFBC
Gnome FlashBack with compiz (different from GSC) visualy same as GFBM
Unity
and several others ...

You can see that from my ~/.xinitrc:```
...
#exec /usr/bin/gnome-session --session=gnome-classic
#exec /usr/bin/gnome-session --session=gdm-shell
#exec /usr/bin/gnome-session --session=gnome-flashback-compiz
#exec /usr/bin/gnome-session --session=ubuntu
#exec enlightenment_start
exec /usr/bin/gnome-session --session=gnome-flashback
#exec /usr/bin/gnome-session --session=gnome...
```

---

### Post by Cavsfan on 2013-07-08
Here are my sessions:
```
cavsfan@cavsfan-MS-7529:~$ cd /usr/share/gnome-session/sessions/
cavsfan@cavsfan-MS-7529:/usr/share/gnome-session/sessions$ ls -l
total 32
-rw-r--r-- 1 root root  110 Jun 22 07:31 cairo-dock.session
-rw-r--r-- 1 root root  205 Jun  6 16:28 gdm-fallback.session
-rw-r--r-- 1 root root   91 Jun  6 16:28 gdm-shell.session
-rw-r--r-- 1 root root  609 Jun 19 10:45 gnome-classic.session
-rw-r--r-- 1 root root  116 Jun 21 00:06 gnome-flashback-compiz.session
-rw-r--r-- 1 root root  131 Jun 21 00:06 gnome-flashback.session
-rw-r--r-- 1 root root 1477 Jun 25 11:23 gnome.session
-rw-r--r-- 1 root root   95 Jun 25 11:23 ubuntu.session

```

I don't have any ~/.xinitrc file. :???:

---

### Post by zika on 2013-07-08
> **Cavsfan said:**
> Here are my sessions:
```
cavsfan@cavsfan-MS-7529:~$ cd /usr/share/gnome-session/sessions/
cavsfan@cavsfan-MS-7529:/usr/share/gnome-session/sessions$ ls -l
total 32
-rw-r--r-- 1 root root  110 Jun 22 07:31 cairo-dock.session
-rw-r--r-- 1 root root  205 Jun  6 16:28 gdm-fallback.session
-rw-r--r-- 1 root root   91 Jun  6 16:28 gdm-shell.session
-rw-r--r-- 1 root root  609 Jun 19 10:45 gnome-classic.session
-rw-r--r-- 1 root root  116 Jun 21 00:06 gnome-flashback-compiz.session
-rw-r--r-- 1 root root  131 Jun 21 00:06 gnome-flashback.session
-rw-r--r-- 1 root root 1477 Jun 25 11:23 gnome.session
-rw-r--r-- 1 root root   95 Jun 25 11:23 ubuntu.session

```

I don't have any ~/.xinitrc file. :???:You do not have to have it... I just wanted to list what are sessions here and difference between them since that was a point of talk, as I saw it... It seemed that some sessions behaved differently on the machine of the person I replied to... Never mind... ;)

---

### Post by Cavsfan on 2013-07-08
> **zika said:**
> You do not have to have it... I just wanted to list what are sessions here and difference between them since that was a point of talk, as I saw it... It seemed that some sessions behaved differently on the machine of the person I replied to... Never mind... ;)

All right then. Perhaps we should leave this thread alone now as it has served it's purpose and is resolved. MmmmKay? ;)

---

### Post by muktupavels on 2013-07-08
> **Cavsfan said:**
> Does that solve your problem as well albertsmuktupavels?

Yes and no... It is not a solution. There is problem/bug which needs to be fixed.

---

### Post by Cavsfan on 2013-07-08
> **albertsmuktupavels said:**
> Yes and no... It is not a solution. There is problem/bug which needs to be fixed.

Yes, I guess you are right. It does fix the problem but, we should not have to change a setting to solve a problem. That is just a work around.

Edit: I marked it back to open.

---

### Post by muktupavels on 2013-07-12
Filled new bug against gtk3 - [https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1200689](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1200689)

It seems to be problem with gtk. Problem disappears downgrading libgtk-3-0 package to version 3.6.4-0ubuntu8.

---

### Post by Cavsfan on 2013-07-15
> **albertsmuktupavels said:**
> Filled new bug against gtk3 - [https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1200689](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1200689)

It seems to be problem with gtk. Problem disappears downgrading libgtk-3-0 package to version 3.6.4-0ubuntu8.

I would agree that the problem is probaly with gtk. I switched it back to Ambiance in gnome tweak tool. It seemed good but, I could not read anything in Ubuntu Software Center.
The text on many things including that made it so unreadable it was not worth it.
So, I am back to dealing with the white top and bottom panels. Wonder if it will even be fixed or if the primary concern is Unity.

---

### Post by muktupavels on 2013-07-15
> **Cavsfan said:**
> So, I am back to dealing with the white top and bottom panels. Wonder if it will even be fixed or if the primary concern is Unity.

White color is from theme. In /usr/share/themes/Ambiance/gtk-3.0/gtk-main.css bg_color is #f2f1f0, so it is not realy pure white. You can change it to whatever you want and you will see it on panel.

I guess it is hard to track down this bug. It would be easier if for example gradient wont work at all, but in our case it works under menu and indicator applet. + we are able to get it for whole panel, changing panels background color from none to solid color and than back to none.

Probably easiest way to fix panel would be editing theme - changing gradient to simple color.

Tonight I will read gnome-panel source code and try to understand how it works. Maybe I will be able to fix it in case it is bug in gnome-panel.

---

### Post by muktupavels on 2013-07-15
I found fix. :)

---

### Post by Cavsfan on 2013-07-19
> **albertsmuktupavels said:**
> I found fix. :)

We share on this forum. :)

---

### Post by muktupavels on 2013-07-19
It was not real fix when I wrote that...

Now I am using gnome-panel with other fix. I don't now how correct it is, but now gnome-panel really works for me. I have submitted patch on bugzilla.gnome.org, launchpad.net and created branch which includes patch.

Anyone can download branch (bzr branch lp:~albertsmuktupavels/gnome-panel/fix-for-1196177) with fix and build new packages.

---

### Post by muktupavels on 2013-07-30
Added two deb packages to [launchpad bug]("https://bugs.launchpad.net/gnome-panel/+bug/1196177") built for saucy, amd64 with my fix.

---

### Post by Cavsfan on 2013-07-30
> **albertsmuktupavels said:**
> Added two deb packages to [launchpad bug]("https://bugs.launchpad.net/gnome-panel/+bug/1196177") built for saucy, amd64 with my fix.

I tried the amd64 deb and got these errors: (I also posted this on the bug.)
```
cavsfan@cavsfan-desktop:~/Downloads$ sudo dpkg -i gnome-panel_3.6.2-0ubuntu12_amd64.deb[sudo] password for cavsfan: 
(Reading database ... 236597 files and directories currently installed.)
Preparing to replace gnome-panel 1:3.4.1-0ubuntu1.1 (using gnome-panel_3.6.2-0ubuntu12_amd64.deb) ...
Unpacking replacement gnome-panel ...
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libdconf1 (>= 0.14.0); however:
  Package libdconf1 is not installed.
 gnome-panel depends on libecal-1.2-15 (>= 3.5.91); however:
  Package libecal-1.2-15 is not installed.
 gnome-panel depends on libedataserver-1.2-17 (>= 3.5.91); however:
  Package libedataserver-1.2-17 is not installed.
 gnome-panel depends on libglib2.0-0 (>= 2.37.3); however:
  Version of libglib2.0-0 on system is 2.32.3-0ubuntu1.
 gnome-panel depends on libgnome-desktop-3-7 (>= 3.2.0); however:
  Package libgnome-desktop-3-7 is not installed.
 gnome-panel depends on libgweather-3-3 (>= 3.7.91); however:
  Package libgweather-3-3 is not installed.
 gnome-panel depends on libical1 (>= 1.0); however:
  Package libical1 is not installed.
 gnome-panel depends on libpango-1.0-0 (>= 1.18.0); however:
  Package libpango-1.0-0 is not installed.
 gnome-panel depends on gnome-panel-data (= 1:3.6.2-0ubuntu12); however:
  Version of gnome-panel-data on system is 1:3.4.1-0ubuntu1.1.
dpkg: error processing gnome-panel (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Errors were encountered while processing:
 gnome-panel

```

---

### Post by Cavsfan on 2013-07-30
My bad! Ignore that post! I had booted into another OS and forgot. #-o
I'm going to try it again.

---

### Post by Cavsfan on 2013-07-30
I still got errors:

```
cavsfan@cavsfan-MS-7529:~/Downloads$ sudo dpkg -i gnome-panel_3.6.2-0ubuntu12_amd64.deb[sudo] password for cavsfan:
(Reading database ... 209648 files and directories currently installed.)
Preparing to replace gnome-panel 1:3.6.2-0ubuntu11 (using gnome-panel_3.6.2-0ubuntu12_amd64.deb) ...
Unpacking replacement gnome-panel ...
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:3.6.2-0ubuntu12); however:
  Version of gnome-panel-data on system is 1:3.6.2-0ubuntu11.

 dpkg: error processing gnome-panel (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for man-db ...
Errors were encountered while processing:
 gnome-panel


```

sudo apt-get update & sudo apt-get-upgrade returns this error now:

```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-panel : Depends: gnome-panel-data (= 1:3.6.2-0ubuntu12) but 1:3.6.2-0ubuntu11 is installed
               Recommends: gnome-session-fallback but it is not installed
E: Unmet dependencies. Try using -f.
```


```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  gnome-panel-data
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  gnome-applets gnome-panel gnome-session-flashback
0 upgraded, 0 newly installed, 3 to remove and 19 not upgraded.
1 not fully installed or removed.
After this operation, 2,285 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by muktupavels on 2013-07-30
You need install both packages (gnome-panel and gnome-panel-data) -** sudo dpkg -i gnome-panel*.deb**

---

### Post by Cavsfan on 2013-07-30
However, I went ahead and entered **sudo apt-get -f install** and then reinstalled what it uninstalled and it looks good so far.
I will reboot to see if the problem is fixed.

---

### Post by Cavsfan on 2013-07-30
> **albertsmuktupavels said:**
> You need install both packages (gnome-panel and gnome-panel-data) -** sudo dpkg -i gnome-panel*.deb**

OK, I installed both packages, rebooted and still have the white panels as before.

---

### Post by muktupavels on 2013-07-30
> **Cavsfan said:**
> OK, I installed both packages, rebooted and still have the white panels as before.

Post output of - apt-cache policy gnome-panel

---

### Post by Cavsfan on 2013-07-30
> **albertsmuktupavels said:**
> Post output of - apt-cache policy gnome-panel

You read my mind! I was going to do just that.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-panel*
gnome-panel-dbg:
  Installed: (none)
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
     1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
gnome-panel-data:
  Installed: 1:3.6.2-0ubuntu11
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
 *** 1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
gnome-panel:
  Installed: 1:3.6.2-0ubuntu11
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
 *** 1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by muktupavels on 2013-07-30
You didn't install downloaded packages. Installed package version should be - 1:3.6.2-0ubuntu12 not 1:3.6.2-0ubuntu11
> alberts@ga-b75m-d3h:~$ apt-cache policy gnome-panel
gnome-panel:
  Installed: 1:3.6.2-0ubuntu12
  Candidate: 1:3.6.2-0ubuntu12
  Version table:
 *** 1:3.6.2-0ubuntu12 0
        100 /var/lib/dpkg/status
     1:3.6.2-0ubuntu11 0
        500 [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) saucy/universe amd64 Packages

---

### Post by Cavsfan on 2013-07-30
> **albertsmuktupavels said:**
> You didn't install downloaded packages. Installed package version should be - 1:3.6.2-0ubuntu12 not 1:3.6.2-0ubuntu11

I think I messed up by not dpkg(ing) both debs at the same time. I had removed and installed them because there were unmet dependencies.
And this time I did it as in your post **sudo dpkg -i gnome-panel*.deb** and it worked great. No more white panels!

So, good job you did fix this problem!

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-panel*
gnome-panel-dbg:
  Installed: (none)
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
     1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
gnome-panel-data:
  Installed: 1:3.6.2-0ubuntu12
  Candidate: 1:3.6.2-0ubuntu12
  Version table:
 *** 1:3.6.2-0ubuntu12 0
        100 /var/lib/dpkg/status
     1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
gnome-panel:
  Installed: 1:3.6.2-0ubuntu12
  Candidate: 1:3.6.2-0ubuntu12
  Version table:
 *** 1:3.6.2-0ubuntu12 0
        100 /var/lib/dpkg/status
     1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages

```

---

### Post by Cavsfan on 2013-07-31
This problem now is resolved thanks to **albertsmuktupavels**.

Just make sure you install both debs at the same time. It will not work if you do each individually. (I proved this as I messed up and tried installing them one at at time).

---

