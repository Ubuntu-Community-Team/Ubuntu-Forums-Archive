---
title: "HOW TO: Change Splash Screen"
date: 2005-01-17
forum: Tutorials
---

### Post by Yukonjack on 2005-01-17
To change the splash screen, put the downloaded image in ~/.gnome or any place you would like but ~/.gnome is a good place. ~ means /home/yourname/.gnome/splash.png. This way it will be easy to change splash screen in the future. Rename your new splash screen to splash.png if it's a png file or splash.jpeg if it's a jpeg file. Now we have the splash screen ready ~/.gnome/splash.png. Then edit the GConf key /apps/gnome-session/options/splash_image using the Configuration Editor (Panel menu->System Tools->Configuration Editor) right click on splash_image key and choose edit key, where you see Key Value enter the new key value /home/yourname/.gnome/splash.png  or the commandline tool gconftool-2. Now do a quick reboot Ctrl-Alt-Backspace and bingo your new splash screen. In the future if you want to change the splash screen just rename you new downloaded splash screen to splash.png or .jpeg and move or rename your old one and drop the new splash screen in ~/.gnome this way it save renaming the Key Value everytime you want to change splash screen. Next time you reboot you will see the new splash screen.

/for the real newbee/if you change from a png to a jpeg file don't forget to change the Key Value to the new file format/ that is all

---

### Post by rctxtreme on 2006-12-30
Update for Edgy please.

---

### Post by dxxvi on 2006-12-30
In my Edgy:

- Applications | System Tools | Configuration Editor

- In the left box: apps | gnome-session | options

- In the right box: change the splash_image to your image (may include path) which must be in /usr/share/pixmaps

---

### Post by rctxtreme on 2006-12-30
Never mind, I just had to use the menu editor to tick config editor.

---

### Post by wscheer on 2007-01-16
Yukonjack,
Thanks for the tutorial worked great in edgy.

My gnome configurator was not located under apps>system tools

But it was installed, i just searched for gconf-editor and found the executable and ran it from the search. Could be an edgy thing...:-k

---

### Post by T3h_Dohtem on 2007-01-24
Yeah, Im in edgy, and I dont have "System Tools" in my Apps menu :( I feel neglected.

---

### Post by erflol on 2007-01-25
To get your system tools menu:

System->Preferences->Menu Layout

Select System tools on the left hand side.

You will see a list of items that would normally be stored in the system tools menu, just put a check in "Configuration Editor"

You could also run gconf-editor from the terminal if you don't want to have a menu-item that you rarely ever use

Cheers
eRflol

---

### Post by k-let-powa on 2007-01-29
**[SIZE="2"]An easier way for Edgy ! [/SIZE]**

I noticed there's a symbolic link in /usr/share/pixmaps/splash pointing to the ubuntu splash image.

Just recreate it pointing to YOUR png file like this:

```

cd /usr/share/pixmaps/splash
sudo mv path_to_your_splash.png ./mysplash.png
sudo rm ubuntu-splash.png       => we're just deleting a link, not the png
sudo ln -s mysplash.png ubuntu-splash.png
```

Done! Fast and easy!


To cancel changes, just  delete the link again and rebuilt it pointing to the original png:

```

cd /usr/share/pixmaps/splash
sudo rm ubuntu-splash.png
sudo ln -s ubuntu-slick.png ubuntu-splash.png

```

---

### Post by marcthepunk on 2007-01-29
or you can try installing gnome-splashscreen-manager.

---

### Post by hyperair on 2007-05-11
Thanks for the tip on the gnome-splashscreen-manager. I prefer that method really, although it's just a frontend for whatever was said above.

---

### Post by Seeker84 on 2007-06-15
I'm in edgy and I don't see configuration manager.  But if I go to terminal and type gconf-editor I get to the same place.  Hope it helps someone.

---

### Post by sr20ve on 2007-06-27
gnome-splashscreen-manager works great, thanks.

---

### Post by hyperair on 2007-06-27
Install gnome-splashscreen-manager in synaptic or using this command:
```
sudo apt-get install gnome-splashscreen-manager
```

Then go to System->Preferences->Splash Screen and change it there.

---

### Post by Golyadkin on 2007-06-27
It might be handy to also post that this is for changing the splashscreen in GNOME, not the boot splashscreen (Ubuntu with the orange progress bar) or for KDE. Maybe you can change the topic title? It will be a bit more clear this way.

---

### Post by ironcitadel on 2007-07-07
How to change the gnome splashimage.
1. Put the splash image you want in "png" format and store it in /usr/share/pixmaps/splash.  (You can use Nautilus or the "cp" or the "mv" command from the terminal window if you want.  Just remember to use "sudo" before your command. )
2. Press ALT-F2 then at the prompt type "gconf-editor" (without the quotes).
3. Click on "apps" then "gnome-session" then "options".
4. To the right of the Name "splash_image" double click on the Value "splash/ubuntu-splash.png".
5. Change "splash/ubuntu-splash.png" to reflect your new splash image: "splash/newsplash.png".
6. Click on "File" then "Quit".
7. Logout then login in again to see your new splashimage.

---

### Post by hyperair on 2007-07-07
Those instructions only work for GNOME. And for GNOME we already have the gnome-splashscreen-manager which does the job much more efficiently. 
Perhaps someone with KDE experience might like to post?

---

### Post by fornax01 on 2007-09-05
well personaly i think its rather pointless to ask someone who has experiance with kde how to change the gnome splash screen which is what the post is all about. 

I dont see how you can say that gnome-splashscreen-manager does the job more efficiently when this method uses a default installed program, rather than having to install another seperate tool which also has dependancies, especially when essentialy the gnome-splashscreen-manager does the same thing described in this post.

---

### Post by hyperair on 2007-09-05
If you had taken a look at the topic title, it said "Change Splash Screen". Evidently, the topic title does not specify, GNOME or KDE. So since GNOME has been covered here, I thought that covering KDE might be good for KDE beginners.

While you don't see how gnome-splashscreen-manager does this more efficiently, others might. I certainly don't like the idea of having to navigate to a certain key and changing that value every time I want to change my splash screen. I don't know about you, but it feels hackish to me. A GUI front-end to this kind of thing sounds good to me, at least you aren't throwing beginners into the deep end of the water, and giving them extremely specific instructions on how to swim out.

---

### Post by Eicca on 2007-09-29
Thanks for the guide! :)

---

### Post by MicroBoy on 2008-03-31
**Can anyone tell me if this tutorial is helpfull for 7.10? Because on 7.10 It doesn't work.**

---

### Post by piousp on 2008-03-31
> **Golyadkin said:**
> It might be handy to also post that this is for changing the splashscreen in GNOME, not the boot splashscreen (Ubuntu with the orange progress bar) or for KDE. Maybe you can change the topic title? It will be a bit more clear this way.

Just wondering, where i can find a guide for this? For the boot splash

---

### Post by Kekk0 on 2008-06-01
Thank you very much. :)

---

### Post by guest_user on 2008-09-20
> **piousp said:**
> Just wondering, where i can find a guide for this? For the boot splash

I would like to know how to change the boot splash of hardy heron too.

---

### Post by calito on 2008-09-21
download a bootsplash theme from [www.gnome-look.org](www.gnome-look.org) or [www.ubuntu-art.org](www.ubuntu-art.org). Extract it if it comes in a tar.gz format

Run sudo apt-get install startupmanager

Run startup manager and go to the appearance tab
Select the Manage usplash themes button at the bottom
Add your .so splash theme
Select it in the dropdown box above 
Exit the startup manager and the next time you reboot it should be the desired splash screen

---

### Post by Cloud4Twenty on 2008-12-31
Maybe it's just me but I seem to be having an issue getting the splash screen I want. I installed the GNOME-Splashscreen-manager, tried to install using the button a dif splash screen but the program then closes and I cannot select the new splash screen...... Whenever I reboot without re opening the program or when I do try to re open the program I still get the same blue splash screen with the foot. I could just be totally durr at the whole process but if anybody can help me I would appreciate it.

---

### Post by Eritrean on 2009-03-31
StartUp-Manager (Sudo apt-get install StartUp-Manager or from Synaptic Package Manager) will allow you to download themes, control and change your splash screens.

---

### Post by FraggedLocust on 2009-03-31
> **Golyadkin said:**
> It might be handy to also post that this is for changing the splashscreen in GNOME, not the boot splashscreen (Ubuntu with the orange progress bar) or for KDE. Maybe you can change the topic title? It will be a bit more clear this way.

+1. I didn't know what I was reading til I got to this post.

---

### Post by MarkieB on 2009-10-22
no longer participating in ubuntuforums.org

---

### Post by Bone Crusher on 2010-01-12
I tried just about every thing. I have been googling this for past 5 hours. I can not find out how to change it. I want the MAC theme login. I have it in my downloads folder. Can any one please help me? I running ubuntu 9.10.

---

### Post by hyperair on 2010-01-13
> **Bone Crusher said:**
> I tried just about every thing. I have been googling this for past 5 hours. I can not find out how to change it. I want the MAC theme login. I have it in my downloads folder. Can any one please help me? I running ubuntu 9.10.
This MAC theme you've downloaded, where did you get it from, and what form does it take?

---

### Post by manit on 2010-03-04
I went in gconf-editor & saw the key /apps/gnome-session/options
Here show_splash_screen is UNTICKED
string splash_image says splash/ubuntu-splash.png
But there is no such file on system.
In /usr/share/pixmaps/splash there are gnome-debian-splash.png , gnome-splash.png & no symbolic links.
I have tried
#updatedb;locate ubuntu-splash
/usr/share/example-content/gimp-ubuntu-splash.xcf
#

Also can I change the animation that occurs during booting that is the bar gets filled with orange gradually.

[SIZE="5"]I am interested in doing it via commands without installing additional softwares.[/SIZE]

---

### Post by doas777 on 2010-03-04
this tutorial is over 5 years old, so perhaps a newer one is in order:
[http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html)

---

### Post by Rciky on 2011-02-20
Thanks for the help, I found a lot more useful tools trying to figure this out 8-)

---

### Post by mariavincent on 2011-10-06
[FONT=Comic Sans MS][SIZE=4]*checkout this post to change your startup screen of windows...... amazing post....!!*[/SIZE][/FONT]
[[FONT=Comic Sans MS][SIZE=4]*http://techinfoguru.com/change-startup-log-off-screen-of-windows/*[/SIZE][/FONT]]("http://techinfoguru.com/change-startup-log-off-screen-of-windows/")

---

### Post by phDaemon on 2011-10-20
Figured I'd post something in here relevant to the thread and updated to work the the new versions of ubuntu (10.04-11.10+)...

@MariaVincent, Please only make posts relevant to changing the splash(plymouth) screen on LINUX.

Perhaps this thread can be made sticky and updated as new versions of ubuntu come up or as necessary.

=====

How TO (Taken from [Here](http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04) (Works on 10.04 through 11.10 Tested by me):

Choose your favorite theme and use this command to install (Ex.):
```

sudo apt-get install plymouth-theme-ubuntustudio

```

Now run the command:
```

sudo update-alternatives --config default.plymouth

```

and it should lists currently installed themes and you can type the number and hit enter to choose one you want to use
```

sudo update-alternatives --config default.plymouth

```

There choices for the alternative default.plymouth  display:

```

------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       auto mode
  1            /lib/plymouth/themes/solar/solar.plymouth                           10        manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       manual mode
* 3            /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   100       manual mode

```

Finally execute following command to apply changes and restart your machine to see the new splash screen

```

sudo update-initramfs -u

```



ALTERNATIVELY, you can install Plymouth manager (For 10.04-11.10)
```

sudo apt-add-repository ppa:mefrio-g/plymouthmanager
sudo apt-get update
sudo apt-get install plymouth-manager

```

---

