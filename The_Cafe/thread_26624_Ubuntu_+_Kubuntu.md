---
title: "Ubuntu + Kubuntu"
date: 2005-04-13
forum: The Cafe
---

### Post by james_mad on 2005-04-13
I want to try both kde and gnome, meaning both Ubuntu + Kubuntu.  What is the best way to do this?  I already have the ubuntu iso downloaded, should I now download kubuntu?  Should I just install kde on Ubuntu, or is there some other way?  I bascially want to have a dual boot with Ubuntu and Kubuntu.  However, if having gnome + kde on Ubuntu is almost the same then I would prefer that.  What do you all think would be the best way to try them both out?  Thanks.

---

### Post by totalshredder on 2005-04-13
[QUOTE=james_mad]I want to try both kde and gnome, meaning both Ubuntu + Kubuntu.  What is the best way to do this?  I already have the ubuntu iso downloaded, should I now download kubuntu?  Should I just install kde on Ubuntu, or is there some other way?  I bascially want to have a dual boot with Ubuntu and Kubuntu.  However, if having gnome + kde on Ubuntu is almost the same then I would prefer that.  What do you all think would be the best way to try them both out?  Thanks.[/QUOTE]

It's quite easy, 

```
sudo apt-get install kubuntu-desktop
``` 

I did it just today! All you need to do to change in between gnome and kde, is when you are logged out, click sessions, and then select which one you would like to log into. 

Good Luck!

---

### Post by james_mad on 2005-04-13
Ok cool, I thought that would be the best way.  I just was not sure if Kubuntu was specifically made for KDE, and thus better than having KDE intergrated into Ubuntu.  Thanks  :smile:

---

### Post by MasonM on 2005-04-13
I really don't see the point of having a Kubuntu as KDE is easily installed on Ubuntu.

---

### Post by HungSquirrel on 2005-04-13
[QUOTE=MasonM]I really don't see the point of having a Kubuntu as KDE is easily installed on Ubuntu.[/QUOTE]
 The point is most Linux users are familiar with KDE and prefer it to GNOME, so they don't feel like downloading an ISO that installs GNOME, then installing KDE manually.  This is particularly important for dialup users.

---

### Post by totalshredder on 2005-04-13
[QUOTE=MasonM]I really don't see the point of having a Kubuntu as KDE is easily installed on Ubuntu.[/QUOTE]

Kubuntu is a lot easier, trust me. You don't have to configure anything except kdm, which you can simply skip. Plus you feel like you're using ubuntu more.

Luke

---

### Post by discourse on 2005-04-13
ok, i have a cd with kde 3.3. how do i go about installing it on top of my existing ubuntu setup. please give a detailed explanation, not just ./configure etc.#$%. noobs need screenshots. please be aware of this.

---

### Post by MasonM on 2005-04-13
Yeah I see your point Squirrel, wasn't thinking about dial-up. You can get so used to broadband that sometimes you can forget what it was like to be on dial-up. Makes sense now.

---

### Post by jdong on 2005-04-13
Ubuntu + GNOME + KDE doesn't fit on one CD too well. Plus, you need to prompt the user with one more annoyance during setup (WTF is GNOME/KDE?!?!)

---

### Post by poofyhairguy on 2005-04-14
Be sure to get the menu editor from Gnome if you plan to install Kubuntu. The KDE apps take over your menus. Its easy to fix, but ugly to look at...

---

### Post by Tsjoklat on 2005-04-14
[QUOTE=poofyhairguy]Be sure to get the menu editor from Gnome if you plan to install Kubuntu. The KDE apps take over your menus. Its easy to fix, but ugly to look at...[/QUOTE]

I wouldn't do that. It didn't work for me at all. I run Ubuntu/Kubuntu with both clean menus. I did this:

For clean Gnome menus (in terminal): 

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

K3b, Kaffeine and Amarok may still show up in Gnome. To fix this K3b, amarok and Kaffeine have to be edit manually. 

cd /usr/share/applnk/Multimedia/
sudo gedit k3b.desktop --> add: OnlyShowIn=KDE (at the bottom)
sudo gedit kaffeine.desktop --> add: Only ShowIn=KDE (at the bottom)

Amarok is tricky. It has two parts where the OnlyShowIn=KDE have to be placed.

cd /usr/share/applications/kde
sudo gedit amarok.desktop

You will see that it is already been put at the bottom if you have done above instructions. You have to scroll up a bit.. somewhere in the middle where you will find:

[Desktop Action Enqueue] <-- right above there you put: OnlyShowIn=KDE

After this do (in terminal):

killall gnome-panel

For clean KDE menus:

Right click on the KDE button (usually left bottom corner), this will start up the KDE menu editor. Scroll through the list and delete all the entries you don't want.

It will take twenty minutes but then you have a perfect clean Ubuntu/Kubuntu system without having to install the menueditor :)

D

*edit: typo*

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=Tsjoklat]
It will take twenty minutes but then you have a perfect clean Ubuntu/Kubuntu system without having to install a the menueditor :)

D[/QUOTE]


Thanks, just reinstalled kubuntu, will try it!

---

### Post by totalshredder on 2005-04-14
Good stuff, but now my CPU is running at 101%! It will be really helpful if it works :)
Luke

---

### Post by xtreem on 2005-04-15
> **Tsjoklat]I wouldn't do that. It didn't work for me at all. I run Ubuntu/Kubuntu with both clean menus. I did this:

For clean Gnome menus (in terminal): 

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in * said:**
>  <-- right above there you put: OnlyShowIn=KDE

After this do (in terminal):

killall gnome-panel

For clean KDE menus:

Right click on the KDE button (usually left bottom corner), this will start up the KDE menu editor. Scroll through the list and delete all the entries you don't want.

It will take twenty minutes but then you have a perfect clean Ubuntu/Kubuntu system without having to install the menueditor :)

D

*edit: typo*
 Excellent works a charm. Thank-you.

---

### Post by Gandalf on 2005-04-15
i just have something to add, when i installed ubuntu and kubuntu, i had a problem using vlc, when i go forward or backward, i could not hear anymore any sound output plus i can notice that the video output is a bit faster, so i think for the first thing, i'm gonna split menus as described in the post above (thanks) and i will try reinstalling vlc, BTW KDE fonts sucks, i can't see what is written in the address bar above :S

---

### Post by wyth on 2005-04-30
:roll: I followed this to the letter, and it worked great for Gubuntu.  I went back to Kubuntu later (I love 'em both), and I'm missing all my KDE apps in the menu --no control center, no konsole, no konqueror, nada.  And when I run kcontrol from the terminal, the only two options there are appearance & themes (with just an option for GTK Styles & Fonts) and the network tree.  When I use menu editor, the KDE apps don't show up.

This has *got* to be some simple thing that I, in my relative newbieness, am just too dense to get.  Before I go and reinstall everything, I just want to find out if there's a fix for this.  Is there a way to undo the hack?  Or is there some hidden thing I've turned on by mistake and don't know?  I don't even have my home folder anymore --I can get there through the terminal, and can save documents there, but otherwise it's just not to be seen.   ](*,) 

Any help would be appreciated.  I had it all customized, and don't want to do this all again if I can help it.

Cheers

---

### Post by wyth on 2005-04-30
Re-installed and all's well.  But if anyone is on to this, might be worth a response for others.

---

