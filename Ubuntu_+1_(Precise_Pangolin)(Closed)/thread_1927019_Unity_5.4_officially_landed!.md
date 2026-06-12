---
title: "Unity 5.4 officially landed!"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-02-17
3D version:
[https://lists.ubuntu.com/archives/precise-changes/2012-February/010151.html](https://lists.ubuntu.com/archives/precise-changes/2012-February/010151.html)

2D version:
[https://lists.ubuntu.com/archives/precise-changes/2012-February/010152.html](https://lists.ubuntu.com/archives/precise-changes/2012-February/010152.html)

---

### Post by philinux on 2012-02-17
[http://www.omgubuntu.co.uk/2012/02/unity-5-4-lands-in-precise-brings-hud-video-lens-minor-ui-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/02/unity-5-4-lands-in-precise-brings-hud-video-lens-minor-ui-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by Milos_SD on 2012-02-17
How can I disable chameleonic Ubuntu button, workspace switcher, and mounted devices?

---

### Post by mc4man on 2012-02-17
> **Milos_SD said:**
> How can I disable chameleonic Ubuntu button, workspace switcher, and mounted devices?
You can't, someone decided that they should be colored off of the desktop background, another ill-concieved design decision if no option is provided

You can alter it somewhat in unity plugin settings thru the custom background color  option but that is somewhat limiting & tends to produce fruitloops colors or grey

Edit: I forgot - if you turn the backlight off, use edge illumination, it's not as bad

---

### Post by BigSilly on 2012-02-17
Well I think it looks amazing. :)  Ubuntu really means business these days.

---

### Post by ubiquitin.jf on 2012-02-17
The chameleonic buttons depend on the colour of Unity (which now supports custom colouration), rather than the background.

What's really upset me is the complete removal of window dodge, which is a must-have on a netbook.

---

### Post by mc4man on 2012-02-17
> **ubiquitin.jf said:**
> The chameleonic buttons depend on the colour of Unity (which now supports custom colouration), rather than the background.

And the 'unity' color is based off of the desktop background image with a bias towards the center of the screen

---

### Post by ubiquitin.jf on 2012-02-17
> **mc4man said:**
> And the 'unity' color is based off of the desktop background image with a bias towards the center of the screen

By default, yes, but you can set a custom colour using ccsm in 12.04. This also changes the colour of the Dash button.

---

### Post by ubuntu27 on 2012-02-17
Unity 5.4 landed in Ubuntu 12.04 with the HUD, new tooltips, redesigned buttons and more[http://iloveubuntu.net/unity-54-landed-ubuntu-1204-hud-new-tooltips-redesigned-buttons-and-more]("http://iloveubuntu.net/unity-54-landed-ubuntu-1204-hud-new-tooltips-redesigned-buttons-and-more")

---

### Post by morgenstond on 2012-02-17
Anyone else seeing strange coloured notifications with this release?

I understand they are supposed to be the same colour as the Dash, but they are showing up dark blue and opaque instead.

It looks great otherwise (though I still have the compiz bug that shows menu options invisibly until hovered over.)

---

### Post by AlanR8 on 2012-02-18
Just done an update 09:30 am Saturday 18th Feb and no 5.4. How do you get it?

Update, mid day

Have just gone into Software Centre, found Unity and was offered an upgrade.

---

### Post by Faylcon on 2012-02-18
Is the "Show Desktop" icon supposed to be above the Dash launcher button? If not how can I remove it (it is not drag-gable)?

---

### Post by Milos_SD on 2012-02-18
I think it is a bug. It is not logical for it to be the first icon in launcher. :)

---

### Post by Stinger on 2012-02-18
> **morgenstond said:**
> 

It looks great otherwise (though I still have the compiz bug that shows menu options invisibly until hovered over.)

There is a bug at launchpad covering this issue:
[Bug #932813]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/932813")
Please subscribe if you are affected.

---

### Post by morgenstond on 2012-02-18
@Stinger: Done :)

---

### Post by jb5 on 2012-02-19
> **Milos_SD said:**
> How can I disable ...... mounted devices?

install gconf-editor & from command line can run:-
```

gconftool-2 --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option --type int 0

```This will disable mounted devices from appearing on launcher.
Not sure if this is considered the _correct_ way of doing this. Maybe feedback will point to a better way.

To restore default setting```
gconftool-2 --unset /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode
```

Workspace switcher may be in there as well somewhere, just run gconf-editor and have a look around.

NB Use at your own risk, it is entirely possible to break stuff by hitting the wrong key, I know from personal experience!
If you get into trouble can run the following commands to reset configuration. Try them one at a time in order, to see if it solves the problem before moving onto the next command, as each one escalates the _degree_ to which settings are reset, I believe.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compizconfig-1
unity --reset
rm -rf ~/.config/compiz-1/compizconfig/*
```

---

### Post by jb5 on 2012-02-19
> **morgenstond said:**
> Anyone else seeing strange coloured notifications with this release?

I understand they are supposed to be the same colour as the Dash, but they are showing up dark blue and opaque instead.


Somebody submitted bug report on this [BUG 935659](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/935659)
Please subscribe if you are affected.

---

### Post by durand on 2012-02-19
Unity was almost decent with 5.2 and then they decided to remove the dodging and edge pressure reveal... What the heck is going on in the design/usability dept.?

Also, can anybody else not use the Scale plugin to see windows on other workspaces? It used to work until 5.4 :/

---

### Post by mc4man on 2012-02-19
> **durand said:**
> 
Also, can anybody else not use the Scale plugin to see windows on other workspaces? It used to work until 5.4 :/

I don't know if I'll get any play on this bug - but atm scale can only use 'all windows' from the current workspace though not sure if broken or intentional.
group is totally non-functional, as is  all from all workspaces

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)

---

### Post by durand on 2012-02-19
> **mc4man said:**
> I don't know if I'll get any play on this bug - but atm scale can only use 'all windows' from the current workspace though not sure if broken or intentional.
group is totally non-functional, as is  all from all workspaces

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931601)

Cool, subscribed to that bug.

---

### Post by father_ted on 2012-03-02
Hoping that this release is less leaky under x64 as many of us have experienced high memory usage with unity-panel-service and compiz.

---

### Post by yarsdoom on 2012-03-02
I finally upgraded from 10.10 to the latest greatest. I hate it. It turned my pc into a mac. Is there any way to get back to the classic ubuntu, or at least get rid of launcher? Hiding isn't good enough it's gotta go... since even when hidden it robs you of a row of usable icon space on your desktop.
 
Please forgive (or gently redirect) if I'm off topic. First post.

---

### Post by cariboo on 2012-03-02
> **yarsdoom said:**
> I finally upgraded from 10.10 to the latest greatest. I hate it. It turned my pc into a mac. Is there any way to get back to the classic ubuntu, or at least get rid of launcher? Hiding isn't good enough it's gotta go... since even when hidden it robs you of a row of usable icon space on your desktop.
 
Please forgive (or gently redirect) if I'm off topic. First post.

You obviously have never used a Mac.

The thread you want to look at is located [here]("http://ubuntuforums.org/showthread.php?t=1873765&highlight=gnome-classic"), it tells you how to set up the old style two panel interface.

---

