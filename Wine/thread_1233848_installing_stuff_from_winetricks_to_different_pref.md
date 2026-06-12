---
title: "installing stuff from winetricks to different prefixes"
date: 2009-08-07
forum: Wine
---

### Post by diggedy on 2009-08-07
Ive been using playonline for a while now but I need to install certain things with winetricks to get games working ie. monkey island
So, how do I install things to specific prefixes. Forgive if its a silly question, im a complete noob and not ashamed to admit it :)

---

### Post by ackanao on 2009-08-07
It's not that difficult - take a look at this page:

[http://ubuntuforums.org/showthread.php?t=1199856]("http://ubuntuforums.org/showthread.php?t=1199856")

---

### Post by diggedy on 2009-08-07
ok cheers so assuming I wanted to install vcrun2005sp1 to my steam folder would I use

WINEPREFIX=~playonlinux/steam/ sh winetricks vcrun2005sp1

---

### Post by ackanao on 2009-08-07
I guess I misunderstood your intention; I assumed that you want to use winetricks on your Wine prefix - you actually wanted to use it on your POL's prefix - sorry about that.

There's a plugin for POL made by NSLW that you can use - it's a "POL Helper" plugin and you can download it from here:

[http://www.playonlinux.com/en/topic-2415-Plugin_POL_Helper.html]("http://www.playonlinux.com/en/topic-2415-Plugin_POL_Helper.html")

Extract it to your "/home/YourUsername/.PlayOnLinux/plugins/" folder, start POL and goto "Plugins -> Plugins manager"; Select it and  click on "Enable". Restart POL and after that you can run it from POL's menu.

In my case, I couldn't find POL Helper menu in POL - if this happens to you, run it from here (like I did):

/home/YourUsername/.PlayOnLinux/plugins/POL Helper 07052009/POL Helper/bin

just double-click on "POLH".

Now, in POL Helper, choose "winetricks", click on "**To POL Launcher**", select your Steam prefix and then click on "**get winetricks**"; After that click on "**run winetricks**" and select what you want to install.

---

### Post by diggedy on 2009-08-09
Thanks for the help.

Ive tried this but nothing happens. Ive extracted it to the plugins directory, enabled it from plugins manager but nothing appears after I restart POL. when I double click on it nothing happens and it also doesnt show in my menus, its as though its not actually there

---

### Post by ackanao on 2009-08-09
I've made a mistake - After you extract POL Helper plugin, you need to copy "POL Helper" folder from "POL Helper 07052009" folder to POL's "plugin" folder. POL Helper menu should be available now.

But it looks like POL Helper plugin does not work for you for some reason - not a big issue as long as your POL works as intended.

There's another way to use winetricks on your POL's prefixes - try this command:

```
WINEPREFIX=$HOME/.PlayOnLinux/wineprefix/Steam sh winetricks vcrun2005sp1
```
*Adjust path accordingly for your Steam prefix*

I don't know of any other way to use winetricks on POL's prefixes...

---

### Post by diggedy on 2009-08-09
> **ackanao said:**
> I've made a mistake - After you extract POL Helper plugin, you need to copy "POL Helper" folder from "POL Helper 07052009" folder to POL's "plugin" folder. POL Helper menu should be available now.

But it looks like POL Helper plugin does not work for you for some reason - not a big issue as long as your POL works as intended.

There's another way to use winetricks on your POL's prefixes - try this command:

```
WINEPREFIX=$HOME/.PlayOnLinux/wineprefix/Steam sh winetricks vcrun2005sp1
```*Adjust path accordingly for your Steam prefix*

I don't know of any other way to use winetricks on POL's prefixes...

Ive managed to get POL helper working, it just kinda started working for some reason. Anyway what youve given me above is exactly what I needed. Thanks very much

---

### Post by ackanao on 2009-08-10
You're welcome diggedy, I'm glad I was able to help.

Cheers.

---

