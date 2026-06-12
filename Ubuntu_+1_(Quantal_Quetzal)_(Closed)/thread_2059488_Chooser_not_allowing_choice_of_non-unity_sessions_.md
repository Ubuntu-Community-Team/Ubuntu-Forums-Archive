---
title: "Chooser not allowing choice of non-unity sessions after 12.04-&gt;12.10 upgrade"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by professordes on 2012-09-18
I have upgraded 3 machines (netbook, ThinkPad, generic desktop) from 12.04 to 12.10 beta and none of them will allow alternative sessions (gnome, kde..) to be picked from the chooser.  The list appears when clicking on the ubuntu symbol in the login box and the other sessions can be highlighted, but there is no "OK" to click through on and going back to the login box still gives unity.

Has anyone else encountered this behaviour? I don't see any obvious bugs listed.

---

### Post by dino99 on 2012-09-18
pay attention at the installed greeter, which one(s) are you using ? is ubuntu meta-package installed ?

---

### Post by professordes on 2012-09-18
> **dino99 said:**
> pay attention at the installed greeter, which one(s) are you using ? is ubuntu meta-package installed ?

Yes ubuntu-desktop is installed. I am using unity-greeter (I think).

I have just tried upgrading another desktop PC out of curiosity from 12.04 to 12.10 and there the chooser _does_ allow me to pick the other sessions.

v. odd 

I guess I can now play spot the difference with the setup to try and see what is going on.

---

### Post by grahammechanical on 2012-09-18
Have you tried re-installing those alternative desktops?

I have not tried upgrading from 12.04 with alternative desktops installed to 12.10 but since Unity 2D has been removed from 12.10 I have installed fvwm-crystal as an fall-back option for when Compiz breaks. And I do get a list of desktop options and an OK panel.

May be the thing works best if alternate desktops are installed after 12.10 is installed.

Regards.

---

### Post by stinkeye on 2012-09-18
Just noticed I can't select alternative sessions with the mouse.
Besides unity I only have the gnome-classic and gnome-classic(no effects)
sessions.
This is a 12.10 beta install, not an upgrade from 12.04.
I could select before but now can only select by tabbing to highlight and then pressing enter.

---

### Post by professordes on 2012-09-18
> **grahammechanical said:**
> Have you tried re-installing those alternative desktops?

I have not tried upgrading from 12.04 with alternative desktops installed to 12.10 but since Unity 2D has been removed from 12.10 I have installed fvwm-crystal as an fall-back option for when Compiz breaks. And I do get a list of desktop options and an OK panel.

May be the thing works best if alternate desktops are installed after 12.10 is installed.

Regards.

It was the cairo-dock session it didn't like, removing that from the list gets an OK back.... 

I had fvwm-crystal too :)

---

### Post by jerrylamos on 2012-09-24
amd64
Chooser not working.  It used to.
Mouse cannot select other sessions.
Tab does not select other sessions.
up/down arrow does not select other sessions.

I did get a crash reported as bug #1955828
signonui crashed with SIGSEGV in exit()
Similar bug #1053444 with 144 people affected.

No workaround or any other suggestions that I could see.

Might have to do another install Beta 2's coming up.

---

### Post by effenberg0x0 on 2012-09-24
+1 for not being able to select another DE using the mouse. Clicking over Gnome doesn't select it. But it's working with the tab key here.

Regards,
Effenberg

---

### Post by VinDSL on 2012-09-25
> **effenberg0x0 said:**
> +1 for not being able to select another DE using the mouse. Clicking over Gnome doesn't select it. But it's working with the tab key here.
Dittos!

I couldn't select GS for days (still can't with the mouse).  The workaround:

[LIST]
[*][Tab] though the choices until the "Gnome" box is highlighted
[*][Spacebar] to select "Gnome"
[*]Enter your password
[*]Bada bing, bada boom  :D
[/LIST]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-sep-2012-1.png")[/INDENT]

---

### Post by jerrylamos on 2012-09-25
amd64 I couldnt choose until today's update.  Then it worked.  Look at bug Bug #1053444 which might be relevant.

---

### Post by effenberg0x0 on 2012-09-25
> **VinDSL said:**
> Dittos!

I couldn't select GS for days (still can't with the mouse).  The workaround:

[LIST]
[*][Tab] though the choices until the "Gnome" box is highlighted
[*][Spacebar] to select "Gnome"
[*]Enter your password
[*]Bada bing, bada boom  :D
[/LIST]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-sep-2012-1.png")[/INDENT]

Exactly... And btw I'm still amazed by your desktops, as usual :)
VinDSL, why don't you approach the design people, submit stuff like wallpapers, themes, icons, etc? 

Regards,
Effenberg

---

### Post by VinDSL on 2012-09-25
> **jerrylamos said:**
> amd64 I couldnt choose until today's update.  Then it worked.  Look at bug Bug #1053444 which might be relevant.
Interesting!

I checked for upgrades an hour or so ago, and Synaptic didn't find anything.

Based on your post, I checked again.  Now, it wants to remove gnome-shell & gnome-shell-extensions.

Bwahahahaha!  I don't think so...  :D

Maybe a case of bad timing?!?!??

Heh!  I'll check again in a few hours.

---

### Post by VinDSL on 2012-09-25
> **effenberg0x0 said:**
> Exactly... And btw I'm still amazed by your desktops, as usual :)
Thanks, Effenberg!

---

### Post by mc4man on 2012-09-25
> **jerrylamos said:**
> amd64 I couldnt choose until today's update.  Then it worked.  Look at bug Bug #1053444 which might be relevant.
Not sure what that has to do with the unity-greeter (& no fix released there yet anyway, only commited
[https://bugs.launchpad.net/online-accounts-signon-ui/+bug/1053444](https://bugs.launchpad.net/online-accounts-signon-ui/+bug/1053444)

Anyway there is a fix for the current greeter bug, just not released yet
[https://bugs.launchpad.net/unity-greeter/+bug/1052453](https://bugs.launchpad.net/unity-greeter/+bug/1052453)

Vin- the issue with the repo GS is mutter has gone to 3.6 but GS is still at 3.5.92, should resolve in due course

---

### Post by VinDSL on 2012-09-25
> **mc4man said:**
> Vin- the issue with the repo GS is mutter has gone to 3.6 but GS is still at 3.5.92, should resolve in due course
Thanks!  I just noticed that.

I went ahead and did a "Default Upgrade", instead of a "Smart Upgrade".  The only thing that remained, were three mutter 3.6 upgrades, as you said.

I'm going to do a restart now and see if the upgrades, that I did perform, affected the greeter.

I don't know why they would, but you never know...  ;)

---

### Post by VinDSL on 2012-09-25
Nope!  Still have to use the [Tab] trick.

As an aside, I've never been a GS fanboi.  Historically, I just use it to manipulate Unity, but...

I'm really starting to like Gnome-Shell.  IMO, they've greatly improved it, the past few weeks.

---

### Post by VinDSL on 2012-09-25
Got tired of waiting and enabled the Ricotz Testing PPA.

Didn't fix the "non-unity session" greeter problem, of course, but the 3.6 upgrades went smoothly. :D

```
Commit Log for Tue Sep 25 19:41:53 2012

Upgraded the following packages:
gir1.2-clutter-1.0 (1.11.16-0ubuntu1) to 1.12.0-0ubuntu1~12.10~ricotz0
gir1.2-cogl-1.0 (1.10.4-0ubuntu1) to 1.10.5+git20120907.458c7ce9-0ubuntu1~12.10~ricotz0
gir1.2-coglpango-1.0 (1.10.4-0ubuntu1) to 1.10.5+git20120907.458c7ce9-0ubuntu1~12.10~ricotz0
gir1.2-freedesktop (1.33.10-1build1) to 1.34.0-0ubuntu1~12.10~ricotz0
gir1.2-gdesktopenums-3.0 (3.5.92-0ubuntu2) to 3.6.0-0ubuntu1~12.10~ricotz0
gir1.2-glib-2.0 (1.33.10-1build1) to 1.34.0-0ubuntu1~12.10~ricotz0
gir1.2-mutter-3.0 (3.5.92-0ubuntu1) to 3.6.0-0ubuntu1
gir1.2-rb-3.0 (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
gir1.2-totem-1.0 (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3
gjs (1.33.10-0ubuntu1) to 1.34.0-0ubuntu1~12.10~ricotz0
gnome-accessibility-themes (3.5.91-0ubuntu1) to 3.5.91+git20120914.88a2651d-0ubuntu1~12.10~ricotz1
gnome-shell (3.5.92-0ubuntu2) to 3.6.0-0ubuntu1~12.10~ricotz0
gnome-shell-common (3.5.92-0ubuntu2) to 3.6.0-0ubuntu1~12.10~ricotz0
gnome-shell-extensions (3.5.91-0ubuntu1) to 3.6.0~git20120922.e0518f0b-0ubuntu1~12.10~ricotz0
gnome-themes-standard (3.5.91-0ubuntu1) to 3.5.91+git20120914.88a2651d-0ubuntu1~12.10~ricotz1
gnome-tweak-tool (3.5.5-0ubuntu1) to 3.5.5+git20120813.e382b795-0ubuntu1~12.10~ricotz0
gsettings-desktop-schemas (3.5.92-0ubuntu2) to 3.6.0-0ubuntu1~12.10~ricotz0
libclutter-1.0-0 (1.11.16-0ubuntu1) to 1.12.0-0ubuntu1~12.10~ricotz0
libclutter-1.0-common (1.11.16-0ubuntu1) to 1.12.0-0ubuntu1~12.10~ricotz0
libcogl-common (1.10.4-0ubuntu1) to 1.10.5+git20120907.458c7ce9-0ubuntu1~12.10~ricotz0
libcogl-pango0 (1.10.5+git20120828.499784f4-0ubuntu1~12.10~ricotz0) to 1.10.5+git20120907.458c7ce9-0ubuntu1~12.10~ricotz0
libcogl9 (1.10.5+git20120828.499784f4-0ubuntu1~12.10~ricotz0) to 1.10.5+git20120907.458c7ce9-0ubuntu1~12.10~ricotz0
libgirepository-1.0-1 (1.33.10-1build1) to 1.34.0-0ubuntu1~12.10~ricotz0
libgjs0c (1.33.10-0ubuntu1) to 1.34.0-0ubuntu1~12.10~ricotz0
libglib2.0-0 (2.33.14-1) to 2.34.0-0ubuntu1~12.10~ricotz1
libglib2.0-bin (2.33.14-1) to 2.34.0-0ubuntu1~12.10~ricotz1
libglib2.0-data (2.33.14-1) to 2.34.0-0ubuntu1~12.10~ricotz1
libglib2.0-dev (2.33.14-1) to 2.34.0-0ubuntu1~12.10~ricotz1
libglib2.0-doc (2.33.14-1) to 2.34.0-0ubuntu1~12.10~ricotz1
libmutter0 (3.5.92-0ubuntu1) to 3.6.0-0ubuntu1
librhythmbox-core6 (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
libtotem0 (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3
mutter-common (3.5.92-0ubuntu1) to 3.6.0-0ubuntu1
rhythmbox (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
rhythmbox-data (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
rhythmbox-mozilla (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
rhythmbox-plugin-cdrecorder (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
rhythmbox-plugin-zeitgeist (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
rhythmbox-plugins (2.97-1ubuntu5) to 2.97+git20120924.380f4840-0ubuntu1~12.10~ricotz0
totem (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3
totem-common (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3
totem-mozilla (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3
totem-plugins (3.4.3-0ubuntu4) to 3.5.90-0ubuntu1~12.10~ricotz3

```

Gotta say... GS is flying now!

---

### Post by VinDSL on 2012-10-07
_UPDATE_

Haven't logged into GS in a few days, but the "chooser" for alternatives is now working...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-oct-2012-1.png")[/INDENT]


GS is looking foxier than ever, too...

Not sure which package upgrade did the trick.  There have been literally 100's of upgrades, since I posted last.

Anyway, all's well that ends well!  ;)

---

