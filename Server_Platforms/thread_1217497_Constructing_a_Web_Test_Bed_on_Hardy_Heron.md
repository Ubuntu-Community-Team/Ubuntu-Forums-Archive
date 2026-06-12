---
title: "Constructing a Web Test Bed on Hardy Heron"
date: 2009-07-19
forum: Server Platforms
---

### Post by aptdude on 2009-07-19
[SIZE=4]**Constructing a Web Test Bed on Hardy Heron**[/SIZE]
aptdude
19Jul2009
 
 
[SIZE=3]**Forward:**[/SIZE]
I would like to develop this post into a "How to," though right now, I have a sampling of ONE, and that's a bit limiting. So, I'd like for folks to add any contributions that they could to this effort. The intent is to come up with a "minimum" set of applications on Hardy Heron that will provide a two-CD recovery for a web test bed (aka web development environment). 
 
 
[SIZE=3]**Prolog:**[/SIZE]
I'm in the process of starting up a business and I was concerned about my eventual web presence. I want most of the items to be open source, such as the shopping cart, content manager, etc., and I wanted to ensure their interoperability, base functionality, and look-and-feel. I checked out various sites, but I couldn't really get a feel for the complexity of the individual component, let alone how these bits and pieces would weave together into something that looked uniform to a potential customer. In short, I needed a web test bed: An install that would be compatible with my hosting service, and something I could wipe out and reinstall quickly and easily.
 
 
[SIZE=3]**Specifications:**[/SIZE]
My particular provider runs Debian with Apache Server, PHP, and MySQL. Ubuntu lined up with this perfectly. At this point, I should express that I am not a guru of any Linux, or any UNIX, or for that matter, any particular OS. I know enough to be dangerous on many OS's, and I have had some exposure to both BSD and AT&T UNIX's, but that was years ago.
 
 
My target hardware is a PC I bought years ago, and it no longer can be migrated along the Windows product line. It had Win2000 on it, but support for that will end later this year. Here's a summary of this machine:
Dell XPS_R
Intel Pentium III 400MHz
STI 4MB Graphics Card
[LEFT]Linksys WMP11 v27 Wireless B Card
Onboard Intel 10/100bT NIC
Onboard USB 1.0 
384 MB Memory
10 GB IDE Hard Drive
CD ROM Drive
Floppy Drive[/LEFT]
 
 
[LEFT]As you can see, this isn't exactly the cutting edge of today's technology, but it will do. [/LEFT]
 
 
[LEFT][SIZE=3]**Methodology:**[/SIZE]
My advantage with this particular hardware is that I know it all worked under the previous operating system. In fact, I kept that hard drive just in case I needed something during the build. The major issue with the setup is with the LAN connection. This particular PC is in another room, using the wireless. So, I needed to provide some temporary connectivity until wireless was working on Ubuntu. This is how I began:[/LEFT]
 
 
[LEFT]1. Keep a journal.
2. Find your current wireless and USB drivers on the old OS. Copy and burn these to CD.
3. With the old OS installed, upgrade the BIOS to the latest version available.
4. Find a usable hard drive so that you can keep the original as a reference. 
5. Buy or build a CAT 5 cable so that you are dealing with hardwired connections to the internet.
6. Make sure the old OS still works with the upgraded BIOS and the cable connection.[/LEFT]
[INDENT]In this case, the hardware was out-of-date, but I could still get an upgrade to the BIOS. The BIOS limited me to 60 GB for the hard drive, and I just happened to have a 10 GB IDE drive lying around. I hadn't used the hardwire NIC for about five years, so I needed to make sure it worked before I continued.
 
[LEFT]I have access to another PC that has the capabilities to burn CD's. On that machine, I downloaded both Jaunty Jackalope and Hardy Heron Server version ISO images and burned them to CD's. So, the next step is:[/LEFT]
 
[/INDENT]7. Download and burn images of Ubuntu server for both the current release, as well as the LTS release.
[LEFT]8. Install the new drive in the PC.
9. Ensure the CDROM is in the BIOS boot path.[/LEFT]
[INDENT]I first tried Jaunty Jackalope, but Jaunty didn't work out. I ended up with a "Loading Please Wait..." and the PC died, even after adding acpi=off to the boot line. Hardy didn't have that issue, so I continued with that release. I also turned off acpi with Hardy, since motherboard power control wasn't an interest for me. So, continuing the install:
 
[/INDENT]10. Boot from the Ubuntu CD (in my case, Hardy Heron).
[LEFT]11. At the welcome screen, edit the boot command line to include "acpi=off" at the end of it.
12. Follow the install guide for the particular release (details vary; document everything).
13. At the application installation selection, install LAMP and SAMBA.
14. Boot.[/LEFT]
[INDENT]I defer to the many helpful threads to help get your particular harware to this point. As a point of reference, it only took me one try with Hardy to get the system to come up with a CLI login. LAMP will install Apache server, MySQL, and PHP. SAMBA will allow you to share files, which will be needed later.
 
[LEFT]Though a server install typically would not involve a GUI, I prefer to use one, and one of the eventual goals is to view web pages locally so I can tweek their operation and look. I also needed to use ndiswrapper to get the wireless working, so I went with the GUI version, ndisgtk. [/LEFT]
 
[/INDENT]15. Install the following applications:
```

[LEFT]sudo apt-get install xorg gdm gnome-core 
sudo apt-get install firefox[/LEFT]
sudo apt-get install synaptic
[LEFT]sudo apt-get install netapplic
sudo apt-get install ndisgtk
sudo apt-get install gnome-system-tools
sudo apt-get install policykit-gnome
sudo apt-get install phpmyadmin[/LEFT]

```
[INDENT]When installing phpmyadmin, choose apache2 server. 
 
[/INDENT]16. Configure wireless.
[INDENT]I spent two weeks on that one line. To save some time, I highly recommend following url:
[LEFT][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions)
I used ndisgtk GUI to associate the windows driver for my wireless with ndiswrapper. I then built a script that I run after reboot to get the wireless working. If you also end up using a script, don't forget to set the file attributes with:[/LEFT]
[/INDENT][INDENT]```

[LEFT]chmod 755 [filename][/LEFT]

```
 
[LEFT]so that it will be executable.[/LEFT]
[/INDENT]17. Verify that wireless works after reboot.
[INDENT]```

 
[LEFT]iwconfig[/LEFT]

```
 
[LEFT]This should show that wlan is configured and up. Pinging you router will also verify connectivity.[/LEFT]
 
```

 
[LEFT]ping [routerIPaddress][/LEFT]
 

```
 
[LEFT]Use Ctrl-C to cease the ping.[/LEFT]
 
 
 
 
[/INDENT]18. Permanently remove the CAT 5 cable.
[LEFT]19. Configure SAMBA.[/LEFT]
[INDENT]SAMBA's configuration is fairly simple. Using an existing username, add it as a samba account:
```

[LEFT]sudo smbpasswd -a [username][/LEFT]

```
 
[LEFT]Create a share. This creates a fileshare folder under desktop:[/LEFT]
```

[LEFT]cd ~[username]/desktop
mkdir fileshare[/LEFT]

```
 
[LEFT]Add that info to SAMBA's configuration file:[/LEFT]
```

[LEFT]sudo gedit /etc/samba.smb.conf[/LEFT]

```
 
[LEFT]At the bottom of the file, add:[/LEFT]
```

[LEFT][test]
path = /home/[username]/Desktop/fileshare
available = yes
valid users = [username]
read only = no
browsable = yes
public = yes
writable = yes[/LEFT]

```
[LEFT]where [username] is the account added with smbpasswd. Test will be the sharename. Then, restart SAMBA:[/LEFT]
```

[LEFT]sudo /etc/init.d/samba restart[/LEFT]

```
 
 
[/INDENT]20. Check SAMBA operation by passing files between this machine and a Windows one. Note that Windows uses CR+LF as a newline vice just CR for Linux, so the formatting of text files may not be what you expect.
 
21. Check the operation of phpmyadmin by launching firefox and opening the url:
> [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
[INDENT] 
[LEFT]The credentials are a username of "root", with the MySQL administrative password you set when LAMP was installed.[/LEFT]
 
 
 
 
[LEFT]At this point, my hard drive had roughly 2 GB allocated. I felt that I was getting close to a full CDROM with compression on a backup.[/LEFT]
 
 
 
 
[/INDENT]22. Backup the system by using tar. This is done by:
[INDENT]```

 
[LEFT]sudo su[/LEFT]
 
[LEFT]cd /[/LEFT]
 
[LEFT]tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /[/LEFT]
 
 
 
 

```
 
[LEFT][SIZE=2][FONT=Verdana]My archive was roughly 450 MB, which is less than the 2GB SAMBA limit and it will easily fit on a CDROM. [/FONT][/SIZE][/LEFT]
 
 
 
 
 
[/INDENT][FONT=Verdana][SIZE=2]23. Move the backup.tgz file to the SAMBA share.[/SIZE][/FONT]
[LEFT][SIZE=2][FONT=Verdana]24. Copy it across and burn it to CD.[/FONT][/SIZE][/LEFT]
[INDENT][FONT=Verdana][SIZE=2]The copy took considerable time (25 minutes). This final set of steps constitues the "moment of truth." This will wipe out the hard drive and recover from the backup.[/SIZE][/FONT]
 
 
 
[/INDENT][FONT=Verdana][SIZE=2]25. Put the Ubuntu CDROM in the drive. Use the same release that you built this system with.[/SIZE][/FONT]
[LEFT][SIZE=2][FONT=Verdana]26. Boot from the CD, making exactly the same choices you made previously. Don't forget to edit the command line with "acpi=off".[/FONT][/SIZE]
[SIZE=2][FONT=Verdana]27. Boot the system to a command prompt. You will need to remove the Ubuntu CD first.[/FONT][/SIZE]
[SIZE=2][FONT=Verdana]28. Place the CD containing backup.tgz in the tray.[/FONT][/SIZE]
[SIZE=2][FONT=Verdana]29. Mount the CD and copy the file to root (/).[/FONT][/SIZE][/LEFT]
 
[SIZE=2][FONT=Verdana]30. Restore the system with the following:[/FONT][/SIZE]
[INDENT]```

 
[LEFT]sudo su[/LEFT]
 
[LEFT]cd /

tar xvpfz backup.tgz -C /[/LEFT]

 
 

```
 
 
[/INDENT][FONT=Verdana][SIZE=2]31. Reboot &#8211; everything will return to the state that existed at step 21.[/SIZE][/FONT]
 
[LEFT][SIZE=2][FONT=Verdana]I now have a two disk backup that configures my wireless and has the base cofiguration that mimics my hosting supplier, without running temporary cables between rooms. I probably could add USB testing, Java testing, and others, but I felt that this configuration was a good minimum set for a web test bed. Please post a note is you have done something similar, so that the community can learn from your experience.[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=2][FONT=Verdana][SIZE=3]**Reference URL's:**[/SIZE][/FONT][/SIZE]
[SIZE=2][FONT=Verdana]Ubuntu boot options: [/FONT][/SIZE]
[[SIZE=2]https://help.ubuntu.com/community/BootOptions[/SIZE]]("https://help.ubuntu.com/community/BootOptions")
[SIZE=2]Gnome:[/SIZE]
[[SIZE=2]http://ubuntuforums.org/showthread.php?t=799850[/SIZE]]("http://ubuntuforums.org/showthread.php?t=799850")
[[SIZE=2]https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496[/SIZE]]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496")
[SIZE=2]Firefox:[/SIZE]
[[SIZE=2]http://ubuntuforums.org/showthread.php?t=72496[/SIZE]]("http://ubuntuforums.org/showthread.php?t=72496")
[SIZE=2]Boot Log (I didn't perform this change):[/SIZE]
[[SIZE=2]https://bugs.launchpad.net/upstart/+bug/98955[/SIZE]]("https://bugs.launchpad.net/upstart/+bug/98955")
[SIZE=2]Wireless:[/SIZE]
[[SIZE=2]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions[/SIZE]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions")
[[SIZE=2]http://lxer.com/module/newswire/view/46385/index.html[/SIZE]]("http://lxer.com/module/newswire/view/46385/index.html")
[[SIZE=2]http://www.linuxant.com/driverloader/drivers.php[/SIZE]]("http://www.linuxant.com/driverloader/drivers.php")
[SIZE=2]Samba:[/SIZE]
[FONT=Verdana][SIZE=2][https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]tar Backups:[/SIZE][/FONT]
[SIZE=2][FONT=Verdana][http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+usb](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+usb)[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=2][FONT=Verdana]/aptdude[/FONT][/SIZE][/LEFT]

---

### Post by windependence on 2009-07-19
You can save yourself a ton of trouble by using an external wireless access point instead of trying to get wireless working on Linux. IMHO, wireless is still not ready for prime time in Linux, even on newer versions of the OS. You can just stick a WAP by your machine, and bammo! You're there. They're cheap too.

-Tim

---

