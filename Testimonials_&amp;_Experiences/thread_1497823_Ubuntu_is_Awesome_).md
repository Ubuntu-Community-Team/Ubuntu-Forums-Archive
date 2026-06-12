---
title: "Ubuntu is Awesome :)"
date: 2010-05-31
forum: Testimonials &amp; Experiences
---

### Post by frank1e on 2010-05-31
I've been using windows forever..  using computers since dos and I can't believe I haven't gotten to linux before =)  I decided to install ubuntu today and to use it just to learn it but by the end of the day I had already realized how badly it trashes windows..  just wanted to let yall know i've been converted :)  

        if anyone has any suggestions for me.. like good sites, good downloads and programs maybe tricks on optimizing it and what not i would be glad to hear it

---

### Post by Ozymandias_117 on 2010-05-31
A few problems a lot of converts have:

This will get you flash, java, mp3 etc.:```
sudo aptitude install ubuntu-restricted-extras
```

If you need DVD playback check out: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Good site for themes: [http://gnome-look.org]("http://gnome-look.org")

Oh, and a great site for learning about Linux (Probably my favorite): [http://tldp.org/]("http://tldp.org/")

---

### Post by inameiname on 2010-05-31
Wow, in just one day you've converted, ehy? That's cool. I've been using it since August and have also found myself never returning to Windows. Once you get the hang of it, it can be tweaked and used so much more efficiently for an individual, however you want it. Also, another great thing is the linux community. It's truly much nicer and more helpful than Windows. You seriously can speak to the creators of the programs you use daily and get help from those that know what they are talking about. And by being open-source, you are free to offer suggestions and tweaks to other's creations so as to improve it for all. IDK, I just think that's pretty cool. hehe

Hmmm, as far as programs, here are some good ones:

Wine is nice if you have a few Windows programs you wish to add (you'd need the Wine repository (where you get the wine program and updates))
Ubuntu-tweak is great for all sorts of things (can get from their website at first)
And the following are a few really good/cool things I have on mine that are nice (all by opening a terminal window (which is the one thing that you really need to get used to that's not common with most Windows users) and inserting:

sudo aptitude samba ntp build-essential make automake rar ubuntu-restricted-extras msttcorefonts libdvdread4 libdvdcss2 w32codecs p7zip p7zip-full ncompress sharutils lzop lha arj unace arc p7zip-rar pax rzip unalz vim zoo xfonts-terminus xfonts-terminus-oblique non-free-codecs hardinfo gparted bleachbit sun-java6-fonts sun-java6-jre sun-java6-plugin xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra nautilus-actions

...some are for networking with Windows computers and whatnot, some for playing dvds and various other formats, some are for compressing and decompressing numerous file types (like rar, zip, tar, etc), Windows fonts, Hardinfo is like System Info for Windows, Bleachbit cleans everything up on your system very well, Java, Gparted allows you to format flash drives and hard drives or whatever very easily, xscreensaver packages installs 200 screensavers (only 25mb or so) in which you can run at random and always have cool ones, nautilus-actions is really nice, as you can install various little actions which will make things very easy for you

As Ozymandias_117 mentioned_, _[www.gnome-look.org]("http://www.gnome-look.org") is a great site to use for themes, wallpapers, nautilus-scripts (which are amazing and grand for easily doing various things)

...I personally use the Linsta3 theme on there with the icons from Win7 app, which I really love, and if you really want it to resemble windows as much as possible, making it easiest to learn, just install the Win7 app on there, which is super duper easy, and it'll blow your mind how close it resembles Windows 7...

The following sites are others I check out often which let's you know what's up with Ubuntu and some help on what's cool and what can be tweaked and whatnot:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)
[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)
[http://linuxappfinder.com/](http://linuxappfinder.com/)
[http://np.archive.ubuntu.com/ubuntu/pool/universe/](http://np.archive.ubuntu.com/ubuntu/pool/universe/)
[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
[http://www.gnomefiles.org/index.php](http://www.gnomefiles.org/index.php)
[http://www.getdeb.net/](http://www.getdeb.net/)
[http://www.playdeb.net/](http://www.playdeb.net/)
[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://www.webupd8.org/](http://www.webupd8.org/)
[http://www.linuxtv.org/](http://www.linuxtv.org/)
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

The following website is for numerous nautilus-scripts, which basically gives you right click options to do all sorts of things:

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

As far as tweaks, uhm...here's a few easy ones you can do at the terminal which make things the way I like them:

1. Disable login sound (that annoyingly loud drum sound at the very beginning, before you even login (still retains actual login music))
2. To add computer, home, trash, and volumes icons to desktop
3. To move buttons from left side to right side (as most would agree is a huge desire)
4. To open a terminal with the "Windows Key" (Super L) (makes opening a terminal really easy)
5. To open the system monitor with the "Windows Menu Key" (Menu) (easily opening the system monitor to check resources)
6. To add menu icons and text below icons (personal choice for me)

sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
gconftool-2 --set /apps/nautilus/desktop/computer_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/trash_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool true
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_1 --type string "Menu"
gconftool-2 --set /apps/metacity/keybinding_commands/command_1 --type string "gnome-system-monitor"
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool true
gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "both"

Ubuntu restart (which a lot of people like tweaking so it's easy to do, like in Windows)

Step 1: Go to the System> Preferences > Keyboard settings
Step 2: Move to the Layout tab and under the keyboard settings click Key sequence to kill the X server
Step 3: To set it check the Control + Alt + Backspace

To add the volume icon in the notification area, which was left out in Lucid (just a preference for me):
Go to System > Preferences > Startup Applications
in the startup tab, look for 'Volume Control' and check it if its unchecked.
If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

Finally, for a true beginner, here is one of the best manuals/guides that seems to not be too technical, which is always a plus in learning something new in my book:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Hopefully some of this will help you. Sorry, I seem to have gone a little overboard here. :P

---

### Post by frank1e on 2010-05-31
> **Ozymandias_117 said:**
> A few problems a lot of converts have:

This will get you flash, java, mp3 etc.:```
sudo aptitude install ubuntu-restricted-extras
```

If you need DVD playback check out: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Good site for themes: [http://gnome-look.org]("http://gnome-look.org")

Oh, and a great site for learning about Linux (Probably my favorite): [http://tldp.org/]("http://tldp.org/")


Thanks a lot man

---

### Post by frank1e on 2010-05-31
> **inameiname said:**
> Wow, in just one day you've converted, ehy? That's cool. I've been using it since August and have also found myself never returning to Windows. Once you get the hang of it, it can be tweaked and used so much more efficiently for an individual, however you want it. Also, another great thing is the linux community. It's truly much nicer and more helpful than Windows. You seriously can speak to the creators of the programs you use daily and get help from those that know what they are talking about. And by being open-source, you are free to offer suggestions and tweaks to other's creations so as to improve it for all. IDK, I just think that's pretty cool. hehe

Hmmm, as far as programs, here are some good ones:

Wine is nice if you have a few Windows programs you wish to add (you'd need the Wine repository (where you get the wine program and updates))
Ubuntu-tweak is great for all sorts of things (can get from their website at first)
And the following are a few really good/cool things I have on mine that are nice (all by opening a terminal window (which is the one thing that you really need to get used to that's not common with most Windows users) and inserting:

sudo aptitude samba ntp build-essential make automake rar ubuntu-restricted-extras msttcorefonts libdvdread4 libdvdcss2 w32codecs p7zip p7zip-full ncompress sharutils lzop lha arj unace arc p7zip-rar pax rzip unalz vim zoo xfonts-terminus xfonts-terminus-oblique non-free-codecs hardinfo gparted bleachbit sun-java6-fonts sun-java6-jre sun-java6-plugin xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra nautilus-actions

...some are for networking with Windows computers and whatnot, some for playing dvds and various other formats, some are for compressing and decompressing numerous file types (like rar, zip, tar, etc), Windows fonts, Hardinfo is like System Info for Windows, Bleachbit cleans everything up on your system very well, Java, Gparted allows you to format flash drives and hard drives or whatever very easily, xscreensaver packages installs 200 screensavers (only 25mb or so) in which you can run at random and always have cool ones, nautilus-actions is really nice, as you can install various little actions which will make things very easy for you

As Ozymandias_117 mentioned_, _[www.gnome-look.org]("http://www.gnome-look.org") is a great site to use for themes, wallpapers, nautilus-scripts (which are amazing and grand for easily doing various things)

...I personally use the Linsta3 theme on there with the icons from Win7 app, which I really love, and if you really want it to resemble windows as much as possible, making it easiest to learn, just install the Win7 app on there, which is super duper easy, and it'll blow your mind how close it resembles Windows 7...

The following sites are others I check out often which let's you know what's up with Ubuntu and some help on what's cool and what can be tweaked and whatnot:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)
[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)
[http://linuxappfinder.com/](http://linuxappfinder.com/)
[http://np.archive.ubuntu.com/ubuntu/pool/universe/](http://np.archive.ubuntu.com/ubuntu/pool/universe/)
[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
[http://www.gnomefiles.org/index.php](http://www.gnomefiles.org/index.php)
[http://www.getdeb.net/](http://www.getdeb.net/)
[http://www.playdeb.net/](http://www.playdeb.net/)
[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://www.webupd8.org/](http://www.webupd8.org/)
[http://www.linuxtv.org/](http://www.linuxtv.org/)
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

The following website is for numerous nautilus-scripts, which basically gives you right click options to do all sorts of things:

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

As far as tweaks, uhm...here's a few easy ones you can do at the terminal which make things the way I like them:

1. Disable login sound (that annoyingly loud drum sound at the very beginning, before you even login (still retains actual login music))
2. To add computer, home, trash, and volumes icons to desktop
3. To move buttons from left side to right side (as most would agree is a huge desire)
4. To open a terminal with the "Windows Key" (Super L) (makes opening a terminal really easy)
5. To open the system monitor with the "Windows Menu Key" (Menu) (easily opening the system monitor to check resources)
6. To add menu icons and text below icons (personal choice for me)

sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
gconftool-2 --set /apps/nautilus/desktop/computer_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/trash_icon_visible --type bool true
gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool true
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_1 --type string "Menu"
gconftool-2 --set /apps/metacity/keybinding_commands/command_1 --type string "gnome-system-monitor"
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool true
gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "both"

Ubuntu restart (which a lot of people like tweaking so it's easy to do, like in Windows)

Step 1: Go to the System> Preferences > Keyboard settings
Step 2: Move to the Layout tab and under the keyboard settings click Key sequence to kill the X server
Step 3: To set it check the Control + Alt + Backspace

To add the volume icon in the notification area, which was left out in Lucid (just a preference for me):
Go to System > Preferences > Startup Applications
in the startup tab, look for 'Volume Control' and check it if its unchecked.
If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

Finally, for a true beginner, here is one of the best manuals/guides that seems to not be too technical, which is always a plus in learning something new in my book:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Hopefully some of this will help you. Sorry, I seem to have gone a little overboard here. :P

One day =)  Yeah I was downloading and installing custom themes which I already thought was pretty cool and then whatever music player I installed automatically got the lyrics for all my songs which I thought was badass.  Seems like everything I do on Ubuntu it does better than windows and looks better to =)

  Thanks for the links I downloaded all that stuff. Also added the  volume control that was driving me crazy =)
   Im kinda annoyed right now cuz orignally I installed ubuntu inside windows so last night I decided before I made to many changes I would go on and install it to my 2nd harddrive with its own partition but I can't get the cd to work.  
   Keeps hanging at the install menu screen..  Freezes up and I've already tried noapci, nomodeset options.  Nothing works so far maybe you might have an idea?

---

### Post by WinterRain on 2010-05-31
> **Ozymandias_117 said:**
> A few problems a lot of converts have:

This will get you flash, java, mp3 etc.:```
sudo aptitude install ubuntu-restricted-extras
```

If you need DVD playback check out: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Good site for themes: [http://gnome-look.org]("http://gnome-look.org")

Oh, and a great site for learning about Linux (Probably my favorite): [http://tldp.org/]("http://tldp.org/")
Something some people are not aware of, but if you do: (and you can copy and paste into terminal)
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Then:
```
sudo apt-get install non-free-codecs
```
gives you ubuntu-restricted-extras, flash, plus even more codecs such as gstreamer-ugly.

---

### Post by lancest on 2010-05-31
> **frank1e said:**
>  I can't get the cd to work.  
   Keeps hanging at the install menu screen..  Freezes up and I've already tried noapci, nomodeset options.  Nothing works so far maybe you might have an idea?

If you run into a problem use the Ubuntu alternate CD.

---

### Post by inameiname on 2010-05-31
Sure, no prob regarding the links and stuff. Glad I could help. And as for your problem, I agree with Lancest, try the alternate install cd. I'm afraid it's beyond me as far as what might be your issue outside of maybe having it resolved using the alternative method. IDK.

---

### Post by frank1e on 2010-05-31
> **inameiname said:**
> Sure, no prob regarding the links and stuff. Glad I could help. And as for your problem, I agree with Lancest, try the alternate install cd. I'm afraid it's beyond me as far as what might be your issue outside of maybe having it resolved using the alternative method. IDK.

I think I found another way around the problem. instead of reinstalling I can just turn my wubi install into a real one by copying it onto a new linux partition..

---

### Post by inameiname on 2010-05-31
Not sure if that would work, but I'm curious to know if it does for ya. I'm just thinking how Windows won't let you do that, copy the contents from one drive (essentially) to another partition, but guess I haven't tried if it's possible in Ubuntu.

---

### Post by za.zen on 2010-06-01
> **frank1e said:**
> I think I found another way around the problem. instead of reinstalling I can just turn my wubi install into a real one by copying it onto a new linux partition..

Enjoy your Linux.  Remember, support forums available for specific questions.  

And thank you for sharing your experience.  It is nice to hear from happy users.

---

### Post by frank1e on 2010-06-01
> **inameiname said:**
> Not sure if that would work, but I'm curious to know if it does for ya. I'm just thinking how Windows won't let you do that, copy the contents from one drive (essentially) to another partition, but guess I haven't tried if it's possible in Ubuntu.

I found an Ubuntu program google LVPM for Ubuntu.  It transfers your wubi install to a real linux partition.  I wouldn't be doing it in Windows.  And I have to have the Linux partition / drive setup beforehand.  I haven't done it yet but thats only because I'm lazy.  I have to  plugin a new external hd so I can move the wubi install onto it, and off the HD its on now.  Then I'll format and partition that harddrive and use LVPM to move the install back onto that HD.  So it's gonna be a little bit of work but it's supposedly all doable.
   Update : Still loving Ubuntu =) It's great man.  It never crashes.  And it's so funny cause while I was running Windows it was like always walking on eggshells.  I was scared to install any programs cause of what they might do to the system.  I ended up reformatting and installing like twice a month!  Now with Ubuntu I download and install shitloads of programs and it still seems to run fine =)  And in windows it seemed like the more programs that were in mym system tray the slower the system would go but on Ubuntu I keep a dozen programs running at once and the system runs just fine. I really can't believe how much better this run compared to Windows it's great.
     
      btw anyone happen to know about any nvidia config programs or gpu programs?  Specifcally something to switch resolutions, monitor nvidia graphic card settings, card temperatures, and possibly overclock?  I had some utilities on windows not sure if theres any for Ubuntu.

---

### Post by lancest on 2010-06-01
> **frank1e said:**
>   Specifcally something to switch resolutions, monitor nvidia graphic card settings, card temperatures, and possibly overclock?  I had some utilities on windows not sure if theres any for Ubuntu.

If you have installed the nvidia restricted driver you will find the nvidia settings applet in System/Administration/Nvidia X Server Settings. 

It does everything you mention.

I'm waiting for this to mature: 

Nouveau accelerated Open Source driver for nVidia cards

---

### Post by Random_Dude on 2010-06-01
I don't know if anyone has mentioned the firewall yet, but you should install GUFW.

It's the GUI for the UFW (uncomplicated firewall), which you can enable by using GUFW or by typing in the terminal:

```
sudo ufw enable
```Cheers :cool:

---

### Post by Timmer1240 on 2010-06-06
Its a keeper for me too!Luv the Karmic wow!

---

