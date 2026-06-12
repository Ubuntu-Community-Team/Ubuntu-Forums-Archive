---
title: "Strange touchpad behavior"
date: 2011-09-19
forum: System76 Support
---

### Post by Carleas on 2011-09-19
11.04, star4

Out of the blue, the configuration I set up following the [knowledge76 Star4 guide]("http://knowledge76.com/index.php/Star4") stopped working for my touchpad.  I checked my settings, and I accidentally followed the [Bonobo Professional]("http://knowledge76.com/index.php/BonP4") instructions, because my Star4 says it is a Bonobo *Performance* ("model:bonp4") on the bottom.

Following those instructions, I noticed that they suggest using ```
#! /bin/bash
**gk**sudo fspc -t -l ~/.fspc/fspc.ini
```
where the Star4 instructions suggest regular sudo.  I made that change, and while my settings don't load when I reboot, the GUI configuration panel opens.  This is suboptimal, but at least I don't have ****ing touch-to-click enabled anymore :P

After I noticed that the instructions for the Bonp4 and the Star4 were different, I tried changing it back.  When I do that the GUI doesn't open when I run start-touchpad, but my settings don't load either.  *And* if I open the GUI by running fspc from the terminal, I can't change the configuration, I get an error message when I hit 'apply'.

Ideally, I'd like my settings to load, and to not have the GUI open every time I start up.  But I'm also curious why the change from sudo to gksudo would cause this.  Don't they do basically the same thing?  And if the command ```
fspc -t -l ~/.fspc/fspc.ini
``` isn't supposed to open the GUI, why is it?  And what could I have changed to break the original settings and bring about this state of affairs? or has there been a recent update that could have changed something?

---

### Post by isantop on 2011-09-21
It should be sudo, not gksudo, on both the Bonobo and the Starling. I'm not sure why the discrepancy was there, but I've edited the articles to reflect the proper command. 

As far as I know, there were no updates that would have caused the touchpad to stop working. My recommendation would be to remove the fspc package you have installed with this command:
```
sudo apt-get remove --purge fspc
```
This will remove the package completely, at which point you can go back through the guide and set the touchpad back up again.

---

### Post by Carleas on 2011-10-06
That seems to have done it, hopefully it stays working :)

Thanks for your help!  This seems a generally applicable rule for troubleshooting: when in doubt, reinstall.

---

### Post by Carleas on 2011-10-10
Unfortunately, after restarting again, the stored settings aren't loading.  I can manually change the setting after restarting.

I checked the sudoers file, and I don't see anything wrong with it:
```
username ALL=(ALL) NOPASSWD: /usr/bin/fspc
```
Where 'username' is my username.

What else could be going wrong?  Could upgrading from 10.04 to 11.04 have caused this?  It didn't begin until after I upgraded.

---

### Post by isantop on 2011-10-10
Can you run these commands:
```
which fspc
ls /home
```
This will tell me what the exact path to the fspc binary is, and let me check that the sudoers file is pointing to the proper file. It will also let you check your username for accuracy, and ensure that everything works fine.

---

### Post by Carleas on 2011-11-09
```
$ which fspc
/usr/bin/fspc
$ ls /home
mjc
```

Also, I've updated to 11.10, and the problem persists here.  One change:  I get an error message when I run fspc in the terminal:
```
$ sudo fspc

(fspc:3706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(fspc:3706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(fspc:3706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(fspc:3706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```
It prints out four times like that, but the fspc gui opens anyway.  Thought that might be relevant (?).

---

### Post by isantop on 2011-11-09
Those error messages don't indicate a problem, at least not a big one. It looks like a minor theming incompatibility between fspc's GTK2 and Ubuntu's GTK3. It shouldn't pose any problems in getting the utility to run.

What happens when you run sudo fspc from a terminal?

---

### Post by Carleas on 2011-11-21
When I run sudo fspc, the GUI pops up and I can manually change the behavior.  It's just not loading the settings I've set it to load as default.

---

### Post by isantop on 2011-11-22
Is the "start-touchpad" command added to your startup applications list?

---

### Post by Carleas on 2011-12-02
It seems to working normally now at startup, I don't know what changed or why that happened, the only setting I've changed recently is the boot order :confused:

It is doing a strange thing of forgetting the horizontal scroll settings when it wakes up (and only horizontal scroll, tap-to-click setting persists).  That's a fairly minor annoyance.  The biggest problem with it is that the horizontal scroll areas of the touchpad function as mouse clicks in certain circumstances, so that even if tap-to-click is off, it will occasionally click with only touchpad input.  The happens mainly in the filesystem explorer, and the click won't open a folder, but it will highlight it.  Not critical, but probably not how it's supposed to work.

Thanks for your help, this is resolved as far as I'm concerned.

BTW, is there a manual available for fspc?  I don't get anything with 'man fspc'.

---

