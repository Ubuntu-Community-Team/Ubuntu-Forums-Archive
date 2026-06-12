---
title: "First letter of everything in Unity badly Aliased"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shamusl on 2012-02-02
Fonts are anti aliased while the first letter is not? This can be seen on almost all the menus on my machine since the upgrade to 12.04. I have ATI drivers. I can provide a screenshot if neccessary.

---

### Post by xyzzyman on 2012-02-02
A screenshot will be necessary to start with.

---

### Post by effenberg0x0 on 2012-02-02
If you could pick a good and very visible example, it would help. I'm trying to see it, but I can't. However, I do need stronger eyeglasses (and have been postponing that for more than half a year) so maybe it's right in my face :)

---

### Post by shamusl on 2012-02-03
nevermind.

---

### Post by lucazade on 2012-02-03
from a dirty scaled jpg is impossible to see the font rendering... isn't it?

link to a png image not scaled, please :)

---

### Post by Penguinnerd on 2012-02-03
Or even just a cropped image of a particular example?

---

### Post by shamusl on 2012-02-03
> **Penguinnerd said:**
> Or even just a cropped image of a particular example?

Here you go:

It might be a little hard to see, but that is consistent on all first letters of everything, including in the unity panel and on the window panel when maximized.

[http://imgur.com/7Wjmt](http://imgur.com/7Wjmt)

---

### Post by sffvba[e0rt on 2012-02-04
+1 to this...

Even the first letter of the top bar is dodgy... I tried to take a picture but it just doesn't come out at any resolution or size better than the post before mines shows it.

Edit - I am using Intel Graphics (945) so I doubt it is driver related etc.


404

---

### Post by shamusl on 2012-02-04
> **not found said:**
> +1 to this...

Even the first letter of the top bar is dodgy... I tried to take a picture but it just doesn't come out at any resolution or size better than the post before mines shows it.

Edit - I am using Intel Graphics (945) so I doubt it is driver related etc.


404

Ditto on not driver related, ATI drivers are in use on this system, so its definitely not that.

---

### Post by coffeecat on 2012-02-04
> **not found said:**
> Edit - I am using Intel Graphics (945) so I doubt it is driver related etc.


> **shamusl said:**
> Ditto on not driver related, ATI drivers are in use on this system, so its definitely not that.

Well - I'm going to muddy the water here. :) Have a look at my screenshot. Unless my tired old eyes are deceiving me, I'm not getting this issue.

That's on my laptop, Pangolin updated a few minutes ago, nvidia-current (290.10) and the card is what lspci unhelpfully refers to as "Nvidia Device 1055 (rev A1)" and which Windows identifies as a GeForce 410M.

---

### Post by redcylon on 2012-02-04
> **coffeecat said:**
> Well - I'm going to muddy the water here. :) Have a look at my screenshot. Unless my tired old eyes are deceiving me, I'm not getting this issue.

That's on my laptop, Pangolin updated a few minutes ago, nvidia-current (290.10) and the card is what lspci unhelpfully refers to as "Nvidia Device 1055 (rev A1)" and which Windows identifies as a GeForce 410M.


Hi, 1st time in the forum but I concurred that this is indeed exist. I think it came out right after Unity 5.2 update. Attached screenshot of quicklist (look at the letter H, as in "Home Folder"). It also came out in Dash.

Running it on Integrated Radeon 3200.

---

### Post by effenberg0x0 on 2012-02-04
I don't don't know what is going on lately. I can't reproduce the bugs people report anymore. It's getting on my nerves.

I had 5 people (with good vision and use no glasses) look at my installs of Precise and identify the examples you guys posted. It definitely is not happening here in the daily update machine or in the clean installations, VM or not, any hardware. I have asked them to test my Intel HD3000 based laptop, a Lenovo C2D (Intel GMA) Laptop, Nvidia GTS450 (I actually opened Unity in a 40 LED TV so people could look at it for me) and Nvidia 9500 GT on my default home monitors (2x LG FLatron W2253V). It's not here.

The only time I remember ever messing around with fonts (in my daily install): Using **gnome-tweak-tool** I reduced the size of fonts, because they get unnecessarily large on my monitors. Here are my settings: U**buntu/9, Sans/9, Ubuntu Mono/10, Ubuntu Bold/9, Slight, Rgba**. See the screenshot.
[ATTACH]211995[/ATTACH]

If you have gnome-tweak-tool installed, can you please check if it changes anything for you guys when using these settings?

Thanks,
Effenberg

---

### Post by coffeecat on 2012-02-04
> **effenberg0x0 said:**
> I had 5 people (with good vision and use no glasses) look at my installs of Precise and identify the examples you guys posted. It definitely is not happening here in the daily update machine or in the clean installations, VM or not, any hardware. I have asked them to test my Intel HD3000 based laptop, a Lenovo C2D (Intel GMA) Laptop, Nvidia GTS450 (I actually opened Unity in a 40 LED TV so people could look at it for me) and Nvidia 9500 GT on my default home monitors (2x LG FLatron W2253V). It's not here.

Hi, effenberg0x0. :) So you're not getting it with nvidia cards (proprietary driver?) or in a VM (have I got that right?), and I'm not getting it with a nvidia card and proprietary driver, but others are getting it with Intel or ATI GPUs. Interesting.

I'll boot up my Intel GPU laptop later and also try a live USB of today's daily on my ATI Radeon HD5450 desktop and see what I get with those.

---

### Post by dino99 on 2012-02-04
Can be some old settings left behind, so some cleaning might help:

- but remind Lucazade previous post: [http://ubuntuforums.org/showpost.php?p=11660720&postcount=5](http://ubuntuforums.org/showpost.php?p=11660720&postcount=5)

- be sure of your language utf-8 settings be applied on whole system
- switch back/forward theme used
- purge then reinstall: compiz/unity

and of course deactivate first extra source like ppa (and force back package version if necessary)

---

### Post by sffvba[e0rt on 2012-02-04
I think there might be enough good pictures now to show the point... but if more are needed I grabbed my whole screen at the correct resolution just to show the issue again...

Please note the red circles was me and Gimp :p

Also, I did an upgrade from 11.10 to 12.04 as I couldn't get 12.04 to install for anything...

[http://ubuntuone.com/2PS8tpRgD7H5jNmLpnTiVS](http://ubuntuone.com/2PS8tpRgD7H5jNmLpnTiVS)

[http://ubuntuone.com/6a2ckwlNOLPxLi3BXCkphQ](http://ubuntuone.com/6a2ckwlNOLPxLi3BXCkphQ)


404

---

### Post by mc4man on 2012-02-04
Don't see it at all either (nvidia), only semi-issue is with truncated window titles but that is a fairly longstanding issue

---

### Post by effenberg0x0 on 2012-02-04
> **coffeecat said:**
> Hi, effenberg0x0. :) So you're not getting it with nvidia cards (proprietary driver?) or in a VM (have I got that right?), and I'm not getting it with a nvidia card and proprietary driver, but others are getting it with Intel or ATI GPUs. Interesting.

I'll boot up my Intel GPU laptop later and also try a live USB of today's daily on my ATI Radeon HD5450 desktop and see what I get with those.

Hey CoffeeCat, I get Nothing, zero, nada in my home hardware. Let me describe the stuff better:


[LIST]
[*]**AMD Phenom II X6 1100 BE + Nvidia 9500 GT + NVidia 9600 GT plugged to three 3 (40", 40", 42") TVs and one 19" LCD monitor. Tested: **
[/LIST]
[INDENT]Running a fresh PP Alpha 2 real install, Primary HDD (NVidia Proprietary 290.10).
Running a VM (VMWare) PP Alpha 2 install[/INDENT]
[LIST]
[*]**AMD Phenom II X6 1100 BE + 2x GTS450 plugged to two 23" LCD monitors.**
[/LIST]
[INDENT]Running a fresh PP Alpha 2 real install, Primary SSD. (NVidia Proprietary 290.10).
Running a fresh PP Alpha 2 real install, eSata HDD, (NVidia Proprietary 290.10).
Running a VM (VMWare) Remote PP Alpha 2 install.
Running a VM (VMWare) Local PP Alpha 2 install.
Running a Local VirtualBox PP Alpha 2 install.[/INDENT]
[LIST]
[*]**Asus K43E i5 + hd3000 laptop **
[/LIST]
[INDENT]Running a fresh PP Alpha 2 real install (HDD, Primary).
[/INDENT][INDENT] Running a fresh PP Alpha 2 real install (USB HDD).
[/INDENT][INDENT]Running a VM (VMWare) Remote PP Alpha 2 install.
[/INDENT]
[LIST]
[*]**Lenovo G450 C2D +Intel GMA laptop. Tested:**
[/LIST]
[INDENT]Running a fresh PP Alpha 2 real install (SSD, Primary).
[/INDENT][INDENT]  Running a fresh PP Alpha 2 real install (USB HDD).
[/INDENT][INDENT] Running a VM (VMWare) Remote PP Alpha 2 install.[/INDENT]
It's all I got currently.... I can't see this bug no matter what I try. I'm gonna give up on that one.

Regards,
Effenberg

---

### Post by coffeecat on 2012-02-04
Well - I can't reproduce this at all. Not on three machines now.

Screenshot 1 - fully updated 12.04 from my laptop with:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Screenshot 2 - today's Daily running live in my desktop with:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
```

That's with the default open source ati driver, of course.

:-k

---

### Post by JRV on 2012-02-04
> **redcylon said:**
> Hi, 1st time in the forum but I concurred that this is indeed exist. I think it came out right after Unity 5.2 update. Attached screenshot of quicklist (look at the letter H, as in "Home Folder"). It also came out in Dash.

Running it on Integrated Radeon 3200.

I see it too. Intel 945 graphics.

---

### Post by effenberg0x0 on 2012-02-04
I'm completely ignorant about it: Is there anything dynamic about the way /etc/fonts/* is set during install, like some hardware-dependent settings?

Also, have you guys preserved HOME during yous installs? I'm guessing a .fonts could interfere.

Regards,
Effenberg

---

### Post by sffvba[e0rt on 2012-02-05
> **effenberg0x0 said:**
> I'm completely ignorant about it: Is there anything dynamic about the way /etc/fonts/* is set during install, like some hardware-dependent settings?

Also, have you guys preserved HOME during yous installs? I'm guessing a .fonts could interfere.

Regards,
Effenberg

I had preserved my home (I have it as a separate partition).  I will have a look when I get home what is in there and I can post the output of something there if it will help to compare it to one that isn't having an issue perhaps?


404

---

### Post by redcylon on 2012-02-05
> **effenberg0x0 said:**
> 

The only time I remember ever messing around with fonts (in my daily install): Using **gnome-tweak-tool** I reduced the size of fonts, because they get unnecessarily large on my monitors. Here are my settings: U**buntu/9, Sans/9, Ubuntu Mono/10, Ubuntu Bold/9, Slight, Rgba**. See the screenshot.
[ATTACH]211995[/ATTACH]

If you have gnome-tweak-tool installed, can you please check if it changes anything for you guys when using these settings?

Thanks,
Effenberg

Nope..still there.

---

### Post by coffeecat on 2012-02-05
> **not found said:**
> I had preserved my home (I have it as a separate partition).  I will have a look when I get home what is in there and I can post the output of something there if it will help to compare it to one that isn't having an issue perhaps?

Or could you run one of the recent dailies live? That might help to see if it's related to your particular GPU or your personal configs.

---

### Post by sffvba[e0rt on 2012-02-05
> **coffeecat said:**
> Or could you run one of the recent dailies live? That might help to see if it's related to your particular GPU or your personal configs.

To be honest I have not been able to get any of the alphas since Natty to install for me (once the RC roll out it works) and I have no idea why (this is the reason I did an upgrade and not a fresh install)...


404

---

### Post by redcylon on 2012-02-05
Hi, did another fresh install. Nothing wrong with Unity with wrong aliased font then. Straight run software-updates, reboot and the problem occurs.

Gonna try another fresh install and test.

p/s: does anyone knows if there's a way to choose from which server to select updates from during install? I believe it defaults to nearest server of which in my place is kinda slow....to damn slow.

---

### Post by xyzzyman on 2012-02-05
> **redcylon said:**
> Hi, did another fresh install. Nothing wrong with Unity with wrong aliased font then. Straight run software-updates, reboot and the problem occurs.

Gonna try another fresh install and test.

p/s: does anyone knows if there's a way to choose from which server to select updates from during install? I believe it defaults to nearest server of which in my place is kinda slow....to damn slow.

Was the fresh install a daily or the alpha 2 milestone? If it's the daily it'll be much easier to narrow down which package is causing this for you.

---

### Post by redcylon on 2012-02-05
> **xyzzyman said:**
> Was the fresh install a daily or the alpha 2 milestone? If it's the daily it'll be much easier to narrow down which package is causing this for you.

It's Alpha 2.

Also noticed 2 anomalies after updates, one of which was reported on another thread (the volume indicator).

The second pic shows a grey background for pop-up, instead of black. It's black in firefox and libreoffice though.

---

### Post by effenberg0x0 on 2012-02-05
I have a couple ideas on the cause of it according to local tests. It would be great if people affected by this bug could help by doing this test. Just copy/paste the following lines to a gnome-terminal and paste results back here please. It makes no change to the system, just check for values and a package. Depending on the results posted back, I think I'll be able to provide a fix.

```

cd && touch $HOME/MyLog.log && echo -e "\n-----Paste This into the forum----\n" | tee -a $HOME/MyLog.log && if [[ ! -x /usr/bin/gconftool-2 ]]; then sudo apt-get install gconf2;else gconftool-2 -g /desktop/gnome/font_rendering/{antialiasing,dpi,hinting} | tee -a $HOME/MyLog.log; fi && dconf read /org/gnome/settings-daemon/plugins/xsettings/antialiasing | tee -a $HOME/MyLog.log && dconf read /org/gnome/settings-daemon/plugins/xsettings/hinting | tee -a $HOME/MyLog.log && if [[ $(dpkg -s fontconfig | grep "Status:" | grep "ok" | wc -l) -eq 1 ]]; then dpkg -s fontconfig | grep "Version:" | tee -a $HOME/MyLog.log; else echo "fontconfig not installed" | tee -a $HOME/MyLog.log; fi && echo -e "\n-----Paste This into the forum----\n" | tee -a $HOME/MyLog.log


```Regards,
Effenberg

**EDIT: Script changed for easier reporting of results.**

---

### Post by redcylon on 2012-02-05
> **effenberg0x0 said:**
> I have a couple ideas on the cause of it according to local tests. It would be great if people affected by this bug could help by doing this test. Just copy/paste the following lines to a gnome-terminal and paste results back here please. It makes no change to the system, just check for values and a package. Depending on the results posted back, I think I'll be able to provide a fix.

```
if [[ ! -x /usr/bin/gconftool-2 ]]; then sudo apt-get install gconf2;else gconftool-2 -g /desktop/gnome/font_rendering/{antialiasing,dpi,hinting}; fi
dconf read /org/gnome/settings-daemon/plugins/xsettings/antialiasing
dconf read /org/gnome/settings-daemon/plugins/xsettings/hinting
if [[ $(dpkg -s fontconfig | grep "Status:" | grep "ok" | wc -l) -eq 1 ]]; then dpkg -s fontconfig | grep "Version:"; else echo "fontconfig not installed"; fi
```Regards,
Effenberg

It says Version: 2.8.0-3ubuntu2

---

### Post by effenberg0x0 on 2012-02-05
> **redcylon said:**
> It says Version: 2.8.0-3ubuntu2

Thanks. I edited the script to make it easier to report back the results. Please copy/paste the new code. The part to be posted back will be clearly indicated in the terminal.

Regards,
Effenberg

---

### Post by redcylon on 2012-02-05
> **effenberg0x0 said:**
> Thanks. I edited the script to make it easier to report back the results. Please copy/paste the new code. The part to be posted back will be clearly indicated in the terminal.

Regards,
Effenberg

rgba
96
slight
Version: 2.8.0-3ubuntu2

---

### Post by effenberg0x0 on 2012-02-05
Great, it matches one of the possibilities I have tried when attempting to re-create this behavior. Settings are on gconf but not on dconf. Let's try to set them on dconf.

Activate it.
```
gsettings set org.gnome.settings-daemon.plugins.xsettings active true
```Possible values are: none, grayscale and rgba. 
```
gsettings set org.gnome.settings-daemon.plugins.xsettings antialiasing rgba
```Possible values are: none, slight, medium and full. Try the default (medium)
```
gsettings set org.gnome.settings-daemon.plugins.xsettings hinting medium
```Each command should produce immediate results. Let me know how it went.

Thanks,
Effenberg

---

### Post by redcylon on 2012-02-05
> **effenberg0x0 said:**
> Great, it matches one of the possibilities I have tried when attempting to re-create this behavior. Settings are on gconf but not on dconf. Let's try to set them on dconf.

Activate it.
```
gsettings set org.gnome.settings-daemon.plugins.xsettings active true
```Possible values are: none, grayscale and rgba. 
```
gsettings set org.gnome.settings-daemon.plugins.xsettings antialiasing rgba
```Possible values are: none, slight, medisum and full. Try the default (medium)
```
gsettings set org.gnome.settings-daemon.plugins.xsettings hinting medium
```Each command should produce immediate results. Let me know how it went.

Thanks,
Effenberg

Nope..nothing really. In fact I don't it got anything to do with these settings per se, as it was the same settings post install. It got crap out after 5.2 updates.

---

### Post by effenberg0x0 on 2012-02-05
> **redcylon said:**
> Nope..nothing really. In fact I don't it got anything to do with these settings per se, as it was the same settings post install. It got crap out after 5.2 updates.
Unity has dependencies and reverse deps, uses system settings, etc. You can alter the way some of it works and appears by playing with system settings. Fonts aliasing is in gconf/dconf, it has to be here.

Questions: 
1) You do see some difference when changing antialiasing via dconf, right? Examples:
```
gsettings set org.gnome.settings-daemon.plugins.xsettings hinting slight
```Use the desktop and see if there's any change. Revert with:
```
gsettings set org.gnome.settings-daemon.plugins.xsettings hinting full
```2) What about deactivating it entirely?[FONT=monospace] Is there visible change?
[/FONT]```
gsettings set org.gnome.settings-daemon.plugins.xsettings active false
```Use the desktop and see if there's any change. Revert with:
```
gsettings set org.gnome.settings-daemon.plugins.xsettings active true

```3) Letters in the global menu also show this effect (example: File, Edit, etc)? What about letters in sub-menu items?

4) Any change if you reinstall fontconfig? 
```
sudo apt-get install --reinstall fontconfig fontconfig-config
sudo dpkg-reconfigure fontconfig
sudo dpkg-reconfigure fontconfig-config
```**EDIT: **Also, org.gnome.settings-daemon.plugins.xsettings comes from /usr/share/glib-2.0/schemas/org.gnome.settings-daemon.plugins.xsettings.gschema.xml from gnome-settings-daemon package, so:
```
sudo apt-get install --reinstall gnome-settings-daemon
sudo dpkg-reconfigure gnome-settings-daemon
sudo service lightdm restart
```**OBS: **Last command will restart your session. Save your work first!

**EDIT2: **Reinstalling it also because if you can't see any visible change when running the gsettings commands above, you probably don't have this schemas/keys installed. Visual change should be obvious at any of those commands.

---

### Post by redcylon on 2012-02-05
Sorry..still nothing!

> **effenberg0x0 said:**
> 
[/CODE]3) Letters in the global menu also show this effect (example: File, Edit, etc)? What about letters in sub-menu items?


It's only on the launcher and Dash. Nothing global menu, except if you maximize an app..the title bar will have the same problem (not the menu on the global menu bar)

---

### Post by effenberg0x0 on 2012-02-05
Ok, Thanks.

That is impossible. Each one of my installs respond immediately to turning of antialiasing globally or to changes in antialising and hinting options, inside and outside the dash. I can't see how any of the commands would produce any change in visuals. If that is really what you have there, I'm not sure how this is possible. I'll wait for more feedback from other users before proceeding. 

You may try MyUnity as an easy way to visually set antialising options:
[http://askubuntu.com/questions/19770/how-do-i-change-fonts-and-adjust-their-size](http://askubuntu.com/questions/19770/how-do-i-change-fonts-and-adjust-their-size) 

Thanks,
Effenberg

---

### Post by mc4man on 2012-02-05
I'd probably create a new user & check there (see none of this here, But there are currently many issues with light-themes & the unity* panel

---

### Post by effenberg0x0 on 2012-02-05
> **mc4man said:**
> I'd probably create a new user & check there (see none of this here, But there are currently many issues with light-themes & the unity* panel

Hi mc4man, maybe you can give me some insight here. Heres the situation status:

I have played around with this for some hours this weekend. The only way I can reproduce a similar behavior is by playing with antialiasing/hinting/dpi/text-scale settings. 

Some users have this set only in gconf. Others have gconf && dconf settings. Some have different values set in gconf/dconf (!?). Don't ask me why/how: All I did was ask people to run script such as [this]("http://ubuntuforums.org/showpost.php?p=11666682&postcount=28") in a local forum and compare the results for about 10 users. 

Also, there are people that have a ~/.fonts, probably from when installing over a preserved $HOME. In this case, it's not unusual to find people with stuff like this in their $HOME (I can find it on Google as an old antialiasing tweak):

#~/.fonts.conf
```
<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
   <fontconfig>
      <match target="font">
         <edit name="autohint" mode="assign">
            <bool>true</bool>
         </edit>
      </match>
</fontconfig>
```To make it worse:

- Directly changing antialiasing/hinting via gsettings commands seems to break themes for some users. 
- Changes to antialiasing/hinting are only seen on the Unity Dash if the user runs a search or access a lens he hasn't used yet or reloads Unity. The looks from previous antialiasing/hinting settings are cached. 

So, you see, it's a mess... Any ideas?

Regards,
Effenberg

---

### Post by redcylon on 2012-02-06
Reinstall again, and the first thing I did was run an update. Instead of do a full update, I cherry picked a single update related to Unity...something *-space (can't really remember though). And yet it happened again. Really didn't mind though. Just wait for another Unity updates.

It didn't effects Unity 2D though, maybe since the version number are higher at 5.2.1 while Unity 3D are at 5.2.0.

---

### Post by mc4man on 2012-02-06
> **redcylon said:**
> Reinstall again, and the first thing I did was run an update. Instead of do a full update, I cherry picked a single update related to Unity...something *-space (can't really remember though). ECT.
So be it then..

If you wanted to you could probably figure out from your /var/log/dpkg.log though one of the good reasons to use synaptic for updates is it keeps a very structured history

---

### Post by badhorse on 2012-02-07
Hi!
i also have this problem, but not only with fonts (first letter in global menu or dash). The button for close application (the red circle with X ) present the same problem.

---

### Post by andrek on 2012-02-17
Bump! I've got the same thing.

> **badhorse said:**
> Hi!
i also have this problem, but not only with fonts (first letter in global menu or dash). The button for close application (the red circle with X ) present the same problem.

Changing fonts settings in gnome-tweak-tool doesn't do anything.

---

### Post by jimv on 2012-02-17
Looks like this for me: [http://imgur.com/wwJyg](http://imgur.com/wwJyg)

[IMG]http://i.imgur.com/wwJyg.png[/IMG]

---

### Post by andrek on 2012-02-17
Exactly the same here. I'm using amd's fglrx driver if that matters.

---

### Post by redcylon on 2012-02-17
It used to be that Launcher tooltips and quicklist were having the same problem, but latest updates resolved those problems.

Now it only remains in the Dash and close button.

---

### Post by fluteflute on 2012-02-18
Everyone mark the bug as affecting them:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/927441](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/927441)

---

### Post by JRV on 2012-02-18
I just finished a fresh install from the daily live (2/18/12) and it is much improved, but still not right.

---

