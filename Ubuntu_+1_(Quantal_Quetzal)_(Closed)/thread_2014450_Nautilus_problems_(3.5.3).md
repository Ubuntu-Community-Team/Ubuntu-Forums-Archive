---
title: "Nautilus problems (3.5.3)"
date: 2012-07-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-07-02
Well after upgrading to nautilus_3.5.3-0ubuntu1 I have had severe problems with nautilus and especially calling "gksu nautilus".

Sometimes the desktop icons (like packages) disappear.  Sometimes nautilus just crash.
Calling gksu nautilus is even worse experience.
Desktop icons almost never show up.
Then, if I try to click on any folder, nautilus hangs forever.

All this works well with the natilus version 3.5.2-0obuntu3.

:guitar:

---

### Post by dino99 on 2012-07-02
i've got the same issues, so now i use ricotz/testing gtk3 packages and have less trouble, only crash

---

### Post by ventrical on 2012-07-02
Same here and I reported this:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995)

If it describes your bug then please feel free to click on it.

---

### Post by dino99 on 2012-07-02
> **ventrical said:**
> Same here and I reported this:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995)

If it describes your bug then please feel free to click on it.

nautilus is not meant to be used under gksu  :p

---

### Post by mdurham on 2012-07-02
> **dino99 said:**
> nautilus is not meant to be used under gksu  :p

Why not?

---

### Post by philinux on 2012-07-02
> **mdurham said:**
> Why not?

See the bug report for an explanation.

 [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995)

---

### Post by dino99 on 2012-07-02
> **mdurham said:**
> Why not?

dev said

---

### Post by Morbius1 on 2012-07-02
> philinux (philcb) wrote 53 minutes ago:     #5

Ah. No disrespect intended but we've all been lucky for 5 years or more without issue. Is this a gnome 3 gtk3 problem. Could you explain what would happen of we got unlucky. Thanks.

Also what is the alternative to gksu nautilus.Now there's an aspect of successfully running software I've never considered: Luck.

Until the Gnome3 developers graduate from their gtk3 course you might consider:
```
gksu thunar
```
You'll need thunar anyway to create a custom file association.

---

### Post by mc4man on 2012-07-02
> **philinux said:**
> See the bug report for an explanation.

 [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1019995)

The ask ubuntu deal about file recovery, ect,  just to  note that if you create & log in to a new user in the live session with the same name as the user whose files are to be recovered then you'll get full access (to that user's files
(- that's the preferred way to copy out when recovering from an encrypted but could be used if gksudo nautilus isn't viable

---

### Post by philinux on 2012-07-02
> **mc4man said:**
> The ask ubuntu deal about file recovery, ect,  just to  note that if you create & log in to a new user in the live session with the same name as the user whose files are to be recovered then you'll get full access (to that user's files
(- that's the preferred way to copy out when recovering from an encrypted but could be used if gksudo nautilus isn't viable

Fascinating. Learn something new every day. Never heard that one. ;)

---

### Post by ronacc on 2012-07-02
at what point do the workarounds , put up withs , and make do's get piled so deep that Ubuntu is no longer worth the PITA that it takes to use it . It is not like we gain anything useful from this crap they keep piling on , only our blood pressure cranked up another few notches .

---

### Post by xebian on 2012-07-02
> **ronacc said:**
> at what point do the workarounds , put up withs , and make do's get piled so deep that Ubuntu is no longer worth the PITA that it takes to use it . It is not like we gain anything useful from this crap they keep piling on , only our blood pressure cranked up another few notches .

It's still in development so it's expected.  If you are not happy with it then demand a refund.

---

### Post by Morbius1 on 2012-07-02
You know that brings up an interesting point. 12.10 is considered alpha level software and Nautilus because it's an odd numbered point release is considered experimental:
> GNOME 3.5.x is an unstable development series intended for testing and hacking purposes. GNOME uses odd minor version numbers to indicate development status, so this unstable 3.5.x series will become the official 3.6 stable release. Let's face it the only safe place to install 12.10 is in VirtualBox.

Now let's all find a thread about Nautilus 3.4.2 where we can all legitimately trash that one for it's lack of functionality ;)

---

### Post by mc4man on 2012-07-02
> **Harry33 said:**
> Well after upgrading to nautilus_3.5.3-0ubuntu1 I have had severe problems with nautilus and especially calling "gksu nautilus".

Sometimes the desktop icons (like packages) disappear.  Sometimes nautilus just crash.
Calling gksu nautilus is even worse experience.
Desktop icons almost never show up.
Then, if I try to click on any folder, nautilus hangs forever.

All this works well with the natilus version 3.5.2-0obuntu3.

:guitar:
You may be seeing this bug which seems to be affecting more users lately. 
(here it happens all the time so am glad to see a wider affected, nautilus is unusable atm here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018896](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018896)

---

### Post by ronacc on 2012-07-02
> **xebian said:**
> It's still in development so it's expected.  If you are not happy with it then demand a refund.

I was not just referring to the current nautilus problem but also to the ongoing loss of functionality not all or even most of which is related to bugs . And when I decide a refund is due I will issue one to myself since as the "consumer" I am the boss .

---

### Post by VinDSL on 2012-07-02
> **Harry33 said:**
> Well after upgrading to nautilus_3.5.3-0ubuntu1 I have had severe problems with nautilus [...]
I don't know what I'm doing "wrong", but...

I keep waiting for Nautilus to pack it in, on my install(s), but so far it's still working on Unity, GS, et cetera.

Here it is, for instance, in my current session (LXDE/Openbox/UbuQQ):


[INDENT][[IMG]http://vindsl.com/images/vindsl-nautilus-2-jul-2012-1(650x659).png[/IMG]]("http://vindsl.com/images/vindsl-nautilus-2-jul-2012-1.png")[/INDENT]


Only continuing problem I've experienced is, Nautilus won't search hidden folders...

---

### Post by ronacc on 2012-07-02
on my sys it is not just nautilus 3.5.3 that is having problems it is jaut about everything to do with the 3.5 kernel including the kernel its self . nautilus and other things like gedit crash for random and inconsistant reasons , apport either can't report the crashes for assorted reasons or else screws up the report if it can be coaxed into actually making one . kernel panics at random times for random often un sprcified reasons ,these problems occur (not always the same ones but similar ) on my updated from precise install  occured on my A1 install after upgrading to the 3.5.0-1 generic, occured on my A1 install after upgrading to the 3.5.0-1 generic occured on my A2 install starting with first boot since it started out with the 3.5.0-2 generic kernel .

NOTE ! it is not my box or hardware . all on the same box 2 installs of Sabayon 1 each of Suse and debian (sid ) and also quantal when booted into one of the 3.4 generic kernels ( yes I keep ALL my kernels during development ) . do not exhibit any of these problems .

---

### Post by ventrical on 2012-07-02
> **VinDSL said:**
> I don't know what I'm doing "wrong", but...

I keep waiting for Nautilus to pack it in, on my install(s), but so far it's still working on Unity, GS, et cetera.

Here it is, for instance, in my current session (LXDE/Openbox/UbuQQ):

[INDENT][[IMG]http://vindsl.com/images/vindsl-nautilus-2-jul-2012-1%28650x659%29.png[/IMG]]("http://vindsl.com/images/vindsl-nautilus-2-jul-2012-1.png")[/INDENT]
Only continuing problem I've experienced is, Nautilus won't search hidden folders...


Hi Vin,

Try: 

gksu nautulis

in terminal.

---

### Post by VinDSL on 2012-07-02
> **ventrical said:**
> Hi Vin,

Try: 

gksu nautulis

in terminal.
Aha!  That's what I was doing "wrong".

Epic FAIL!  Totally exploded my desktop, it did!

Er.  Excuse me while I reboot and fix the damage.  LoL!  :D


**EDIT**


Okay, fine!  All fixed (desktop).

I won't be doing that again, any time soon...  :)

---

### Post by philinux on 2012-07-02
> **ronacc said:**
> i was not just referring to the current nautilus problem but also to the ongoing loss of functionality not all or even most of which is related to bugs . And when i decide a refund is due i will issue one to myself since as the "consumer" i am the boss .

+1 and thanks for the restraint. I think I might have had to count to ten before posting too.

---

### Post by mc4man on 2012-07-02
> **VinDSL said:**
> I don't know what I'm doing "wrong", but...

I keep waiting for Nautilus to pack it in, on my install(s), but so far it's still working on Unity, GS, 

Have to ask - are you using the current gtk-3-0 from Ubuntu repos?
(3.5.6-0ubuntu2

---

### Post by VinDSL on 2012-07-02
> **mc4man said:**
> Have to ask - are you using the current gtk-3-0 from Ubuntu repos?
(3.5.6-0ubuntu2
Yeppers...
```
vindsl@Zuul:~$ dpkg -l libgtk-[0-9]* | grep ^i
ii  libgtk-3-0:i386                                3.5.6-0ubuntu2                                                      GTK+ graphical user interface library
ii  libgtk-3-bin                                   3.5.6-0ubuntu2                                                      programs for the GTK+ graphical user interface library
ii  libgtk-3-common                                3.5.6-0ubuntu2                                                      common files for the GTK+ graphical user interface library

```

Plus...
```
vindsl@Zuul:~$ dpkg -l libgtk[0-9]* | grep ^i
ii  libgtk2-perl                                   2:1.244-1                                                           Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:i386                               2.24.10-0ubuntu6                                                    GTK+ graphical user interface library
ii  libgtk2.0-bin                                  2.24.10-0ubuntu6                                                    programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                  2.12.10-4                                                           CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                               2.24.10-0ubuntu6                                                    common files for the GTK+ graphical user interface library

```

---

### Post by ventrical on 2012-07-03
I went into a Marveric Meerkat install and <gksu nautilus> works beautifully. I was just experimenting. Still non-responsive with quantal.

---

### Post by stoneguy on 2012-07-03
For me, it's not gksu nautilus. It's any invocation of nautilus. I'm still sticking to Classic no effects, and when I click on Places, it's hard to predict how the window contents are going to display or react. If there was anything consistent enough to reproduce, I'd happily file a launchpad report. But this time I think I'll just sit it out for awhile and come back when things improve. When things are this borked, the devs shouldn't take long to notice.

For the old-timers, you can always install emelfm2. Not a thing of beauty, but mostly gets the job done.

---

### Post by VinDSL on 2012-07-03
> **stoneguy said:**
> For me, it's not gksu nautilus[...]

For the old-timers, you can always install emelfm2. Not a thing of beauty, but mostly gets the job done.
Tell ya what...

I've been using PCManFM a lot lately. Their Wiki says it's "meant to be a replacement for Nautilus, Konqueror and Thunar".

PCManFM looks just as good as Nautilus (sometimes I forget which one I'm using).

If this keeps up, I'm going to purge Nautilus, in favor of it...

---

### Post by Harry33 on 2012-07-04
> **VinDSL said:**
> Tell ya what...

I've been using PCManFM a lot lately. Their Wiki says it's "meant to be a replacement for Nautilus, Konqueror and Thunar".

PCManFM looks just as good as Nautilus (sometimes I forget which one I'm using).

If this keeps up, I'm going to purge Nautilus, in favor of it...

Package Nautilus can be purged, but
removing nautilus-data would remove gnome-session, gnome-shell, gnome-control-center and gnome-power-manger too; and
removing libnautilus-extension1a would remove evince and file-roller too.

---

### Post by ventrical on 2012-07-04
A strange thing .. it seems that Naulilus is getting progressively worse. 4 in the morning here and haven't updated and it's really very buggy. And whatever is the matter with it, apport seems to be sleeping.

---

### Post by ventrical on 2012-07-04
These updates have seemed to create a dramatic fix .. however I did not see no commit.
```

Upgraded the following packages:
base-files (6.5ubuntu7) to 6.5ubuntu8
bluez (4.99-2ubuntu2) to 4.101-0ubuntu1
bluez-alsa (4.99-2ubuntu2) to 4.101-0ubuntu1
bluez-cups (4.99-2ubuntu2) to 4.101-0ubuntu1
bluez-gstreamer (4.99-2ubuntu2) to 4.101-0ubuntu1
debianutils (4.2.1ubuntu2) to 4.3.2
empathy (3.5.2-0ubuntu1) to 3.5.3-0ubuntu1
empathy-common (3.5.2-0ubuntu1) to 3.5.3-0ubuntu1
evolution-data-server (3.4.3-1) to 3.5.3.1-0ubuntu1
evolution-data-server-common (3.4.3-1) to 3.5.3.1-0ubuntu1
fglrx (2:8.960-0ubuntu4) to 2:8.960-0ubuntu5
fglrx-amdcccle (2:8.960-0ubuntu4) to 2:8.960-0ubuntu5
folks-common (0.6.9-1build1) to 0.7.2.2-0ubuntu1
gir1.2-folks-0.6 (0.6.9-1build1) to 0.7.2.2-0ubuntu1
ifupdown (0.7~rc2+experimentalubuntu2) to 0.7.1ubuntu1
isc-dhcp-client (4.1.ESV-R4-0ubuntu8) to 4.2.4-1ubuntu2
isc-dhcp-common (4.1.ESV-R4-0ubuntu8) to 4.2.4-1ubuntu2
libatk-adaptor (2.5.3-0ubuntu1) to 2.5.3-1
libatk-adaptor-data (2.5.3-0ubuntu1) to 2.5.3-1
libatk-bridge2.0-0 (2.5.3-0ubuntu1) to 2.5.3-1
libatk-bridge2.0-dev (2.5.3-0ubuntu1) to 2.5.3-1
libbluetooth3 (4.99-2ubuntu2) to 4.101-0ubuntu1
libfolks-eds25 (0.6.9-1build1) to 0.7.2.2-0ubuntu1
libfolks-telepathy25 (0.6.9-1build1) to 0.7.2.2-0ubuntu1
libfolks25 (0.6.9-1build1) to 0.7.2.2-0ubuntu1
libssl1.0.0 (1.0.1-4ubuntu6) to 1.0.1c-3ubuntu1
mobile-broadband-provider-info (20120410-0ubuntu1) to 20120614-0ubuntu1
nautilus-sendto-empathy (3.5.2-0ubuntu1) to 3.5.3-0ubuntu1
netbase (4.47ubuntu1) to 5.0ubuntu1
openssl (1.0.1-4ubuntu6) to 1.0.1c-3ubuntu1
python-pam (0.4.2-12.2ubuntu6) to 0.4.2-13ubuntu2
python-pyatspi2 (2.5.3+dfsg-0ubuntu1) to 2.5.3+dfsg-1
python3-pyatspi2 (2.5.3+dfsg-0ubuntu1) to 2.5.3+dfsg-1
resolvconf (1.65ubuntu4) to 1.67ubuntu1
xdiagnose (2.8) to 2.9
xserver-xorg-input-wacom (1:0.14.0-0ubuntu2) to 1:0.14.0-0ubuntu3
xul-ext-ubufox (2.2~r328-0ubuntu1) to 2.2-0ubuntu1

```

---

### Post by dino99 on 2012-07-04
What is a "dramatic fix" ? Are your custom breakages lost ?  :lolflag:

---

### Post by ventrical on 2012-07-04
Nautilus is working normally now - it appears.

err.. I'll reboot now :)

edit:

Ok , but not with gksu in terminal.

---

### Post by dino99 on 2012-07-04
> **ventrical said:**
> 

Ok , but not with gksu in terminal.

if you have followed the whole thread, then you have seen my previous answer:

nautilus is not meant to be used under gksu
(nautilus dev answer)

---

### Post by ventrical on 2012-07-04
> **dino99 said:**
> if you have followed the whole thread, then you have seen my previous answer:

nautilus is not meant to be used under gksu
(nautilus dev answer)

I already know this dino99!

The problem is not with gksu per se. Naultilus *was* dysfunctional  from Unity desktop. I thought I made that clear.

---

### Post by VinDSL on 2012-07-04
> **Harry33 said:**
> Package Nautilus can be purged, but
removing nautilus-data would remove gnome-session, gnome-shell, gnome-control-center and gnome-power-manger too; and
removing libnautilus-extension1a would remove evince and file-roller too.
Yes, you're right.  I should have stated that a different way, e.g. used a different term.

I didn't mean "purge" in a catholic sense...

The better way would be to leave Nautilus intact, but purge its usage.

I saw a hack, a while back, that replaces all of the Nautilus calls in Ubuntu with PCManFM -- by editing various config files, and so forth, and so on...  ;)

---

### Post by philinux on 2012-07-04
Looks like nautilus in a state of flux/improvement.

 [http://iloveubuntu.net/nautilus-finally-receives-full-state-toolbar-monochrome-icons-and-polished-look](http://iloveubuntu.net/nautilus-finally-receives-full-state-toolbar-monochrome-icons-and-polished-look)

---

### Post by mc4man on 2012-07-04
> **philinux said:**
> Looks like nautilus in a state of flux/improvement.

 [http://iloveubuntu.net/nautilus-finally-receives-full-state-toolbar-monochrome-icons-and-polished-look](http://iloveubuntu.net/nautilus-finally-receives-full-state-toolbar-monochrome-icons-and-polished-look)

giving it a quick try here without any Ubuntu patches, guess it'll be ok though here though may have  to rethink dark sidebar 
Wonder how it will go with the Radiance theme as far as mono icons
(and there obviously was no reconsideration of an up button (parent), will have to take a look..

Crashes here just the same as the current naut

Edit: - with Radiance, think the buttons look better here than Ambiance

ATM or foreseeable? there is no "go", so don't see any way to go up, Alt+up does nothing

---

### Post by VinDSL on 2012-07-04
w00t!  Screenie time...  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-pcmanfm-4-jul-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-pcmanfm-4-jul-2012-1.png")[/INDENT]


Pretty good Nautilus knock-off, eh ehat?!?!?

IMO, the only thing Nautilus **[COLOR="DarkRed"]had[/COLOR]** going for it was the dual-pane feature...

---

### Post by mc4man on 2012-07-04
Well certainly shouldn't make judgments on a git clone installed straight up but as seen not too thrilling.
Will be interesting to see what shakes down if Ubuntu uses this & any additional changes, good or bad.
Atm 
ambiance looks poor
continuing issue of lack of an application menu in unity for nautilus
basically no menus in the git anyway, all in cog
no parent option
[open with on folders removed!]("http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16061") (atm easy to restore
keyboard shortcuts & user set accels ?? 
small stuff like default misalignment of location & sidebar
ect.

---

### Post by ventrical on 2012-07-05
> **VinDSL said:**
> w00t!  Screenie time...  :D

[INDENT][[IMG]http://vindsl.com/images/vindsl-pcmanfm-4-jul-2012-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-pcmanfm-4-jul-2012-1.png")[/INDENT]
Pretty good Nautilus knock-off, eh ehat?!?!?

IMO, the only thing Nautilus **[COLOR=DarkRed]had[/COLOR]** going for it was the dual-pane feature...

@vindsl,

Isn't that the Lubuntu Desktop?

---

### Post by ventrical on 2012-07-05
Thunar works  in Unity 3D with gksu and even provides a warning bar!

---

### Post by VinDSL on 2012-07-05
> **ventrical said:**
> @vindsl,

Isn't that the Lubuntu Desktop?
No, it's LXDE/Openbox running on top of Ubuntu 12.10 3D alpha 2.

I'm rolling my own, right now... Vinbuntu, if you will.    :D

I haven't run Lubuntu, so called, since the early days of 12.04 testing, nor Unity since alpha 1.

Hopefully, we've been friends long enough to know I wouldn't BS you.

For everyone else (kinda hard to wrap your mind around, I know)...  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-5-jul-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-jul-2012-1.png")[/INDENT]

---

### Post by ventrical on 2012-07-06
@VinDSL,

I hear you.  I have had some of those roll your owns also. LXDE  is a good one to experiment with.  It's just that you build your desktops  with such style and perspective that it is hard to tell  just exactly what you  are  doing! :) lol

---

### Post by Harry33 on 2012-07-07
I chose to use the newer Ricotz git version of Nautilus 3.5.3.
I guess gksu is out, so I use (in terminal) from now on
```
sudo -s

```
And then
```
nautilus

```

---

### Post by jbicha on 2012-07-09
The Nautilus developers discourage running Nautilus as root. It doesn't matter when you use gksu, su, or pkexec to do it.

---

### Post by Harry33 on 2012-07-10
> **jbicha said:**
> The Nautilus developers discourage running Nautilus as root. It doesn't matter when you use gksu, su, or pkexec to do it.

That is not the point here, however.
With "gksu nautilus" or "sudo nautilus", this nautilus as root will hang and does not work.
I can workaround it by calling sudo -s first (root).
Then starting nautilus works.

I do know what I am doing when using nautilus as root.

---

### Post by Morbius1 on 2012-07-10
> **jbicha said:**
> The Nautilus developers discourage running Nautilus as root. It doesn't matter when you use gksu, su, or pkexec to do it.
> **Harry33 said:**
> That is not the point here, however.
With "gksu nautilus" or "sudo nautilus", this nautilus as root will hang and does not work.
I can workaround it by calling sudo -s first (root).
Then starting nautilus works.

I do know what I am doing when using nautilus as root.
I don't think that jbicha was implying that the developers thought [COLOR=Blue]**you **[/COLOR]didn't know what [COLOR=Blue]**you**[/COLOR] were doing when using nautilus as root:

From: [https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)
> Matthias Clasen                             [developer]                                                              2011-07-08 20:10:17 UTC                    

You shouldn't run nautilus as root. [COLOR=Black]Whats [COLOR=Blue]**probably**[/COLOR] happening here is that not only is nautilus getting started, but also a session bus for root, and diverse session services, etc etc.[/COLOR]The use of the word "probably" in the above quote is somewhat disturbing since it's coming from one of the developers. Gnome should never have fired the Gnome2 developers to make way for the Gnome3 developers.

---

### Post by ronacc on 2012-07-10
> **jbicha said:**
> The Nautilus developers discourage running Nautilus as root. It doesn't matter when you use gksu, su, or pkexec to do it.

neither the Nautilus developers , nor any other developers have the right to tell me how I will use my computer , they are not my nanny .

---

### Post by Morbius1 on 2012-07-10
> **ronacc said:**
> neither the Nautilus developers , nor any other developers have the right to tell me how I will use my computer , they are not my nanny .
That's the difference between Gnome development and real world development. If the developers in real world product development don't know how their software works and can't figure out how to fix a bug the feature that causes the bug is removed and goes to software heaven.

Gnome isn't saying: Thou shalt not use Nautilus as root. They are saying I wouldn't do it if it was me. If Gnome really wanted to be dictatorial about this a "gksu nautilus" would result in an error message and would not run.

---

### Post by Superpelican12 on 2012-07-10
I have no problems running Nautilus as root (Ubuntu 12.04 LTS 64bit). I done it several times with just:
```
sudo nautilus
```
or
```
gksu nautilus
```
Nothing more than that. It doesn't hang.

EDIT:
Sorry I didn't see this was the Quantal Quetzal thread. And therefore my response is completely useless, as I'm using Nautilus 3.4.2...

Sorry for this useless response

---

### Post by ronacc on 2012-07-10
> **Morbius1 said:**
> That's the difference between Gnome development and real world development. If the developers in real world product development don't know how their software works and can't figure out how to fix a bug the feature that causes the bug is removed and goes to software heaven.

Gnome isn't saying: Thou shalt not use Nautilus as root. They are saying I wouldn't do it if it was me. If Gnome really wanted to be dictatorial about this a "gksu nautilus" would result in an error message and would not run.

and I would therefore be running something other than gnome . If they wanted to let us know that it might be unwise to run nautilus as root they could issue a warning as many other apps do , not result in aberrant behavior .

---

### Post by ventrical on 2012-07-10
> **ronacc said:**
> and I would therefore be running something other than gnome . If they wanted to let us know that it might be unwise to run nautilus as root they could issue a warning as many other apps do , not result in aberrant behavior .


As I posted earlier. Thunar file manager DOES report that the root system is being used and and that your system may get broke (when runing gksu thunar).

 As pointed out a few messages above.. I agree that if the devs really do not want us to use Nautilus in root then they should put a flag in there somewhat like Thunar has.

---

### Post by mc4man on 2012-07-10
Now that I've found a workaround to the almost constant crashes of a normal nautilus as seen here have had a chance to see what a root nautilus brings.

While overall opening nautilus from a root terminal is ok for now the host of GTK criticals certainly lend to idea not worth doing. And after a while it also fails to open
Add to that that Nautilus doesn't support a root browser, will not take root browsing into account as the code advances & won't accept any bugs against,  it isn't worth using.

So here have simply added pcmanfm & created a new .desktop just for root file managing

(- for the moment still prefer nautilus for user browsing, though the upcoming nautilus 3.6 may change that, at least in an ubuntu session where the new nautilus will present unity with further issues to resolve if 12.10 goes to 3.6

The removal of open with on dir.'s will be something I'll revert locally if nautilus doesn't reconsider such nonsense

Simply done like this, am using folder.png to diff from nautilus where I use 'user-home' icon

```
[Desktop Entry]
Type=Application
Icon=folder
Name=Root File Manager
Categories=FileManager;Utility;Core;GTK;
Exec=gksu "pcmanfm /" %U
StartupNotify=true
MimeType=x-directory/normal;inode/directory; 
```

For Unity have just added the .desktop to launcher, also it is available from the nautilus context menu for the moment as the current nautilus still allows open with on dir.'s

Edit:
for unity use have added a couple of quicklist entries to go directly to some dir.'s from launcher,

```
[Desktop Entry]
Type=Application
Icon=folder
Name=Root File Manager
Categories=FileManager;Utility;Core;GTK;
Exec=gksu "pcmanfm /" %U
StartupNotify=true
MimeType=x-directory/normal;inode/directory; 
Actions=Share;Etc;Var;

[Desktop Action Share]
Name=Share
Exec=gksu "pcmanfm /usr/share"
TargetEnvironment=Unity

[Desktop Action Etc]
Name=Etc
Exec=gksu "pcmanfm /etc"
TargetEnvironment=Unity

[Desktop Action Var]
Name=Var
Exec=gksu "pcmanfm /var"
TargetEnvironment=Unity
```

---

### Post by Morbius1 on 2012-07-10
OK, so that takes care of a root nautilus. 

But then we have to install leafpad and use "gksu leafpad" because of a bug and the same argument with a "gksu gedit": [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404)
> Quote comment from upstream developer:
< You shouldn't start GNOME programmes with elevated privileges, it's not supported.It's not just nautilus it's any gnome application with a gui.

---

### Post by mc4man on 2012-07-10
> **Morbius1 said:**
> OK, so that takes care of a root nautilus. 

But then we have to install leafpad and use "gksu leafpad" because of a bug and the same argument with a "gksu gedit": [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404)
It's not just nautilus it's any gnome application with a gui.

As I mentioned in the [earlier longstanding bug I filed on this]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076") that one could consider just running 
sudo gedit
or just gedit from a root terminal
(a root terminal .desktop is still installed by default in /usr/share/applications. It has a line - NoDisplay=true so it doesn't show in Dash, ect.

Now while things always can change, I've yet, to date, had anyone offer _specific proof that sudo gedit _is an issue

---

### Post by ronacc on 2012-07-10
one gripe I have always had with gksu nautilus was that even when it was fully functional ( pre quantal ) child processes launched from it did not inherit root status eg "open with"  .

---

### Post by jfernyhough on 2012-07-10
This may have been tried but I haven't read it anywhere yet. When I need to I always run 
$ gksudo 'nautilus --no-desktop' 
to avoid nautilus starting up all its extra crap and just give me a window.

I'm getting a bit tired of Nautilus crashing for my user, though, so I'm going to have to try PCManFM. :D

Hmm... it doesn't show some mounted volumes, e.g. those from cryptkeeper.

---

### Post by mc4man on 2012-07-10
> **jfernyhough said:**
> 

I'm getting a bit tired of Nautilus crashing for my user, though, so I'm going to have to try PCManFM. :D

Here nautilus would crash with every other use, likely this is more than what most people were seeing with nautilus crashes related to this bug
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018896](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018896)

That made using 12.10 with nautilus impossible as shown in vid I attached in comment 11

I've since gotten it down to only 2 isolated crashes in the last 6 hrs. but to do so had to disable allowing the FM to handle the Desktop which isn't a fix here but does allow use. 
(I could get used to it but not sure Unity can..

---

### Post by jfernyhough on 2012-07-10
Hmmm...
$ pcmanfm --desktop
gives a fairly nice result. But how to get GNOME3 to use PCManFM instead of Nautilus?

I've turned off "Have file manager handle the desktop" in gnome-tweak, it insists on using nautilus. Also, nautilus feels far more responsive without the desktop. :D

--edit
Oh, I think I might have done that. Right-click on a directory using PCManFM, Open With..., Accessories, File Manager. Check "Set selected application as default..." Now with "Have file manager handle..." enabled nautilus doesn't load a desktop. Nice.

I also **love** having the option to open files with whichever program I want, not what nautilus deems to show me.

---

### Post by mc4man on 2012-07-11
Another alt. to using nautilus in general but pcmanfm for root browsing is to create a nautilus action for context menu
Path - gksu
Parameters - pcmanfm %f
Working Directory %d
Mimetypes -  inode/directory

---

### Post by philinux on 2012-07-11
Been poking around. Giving Marlin a go.

It has an option "New window as Root".

[http://iloveubuntu.net/marlin-updated-enhanced-quicklist-and-improved-highlighting-behavior](http://iloveubuntu.net/marlin-updated-enhanced-quicklist-and-improved-highlighting-behavior)

I really dislike this dumming down in nautilus. Notably removal of gksu-nautilus which really riled me.

ppa is precise only at the moment but no harm giving it a whirl as an Alt.

[edit] looks like they added QQ after the article was published. [https://launchpad.net/~marlin-devs/+archive/marlin-daily](https://launchpad.net/~marlin-devs/+archive/marlin-daily)

---

### Post by Morbius1 on 2012-07-11
Been doing some poking around and discovered that gksu is so yesterday. So I'm curious did anyone try it's replacement:
```
gksu-polkit nautilus
```From synaptic:
> This is the new generation of gksu, a simple utility to run programs as root, even in X-based environments. This version uses the new libgksu-polkit library, which uses PolicyKit for authorization purposes and a D-Bus service to actually perform the work.I should note that in synaptic there is not the little ubuntu icon next to the package which I always thought meant that ubuntu didn't support it. Don't know if that means it got into the repos from space aliens or what.

There's also a gnome explanation here: [https://live.gnome.org/gksu](https://live.gnome.org/gksu)

EDIT: I should also note that a "gksu-polkit gedit /etc/fstab" still produces an extra "unititled document 1" tab in gedit but maybe they'll fix that in 2.0.

---

### Post by jbicha on 2012-07-11
Well synaptic is in "universe" not "main" and is not officially supported by Canonical these days. Most software not installed by default is in universe though.

---

### Post by ronacc on 2012-07-11
> **philinux said:**
> Been poking around. Giving Marlin a go.

It has an option "New window as Root".

[http://iloveubuntu.net/marlin-updated-enhanced-quicklist-and-improved-highlighting-behavior](http://iloveubuntu.net/marlin-updated-enhanced-quicklist-and-improved-highlighting-behavior)

I really dislike this dumming down in nautilus. Notably removal of gksu-nautilus which really riled me.

ppa is precise only at the moment but no harm giving it a whirl as an Alt.

[edit] looks like they added QQ after the article was published. [https://launchpad.net/~marlin-devs/+archive/marlin-daily](https://launchpad.net/~marlin-devs/+archive/marlin-daily)


qq is not all there , marlin won't install on my QQ install , broken held packages .

---

### Post by mc4man on 2012-07-11
> **ronacc said:**
> qq is not all there , marlin won't install on my QQ install , broken held packages .
While whether advisable  or not - if you wanted marlin today in QQ
Download & install the ppa's PP package  (64 bit install 
extended-actions_0.1-0~5~precise1_amd64.deb 

Then if you've added the ppa for QQ Marlin should install
Have it installed here, seems like it has a ways to go though in the past those devs have been receptive to users so that's a Big + for Marlin

---

### Post by ronacc on 2012-07-11
I did just that but for me marlin starts and then fails with an unknown symbol lookup error in vala , it looks like tha precise extra actions don't like the current Quantal vala , looking at the ppa there were 22 package build failures for extra actions on quantal . I'll keep trying they'll get it sorted eventually . Quantal is turning out to be a great exercise in patience for me :lolflag:

---

### Post by mc4man on 2012-07-12
> **ronacc said:**
> I did just that but for me marlin starts and then fails with an unknown symbol lookup error in vala , it looks like tha precise extra actions don't like the current Quantal vala , looking at the ppa there were 22 package build failures for extra actions on quantal . I'll keep trying they'll get it sorted eventually . Quantal is turning out to be a great exercise in patience for me :lolflag:

The mysteries of 12.10 - Marlin works ok here, had only 2 crashes yesterday related to cairo, otherwise is ok (sorta - the < > ^ & menu buttons are a bit dim on ambiance

Likely better to have an extra actions built for QQ - I didn't see any attempts to build ??

Tried 2 of the actions, compress & send by Email, both worked ok

It is possible to install without the extra - you'd extract the marlin .deb, delete the .deb,  open the Debian > control file in the extracted folder, remove extra-actions from the dep line & then repack the folder with as Ex.

dpkg -b /home/doug/Documents/fix/marlin_0.1-0~876~quantal1_amd64

Down the road if choosing an alt. to nautilus I'd probably go with Marlin over pcmanfm though it's close, am getting used to no Desktop which I believe is the case with Marlin

---

### Post by jerrylamos on 2012-07-12
> bicha: Well synaptic is in "universe" not "main" and is not officially supported by Canonical these days. Most software not installed by default is in universe though.

Hmmm.  When providing launchpad bug info I was asked to run apport-collect (bug number).  Apport collect requires launchpadlib which is not in Quantal as installed.  apt-get install couldn't find it, so I ran synaptic.  Does that mean Canonical doesn't support apport-collect since apport-collect depends on synaptic to install a lib apport-collect needs?

Jerry

---

