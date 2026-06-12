---
title: "How to make CLi always start over installed DE"
date: 2013-09-03
forum: Server Platforms
---

### Post by biggyk on 2013-09-03
Hi there,

I installed Ubuntu Server for home use but I also installed lubunutu-desktop just to have a gui but I want the system to boot up in command and then I can select startx if need be. Right now the DE is starting automatically at boot.


Thanks

---

### Post by tripp98 on 2013-09-03
[http://askubuntu.com/questions/74645/possible-to-install-ubuntu-desktop-and-then-boot-to-no-gui](http://askubuntu.com/questions/74645/possible-to-install-ubuntu-desktop-and-then-boot-to-no-gui)

---

### Post by steeldriver on 2013-09-03
There are several different ways of doing this (through grub, for example), however assuming that you have installed one of the more recent versions of lubuntu-desktop (which use lightdm as the display manager), you should be able to prevent it from starting automatically by creating a file called lightdm.override containing the single word 'manual' in the upstart directory /etc/init, e.g.

```
echo 'manual' | sudo tee /etc/init/lightdm.override
```

You can check whether lightdm *is* your default display manager by looking in the /etc/X11/default-display-manager file, e.g.

```
cat /etc/X11/default-display-manager
```

If your session doesn't look right when you start it manually, you may want to try 'startlxde' instead of plain 'startx'

---

### Post by Bashing-om on 2013-09-03
biggyk; Hi !

Easily done.. for testing purposes to insure you are comfortable, prior to making it permanent:
Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "text" -without the quotes-; ctl+x to continue the boot process.
You should now boot to tty1 console.
Depending on which Desktop Environment you are using depends on the command to start the GUI.
unity -> "sudo service lightdm start
GDM -> sudo service gdm start
xfce -> startxfce4 (if using initrc then -> startx
else ???
Then to make it pemanent:
edit the file "/etc/default/grub" After making a back up.
there are 2 possibilities and either or both together may work;
1. Replace the terms "quite splash" in this file with "text"
2.Within that file is "# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console" ;; just un-comment the line.

As you have changed this file one must run:
```

sudo update-grub

```
for the change(s) to be effective.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by biggyk on 2013-09-03
Added the word text to the grub file and used [FONT=Ubuntu Mono]sudo /etc/init.d/lightdm start[/FONT] and it worked!!

How would then I kill lightdm back to command without restarting?

---

### Post by Bashing-om on 2013-09-03
biggyk; Outstanding ...
now-a-days the use of "/etc/init.d/" has been depreciated .. have you made alterations such that "sudo service lightdm" is not functioning ?

and to stop the GUI ... do:
key combo ctl+alt+f1 to get back to the terminal and then terminal command:
```

sudo service lightdm stop

```
[INDENT][INDENT]should workie great last long time
[/INDENT][/INDENT]

---

### Post by houstonbofh on 2013-09-03
Now for the easy method...

sudo apt-get purge lightdm

You still have X installed, and you can run GUI apps over ssh with "ssh -X user@ipaddress" and launch nautilus running on the remote machine but displaying on your desktop.

---

### Post by biggyk on 2013-09-03
Thank you, will try it out when I have a chance. This was practice on a virtualbox install. I just installed Ubuntu Server on my box and forcing myself to stay away from GUIs to learn command.

---

