---
title: "daily update turns gdm orange/purple , not blue/gray"
date: 2017-09-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-09-05
Fresh install. 17.10
Install unity-session

Now GDM login box is  in ubuntu orange and not blue.

if I were to file a bug , what package would I file it against?

Regards..

---

### Post by Frogs Hair on 2017-09-05
My colors changed with yesterday's updates and this is a non unity installation.

---

### Post by ventrical on 2017-09-05
> **Frogs Hair said:**
> My colors changed with yesterday's updates and this is a non unity installation.

bwahahahaha .. it's the invasion of the  unity purple thingy :)

Thanks frogshair.

---

### Post by Frogs Hair on 2017-09-05
> **ventrical said:**
> bwahahahaha .. it's the invasion of the  unity purple thingy :)

Thanks frogshair.

It was gray at login and purple/orange after reboot.

---

### Post by ventrical on 2017-09-05
> **Frogs Hair said:**
> It was gray at login and purple/orange after reboot.

Yes.. I just see that now on my non-unity gnome install . I also noticed -setting up lightdm.

Is lightdm suppossed to be in there?

Regards..

---

### Post by Frogs Hair on 2017-09-05
I see nothing installed viewing synaptic. :confused:

---

### Post by ventrical on 2017-09-05
On this install I must of did something earlier in the cycle - but there is no unity on it.

Regards..

---

### Post by harry332 on 2017-09-05
This may not have anything to do with the package gdm.
I think this is where the theming changed:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.25.91-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-shell/3.25.91-0ubuntu3)

---

### Post by ventrical on 2017-09-05
> **harry332 said:**
> This may not have anything to do with the package gdm.
I think this is where the theming changed:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.25.91-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-shell/3.25.91-0ubuntu3)

Thanks harry. Nice find.

Regards..

---

### Post by jbicha on 2017-09-05
Please read Didier's recent [series of blog posts]("https://didrocks.fr/"). The new login screen theming is discussed in Day 9. In other words, it's clearly intentional from the Ubuntu Desktop team.

---

### Post by ventrical on 2017-09-05
> **jbicha said:**
> Please read Didier's recent [series of blog posts]("https://didrocks.fr/"). The new login screen theming is discussed in Day 9. In other words, it's clearly intentional from the Ubuntu Desktop team.

+1 :)

Regards..

---

### Post by harry332 on 2017-09-06
Jbicha,

Sure it is intentional.
However, this does not look nice at all, if one is using vanilla gnome, which means gnome-session:
1) ubuntu's red login screen with orange field, followed by
2) original black-beige themed gnome-shell desktop.

---

### Post by Chanath on 2017-09-06
Until a user installs User Themes extension, the default would stay, or are the devs planning to make that a (blocked) system theme?

---

### Post by jbicha on 2017-09-06
It's not easily possible to override the GDM theme.

If there was, Ubuntu would do that since they've tried to separate out changes to an Ubuntu session so that users can run a vanilla GNOME session. This is a continuation of work started by the Ubuntu GNOME team years ago.

---

### Post by Chanath on 2017-09-06
> **jbicha said:**
> It's not easily possible to override the GDM theme.

If there was, Ubuntu would do that since they've tried to separate out changes to an Ubuntu session so that users can run a vanilla GNOME session. This is a continuation of work started by the Ubuntu GNOME team years ago.

Linuxers don't like blocked stuff. They'd find a way to break in to anything blocked, or would leave (Unity). Unity Tweak was taken into fold, but Gnome Tweak or the Gnome Shell Extensions won't be able to. Already there are two Ubuntu Dock related extensions. The 2nd screeny is from the Ubuntu Dock Settings extension.  [https://ubuntuforums.org/showthread.php?t=2370670](https://ubuntuforums.org/showthread.php?t=2370670)

---

### Post by again? on 2017-09-11
Would much rather Ubuntu leave the gdm3 theme alone rather than insert the ugly purple/orange colours if
it can't be easily changed.
Whenever I lock the screen I am getting the purple background flash.

---

### Post by Perfect Storm on 2017-09-12
This happen also for Ubuntu Gnome.

---

### Post by harry332 on 2017-09-12
Yes this is not a gdm issue.
This happens because package gnome-shell was modifidied for ubuntu to enable ubuntu theming.
Gdm changes this back to vanilla gnome style after log in when gnome-session is selected.

---

### Post by ventrical on 2017-09-12
> **harry332 said:**
> Yes this is not a gdm issue.
This happens because package gnome-shell was modifidied for ubuntu to enable ubuntu theming.
Gdm changes this back to vanilla gnome style after log in when gnome-session is selected.

@ harry332

Harry,  Could you spell this out for me? Do I have to *install* gnome-session to get this reverted back to original?

My point is that _default_ is still themed orange.

---

### Post by harry332 on 2017-09-12
Ventrical,
in an ideal situation ubuntu-session would be the one and only to use ubuntu theming and gnome-session would be the one to use vanilla gnome theming.
Unfortunately this is not the case now.
In other words starting ubuntu leads always to gdm opening with ubuntu theming (reddish bg with orange log in window).
Only after this choosing gnome-session, you will get the vanilla gnome theming. That is if you have installed all the necessary gnome packages.
But rebooting your machine will still always start the gdm with ubuntu theming.

I think this is because developers wanted a nice transition experience from plymouth to gdm with ubuntu theming.
This was managed by modifying the package gnome-shell to enable ubuntu theming.
So, the package gnome-shell in ubuntu is not any more vanilla version.

---

### Post by Chanath on 2017-09-12
Actually, you'd see GDM, if you need a password to login, otherwise it appears only for few seconds. 
It appears to be hard coded system wise. One way to change that is by meddling with ubuntu.css in /usr/share/gnome-shell/themes. If you don't like the orange colour, then change the colour #dd4814 to something you like. Other colours can be checked straight from Google and changed to whatever you like. If you keep the name ubuntu.css, then the next upgrade won't change your changes.

---

### Post by again? on 2017-09-22
> **Chanath said:**
> Actually, you'd see GDM, if you need a password to login, otherwise it appears only for few seconds. 
It appears to be hard coded system wise. One way to change that is by meddling with ubuntu.css in /usr/share/gnome-shell/themes. If you don't like the orange colour, then change the colour #dd4814 to something you like. Other colours can be checked straight from Google and changed to whatever you like. If you keep the name ubuntu.css, then the next upgrade won't change your changes.

You can now change by installing gnome-session and using alternatives to choose your css theme file.
[https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/](https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/)

...but the painful purple still flashes at login and screen lock.

---

### Post by harry332 on 2017-09-22
Actually, I tried this on terminal:

   [FONT=Cantarell][SIZE=1]sudo update-alternatives --config gdm3.css[/SIZE][/FONT]

I then pressed 1 and <enter>.

It worked OK, now ubuntu's orange/purple login screen is grey/blue, just as it should.

---

### Post by P-I H on 2017-09-22
Worked OK after restart.

In case you want more blue colors, install Theme Configuration and change the orange "Custom highlight colors" to blue.

---

### Post by ventrical on 2017-09-22
> **harry332 said:**
> Actually, I tried this on terminal:

   [FONT=Cantarell][SIZE=1]sudo update-alternatives --config gdm3.css[/SIZE][/FONT]

I then pressed 1 and <enter>.

It worked OK, now ubuntu's orange/purple login screen is grey/blue, just as it should.

Changed color but got huge commadore64 type screen :) logon anyways ok.

---

### Post by Chanath on 2017-09-22
Have you noticed that GDM is slow? It thinks a bit before going forward to log in. Not like lightdm.

---

### Post by ventrical on 2017-09-22
> **Chanath said:**
> Have you noticed that GDM is slow? It thinks a bit before going forward to log in. Not like lightdm.

There are bugs .. haven't had time to file.

edit - so now : [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1719002](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1719002)

---

### Post by harry332 on 2017-09-23
Chanath,
Possibly the Gdm is a bit slow to get to the desktop.
Possibly I do not see this very well because of my fast hardware, the whole booting to gdm lasts only 2,4 sec.

Ventrical,
I do not experience any kind of flickering in my setup. I am using gnome-session with xorg.

---

### Post by BigCityCat on 2017-09-23
> **harry332 said:**
> Actually, I tried this on terminal:

   [FONT=Cantarell][SIZE=1]sudo update-alternatives --config gdm3.css[/SIZE][/FONT]

I then pressed 1 and <enter>.

It worked OK, now ubuntu's orange/purple login screen is grey/blue, just as it should.

Thanks for that. I hit 2 in order to reiterate how much I like the change.

---

### Post by Chanath on 2017-09-24
> **harry332 said:**
> Chanath,
Possibly the Gdm is a bit slow to get to the desktop.
Possibly I do not see this very well because of my fast hardware, the whole booting to gdm lasts only 2,4 sec.


I can't afford a new i7 at the moment. Mine is i3. I suppose fast enough. 
Lightdm with Unity works instantaneously.

---

### Post by litlesam on 2017-09-24
> **harry332 said:**
> Actually, I tried this on terminal:

   [FONT=Cantarell][SIZE=1]sudo update-alternatives --config gdm3.css[/SIZE][/FONT]

I then pressed 1 and <enter>.

It worked OK, now ubuntu's orange/purple login screen is grey/blue, just as it should.

Thanks, worked perfectly.

---

