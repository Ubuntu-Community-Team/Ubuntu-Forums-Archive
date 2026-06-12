---
title: "Cant Install Wow cataclysm"
date: 2010-12-13
forum: Wine
---

### Post by rob2nd9th on 2010-12-13
Ok Im running ubuntu 9.04

Wine 1.2

Ran "sudo mount -o remount,unhide /dev/sr0" this un-hid the files but I still get Accses Denied when i try to install it

Thank for any help, managed Wotlk & Bc ok??

---

### Post by Tweak42 on 2010-12-13
> **rob2nd9th said:**
> Ok Im running ubuntu 9.04

Wine 1.2

Ran "sudo mount -o remount,unhide /dev/sr0" this un-hid the files but I still get Accses Denied when i try to install it

Thank for any help, managed Wotlk & Bc ok??

I used the Launcher.exe to download my Cataclysm upgrade, but this might help.  There's a similar problem with the Starcraft II dvd installer, something about formatting for mac support causing the access denied error. 

```
sudo umount /dev/cdrom
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
```
Source:[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

---

### Post by rob2nd9th on 2010-12-14
:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

:~$ 

This it what i get?

If i use sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/

I get as far as this

[IMG]http://i138.photobucket.com/albums/q244/rob2nd9th/Screenshot-3.png[/IMG]

---

### Post by rob2nd9th on 2010-12-14
oK

Used sudo umount /dev/cdrom
then sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/

Copied the CD to a file on HD then installed useing the Wine install

all go so far.

---

### Post by chousho on 2010-12-14
While this isn't exactly a solution to your problem, I'll tell you what I've had luck doing.

There are a few options: for WoW I actually copied my folder over from my Windows partition and had it run fine with the -opengl flag and in windows mode.

Also, as far as WC3 and the FT expansion, the downloaders from us.battle.net have worked fine. So you may be able to do that with WoW, too.

One thing you may want to do, though, is to use separate wineprefixes for games. This way if you have trouble with one game, you can delete that specific one, rather than potentially causing issues with other wine games/apps you've installed.

So, for instance if you want a wineprefix just for wow:

You could make a directory called .wine-wow in your home folder.

Then to launch the game from console, or a deskto icon, you'd have this:

```
env WINEPREFIX="/home/<your username>/.wine-wow" wine "C:\Progam Files\WoW\Launcher.exe" -opengl
```

---

### Post by dslreports_snakeoil on 2010-12-15
That is what I am doing. I copied the wow folder from my windows box, onto a USB drive. I then copied that onto my linux box into the .wine/c:/programs/ folder.
I am going to "import" that into playonlinux. I think it should work.
Though the last time I attempted to run WOW cata. on that linux box, it crashed at the launcher screen. The screen opened, it said it was getting news [where the html ads are] and the tools were updating. It "froze" like that for about 2 minutes, then a window opened saying the app had encounters an error. I got tired of that, so I wiped the Hard drive, installed 10.10, wine, and playonlinux. Now I am copying the files over [I ran my PC wow once today before copying, so they should be updated]. I should know soon, if it works.. lol.
Now to fix the sound...

---

### Post by rob2nd9th on 2010-12-16
Thx all, got it sorted playing well with no problems :)

Could some one mark this as Solved plz?

---

### Post by chousho on 2010-12-18
> **dslreports_snakeoil said:**
> I am going to "import" that into playonlinux. I think it should work.
...
Now to fix the sound...

Make sure sound is alsa under winecfg. Also check the "Hardware" option under WoW for audio. Sometimes my audio shuts off randomly, and checking or unchecking the hardware option will cause the sound to come back.

POL is hit or miss for me, so I've been mainly using regular wine from the repos and just using different prefixes for each separate program. I find it easier to just make a new directory and
```
env WINEPREFIX="~/.wine-appname wine "C:\...etc"
```
Than having to use a different program. Plus it leaves me feeling a little more in control (whether that's a placebo or not).

Just wondering, you're using the -opengl after the program name, right? Have you tried it with and without? I'm not sure if it will help, but I'll give you what settings I currently have for my WoW install's winecfg (maybe something will help).
> 
**[SIZE="3"]Applications:[/SIZE]**
  Windows Version: Windows XP

**[SIZE="3"]Graphics:[/SIZE]**
  Allow the windows manager to decorate the windows (checked)
  Allow the windows manager to control the windows (checked)
**  Direct3D**
    Vertex Shader Support: Hardware
  Screen Resolution: 96dpi

**[SIZE="3"]Audio:[/SIZE]**
**  Sound Drivers**
    ALSA Driver (checked)
 ** DirectSound**
    Hardware Acceleration: Emulation
    Default Sample Rate: 44100
    Default Bits Per Sample: 16
As far as video, this is my config file (found in WTF/Config.wtf in your WoW directory: [http://paste.ubuntu.com/545434/](http://paste.ubuntu.com/545434/)

---

