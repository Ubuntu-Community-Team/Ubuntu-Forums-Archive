---
title: "Multiple Desktops with Ubuntu Netbook-Remix"
date: 2010-04-27
forum: Ubuntu Moblin Remix
---

### Post by stn21 on 2010-04-27
Hi,

is there a way to get multiple desktops with ubuntu netbook-remix?

The usual measures like looking through the system-config-tools or adding desktop-switcher to the panel all do not work.

Any ideas?

THX, stn

---

### Post by serggy on 2010-04-27
I think you only can have two desktops, I have read that but I do not remenber where

---

### Post by stn21 on 2010-04-27
> **serggy said:**
> I think you only can have two desktops, I have read that but I do not remenber where

2 Desktops would be great. So far there is only one. Maybe you could try to remember ?

THX, stn

---

### Post by serggy on 2010-04-28
[http://libertadzero.wordpress.com/2010/02/11/cambiar-los-wallpapers-y-backgrounds-en-ubuntu-moblin-remix/](http://libertadzero.wordpress.com/2010/02/11/cambiar-los-wallpapers-y-backgrounds-en-ubuntu-moblin-remix/)

as you can see is written in spanish, I did it and it is very easy, If you have any doubt do not hesitate to keep in touch with me

regards

---

### Post by stn21 on 2010-04-28
> **serggy said:**
> [http://libertadzero.wordpress.com/2010/02/11/cambiar-los-wallpapers-y-backgrounds-en-ubuntu-moblin-remix/](http://libertadzero.wordpress.com/2010/02/11/cambiar-los-wallpapers-y-backgrounds-en-ubuntu-moblin-remix/)

as you can see is written in spanish, I did it and it is very easy, If you have any doubt do not hesitate to keep in touch with me
regards

Hi,

my spanish is not really worth mentioning.
The article you mention seems to be about changing the wallpaper. In case I am wrong please correct me.

What I meant by "multiple desktop" is the function you have in standard ubuntu where you can use CTRL-ALT-left/right/up/down to switch to another empty desktop where you can open other programs.

In the Netbook-Remix that somehow does not seem to work and any menus that would configure this in standard ubuntu are inactive in Netboot-Remix.

So that is what I would like to know: how to active the desktop-switcher as in gnome.

Some confusion here: "desktop-switcher" is also used in the sense of "switch from netbook-desktop to gnome-desktop". That is not what I meant. Even with gnome-desktop on Netbook-Remix multiple desktops do not work.

Some more confusion: apparently there are complicated ways to do this with Netbook-Remix 9.10. 
I am using 10.04. There nothing works. 

One desktop, no more

No adding anything to the panel and compiz settings-manager does not work either.

Reeeally annoying :frown:

Any ideas?

---

### Post by JimTaverna on 2010-04-28
Running 10.4 UNE LTS. Apparently, the final has arrived, along with a name change. Looks to be Netbook Edition instead of Remix.

Switch to the Gnome desktop in 10.4, if you haven't already tried it. Works fine for me.

ctrl+alt+up/dn/lf/rt. Works like a charm. Four desktops, no waiting.

Four little garage doors on the bottom right panel.

May be it was fixed in final.

---

### Post by stn21 on 2010-04-30
> **JimTaverna said:**
> Switch to the Gnome desktop in 10.4, if you haven't already tried it. Works fine for me. ctrl+alt+up/dn/lf/rt. Works like a charm. Four desktops, no waiting. May be it was fixed in final.

Yesterday I installed 10.04 final.
I removed the "netbook-launcher" and hoped that would unlock the panel and allow adding the desktop-switcher applet. Also I thought this is what is meant by "switch to gnome-desktop".

With the pre-release that way you could at least move the panel. Still no adding of appletts, but at least something. Now nothing works anymore. 
One desktop, completely locked panel and that is it. No way out AFAIKT.

The netbook-menu has its charms so installing standard-gnome with no netbook-menu is an option only if really nothing else works.

1) what is the most straightforward way to switch to gnome-desktop? Preferrably without gconf-editing and without editing config-files etc?

2) Is there a way to activate multiple desktops in the ubuntu netbook-edition as released yesterday?

Thanks,
stn

---

### Post by VeeDubb on 2010-04-30
It really sounds to me like you are more or less barking up the wrong tree.  The whole point of the netbook remix, is that it's intended for small, low-power machines that are not going to be doing a lot of multi-tasking.

If you're not doing a lot of multi-tasking, you have no use for multiple desktops.

If you are doing a lot of multi-tasking, you don't want UNR.


Now, to get to your last question, the most straight forward way to switch to gnome desktop, is to install it through synaptic.  UNR does not have gnome installed by default, because it's not a particularly useful DE on a netbook.

The fastest way to get gnome on to your machine would be to either install regular Ubuntu instead of the netbook version, or from the netbook version, "sudo apt-get install ubuntu-desktop" which will essentially install everything that is not part of the netbook remix, including gnome, and set all of that stuff as default.

You can also manually install gnome and all of it's components, but it's probably not worth the trouble to do so.

---

### Post by stn21 on 2010-04-30
> **VeeDubb said:**
> or from the netbook version, "sudo apt-get install ubuntu-desktop" which  will essentially install everything

Thanks, that sounds like a workable solution. I'll try it next chance I get.
Is there a similar way to switch back to Netbook-Edition-desktop ?


> **VeeDubb said:**
> It really sounds to me like you are more or less barking up the wrong tree.  The whole point of the netbook remix, is that it's intended for small, low-power machines that are not going to be doing a lot of multi-tasking.

That is correct if "multitasking" is something like running a develpment-system on one desktop while programming a neural network on the other. That definition of "Multitasking" implies multiple user-interfaces with high-resourced backends like compilers or number-crunching.

What I do is for example multiple ssh-sessions to other computers, multiple firefox-windows, one with my mail, one where I google an one with an ubuntu-forum, and possibly open-office writer. Alle these can of course be switched with alt-tab or by mouse-clicking on the panel but I find it much faster and much easier to press ctrl-alt-left/right and then have a clean desktop with only one visible active category, like only mail or only writer or only ssh-session. In other words: multiple user-interfaces with basic and low-resource backends.

That is the normal everyday-way that I work with computers and it would be really nice if that would also work on the netbook. Preferrably **with** the desktop that ubuntu designed specifically for netbooks **and** with multiple desktops.

stn

---

### Post by VeeDubb on 2010-04-30
> **stn21 said:**
> Thanks, that sounds like a workable solution. I'll try it next chance I get.
Is there a similar way to switch back to Netbook-Edition-desktop ? 

It's important to understand that when you enter the command I referred to, you are not removing anything of substance from your computer.  All you are doing, is installing more stuff, and making that stuff the default.  In effect, you will have both the default Ubuntu desktop, and the Ubuntu Netbook remix environment installed at the same time.

When you get to the login screen, you can simply choose which one you want to use for the session.

> **stn21 said:**
> In other words: multiple user-interfaces with basic and low-resource backends.

If low resources is a very high priority to you, then installing the full ubuntu desktop may not be the best choice either.  You may instead want to try xubuntu, or lubuntu.  I've never used lubuntu, and really have no idea what it's about except that it's supposed to be light weight.  I have used xubuntu, and while I don't particularly like it, it was a god-send on an ancient an underpowered laptop once upon a time.

To install either of those, you would use the exact same command I posted above, replacing "ubuntu-desktop" with "lubuntu-desktop" or "xubuntu-desktop"

Out of curiosity, what kind of hardware are you running on?  In particular, CPU, RAM, and display resolution.

Stock Ubuntu is extremely lightweight compared to, say, Windows Vista/7.

---

### Post by stn21 on 2010-04-30
> **VeeDubb said:**
> ... In effect, you will have both the default Ubuntu desktop, and the Ubuntu Netbook remix environment installed at the same time. When you get to the login screen, you can simply choose which one you want to use for the session.

Thank you, that was the info I was missing.


> **VeeDubb said:**
>  ...  You may instead want to try xubuntu, or lubuntu.

Not so sure here. Netbook-Edition has a lot of things that make sense on netbooks. Like the redesigned menu. Many of the netbook-advantages go away once you install xubuntu and friends.


> **VeeDubb said:**
> Out of curiosity, what kind of hardware are you running on?  In particular, CPU, RAM, and display resolution.

Standard netbook "Medion MD1210" Intel Atom N270 1,6ghz 160gb 1gb ram, 1024x600
It is a bit weak but still has enough power for my "multitasking"-needs, even with XP. Plays divx on external monitor just fine too :P

At home I use a real notebook of course :biggrin:

> **VeeDubb said:**
>  Stock Ubuntu is extremely lightweight compared to, say, Windows Vista/7.

Definitely ! 
That is why I would really like to have UNE and a few more desktops.

---

### Post by cariboo on 2010-04-30
Lucid UNE already has gnome desktop install, you can switch to it on the login screen, just select your name, and you will see a switcher on the bottom panel. You have to have auto-login disabled in order to see it.

---

### Post by stn21 on 2010-05-01
> **cariboo907 said:**
> Lucid UNE already has gnome desktop install, you can switch to it on the login screen, just select your name, and you will see a switcher on the bottom panel. You have to have auto-login disabled in order to see it.

Yes it does!

And there is also a session-type "Ubuntu Netbook-Edition 2D" which is the netbook menu AND the desktop-switcher. With a little rearranging you can even get rid of the bottom panel.

The big fullscreen-menu is only on the first desktop, on the other desktops it looks very much like gnome.

Great !

---

### Post by VeeDubb on 2010-05-01
Wow.  Very good stuff.  I had no idea.

I have an Asus EeePC 1201n being delivered by UPS in a few days, and that sounds like an ideal solution for it, since it's in that no-man's land between netbook and notebook.

---

### Post by JimTaverna on 2010-05-01
Probably should have been a bit more specific in my first post. UNE installs with gnome, as you now know.

In any case, cariboo907 picked up the slack.

---

### Post by ubradford on 2010-05-04
There is quite a bit of confusion in this thread. Hopefully my post will clear some of that up.

**How To: Use multiple desktops (workspaces) in UNR 10.04 and keep the UNR application launcher on each desktop.**

1. Install Compiz.  Open a terminal and enter:

```
sudo apt-get install compiz && sudo apt-get install compizconfig-settings-manager && sudo apt-get install simple-ccsm
```2. Open: System > Preferences > Appearance

3. Click on the "Visual Effects" tab, select "Custom", and click on the "Preferences" button.

4. Select the "Desktop" tab and adjust the sliders to your preferred number of desktops. *(Various other appearance effects can be adjusted from here, but I  prefer to keep those minimal on my netbook.)   *
Click "Close", when finished.  Close the Appearance window as well.

5. To Switch Desktops hold CTRL+ALT and navigate between desktops with the UP / DOWN / LEFT / RIGHT arrow buttons.

6. Enjoy!

---

### Post by stn21 on 2010-05-07
> **ubradford said:**
> **How To: Use multiple desktops (workspaces) in UNR 10.04 and keep the UNR application launcher on each desktop.**

Yes, that works too. And afterwards you have all the compiz-options.
I tried that too. (Didn't get the cube working but that was probably just my fault)

I was happy to find the non-compiz-solution that comes already installed with UNE 10.04 (UNE 2D, see in previous posts). My netbook really is not one of the fastest so anything NOT installed is per se a good thing ;) 

The app-launcher only appears on the first desktop. That's fine with me especially since with UNE-2D the normal gnome-menu is also there. A little rearranging was in order. I replaced the wide 3-item menu-bar (Applications/Places/System) with the one-button gnome-menu and kicked the user-switching-applet out of the panel. (Shutdown etc then automatically appear in the gnome-menu). Also there is a new very compact window-switcher with icons instead of bars. Now I have one panel with everything in it.

Very Cool 8)

---

### Post by VeeDubb on 2010-05-07
It may be an issue with the nvidia driver, since my new netbook has the nvidia ion graphics chip, but UNR 2D doesn't work for me.

The launcher comes up on the first desktop and looks exactly like it does in the regular UNR, and as soon as I launch any program, the UNR launcher goes away and I get a full gnome desktop with 4 workspaces, and no UNR launcher on any of them.

I'm not interested in the compiz option, just because that's not really the point of UNR.  I want to keep things light weight.

On the upside, I'm not having any issues with multi-tasking on it anyway. You can always unmaximize the windows and for me, I really only need multiple desktops if I'm doing a ton of different things at once, which I really only do on my desktop.  The rest of the time, regular windows management and alt-tab is good enough for me.

---

### Post by JimTaverna on 2010-05-08
> **VeeDubb said:**
> ...The launcher comes up on the first desktop and looks exactly like it does in the regular UNR, and as soon as I launch any program, the UNR launcher goes away and I get a full gnome desktop with 4 workspaces, and no UNR launcher on any of them...

Definitely some odd behavior coming out of 2D, at least to my eyes.

Launcher is only active for the first desktop and comes with GNOME panels. If, in 2D, you open any app from the GNOME panel the UNE laucher goes bye-bye and doesn't return. Yet, if you open an app from the launcher, launcher stays (though only for the first desktop, in any case).

If you launch an app from desktops 2-4 (all GNOME), the app appears as running in UNE 2D (DT 1), but is inaccessible.

How much of this is by design or accident is anyone's guess. I like the idea of having the launcher available along with GNOME, but some of the interactions seem somewhat confused and dysfunctional.

***Off topic:*** Is there any way to change the default behavior of GNOME not showing a desktop as having activity (i.e. an open app) when said app is collapsed?

---

### Post by VeeDubb on 2010-05-08
> **JimTaverna said:**
> How much of this is by design or accident is anyone's guess. I like the idea of having the launcher available along with GNOME, but some of the interactions seem somewhat confused and dysfunctional.

***Off topic:*** Is there any way to change the default behavior of GNOME not showing a desktop as having activity (i.e. an open app) when said app is collapsed?


I think most of it is accident.  After several recent updates, UNR 2D is now behaving the way I expected it to.  However, even after tweaking the panel components and condensing down to 1 panel, I've decided I prefer regular UNR.

Also, regular UNR now gives me two workspaces anyway.

As far as the default Gnome behavior, I assume you're refering to the desktop switcher app not having any way to indicate that there are minimized windows on a desktop, I'm not aware of any way to change that.  However, I always disable that applet anyway.

---

### Post by stn21 on 2010-05-10
> **VeeDubb said:**
> The launcher comes up on the first desktop and looks exactly like it does in the regular UNR, and as soon as I launch any program, the UNR launcher goes away and I get a full gnome desktop with 4 workspaces, and no UNR launcher on any of them.

Yes, I noticed too that the laucher in the "2D"-environment is a bit whacky. It shows up only on the first desktop (that would be OK for me) but sometimes it closes and sometimes reappears. I have tried that on different PCs and found no regularity in the behaviour.

On my most recent installation on my netbook the launcher is on the first desktop and reappears once the desktop becomes visible, meaning once I minimize all apps on that first desktop.

I suspect that the app-launcher is a bit buggy and expect it to become more stable with coming updates.

---

### Post by stn21 on 2010-05-10
> **JimTaverna said:**
> ... but some of the interactions seem somewhat confused and dysfunctional.


Yes. So it seems.


Try this dysfunctional workaround: 

- log in
- open terminal (the launcher may stay or may disappear, probably depending on the relative humidity or something :P) 
- enter "killall netbook-launcher" in terminal.
- after that on my netbook the launcher appears on ALL desktops (I have 6) and so far it has not crashed again.

---

### Post by stn21 on 2010-05-10
> **VeeDubb said:**
> Also, regular UNR now gives me two workspaces anyway.


How is that ?

I have the most recent update and still only one desktop in regular UNR :|

Did you configure anything?




Also even with the newest update the netbook-launcher in "2D" still  crashes :frown:

---

### Post by VeeDubb on 2010-05-10
> **stn21 said:**
> How is that ?

I have the most recent update and still only one desktop in regular UNR :|

Did you configure anything?




Also even with the newest update the netbook-launcher in "2D" still  crashes :frown:

To be honest, I'm not sure.

Since I'd only owned my netbook for less than a week, and I had gone through some miss-steps getting everything configured the way I want, I decided to start over with a clean install.  Now it's gone.  I'm guessing it's something that I changed when I was playing in 2-d mode, but I really couldn't tell you what.  I'm actually planning on playing with it a bit over the next couple of days to see if I can reproduce it.

All I can say for sure is that one way or another, it is 'possible.'

---

### Post by VeeDubb on 2010-05-10
HA!  Got it.

If you want to stick with the full UNR launcher, and have nothing be different except multiple desktops, it's SUPER easy.

Open a terminal, (guake is an AWESOME terminal for a netbook by the way) and enter 

```
gconf-editor
```

navigate down to apps>metacity>general>num_workspaces

And change the value from 1 to 2 (or however many you want)

Log out and back in, and bam!  You can switch workspaces with ctrl-alt-left and ctrl-alt-right

No messing with full gnome, no having to deal with window title bars when maximized.  No buggy and crash prone 2-d launcher, no wasting resources on compiz.  Just two desktops with a launcher on each.

---

### Post by stn21 on 2010-05-11
> **VeeDubb said:**
> HA!  Got it.
enter ```
gconf-editor
``` navigate down to apps>metacity>general>num_workspaces
And change the value from 1 to 2 (or however many you want)


Yes, that works!
At last :grin:

> **VeeDubb said:**
> Log out and back in, and bam!  You can switch workspaces with ctrl-alt-left and ctrl-alt-right
No need to logout, it works as soon as you change the number.


You don't per-chance have an idea on how to unlock  the panel and add/delete appetts?

---

### Post by VeeDubb on 2010-05-11
> **stn21 said:**
> You don't per-chance have an idea on how to unlock  the panel and add/delete appetts?

I wish.  I searched the gconf editor for every reference I could find to "panel" or "lock" and every option I found that looked promising, said "object not writable.  Object has no schema"

I'll post back if I ever figure it out.

---

### Post by VeeDubb on 2010-05-12
[https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession](https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession)

looks like it has the answer.

"2-D" uses more of gnome but is really intended for netbooks that can't handle any type of 3-D acceleration, which explains why it seems so buggy and inconsistent.

There are walkthroughs on that page that describe how to change the gnome session so it looks and works like the regular UNE session, but doesn't have the panel completely locked down, which would be super.  I haven't tried it yet, but it looks promising.


Edit:  Works like a charm.  I now have a panel that can be unlocked and reconfigured, and I still have two desktops with the UNR launcher, and "proper" window maximization, and all the goodies.  Every day this new netbook get's a little better.

---

### Post by JimTaverna on 2010-05-13
> **VeeDubb said:**
> I think most of it is accident.  After several recent updates, UNR 2D is now behaving the way I expected it to.  However, even after tweaking the panel components and condensing down to 1 panel, I've decided I prefer regular UNR.

Also, regular UNR now gives me two workspaces anyway.

As far as the default Gnome behavior, I assume you're refering to the desktop switcher app not having any way to indicate that there are minimized windows on a desktop, I'm not aware of any way to change that.  However, I always disable that applet anyway.

Seems like you've managed some workaround. I'll give it a try once I get my Broadcom Crystal HD accelerator working with XBMC.

As for the the DT switcher, yes that's what I was referring to. Granted, for me, it's a minor aggravation, though it should show an active DT, at least IMO, whether the app is minimized or not. Maybe a fix or adjustment to the current way of handling the DT is in the works.

Thanks.

Ooops! Forgot to read the full thread. Nice work VDubb! Time to try gconf.

---

### Post by JimTaverna on 2010-05-13
> **stn21 said:**
> Yes. So it seems.


Try this dysfunctional workaround: 

- log in
- open terminal (the launcher may stay or may disappear, probably depending on the relative humidity or something :P) 
- enter "killall netbook-launcher" in terminal.
- after that on my netbook the launcher appears on ALL desktops (I have 6) and so far it has not crashed again.

LOL. Could be.

Might try a script to disable the launcher upon startup, if it's possible. In any case, it's a nice workaround.

---

### Post by leeds_shrew on 2010-05-27
> **VeeDubb said:**
> Also, regular UNR now gives me two workspaces anyway
What? How?
 
____________
 
Whoops... *embarrased*

---

### Post by kaminal on 2010-11-21
> **ubradford said:**
> There is quite a bit of confusion in this thread. Hopefully my post will clear some of that up.

**How To: Use multiple desktops (workspaces) in UNR 10.04 and keep the UNR application launcher on each desktop.**

1. Install Compiz.  Open a terminal and enter:

```
sudo apt-get install compiz && sudo apt-get install compizconfig-settings-manager && sudo apt-get install simple-ccsm
```2. Open: System > Preferences > Appearance

3. Click on the "Visual Effects" tab, select "Custom", and click on the "Preferences" button.

4. Select the "Desktop" tab and adjust the sliders to your preferred number of desktops. *(Various other appearance effects can be adjusted from here, but I  prefer to keep those minimal on my netbook.)   *
Click "Close", when finished.  Close the Appearance window as well.

5. To Switch Desktops hold CTRL+ALT and navigate between desktops with the UP / DOWN / LEFT / RIGHT arrow buttons.

6. Enjoy!



Hello!
 
I got to the visual preferences tab and I see the custom  radio button and the preferences buttom but they are grayed out.

a message at the top says "Mutter is running can't switch to other effects"

Is there a way to turn off "mutter"?

Thank you so much

---

### Post by cariboo on 2010-11-21
> **kaminal said:**
> Hello!
 
I got to the visual preferences tab and I see the custom  radio button and the preferences buttom but they are grayed out.

a message at the top says "Mutter is running can't switch to other effects"

Is there a way to turn off "mutter"?

Thank you so much

No you can't turn mutter off and use something else, Unity uses mutter as the Window manager. Unity is in the process of being ported to compiz, but it's pretty buggy at the moment.

---

### Post by VeeDubb on 2010-11-22
@kaminal - If you look at the dates before your post, you'll see that this is a fairly old thread talking about Ubuntu Netbook Remix, which is defunk.

Ubuntu Netbook Edition, which is based on the Unity interface, is a whole different beast.  

If you were really asking about UNR, I don't know.  I haven't used it since UNE hit alpha 2 or so.  

If you were asking about UNE (the current Ubuntu Netbook release) I suggest you either take advantage of the search tools, or start a new thread. Trying to discuss it here will only confuse things.

---

