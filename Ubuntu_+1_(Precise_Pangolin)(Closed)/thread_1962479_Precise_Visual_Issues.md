---
title: "Precise Visual Issues?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rectec794613 on 2012-04-21
How are you guys? Before I ask for help, I just want to ask how development is going along. We have only 5 days until release and currently my installation looks a bit shabby...

I have a visual issues with my install of Precise. Which is completely up-to-date as of writing this.

The text inside dialog boxes is too light to read. This affects the Ambiance theme and one other theme. (The Hope theme, only 3rd-party theme I've tested.) The Radiance theme doesn't seem to have this issue. [Here's a picture of the shutdown dialog with the Ambiance theme.]("http://imgbin.org/images/7784.png") [And here it is with Radiance.]("http://imgbin.org/images/7785.png")

Just for the record, I have no idea if this is a known issue and has/has not already been solved, or if I'm the only one with this issue. I try my best to keep up with Ubuntu development, but I can't check *every* bug report. If it is a known bug, point me to its URL and we'll move on. If not, hopefully we can investigate this. For me, installing Ubuntu can be a bit hit-and-miss, and some installs come with irreperable errors...

Thanks for any help.

P.S. I also have several other visual issues but I will wait until after release to seek help for them.

---

### Post by zombifier25 on 2012-04-21
3rd party themes made for GNOME 3.2 won't work properly in GNOME 3.4. About the Ambiance... dunno, sorry.
Try
```
ls ~/.themes
```
and post if there is a folder called Ambiance in it,

---

### Post by grahammechanical on 2012-04-21
I do not get the same effect as you. I do not notice any difference between the themes.

What is more I am getting different messages in my shutdown dialog boxes. Whether it is shutdown or log out I just get a simple offer to restart, cancel or shutdown and just cancel or log out. There are some words but no count down.

My 12.04 started out as 11.10 and has been slowly upgraded to 12.04 but at one point in the previous months I re-installed (perhaps it was alpha 2). Now I now longer have the separate shutdown and restart apps in the Dash.

I am wondering about the history of your version of 12.04. Does it have any 11.10 or earlier left over that could explain this.

I recently tested the upgrade path to 12.04 from both a default 11.10 and 10.04.

I found that with 10.04 applications menus remained in a panel in the application window and did not move to the global menu.

But with 11.10 the upgrade became no different from standard 12.04.

So, I think that different set ups respond differently.

Regards

---

### Post by rectec794613 on 2012-04-21
> **zombifier25 said:**
> 3rd party themes made for GNOME 3.2 won't work properly in GNOME 3.4. About the Ambiance... dunno, sorry.
Try
```
ls ~/.themes
```
and post if there is a folder called Ambiance in it,
Adwaita Cupertino L         Ambiance      Hope-DT
Adwaita Cupertino L Unity   A New Start   Malys
Adwaita Cupertino SL        Elegant Brit  malys-glassArt
Adwaita Cupertino SL Unity  Hope          Ubuntu

This is because I copied my themes over from my Oneiric installation. I think this is where the problem lies. Maybe someone can upload their Ambiance folder from their Precise install? The "Ubuntu" theme is a Cinnamon theme, by the way. 

> **grahammechanical said:**
> I do not get the same effect as you. I do not notice any difference between the themes.

What is more I am getting different messages in my shutdown dialog boxes. Whether it is shutdown or log out I just get a simple offer to restart, cancel or shutdown and just cancel or log out. There are some words but no count down.

My 12.04 started out as 11.10 and has been slowly upgraded to 12.04 but at one point in the previous months I re-installed (perhaps it was alpha 2). Now I now longer have the separate shutdown and restart apps in the Dash.

I am wondering about the history of your version of 12.04. Does it have any 11.10 or earlier left over that could explain this.

I recently tested the upgrade path to 12.04 from both a default 11.10 and 10.04.

I found that with 10.04 applications menus remained in a panel in the application window and did not move to the global menu.

But with 11.10 the upgrade became no different from standard 12.04.

So, I think that different set ups respond differently.

Regards
Maybe try a fresh installation? As mentioned, I don't have much luck with my Ubuntu installs, I also don't have much luck with upgrades to new releases. This is common, though.

As for me, I had a fresh install of Precise back in alpha 1, and I kept it up until beta 2. The install had many problems caused by upgrades. So a week or two ago I installed Precise beta 2 from the 12.04 mini install CD.

---

### Post by mcellius on 2012-04-21
I reported some of the theme problems to a developer of some alternate themes (ambiance-colors and radiance-colors), and he said he was going to have to make some changes for Gtk3, and would have them available within about three days of the release of 12.04 LTS.  

I don't know if he's alone in this.  I hope the developers and the Ubuntu teams are communicating.

---

