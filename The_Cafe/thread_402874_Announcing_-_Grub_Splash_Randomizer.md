---
title: "Announcing - Grub Splash Randomizer"
date: 2007-04-06
forum: The Cafe
---

### Post by WakkiTabakki on 2007-04-06
Hi all

EDIT 2007-12-21: Fixed a few bash-related problems with the script. Should work properly now...

The GrubSplashRandomizer is a shell script that gets run when Ubuntu starts up, and  chooses a random grub boot splash image for the next boot.
The script chooses from all the splash images in a folder, so once installed there is no need for any configuration to add or remove splashes, only to add or remove files in that folder...

First of all, read through steps 5 and 6, which is the uninstall and recovery instructions. If you read it and don't understand squat then this whole thing is probably not for you and may (if something craps up) cause your computer to refuse to boot...

[SIZE="3"]**1. Get and install the script and make it run when entering runlevel 2**[/SIZE]
1. Download and unpack the attached file [randomize-grub-splash.gz]("http://ubuntuforums.org/attachment.php?attachmentid=53865&stc=1&d=1198232939")
2. Install the script to run when entering runlevel 2
```

> sudo cp randomize-grub-splash /etc/init.d
> sudo ln -s /etc/init.d/randomize-grub-splash /etc/rc2.d/S99randomize-grub-splash

```
<edit2>Anyone "in-the-know", would it be better to put the code in [FONT="Courier New"]/etc/rc.local[/FONT]?</edit2>

[SIZE="3"]**2. Configure grub to display splash**[/SIZE]
```
> sudo gedit /boot/grub/menu.lst
```
Find the line starting with splashimage. If it's not in there, add it yourself:
```
splashimage=(hdx,y)/boot/splash.xpm.gz
```
x and y should be replaced with the numbers telling which drive (x) and partition (y) the grub files are on. They're most likely the same as your Ubuntu root partition, so find the grub entry for your default Ubuntu-boot, mine looks something like this
>  
title		Ubuntu, kernel 2.6.20-14-generic
root		**(hd0,5)**
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=560dde69-d78b-45c9-aa98-efe0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet
savedefault

so, my splash-line is:
> splashimage=**(hd0,5)**/boot/splash.xpm.gz


[SIZE="3"]**3. Configure the boot folder for the randomize script**[/SIZE]
Create the folder in which to put all you nifty little boot images
```
> sudo mkdir /boot/splashimages
```
Any grub splash images in 'xpm.gz'-format put in this folder will be used by the randomizer script...


[SIZE="3"]**4. Get some grub splashes...**[/SIZE]
1. Go to [http://www.gnome-look.org](http://www.gnome-look.org)
2. Search for 'grub', and it should give you 40 or so different ones
3. Download the ones you like and save them somwhere
4. Move all the files you downloaded (make sure they are in xpm-format and compressed with gz)
```
> sudo mv *.xpm.gz /boot/splashimages
```

To add more splash images, simly put them in the  /boot/splashimages folder. To disable a splash image, simply delete it from the folder, or rename it's extension (the script uses all files in the /boot/splashimages folder that ends with 'xpm.gz').

[SIZE="3"]**4.5. Make sure a splash is selected for next boot**[/SIZE]
<edit1>Manually run the randomizer script this first time, to get a splash images on the next boot (if not run, you'll need to reboot twice to get your splash image the first time...)
```
> sudo /etc/init.d/randomize-grub-splash start
```
</edit1>

[SIZE="3"]**5. Uninstall the script**[/SIZE]
1. Remove the two files created in step 1
```

> sudo rm /etc/init.d/randomize-grub-splash
> sudo rm /etc/rc2.d/S99randomize-grub-splash

```
2. Remove the splashimage-line from menu.lst (the one you added in step 2 above)


[SIZE="3"]**6. OMG PANIC! My computer won't boot anymore, what do I do!**[/SIZE]
1. Pop your Ubuntu live CD in you CD-drive
[INDENT][I]- What!?! But I don't have one!
- Well dude, I told you, you should have read this before starting
- Yeah, well thats not helpful now, is it!?!
- Nope, it's not.
- So what do I do now?
- I don't know, you apparently don't follow instructions anyway so do whatever...
- Well, screw you and your stupid script!
- Yeah, ok, thanks and please come again <pling>...
[/I][/INDENT]
2. When the comp has booted, open a terminal and mount your root partition
3. Follow the uninstall instructions above (of course, /etc/init.d/... should be <yourRootMountFolder>/etc/init.d/...)


Cheers
/N

---

### Post by kaspersky on 2007-06-26
[SIZE="4"]thanks   WakkiTabakki
it is a nice idea :p
but i   followed  your instructions  but nothing happened  :(:(
i downloaded script - installed it successfully  - mkdir splashimages- edit menu.lst   .... etc
there is one question  : should i  write any  code in this file ( /etc/rc.local)  ?
i do not understand  this point
pleas  more explanation  
thank you[/SIZE]

---

### Post by WakkiTabakki on 2007-10-05
Hi
Sorry, the thread attracted so little attention I managed to forget all about it...

Well, step 1 is supposed to make the script run when entering runlevel 2... But there's been talk about changing the startup procedure. Don't really know if thats been done now in Gutsy...

This should work though:

Step 1:
Skip the ln -s command, and put the following in your /etc/rc.local before the exit 0-line (ofcourse)
```
/etc/init.d/randomize-grub-splash start
```

If it still doesn't work. Make sure the scripts got execute permissions...

Good luck!
/N

---

