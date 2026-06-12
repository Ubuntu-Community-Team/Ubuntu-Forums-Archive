---
title: "Tell me your HOWTO needs"
date: 2008-02-02
forum: The Cafe
---

### Post by x1a4 on 2008-02-02
Hi,

A few months ago I got me a [Web site]("http://hex1a4.net/") containing a [Xubuntu section]("http://xubuntu.hex1a4.net/").  So far I've written three HOWTOs for it and would like to do more but lack ideas.  What are some of the things you would like to be able to do on your *buntu system but don't know how and don't feel like researching?  Let me know and I'll do the work for you.  

Thank you.  

PS  If you feel like doing it, I would appreciate a critique of the site.  Thanks.

---

### Post by Ultra Magnus on 2008-02-02
DVB-T sticks - I still haven't managed to get my freecom stick to work

---

### Post by Nessa on 2008-02-02
How to put Xubuntu on another user account... (main account is Gnome)

---

### Post by hhhhhx on 2008-02-02
how to tri-sli 3 nvidia 8800 ultra's in feorda, its ni-impossible

---

### Post by LostMagix on 2008-02-02
How to get up my side tilt on my scroll wheal to work....

---

### Post by x1a4 on 2008-02-08
I've had a very busy week and couldn't look into your requests but should be have some time next week.  

Ultra Magnus: Which revision is your DVB, 4 or earlier?

Nessa: What do you mean by putting Xubuntu on another account?  You can just install the **xubuntu-desktop** package, select Xfce when you're logging in, and when asked tell GDM to start Xfce by default, or change your user's ~/.dmrc like so: 
```

[Desktop]
Session=xfce4

```

---

### Post by x1a4 on 2008-02-14
> **LostMagix said:**
> How to get up my side tilt on my scroll wheal to work....

What kind of mouse is it? Manufacturer, model?

---

### Post by LostMagix on 2008-02-15
Rocketfish 2,4

[http://www.rocketfishproducts.com/pc-84-3-rocketfish-24ghz-wireless-laser-mouse.aspx]("http://www.rocketfishproducts.com/pc-84-3-rocketfish-24ghz-wireless-laser-mouse.aspx")


I got three days left to get it working.

---

### Post by gn2 on 2008-02-16
> **Nessa said:**
> How to put Xubuntu on another user account... (main account is Gnome)

Switch to the user you want to have Xubuntu, then run ```
sudo apt-get install xubuntu-desktop
```

Then select XFCE under Sessions at log-in.

---

### Post by gn2 on 2008-02-16
How-to: Create a GUI Menu Editor for XFCE that actually works properly......?

---

### Post by billgoldberg on 2008-02-16
The thing that I have always wanted and never found (I did find how-to's but they were to hard) was network how-to's.

Like setting up file sharing between 2 ubuntu boxes (2 computers hooked to the router).

Or file sharing between ubuntu and windows.

Could be samba, shh, ftp, ...

The problem with the existing how-to's is they all presume you know something about networks.

So a drop-dead easy how-to were every step is explained (every!!!).

And the commands should always be explained to.

---

### Post by x1a4 on 2008-02-16
Okay, first something I should have mentioned in my original post.  Please don't ask about hardware issues as I'm not going to buy things that may not work with Linux nor just to add content to my site.  Although I will try to help those of you who posted already, starting with LostMagix since he's on a clock.  Also, please don't ask about Gnome or KDE specific issues as I don't use them.  Xfce, AfterStep, FVWM-Crystal are OK. 

gn2: creating the menu is beyond my capabilities.  To create a better menu editor for Xfce you first have to learn C, get Xfce's source, learn about freedesktop.org's menu rules, modify Xfce menu, and recompile Xfce.  There should be a freedesktop.org-compliant menu in Xfce5. 

LostMagix:  I think I have a solution for you but you will have to test for me, so be sure you backup everything so that you'll be able to undo if something doesn't work.  Also, be sure to tell me if the mose works but not the way it's supposed to--along with what exactly it is doing.  Please also tell me if it does work. 


Here's what I came up with to get your rocketfish going. 

**Step 1**

Open a terminal and get root priviledges: ```
sudo -s
```

**Step 2**

create a device node for the mouse: ```
mknod -m 0644 /dev/input/rocketfishmouse b 2 4
```
(the lone **b** is not a typo--it tells mknod that a block device is being created.  The **2** and **4** are not the value twentyfour, they're separate. 

You should probably skip this step until we get the mouse working properly.  

**Step 3**

Create a udev rule by creating the following file: 

/etc/udev/rules.d/10-udev.rules
(the 10 at the beginning of the file name is important)

add the following to it: 
```
KERNEL=="event*", SYSFS{manufacturer}=="Rocketfish Products.", SYSFS{product}=="Rocketfish Wireless Laser Mouse", NAME=="input/rocketfishmouse", MODE=="0644"
```
(it's all one line)

If you haven't created the device node in Step 2, replace **input/rocketfishmouse** with an available event node which is something like this: **input/event#**.  Where **#** is a number from 0 to 6.  Check to see which of these nodes are in use like so: 
```
ls -l /dev/input/by-id/
ls -l /dev/input/by-path/

```
The symlinks in those directories will point to device nodes in /dev/input/ Use one that's not being used. 

**Step 4**

Add the following to your /etc/X11/xorg.conf file: 
```

Section "InputDevice" 
  Identifier "RocketfishMouse" 
  Driver "mouse" 
  Option "Protocol" "evdev" 
  Device "/dev/input/rocketfishmouse"
  Option "Dev Name" "Rocketfish Wireless Laser Mouse"
  Option "Buttons" "9" 
  Option "ZAxisMapping" "6 7 8 9"
EndSection

```

the "Dev Name" option ***must* be identical** to the device name in the udev rule we defined in Step 3

If you skipped Step 2, replace **/dev/input/rocketfishmouse** with **/dev/input/event#**.  Where **#** is the same number you specified in Step 3. 

Change the mouse's **InputDevice** entry in **Section "ServerLayout"** to **"RocketfishMouse"**

**Step 5**

Execute: ```
xmodmap -e "pointer = 1 2 3 8 9 4 5 6 7"
```

**Step 6**

Restart X: ```
/etc/init.d/gdm restart
```

If you skipped Step 2 and everything works fine, replace all instances of  **input/event#** with **input/rocketfishmouse** and create the node as specified in Step 2.

If your first test is Firefox, and it doesn't work reconfigure Firefox.  In about:config

Set ```
mousewheel.horizscroll.withnokey.action=0
``` and ```
mousewheel.horizscroll.*
```

---

### Post by drfox on 2008-02-16
I have a laptop which I would like to backup to a SMB share on a Buffalo LinkStation. How do I configure the laptop to backup only when it's on the home network (and not, for example, at Starbucks)?

Larry

---

### Post by TeaSwigger on 2008-02-17
Never mind, just read page 2.

---

### Post by LostMagix on 2008-02-17
Didnt seem to work, not sure what went wrong....

---

### Post by madking on 2008-02-17
how to get my kubuntu system to auto mount/detect usb, without having to insert them on bootup. I have a novetell wireless card, thats usb, but i have to have it pluged in at boot up, and if i remove it after, i have to reboot to get it detected again.

---

### Post by Vitamin-Carrot on 2008-02-17
I know this isnt a how too request but ...

Hows about wallpapers that are bigger than 1024x768

---

### Post by LostMagix on 2008-02-18
I wil be leaving in the morning, so you dont have to worry about the HowTo.

Thanks for gesture, i just have not had the time to figure it out.

---

### Post by rabid9797 on 2008-02-18
HOWTO: Fix Bug #1 ?

---

### Post by x1a4 on 2008-02-21
> **LostMagix said:**
> Didnt seem to work, not sure what went wrong....

Did the whole mouse stop working or just the tilt that didn't work?  

Try reconfiguring xorg.conf like so: 
```

Section "InputDevice"
       Identifier "RocketfishMouse"
       Driver      "mouse"
       Option     "Protocol" "evdev" 
       Option      "Device"        "/dev/input/event#"
       Option      "Buttons"       "10"
       Option      "ZAxisMapping"  "4 5 8 9"
EndSection

```
If this doesn't work change "ZAxisMapping" to "4 5 6 7" as well as change the Driver to "evdev" and comment the "Protocol" option. Try different combinations.

---

### Post by x1a4 on 2008-02-21
> **LostMagix said:**
> I wil be leaving in the morning, so you dont have to worry about the HowTo.

Thanks for gesture, i just have not had the time to figure it out.

Oh.  Sorry I couldn't help. :(  It seems like a nice mouse, it's a shame it doesn't work fully.  Although I'm sure it's possible to get it working.  It's just a matter of setting the right button mapping.

---

### Post by x1a4 on 2008-02-21
> **Vitamin-Carrot said:**
> I know this isnt a how too request but ...

Hows about wallpapers that are bigger than 1024x768

[Wallpaper Review]("http://www.wallpaperreview.com/widescreen.html") has links to sites with large wallpapers. 
[Widescreen Wallpaper]("http://www.widescreenwallpaper.info/")
[Sexy Desktop]("http://www.sexydesktop.co.uk/")

---

### Post by Chris Morin on 2008-02-21
How to get Compiz working with an ATI X1400 grafics card

---

