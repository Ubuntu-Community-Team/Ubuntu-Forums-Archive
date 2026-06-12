---
title: "installed 13.04  this weekend and nice, also a couple of questions...."
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by shantiq on 2013-03-12
.... 2 tricks which are just advertised elsewhere but some might want to know and a question for the cognoscenti


&#9679; **Moving windows buttons to right**      ```
gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"
```      
 last 3 words in order you favour; personally i put minimize last as is the most used of the 3 and find it best there






&#9679;  **if you favour old style gnome and want that permanent**   (i thought there was to be an easy choice given you at login on 13.04 but i log in automatically and saw no such choice so please tell me if i have missed a trick or 2 here)


```
sudo apt-get install gnome-session-fallback
```

If you want to make the autologin to login to gnome-classic, do this:

For setting GNOME Classic with effects as default:

```
 sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```

For setting GNOME Classic without effects as default:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
```

also then add

```
gnome-panel  --replace
``` to startup applications


i surmise ```
sudo /usr/lib/lightdm/lightdm-set-defaults -s unity
``` sets it back if you want that undone  [but not sure so check first and please confirm or disconfirm if you know please]


**and now 2 questions:**


 &#9679;both on 12.04 and now 13.04 i have found that the top bar in gnome takes dragged-in icons **but i have as yet never found a way to remove one once in there **any suggestions?


[ATTACH=CONFIG]240087[/ATTACH]


**compounded issue **on this fresh 13.04 the clock is absent but was there in unity and my-weather-indicator is there but does not open out



&#9679;  i have not as yet found a way to create a desktop launcher on this new install with gnome-fallback... how does one do that?   on 12.04 i used [this]("http://ubuntuforums.org/showthread.php?t=1874480&p=11420857#post11420857") from Stinkeye but so far it does not show up on desktop options




 All clever hints and suggestions welcome....     New to 13.04 [like most]...  so clear explanations please

---

### Post by shantiq on 2013-03-13
bump....    especially on desktop launcher please

---

### Post by ibjsb4 on 2013-03-13
```
sudo apt-get install gnome-session-fallback
```

I did not know that command still worked in 13o4.  I thought things got all changed around, good to know.

Do you know about this?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Im thinking it should still work in 13o4.

---

### Post by shantiq on 2013-03-13
----


=thanx for the link ibjsb4  but so far it does not fix any of my grumbles:KSalso not sure most of that info still applies in 13.04


**=============**
something else worth mentioning   xkill   can be made to work very prettily on this gnome 13.04  [to knock out/quit frozen items ):P

&#9679;   ```
sudo apt-get install alacarte
```

&#9679;   then bring it up  ```
alacarte
```   or Applications/System Tools/Preferences/Main Menu

&#9679;  double click on accessories
&#9679;  click on new items
&#9679;  enter xkill in  command and  name


&#9679;  add your own image or this q for quit       right-click and save

[ATTACH=CONFIG]240133[/ATTACH]

 &#9679; finally go to applications/accessories and drag to top bar    then click when you wish to use cross will appear and click on frozen item ):P


[B]
=====================[/B]



also screensaver preferences not present in 13.04 by default [on this gnome-fallback setup]


it requires installing ```
sudo apt-get install xscreensaver
```   then Applications/System Tools/Preferences/Screensaver




[B]
=====================[/B]


[allow hibernate]("http://ubuntuportal.com/2012/05/simply-way-to-enable-hibernate-feature-in-ubuntu-precise.html")   [it is not by default]

[B]

====================[/B]

to **create new desktop icon**

 go to Places/leftclick/Edit Menus/New Item [it is behind your panel so drag out and enter info]
Then go to applications find it and drag to desktop and/or icons-bar

---

### Post by shantiq on 2013-03-13
and then the idiot [me] finds out  there is an [ubuntu-gnome]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/") version   haaaaa
ps it comes in at 946M  so mayhaps use a usb with unetbootin [in repo]


off to see what it looks like

**EDIT**:   so i check it and it still has all these docking things
i am confused; this is not different in appearance really not too sure; i shall stick to the modified "gnome-fallback" regular then


see for yourselves


[IMG]http://1.bp.blogspot.com/-1A_aSrvOAuQ/UFIG56BaK7I/AAAAAAAAKIA/hJ6LrH9AD_Q/s1600/ubuntu-gnome-remix_2.png[/IMG]

---

### Post by shantiq on 2013-03-16
ok found the answers for 13.04 but i understand all this info works for 12.04 upwards for folks who have chosen to remain with gnome-panel  [we knew all this info 2 years ago but many of us have now forgotten it]

This is for the guys who want their desktop to look retro say Karmic days of yore with gnome as the default
but still have the latest Linux Kernel powering everything; like an old car with a brand new v8 under the bonnet



it has all to do with the **Alt key and left right clicks in the right sequence**



 &#9679;  to drag icon-bar to bottom/left/right click Alt then left click and drag to bottom/left/right.

Can also be done this way: place cursor on icon-bar/leftclick/click Alt/rightclick and pick properties/orientation 

 &#9679;  right-click on Applications or Places to access alacarte [main menu]
to move things around say Terminal from Accessories to Office etc..   also new launcher with + new item
 
 &#9679; to remove icon from bar: press Alt then hover on icon leftclick and immediately righclick Remove from panel

 &#9679;  or do more adding and removing **hover on icon-bar and leftclick/press Alt/rightclick**   add to panel or Properties


so you end up with this for example

[ATTACH=CONFIG]240232[/ATTACH]

---

### Post by dino99 on 2013-03-16
All this is quickly outdated if the gnome3-team ppa is used (upgrading to gnome 3.8 & +)
For example, as the "fallback" stuff is no more maintained, now with gnome 3.8 its becoming unusable (mainly due to mutter changes)

Note: your tips & tricks might have been written into the dedicated subforum, and not here, and is redundant with the wiki/howto from the community.

---

### Post by shantiq on 2013-03-16
yes Dino fair remark but as i indicated

> This is for the guys who want their desktop to look retro say Karmic days of yore with gnome as the default
 but still have the latest Linux Kernel powering everything; like an old car with a brand new v8 under the bonnet


 so if there is a better place for this info more than happy for it to go there; no doubt there are people who will benefit from the info; and i am well aware they are not a majority  ::]]


  besides 3.8 is not yet the default [if you gnome fallback you need the stuff above]  and plurality of choice has to be one of the elements that makes the Ubuntu community

---

### Post by cariboo on 2013-03-16
As dino99, suggested, most of us here are advanced users, and don't pay much attention to these guides, kansasnoob has produced several of these type of guides, but also backs them up with bug reports, and that is what we'd like to see here. If you have run into any bugs, please post them here, with links, otherwise, I'd suggest you hold off this type of posting until after Raring is released, and in general usage.

---

