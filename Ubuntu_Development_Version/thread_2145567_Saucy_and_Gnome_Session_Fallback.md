---
title: "Saucy and Gnome Session Fallback"
date: 2013-05-15
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-05-15
Gnome Session Fallback looks really good on Saucy
So far the only problem is Maximized Windows
but that can be an easy fix by right clicking the windows at the botton and choose to Unmaximize then you can manually extend the window to your pleasure
or better yet downgrade clutter from 1.14 to 1.12

---

### Post by ibjsb4 on 2013-05-15
Quick question.  Can classic still be installed in Saucy with the command apt-get install gnome-session-fallback?

---

### Post by Harry33 on 2013-05-16
> **ibjsb4 said:**
> Quick question.  Can classic still be installed in Saucy with the command apt-get install gnome-session-fallback?

Yes it can be installed.
The newest version is 3.6.2-0ubuntu6.
This will also draw in packages like gnome-panel and metacity.
But first, you need to enable the repository component universe proposed, however.

---

### Post by kuvanito on 2013-05-16
this is the only thing I did:
sudo apt-get install gnome-session-fallback
and there you have it!

---

### Post by fantab on 2013-05-16
Yes it can work with Gnome 3.6 but probably not with Gnome 3.8. Instead Gnome is using 'Gnome-Classic' which is nothing but few Extensions maintained by Gnome developers, which means we don't have wait for those 'Extensions' to be upgraded after the Gnome release. For that matter even Cinnamon is not working on with Gnome 3.8 but folks at ArchLinux have run some patches to make it run on 3.8.
I must say Gnome 3.8 quite good, which seems more stable and faster. 

My two cents...

---

### Post by ventrical on 2013-05-16
> **kuvanito said:**
> Gnome Session Fallback looks really good on Saucy
So far the only problem is Maximized Windows
but that can be an easy fix by right clicking the windows at the botton and choose to Unmaximize then you can manually extend the window to your pleasure
or better yet downgrade clutter from 1.14 to 1.12

  It works just fine here. I didn't have to do the right-click / Unmaximize at the bottom.

---

### Post by kuvanito on 2013-05-16
> **ventrical said:**
> It works just fine here. I didn't have to do the right-click / Unmaximize at the bottom.
good for you,yeap it really looks beautiful,now my neighbor wants me to install it on his desktop :)

---

### Post by ventrical on 2013-05-16
> **kuvanito said:**
> good for you,yeap it really looks beautiful,now my neighbor wants me to install it on his desktop :)


Most of ccsm are working great too.

---

### Post by ventrical on 2013-05-16
> **kuvanito said:**
> Gnome Session Fallback looks really good on Saucy
So far the only problem is Maximized Windows
but that can be an easy fix by right clicking the windows at the botton and choose to Unmaximize then you can manually extend the window to your pleasure
or better yet downgrade clutter from 1.14 to 1.12

How did you get the icons to go on the desktop like that?

---

### Post by kuvanito on 2013-05-16
> **ventrical said:**
> How did you get the icons to go on the desktop like that?
simple
just go to Applications,naviagte to an app that you want a shortcut on your desktop,hold left click and drag it to your desktop,then you can rename the shortcut and also you can right click the desktop and select Organize Desktop By Name,that easy :)

---

### Post by kuvanito on 2013-05-16
it totally looks like we are back in time,hehehehe

---

### Post by ventrical on 2013-05-17
> **kuvanito said:**
> simple
just go to Applications,naviagte to an app that you want a shortcut on your desktop,hold left click and drag it to your desktop,then you can rename the shortcut and also you can right click the desktop and select Organize Desktop By Name,that easy :)

Yep .. it actually works. Iv'e been trying to get this to work since Oneric!!:)  It seems more stable that previous releases.  It was always crashing  or just wouldn't work. Looks like they did an overhaul of sorts on it. Nice move for the "Linux for Human Beings" crowd. There are sure of lot of newbies who will be grateful for this.

Edit:

Oh yeah .. and another thing ... setting up ccsm in gnome-session fallback didn't bork Unity on the other Unity DE install. So that's a bonus too.

---

### Post by ventrical on 2013-05-17
It will not allow to change desktop background.

---

### Post by kuvanito on 2013-05-17
> **ventrical said:**
> It will not allow to change desktop background.

Oh YES!
just click on the picture of little Raring and the menu comes up,then you can choose Wallpapers,Pictures or Colors how do you think I got this?
Actually in Unity I can never change the Solid Colors,only to Black but here you can choose any Color you like,isn't that funny,hehehe :)

---

### Post by ventrical on 2013-05-17
Wow! .. It's been so long since Iv'e used Gnome. I never thought they would fix it this far into a new development release.

---

### Post by jbicha on 2013-05-17
> **kuvanito said:**
> 
or better yet downgrade clutter from 1.14 to 1.12

Hmm? I didn't think the fallback session used Clutter directly.

---

### Post by kuvanito on 2013-05-17
> **jbicha said:**
> Hmm? I didn't think the fallback session used Clutter directly.

you will be surprise how many things clutter controls now

---

### Post by jbicha on 2013-05-17
> **kuvanito said:**
> you will be surprise how many things clutter controls now

To be a bit more direct, gnome-fallback does not use clutter although some apps do. gnome-fallback uses either Metacity (the No Effects option in Ubuntu and GNOME's default) or Compiz. gnome-fallback basically works here on Saucy but there are a few regressions when used with GNOME 3.8.

---

### Post by kansasnoob on 2013-05-18
> **jbicha said:**
> To be a bit more direct, gnome-fallback does not use clutter although some apps do. gnome-fallback uses either Metacity (the No Effects option in Ubuntu and GNOME's default) or Compiz. gnome-fallback basically works here on Saucy but there are a few regressions when used with GNOME 3.8.

I'm not sure, but shouldn't you say "mutter" where you said "clutter" :confused:

I remember getting criticized greatly for suggesting that mutter amounted to metacity + clutter.

---

### Post by tista on 2013-05-19
Hi guys,

I've been living with Mutter as a fallback session but, now 3.8 or higher can't expose any desktop background images on running mutter as "stand-alone" window-manager... :(

So I asked Ray, a main developer of mutter, then he told me "Today Mutter doesn't support any fallback sessions as a window-manager".
If there was someone guys who runs mutter as a fallback window-manager like me, please go back to metacity...:(
Yeah my bug report for it on Bugzilla was changed status to "resolved"... so sad!!:cry:

1st attached shot shows mutter's desktop with 3.9.1, and 2nd one shows metacity's desktop as well.

Best Regards,
Tista

---

### Post by dino99 on 2013-05-19
> **tista said:**
> Hi guys,

I've been living with Mutter as a fallback session but, now 3.8 or higher can't expose any desktop background images on running mutter as "stand-alone" window-manager... :(

So I asked Ray, a main developer of mutter, then he told me "Today Mutter doesn't support any fallback sessions as a window-manager".
If there was someone guys who runs mutter as a fallback window-manager like me, please go back to metacity...:(
Yeah my bug report for it on Bugzilla was changed status to "resolved"... so sad!!:cry:

1st attached shot shows mutter's desktop with 3.9.1, and 2nd one shows metacity's desktop as well.

Best Regards,
Tista

Thanks for the heads up  :P and happy to see you back here  :guitar:
have you opened a launchpad report about that confirmed issue ?

---

### Post by tista on 2013-05-19
Hi dino99!! :)

And not yet on lunchpad, hopefully because I want jelemy to confirm this issue first before posting to launcpad, you know. ;)
Anyway I'll open that report on launchpad soon...

P.S
what a nice "salamander" avatar!! :)

---

### Post by kuvanito on 2013-05-20
Today 2013/05/20 just for fun I installed Saucy 32 Bits and after all was done and set I decided to install Gnome Session Fallback and completely remove Unity just to see if it worked and it did,as a result I now have a clean install of Saucy Classic 13.10 and I also removed a bunch of Apps that I had no use for.If you want to try it here we go:

sudo apt-get install gnome-session-fallback
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean
sudo reboot
sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d' ' -f3`

after all was done I removed a bunch of Apps:
sudo apt-get purge aisleriot* baobab* empathy-common* gir1.2-rb-3.0* gnome-disk-utility* gnome-mahjongg* gnome-mines* gnome-orca* gnome-sudoku* gnomine* librhythmbox-core6* libsyncdaemon-1.0-1* onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* python-ubuntuone-client* python-ubuntuone-control-panel* python-ubuntuone-storageprotocol* remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-vnc* rhythmbox* rhythmbox-data* rhythmbox-mozilla* rhythmbox-plugin-magnatune* rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-data* ubuntuone-client-gnome* ubuntuone-control-panel* ubuntuone-control-panel-qt* usb-creator-common* xdiagnose* xterm* && sudo apt-get autoremove && sudo apt-get autoclean

Warning! Use Gnome Session Fallback with Atomatic Login if you turn it Off you are in trouble....
If you get in trouble I suggest you take your HD out and hook it up to another PC and then modify the lighdm.conf file:
gksudo nautilus
go to etc/lightdm and open lightdm.conf file with Text Editor and change it to this:

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
autologin-user=[COLOR="#FF0000"](your user name)[/COLOR]
allow-guest=false

now save it and take the drive to your pc and reboot.

---

### Post by zika on 2013-05-21
> **kuvanito said:**
> Today 2013/05/20 just for fun I installed Saucy 32 Bits and after all was done and set I decided to install Gnome Session Fallback and completely remove Unity just to see if it worked and it did,as a result I now have a clean install of Saucy Classic 13.10 and I also removed a bunch of Apps that I had no use for.If you want to try it here we go:

sudo apt-get install gnome-session-fallback
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean
sudo reboot
sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d' ' -f3`

after all was done I removed a bunch of Apps:
sudo apt-get purge aisleriot* baobab* empathy-common* gir1.2-rb-3.0* gnome-disk-utility* gnome-mahjongg* gnome-mines* gnome-orca* gnome-sudoku* gnomine* librhythmbox-core6* libsyncdaemon-1.0-1* onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* python-ubuntuone-client* python-ubuntuone-control-panel* python-ubuntuone-storageprotocol* remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-vnc* rhythmbox* rhythmbox-data* rhythmbox-mozilla* rhythmbox-plugin-magnatune* rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-data* ubuntuone-client-gnome* ubuntuone-control-panel* ubuntuone-control-panel-qt* usb-creator-common* xdiagnose* xterm* && sudo apt-get autoremove && sudo apt-get autoclean

Warning! Use Gnome Session Fallback with Atomatic Login if you turn it Off you are in trouble....
If you get in trouble I suggest you take your HD out and hook it up to another PC and then modify the lighdm.conf file:
gksudo nautilus
go to etc/lightdm and open lightdm.conf file with Text Editor and change it to this:

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
autologin-user=[COLOR=#FF0000](your user name)[/COLOR]
allow-guest=false

now save it and take the drive to your pc and reboot.Thank You for this advice about moving HD to another PC... I am still laughning! [img]http://www.sherv.net/cm/emo/laughing/animated-laughing-smiley-emoticon.gif[/img]
Should that other PC be in another state...?

---

### Post by kuvanito on 2013-05-21
> **zika said:**
> Thank You for this advice about moving HD to another PC... I am still laughning! [img]http://www.sherv.net/cm/emo/laughing/animated-laughing-smiley-emoticon.gif[/img]
Should that other PC be in another state...?

laugh all you want,hehehehehe me 2
BUT since I had no luck with the Live OS I also could not do it from the Grub Menu ( for unknown reasons)
and since I really test Ubu and have half a dozen HD with the same installation and credential it was pretty easy to do :)

---

### Post by ventrical on 2013-05-21
> **kuvanito said:**
> laugh all you want,hehehehehe me 2
BUT since I had no luck with the Live OS I also could not do it from the Grub Menu ( for unknown reasons)
and since I really test Ubu and have half a dozen HD with the same installation and credential it was pretty easy to do :)

Actually Ubuntu will work from one hdd on one PC to another most of the time without modification. On some occasions there will be a conflict if you have a nvidia driver installed and  you switch it to an intel based machine.

---

### Post by zika on 2013-05-21
> **kuvanito said:**
> laugh all you want,hehehehehe me 2
BUT since I had no luck with the Live OS I also could not do it from the Grub Menu ( for unknown reasons)
and since I really test Ubu and have half a dozen HD with the same installation and credential it was pretty easy to do :)tty?

---

### Post by kuvanito on 2013-05-21
> **zika said:**
> tty?
sure!

---

### Post by kuvanito on 2013-05-21
what I am trying to say guys is that in one of my installations and after playing around with fallback I purged Unity and it did worked fine,I mean 13.10 with no unity at all just lightdm and fallback as the only desktop,it does work but you can not have it passworded it must automatic login if for any reason you choose to login with a password you are in trouble,since half of ubuntu is GONE the terminal will not work Grub acts weird and the only choice I had to modify my lightdm.conf was to have the hdd phisically moved to my pc as a usb hdd and then I was able to do it,restart my pc with the hdd modified and bang! it worked again,you know the BSD (black screen of death) i like to play,i mean really play around with ubu to check the limits of it,removing unity is something I do almost once a day sudo apt-get purge unity* some desktops work by itself with no unity and others must be side by side with unity.have you seen a pic of my machine?
i can change hard drives in a second(two swap bays)

---

### Post by zika on 2013-05-22
> **kuvanito said:**
> what I am trying to say guys is that in one of my installations and after playing around with fallback I purged Unity and it did worked fine,I mean 13.10 with no unity at all just lightdm and fallback as the only desktop,it does work but you can not have it passworded it must automatic login if for any reason you choose to login with a password you are in trouble,since have of ubuntu is GONE the terminal will not work Grub acts weird and the only choice I had to modify my lightdm.conf was to have the hdd phisically moved to my pc as a usb hdd and then I was able to do it,restart my pc with the hdd modified and bang! it worked again,you know the BSD (black screen of death) i like to play,i mean really play around with ubu to check the limits of it,removing unity is something I do almost once a day sudo apt-get purge unity* some desktops work by itself with no unity and others must be side by side with unity.have you seen a pic of my machine?
i can change hard drives in a second(two swap bays)Did You try removing all kernels? Does it work then?

---

