---
title: "Testing the software updates route 10.04.4 to 12.04b2"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-04-04
Hello All

Set up 10.04.4 32bit on an Asus Pundit AH1 dual core pc with nvidia geforce 6150 integrated graphics, installed restricted nvidia drivers, ubuntu-restricted-extras, set up an email account in evolution, added some photos, music, templates for openoffice 3.2. I have a backup of that home drive.

Then followed [these instructions]("http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/") for a distribution upgrade using Software Update.

Basically just over two hours later, I'm on Unity desktop with no major issues. Very smooth, much better than yesterdays [11.04 -> 12.04 upgrade using live CD]("http://ubuntuforums.org/showpost.php?p=11815098&postcount=20"). If there are any known issues that anyone wants me to check, reply here. I have the pre and post upgrade home drives preserved.

Nvidia drivers updated
Ubuntu-restricted-extras updated and found
Didn't have to dump the dotfiles - configurations seem ok
Wallpaper preserved

Minor stuff

Shotwell offered to import my F-Spot photos, but then quit silently. Restarting and just using File | Import tp import the Pictures/Photos folder worked ok

LibreOffice lost my templates, but Option settings kept (Memory, Java &c). .openoffice.org profile folder still there, and marked as MIGRATED. Template file still in profile, just not recognised as default by libreoffice. 

Evolution migrated my email account over to new version, working fine.

Rhythmbox just worked after rescanning the Music folder

Annoying warning from apt...

```
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Landscape icon arrived in my Application lens. I have not seen that before?

Themes: I had the Radience theme set in 10.04.4, but the upgraded system had a piebald combination of Radience light top bar and window title bars, but dark menubars. Just reset theme.

Global menu: Holy Bats**t,just realised that Global Menus are not working. I've got menu bars in each application window, is that a bug or feature of the upgrade!

Suggestions

Could the Evolution and GIMP icons appear in launcher? I can imagine an office worker type person not realising that their email was still there after the upgrade.

---

### Post by philinux on 2012-04-04
Landscape.

[http://ubuntuforums.org/showpost.php?p=11789897&postcount=82](http://ubuntuforums.org/showpost.php?p=11789897&postcount=82)

---

### Post by keithpeter on 2012-04-04
Hello philinux

Could someone with a few dozen machines use Landscape to help with the post upgrade shenanigans at no cost?

Looks like addware to me at present.

Cheers

---

### Post by philinux on 2012-04-04
> **keithpeter said:**
> Hello philinux

Could someone with a few dozen machines use Landscape to help with the post upgrade shenanigans at no cost?

Looks like addware to me at present.

Cheers

It's of no use to me that's for sure. Maybe some others may use it.

---

### Post by cariboo on 2012-04-04
@keithpeter, you can sign up with Canonical for a free 30 trial of Landscape, but after that, you have to pay for the service. That's one of the ways that Canonical makes money so that they can continue developing Ubuntu. The icon is only there to install the client service, nothing but an applet to install the client is actually installed on your system, until you click the icon and follow the instructions.

---

### Post by keithpeter on 2012-04-04
> **cariboo907 said:**
> @keithpeter, you can sign up with Canonical for a free 30 trial of Landscape, but after that, you have to pay for the service. That's one of the ways that Canonical makes money so that they can continue developing Ubuntu. The icon is only there to install the client service, nothing but an applet to install the client is actually installed on your system, until you click the icon and follow the instructions.

As I understand it Landscape is relevant for larger installations where remote admin of client PCs would be useful. I just had not seen the application before, and wondered where it came from.

Does Canonical run any statistics on the Landscape installations that are hosted on their own server? Will they know what percentage of the installed base upgrade from 10.04.4 -> 12.04? Could be interesting.

---

### Post by kansasnoob on 2012-04-04
> **keithpeter said:**
> Hello All

Set up 10.04.4 32bit on an Asus Pundit AH1 dual core pc with nvidia geforce 6150 integrated graphics, installed restricted nvidia drivers, ubuntu-restricted-extras, set up an email account in evolution, added some photos, music, templates for openoffice 3.2. I have a backup of that home drive.

Then followed [these instructions]("http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/") for a distribution upgrade using Software Update.

Basically just over two hours later, I'm on Unity desktop with no major issues. Very smooth, much better than yesterdays [11.04 -> 12.04 upgrade using live CD]("http://ubuntuforums.org/showpost.php?p=11815098&postcount=20"). If there are any known issues that anyone wants me to check, reply here. I have the pre and post upgrade home drives preserved.

Nvidia drivers updated
Ubuntu-restricted-extras updated and found
Didn't have to dump the dotfiles - configurations seem ok
Wallpaper preserved

Minor stuff

Shotwell offered to import my F-Spot photos, but then quit silently. Restarting and just using File | Import tp import the Pictures/Photos folder worked ok

LibreOffice lost my templates, but Option settings kept (Memory, Java &c). .openoffice.org profile folder still there, and marked as MIGRATED. Template file still in profile, just not recognised as default by libreoffice. 

Evolution migrated my email account over to new version, working fine.

Rhythmbox just worked after rescanning the Music folder

Annoying warning from apt...

```
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Landscape icon arrived in my Application lens. I have not seen that before?

Themes: I had the Radience theme set in 10.04.4, but the upgraded system had a piebald combination of Radience light top bar and window title bars, but dark menubars. Just reset theme.

Global menu: Holy Bats**t,just realised that Global Menus are not working. I've got menu bars in each application window, is that a bug or feature of the upgrade!

Suggestions

Could the Evolution and GIMP icons appear in launcher? I can imagine an office worker type person not realising that their email was still there after the upgrade.

I had the same software sources error:

[http://ubuntuforums.org/showthread.php?t=1950716](http://ubuntuforums.org/showthread.php?t=1950716)

I've just been busy and never got back to that :(

---

### Post by dcstar on 2012-04-04
> **keithpeter said:**
> 
........
Evolution migrated my email account over to new version, working fine.
........

Can you check that all the Contacts Address Books in Evolution work?

---

