---
title: "Presenting myself &amp; problems with zv6000"
date: 2005-12-08
forum: The Cafe
---

### Post by debernardis on 2005-12-08
Hi, I am new to this forum.

I live in Sicily with my wife (and hopefully in the next five months a toddler, which presently is happily growing in her womb), two notebooks and one smartphone, plus a number of other gadgets.

I have always been attracted by linux, but sticked with M$ products until I got too much fed up with their kludgy behaviour. I have been experimenting with penguin distros just in the last two or three months.
Ubuntu (Kubuntu) and Puppy linux gave me nice results, and some days ago I bought a brand new notebook, on which I intended to install a nice Ubuntu environment.

BUT! X doesn't like to start on this HP Pavilion zv6000 with ati radeon xpress 200, complaining of strange things about this video card.

Presently I am investigating around the 'Net for a workaround.

When I don't mess with computers, I am an addiction doctor working in a community hospital.

Hello all :razz:

---

### Post by newbie2 on 2005-12-08
i googled this -->
[http://gentoo-wiki.com/HARDWARE_Gentoo_Linux_64bit_on_HP_Pavilion_zv6000_series_notebook](http://gentoo-wiki.com/HARDWARE_Gentoo_Linux_64bit_on_HP_Pavilion_zv6000_series_notebook)
also on this boardsearch i found this -->
[http://ubuntuforums.org/search.php?searchid=2858600](http://ubuntuforums.org/search.php?searchid=2858600)

---

### Post by WildTangent on 2005-12-08
The Xpress 200 doesn't seem to work for anyone, including me :(

-Wild

---

### Post by debernardis on 2005-12-10
1) The "NoAccel" trick allowed myself to login X
2) After one day trials I was able to make my wi-fi card work with ndiswrapper; I had to disable ACPI with ACPI=OFF boot parameter, so now the battery indicator is also disabled.
3) Presently trying to install accellerated ATI drivers.

---

### Post by jarnold_ubuntu on 2005-12-10
I don't know why everyone seems to be having problems with the ATI RADEON x200 chip; mine worked fine out of the box (I have a Compaq v2405us) unaccelerated, and all I had to do to get 3D was

sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev fglrx-control

and edit my /etc/X11/xorg.conf file to use the fglrx module.

I'm running Breezy

---

### Post by debernardis on 2005-12-11
[QUOTE=jarnold_ubuntu]and edit my /etc/X11/xorg.conf file to use the fglrx module.[/QUOTE]

Would you mind explain me how did you edit xorg.conf? I am a noob :cool:

---

### Post by garretthylltun on 2006-03-04
Boot up your computer.
Select "Recovery Mode"

Type the following:

```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev fglrx-control
```

Say yes to downloading and installing

When it is complete, type the following:

```
cp /etc/X11/xorg.conf xorg.conf.backup
```

That copies the file you are about to edit to a backup just in case.

Then type:

```
pico /etc/X11/xorg.conf
```

You will now be in an editor with the file needed.  Arrow down or PgDn until you see a section of text that looks like this:

```
Section "Device"
        Identifier        "ATI Technologies, Inc. Radeon Xpress 200M (RS480)
        Driver            "ati"
        BusID             "PCI:1:5:0"
```

The line you want to edit is the "Driver" line.  Change the "ati" to "fglrx".  

```
Section "Device"
        Identifier        "ATI Technologies, Inc. Radeon Xpress 200M (RS480)
        Driver            "fglrx"
        BusID             "PCI:1:5:0"
```

Then press the CTRL and X keys to exit.  It will ask you if you want to save, press Y for yes, and then it will want the file name, but it's already set, just hit the enter key.

Now CTRL+ALT+DEL, or if that doesn't kick, then type "exit" at the prompt an d hit enter.  This should reboot you, if not, power down and restart your computer.

Now, when it boots up this time, just let it all start up as it should.  The GDM window should be there again, just type your user and pass, and Gnome should kick right in for you.

If it doesn't, then sorry, I have no other ideas.  The above is what worked for me on my V2405US

Good luck,
-Garrett

---

