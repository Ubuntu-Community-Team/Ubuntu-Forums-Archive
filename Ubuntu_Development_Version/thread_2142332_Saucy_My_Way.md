---
title: "Saucy My Way"
date: 2013-05-05
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-05-05
As I have said before I am a True Tester of Ubuntu and as so I have Installed Saucy this morning twice.
I am running Saucy 64 Bits as Unity with no chnages at all and Saucy Gnome My Way with all the changes you can imagine
Both installation are running smooth with no problems to report and all Updates installed.
Now laugh all you want,this is My Gnome My Way:
sudo apt-get install gnome-shell (choose gdm)
sudo reboot (at login choose gnome)
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean
sudo reboot

After reboot I also remove all these:
sudo apt-get purge aisleriot* baobab* empathy-common* gir1.2-rb-3.0* gnome-disk-utility* gnome-mahjongg* gnome-mines* gnome-orca* gnome-sudoku* gnomine* librhythmbox-core6* libsyncdaemon-1.0-1* onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* python-ubuntuone-client* python-ubuntuone-control-panel* python-ubuntuone-storageprotocol* remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-vnc* rhythmbox* rhythmbox-data* rhythmbox-mozilla* rhythmbox-plugin-magnatune* rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-data* ubuntuone-client-gnome* ubuntuone-control-panel* ubuntuone-control-panel-qt* usb-creator-common* xdiagnose* xterm* && sudo apt-get autoremove && sudo apt-get autoclean

I did change my Buttons Layout to my left and did some cosmetic changes to the Applications Folder,as a result I have a Clean Beautiful Install of Ubuntu Saucy 13.10 Gnome My Way with the Apps that I need.

Warning:Unity Will Be Gone!

Now,This is Testing!

---

### Post by VinDSL on 2013-05-05
Good job!  I roll_my_own too.  :)

Doesn't look like you're into Shell Extensions.  Personally, I cannot handle GS without a few extensions.

With the right mixture of extensions, GS/Unity are on par with each other IMO. 

In particular, I've been smitten by [Dock to Dock]("https://github.com/micheleg/dash-to-dock"). * This should be included in the Staging Package(s). ;)

Not sure what the canned version of Gnome-Shell is... probably 3.8.x

If you're running GS 3.9.1, all you need to do is compile D2D from source, and hack the metadata.json file:

```
{
"shell-version": [
 "3.8",
 **[COLOR="#0000CD"]"3.9.1"[/COLOR]**  
 ], 
"uuid": "dash-to-dock@micxgx.gmail.com",
"name": "Dash to Dock", "description": "Transform the dash into an intellihide dock.",
"original-author": "micxgx@gmail.com",
"url": "https://github.com/micheleg/dash-to-dock",
"gettext-domain": "dashtodock",
"version": 0
}
```* Got [Icon Hider]("https://github.com/ikalnitsky/gnome-shell-extension-icon-hider") working, using this same json hack -- another great extension. 

Works great in Saucy / GS Staging!

---

### Post by kansasnoob on 2013-05-05
> **kuvanito said:**
> **[COLOR="#FF0000"]As I have said before I am a True Tester of Ubuntu and as so I have Installed Saucy this morning twice.[/COLOR]**
I am running Saucy 64 Bits as Unity with no chnages at all and Saucy Gnome My Way with all the changes you can imagine
Both installation are running smooth with no problems to report and all Updates installed.
Now laugh all you want,this is My Gnome My Way:
sudo apt-get install gnome-shell (choose gdm)
sudo reboot (at login choose gnome)
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean
sudo reboot

After reboot I also remove all these:
sudo apt-get purge aisleriot* baobab* empathy-common* gir1.2-rb-3.0* gnome-disk-utility* gnome-mahjongg* gnome-mines* gnome-orca* gnome-sudoku* gnomine* librhythmbox-core6* libsyncdaemon-1.0-1* onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* python-ubuntuone-client* python-ubuntuone-control-panel* python-ubuntuone-storageprotocol* remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-vnc* rhythmbox* rhythmbox-data* rhythmbox-mozilla* rhythmbox-plugin-magnatune* rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-data* ubuntuone-client-gnome* ubuntuone-control-panel* ubuntuone-control-panel-qt* usb-creator-common* xdiagnose* xterm* && sudo apt-get autoremove && sudo apt-get autoclean

I did change my Buttons Layout to my left and did some cosmetic changes to the Applications Folder,as a result I have a Clean Beautiful Install of Ubuntu Saucy 13.10 Gnome My Way with the Apps that I need.

Warning:Unity Will Be Gone!

Now,This is Testing!

I love to see that! Do you report your results at the [QA Tracker]("http://iso.qa.ubuntu.com/")?

I don't mean to hound people over subscribing to QA testing but IMHO that's one of the most worthwhile things a person can do :)

---

### Post by jfernyhough on 2013-05-05
I go even further. I start with a mini.iso, do a CLI install, then build up from there. :D

---

### Post by kuvanito on 2013-05-05
My Point here is to prove to people that Ubuntu is the most customisable linux distro available and with the latest version of most linux open source apps
cutting edge technology,latest kernels and so easy to customise(change) even I can do it.
Take Unity for example.It is beautiful and stylish,fresh,new BUT if you don't like it then change it in to Gnome or even Cinnamon,come on guys! I,We have a lot to thank Canonical for.
Thanks Ubuntu,Canonical,Mark and we are not nearly done yet,wait,there is a Phone coming out? Tablets? and TVs too? Jump on the wagon and take Ubu for a test..... :)

Note:Today is Cinco de Mayo.Thank God for Heineken! I am a happy Cuban,what a mixed!!!!

---

### Post by Cheesemill on 2013-05-05
Did you know that there is an official Gnome version of Ubuntu?

Using this instead of the standard Ubuntu to start with would mean that you wouldn't have to uninstall Unity and install gnome-shell. It also comes with GDM as standard instead of LightDM so you would only have the one DM installed (you have 2 with your current setup). You would also have a cleaner home folder because you wouldn't have any of the Unity specific settings saved in it like you do with your current installation.

[http://ubuntugnome.org/](http://ubuntugnome.org/)
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

---

### Post by kuvanito on 2013-05-05
> **Cheesemill said:**
> Did you know that there is an official Gnome version of Ubuntu?

Using this instead of the standard Ubuntu to start with would mean that you wouldn't have to uninstall Unity and install gnome-shell. It also comes with GDM as standard instead of LightDM so you would only have the one DM installed (you have 2 with your current setup). You would also have a cleaner home folder because you wouldn't have any of the Unity specific settings saved in it like you do with your current installation.

[http://ubuntugnome.org/](http://ubuntugnome.org/)
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

Sorry Bud
I never liked the Ubuntu Official Gnome Release
I hate EVOLUTION and all the krap that it brings to Ubuntu
It reminds me of all the hate I had years ago to Ubuntu and Evolution(NEVER AGAIN)
That is why I TEST
Ubuntu My Gnome My Way!!!!!
Besides:You will never get the Beauty of the Ubuntu Themes,like the Colors and Buttons,Windows Decorations and so with the so called official gnome release,yakwwwwwwwwwww NOOOOOOOOOOOOOOOOO.......

---

### Post by Cheesemill on 2013-05-05
> **kuvanito said:**
> Besides:You will never get the Beauty of the Ubuntu Themes,like the Colors and Buttons,Windows Decorations and so with the so called official gnome release,yakwwwwwwwwwww NOOOOOOOOOOOOOOOOO.......
```
sudo apt-get install ubuntu-artwork light-themes
```
I use the standard Ubuntu theme on my installation of Gnome Ubuntu...

---

### Post by kuvanito on 2013-05-05
> **Cheesemill said:**
> ```
sudo apt-get install ubuntu-artwork light-themes
```
I use the standard Ubuntu theme on my installation of Gnome Ubuntu...

No Thanks But Thanks
Rather get the Monster and Tame it myself!!! 
I Test!!!! You Follow!!!! enough,if you don't like it stay away! Nice day to all :)

---

### Post by ventrical on 2013-05-05
> **kansasnoob said:**
> I love to see that! Do you report your results at the [QA Tracker]("http://iso.qa.ubuntu.com/")?

I don't mean to hound people over subscribing to QA testing but IMHO that's one of the most worthwhile things a person can do :)


... but here you report to nick that it's wasting time trying to teach old users new tricks.


[http://ubuntuforums.org/showthread.php?t=2128648&page=2&p=12579232#post12579232](http://ubuntuforums.org/showthread.php?t=2128648&page=2&p=12579232#post12579232)

 I don't get it.

Regards,
Ventrical

---

### Post by kuvanito on 2013-05-05
> **jfernyhough said:**
> I go even further. I start with a mini.iso, do a CLI install, then build up from there. :D

I want to do it just like you,that's my next install BUT I can not find a 13.10 minimal cd only the 13.04 and that I don't need but I can port the repos to saucy right?
need your feedback here,pls.Thank You.... :)

---

### Post by Cheesemill on 2013-05-05
> **kuvanito said:**
> I want to do it just like you,that's my next install BUT I can not find a 13.10 minimal cd only the 13.04 and that I don't need but I can port the repos to saucy right?
need your feedback here,pls.Thank You.... :)

Saucy mini ISO's...
32-bit [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/mini.iso)
64-bit [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/mini.iso)

---

### Post by kuvanito on 2013-05-07
and I keep playing with Saucy
Today I installed Saucy daily build 2013-05-07 and right away I installed gnome-session-fallback and it brought back a lot of good memories
here are few pics of my Saucy My Way,hehehehe

---

### Post by kuvanito on 2013-05-08
the only problem I am having with fallback is the window buttons are not working when the windows are Maximized (full size screen) and I bet it has a lot to do with the new clutter but I can always right click on the button of the window and close it,etc

---

