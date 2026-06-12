---
title: "HOWTO: Lexmark z605 (and possibly other 600 series)"
date: 2005-10-28
forum: Tutorials
---

### Post by tapH20guru on 2005-10-28
Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```

1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```
3. Now we run:
```
/usr/lib/cups/backend/z600 
```
You should be something like: 
```
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```
4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)

---

### Post by Ubuntist on 2005-11-17
These instructions worked for me in installing a Lexmark Z55, although some of the file names in the Z55 driver are not entirely parallel with those in the Z600's.  When testing the backend (executing z55), I got no output at all, but the printer still seems to work just fine.

---

### Post by jimmyj on 2005-11-22
I was having problems getting a Dell 720 (repackaged Lexmark 615) that my roommate gave me for free working. I followed all the steps but the driver didn't output anything and the printer wouldn't work.

Ubuntu automatically pointed the printer to usb://Dell/Photo%20Printer%20720, but cups was complaining that the device did not exist. Finally, after a lot of hair pulling, I  switched it to /dev/usb/lp0 and changed the permissions and I am now printing. I am worried that there is a security issue in my solution though. Is that okay? And how else should I go about fixing it?

---

### Post by brucek on 2005-11-29
[QUOTE=tapH20guru]Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```

1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```
3. Now we run:
```
/usr/lib/cups/backend/z600 
```
You should be something like: 
```
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```
4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)[/QUOTE]

Did all that, and got the expected results from ./z600, and the System->Administration->Printing shows my printer (I'd like it to say it's a Z25, but that's a minor issue). However, attempting to print a test page just sits with the paperfeed light blinking forever and nothing comes out. I pushed the paperfeed button, and the blinking stopped, but the paper still doesn't come out.

Any ideas?

---

### Post by brucek on 2005-11-29
[QUOTE=brucek]Did all that, and got the expected results from ./z600, and the System->Administration->Printing shows my printer (I'd like it to say it's a Z25, but that's a minor issue). However, attempting to print a test page just sits with the paperfeed light blinking forever and nothing comes out. I pushed the paperfeed button, and the blinking stopped, but the paper still doesn't come out.

Any ideas?[/QUOTE]

Found another thread that used a similar format on a z35 file (CJLZ35LE-CUPS-2.0-1.TAR.GZ), and got farther thru the process. However, somehow the z600 process wouldn't finish and release the printer, so I rebooted and now it works fine!

Under Windoze, the printer had a tool where you could fine tune the head alignment, but I'm not seeing that in the './z35 utilities' process. Maybe I don't care, tho.

Anyhow, it's working good enough for me!

Thanx!
-bk

---

### Post by bluevoodoo1 on 2005-12-02
This worked perfectly for my z605! Thanks!

---

### Post by Chris Tucker on 2005-12-11
working on a z715 .. but with the other .rpm's... meant for z700 series, when using z715, and maybe other z700 series, with the z600 driver, printing is off-center.
[http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm](http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm)
[http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm](http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm)
HOWEVER...
I am haveing some issues, well, just one... no matter how many leading blank lines in a document, i get the first line of text right on the top edge of the page!
any help is appreciated.

---

### Post by Gsyman on 2005-12-16
I get as far as the download from Lexmark which appears on the Desktop as a Tarball. When I run the command it does not see the download, what have I done wrong??

---

### Post by Rouge8 on 2005-12-16
Try 'cd Desktop'.

---

### Post by Gsyman on 2005-12-18
Thanks Rouge8 that did the trick !:smile:

---

### Post by DDaland on 2005-12-29
Worked lie a charm- thanks!

---

### Post by monkey4ahead on 2006-01-03
Just got my z23 working. Used the instructions but with the z35 drivers. All i need now is a black cartridge!

---

### Post by seabrook on 2006-01-06
Thanks, have managed to get a Z617 working.

Cheers

---

### Post by coaxx on 2006-01-12
[QUOTE=tapH20guru]
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
[/QUOTE]

**hey man please help me, after that my /usr Folder permissions are "drwx------ root root" and I cannot use /usr/bin/sudo anymore!!!!!!!!!!!**

wtf? I did it once, installed dapper again and now I have exactly the same problem!! su is also useless sins root isnt activated, well what a mess!

---

### Post by mofomikeman on 2006-01-12
[QUOTE=jimmyj]I was having problems getting a Dell 720 (repackaged Lexmark 615) that my roommate gave me for free working. I followed all the steps but the driver didn't output anything and the printer wouldn't work.

Ubuntu automatically pointed the printer to usb://Dell/Photo%20Printer%20720, but cups was complaining that the device did not exist. Finally, after a lot of hair pulling, I  switched it to /dev/usb/lp0 and changed the permissions and I am now printing. I am worried that there is a security issue in my solution though. Is that okay? And how else should I go about fixing it?[/QUOTE]
I have the same thing as you... when I followed the instructions, it no longer automatically detects the printer!  I need to point it to that... and within 5 minutes from now!  I uninstalled windows, and I have to get my homework done! HELP!

---

### Post by mofomikeman on 2006-01-12
Bump

---

### Post by coaxx on 2006-01-13
[QUOTE=coaxx]**hey man please help me, after that my /usr Folder permissions are "drwx------ root root" and I cannot use /usr/bin/sudo anymore!!!!!!!!!!!**

wtf? I did it once, installed dapper again and now I have exactly the same problem!! su is also useless sins root isnt activated, well what a mess![/QUOTE]


Just to be more precise: I had this Problems with the z35 package fro, Lexmark (installation is the same has described in this howto). Be prepare not to extract the two gz files right into the /usr folder. I extracted em first in aother place and sudo copied then the subfolders of usr to /usr. That way I had no problems with the directory accessrights messed up. (btw a solution is to boot a knoppix, rw-mount the partition where /usr is and "sudo chmod -R go+rx /mnt/<yourmountname>/usr".

---

### Post by mofomikeman on 2006-01-13
[QUOTE=mofomikeman]I have the same thing as you... when I followed the instructions, it no longer automatically detects the printer!  I need to point it to that... and within 5 minutes from now!  I uninstalled windows, and I have to get my homework done! HELP![/QUOTE]
BBBBUMP

---

### Post by mofomikeman on 2006-01-13
[QUOTE=jimmyj]I was having problems getting a Dell 720 (repackaged Lexmark 615) that my roommate gave me for free working. I followed all the steps but the driver didn't output anything and the printer wouldn't work.

Ubuntu automatically pointed the printer to usb://Dell/Photo%20Printer%20720, but cups was complaining that the device did not exist. Finally, after a lot of hair pulling, I  switched it to /dev/usb/lp0 and changed the permissions and I am now printing. I am worried that there is a security issue in my solution though. Is that okay? And how else should I go about fixing it?[/QUOTE]
HOW DO I MAKE IT GO TO /dev/usb/lp0!

Oh, and I have no idea what it means to run the driver or plugin or whatever to get output.

---

### Post by fab4am on 2006-01-17
aaaaaahhh!!!!

thank you very much !!!! first time i can really print with linux, and i'm using it for 1 year !!

thank youuuuuuuuuuuuuuuuuuu!!!!!!!!!!!!!!!!!!!!

---

### Post by fab4am on 2006-01-17
i forgot : i'm using a Z615 printer and it works perfectly !

---

### Post by mtlife on 2006-01-19
my z515 shows up in cups, and i followed all instructions.. but when i press print test page really nothing happens.. i think cups is not working correctly, since everyone else gets their printer to work.. can you help me?

edit: works now.. installed some extra cups packages (actually.. all of them that made sense) and now it works..

---

### Post by cwalk on 2006-01-19
Perfect! works like a charm on my z600.
thanks!:)

---

### Post by rippon on 2006-01-21
I get this:

Status: Paused: Unable to open USB device "usb://Lexmark/Z600%20Series": No such device

I did according to the instrusctions ( I have a z611 ). Im sure this is a noob problem with a usb port, but I dont know how to fix it. Any Ideas? Thanks!

---

### Post by rippon on 2006-01-24
[QUOTE=rippon]I get this:

Status: Paused: Unable to open USB device "usb://Lexmark/Z600%20Series": No such device

I did according to the instrusctions ( I have a z611 ). Im sure this is a noob problem with a usb port, but I dont know how to fix it. Any Ideas? Thanks![/QUOTE]
Hmm, I still can't figure this one out. Anyone have any Ideas?
Thanks a lot.

---

### Post by ubunturules on 2006-01-25
Has anyone gotten a Lexmark 510 Series to work with this?

---

### Post by 79centuries on 2006-02-19
Has anyone had success with the E232?  the z600 driver doesn't work, but everything works fine until the test page, which comes out as 20 pages of junk.  so I deleted that 'lexmark' file and started again.  I've found a couple different formats of an E232 driver on the lexmark page, but the closest to this how-to is   'print-drivers-linux-glibc2-x86.rpm.gz'.  I know it's got the same name, but it is listed for E200 series.  here is what i have tried with this file:

$ sudo gunzip print-drivers-linux-glibc2-x86.rpm.gz
now i have a .rpm file
to change to tgz:
$ sudo alien -t print-drivers-linux-glibc2-x86.rpm
which outputs: 
> drivers-LEXPrtDrv-5.3.1.tgz generated

so now i need to extract the tgz:
$ sudo tar xvzf drivers-LEXPrtDrv-5.3.1.tgz -C /
and all kinds of unpacking happened.  so now...
$ sudo ldconfig

but the only lexmark file in /usr/share/cups/model is the z600 driver from attempt #1.  any ideas on how to unpack this driver correctly?  thanks all, and this is a really great how-to.

**EDIT:**  nevermind.  while i would like to know how to unpack this file, the optra-E321 'model' option and the suggested driver (hpjis, i think) work fine.  Whoo!!  now on to wireless print networks...

---

### Post by Khonsu on 2006-05-23
I am using an X1195 and I can't seem to get it to work for me. Anyone know why? Has anyone had problems with this printer?

-Khosnu

---

### Post by TheRingmaster on 2006-06-19
does anyone have a lexmark X75 printer and has it working under dapper?

---

### Post by rough raider on 2006-06-20
hi ! I have lexmark z705 and ubuntu 5.10 , drivers installed fine , test page prints in all colours but ... when I try to print something else like page from writer,calc etc , printer loads paper but it's nothing on it - it is blank 
i tried again test page and it prints everything fine

anyone have same problem ,is there solution for it ? 
ps : i tried also z605 ,z615 and z515 with same result , ink is full

---

### Post by moore.bryan on 2006-06-24
alien hangs with package not found... any ideas?

---

### Post by nbt-tech on 2006-06-28
[QUOTE=tapH20guru]Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```

1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```
3. Now we run:
```
/usr/lib/cups/backend/z600 
```
You should be something like: 
```
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```
4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)[/QUOTE]


Worked first time with Lexmark Z605 on Breezy (5.10 : config-2.6.12-10-386)

thx

---

### Post by moore.bryan on 2006-06-28
the "sudo alien -t z600cups-1.0-1.i386.rpm" returns a "file not found" error.

---

### Post by aviper2k7 on 2006-08-11
> **moore.bryan said:**
> the "sudo alien -t z600cups-1.0-1.i386.rpm" returns a "file not found" error.

Make sure you cd to the folder the file is in. Have a [basic understanding]("http://linux.org.mt/article/terminal") of the terminal and you'll be fine.

I posted [here]("http://www.ubuntuforums.org/showthread.php?t=49714&page=14"), but I think I posted in the wrong spot??? Well, I can't get the Dell AIO 624 (Lexmark z615) to work. 

after 
```

/usr/lib/cups/backend/z600

```

I get nothing.

The printer is detected though in printers, just nothing prints. I get the error:

Printing: Unable to lookup host '' - Unknown server error

and I am not sure what to put under "location"

Help would be appreciated, but if I don't get any I might as well uninstall linux and go back to windows where I can actually print :/

---

### Post by jamesstansell on 2006-08-20
I don't have a lexmark to test this, but I think location should be something like z600:/dev/usb/lp0

You might find some additional help on the linuxprinting.org lexmark group.  Here is a posting from January: [http://lists.freestandards.org/pipermail/printing-user-lexmark/2006/003221.html](http://lists.freestandards.org/pipermail/printing-user-lexmark/2006/003221.html)

Also don't overlook asking in #ubuntu on IRC: [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

Regards,

-james.

---

### Post by BigGP on 2006-10-01
I had no problem installing the driver an my printer works fine.  However, Apt-Get is now halting every time I try to run it giving an error that it can't find a repository for the Z600Cups package.  How do I get apt-get to ignore the package?

---

### Post by johonbravo on 2006-11-08
I Installed the driver without issues, then restarted cups without issue, then did this:

```
jon@jon-ubuntu:~$ /usr/lib/cups/backend/z600
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"

```

Things seemed to be working however I went to add the printer and under "lexmark" there is no z600 driver. I restarted cups again, rebooted, and still no driver viewable.

I have a Lexmark x1195

What could be causing this as there were no apparent install errors?

---

### Post by Meekajahama on 2006-11-30
> **johonbravo said:**
> I Installed the driver without issues, then restarted cups without issue, then did this:

```
jon@jon-ubuntu:~$ /usr/lib/cups/backend/z600
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"

```

Things seemed to be working however I went to add the printer and under "lexmark" there is no z600 driver. I restarted cups again, rebooted, and still no driver viewable.

I have a Lexmark x1195

What could be causing this as there were no apparent install errors?

I have the same problem but I'm using a Lexmark z615
Everything installs correctly and fine but when finding the driver in add printer there is no z600 driver. Restarted cups, rebooted and so on nothing. Any help would be great. ](*,)

---

### Post by mattycoze on 2007-01-08
*QUOTES*
johonbravo  	I Installed the driver without issues, then restarted cups without issue, then did this:

Code:

jon@jon-ubuntu:~$ /usr/lib/cups/backend/z600 direct z600:/dev/usblp0 "Lexmark Lexmark X1100 Series" "Lexmark Printer"

Things seemed to be working however I went to add the printer and under "lexmark" there is no z600 driver. I restarted cups again, rebooted, and still no driver viewable.

I have a Lexmark x1195

What could be causing this as there were no apparent install errors?

*END QUOTE*

Yeah you know i get the same problem, i have a feeling after careful reading that it points to "/dev/usblp0" rather than "/dev/usb/lp0", anyone know how to change this? I've followed both instructions and both return the same thing, and you can't see either driver appear in the cups frontend wizard. That makes 4 people that i'm aware of with this problem, and yet nobody's done anything about it or at least put up a post about it. 

](*,)   PLEASE? 

Preety please with sugar on top... common i'll be your friend *starts acting like a child* lol

 Matty+C

---

### Post by glitterball on 2007-01-11
Same problem here too.
Everything seems to go fine, but no z600 in the list of models or drivers.

---

### Post by josno on 2007-02-10
> **glitterball said:**
> Same problem here too.
Everything seems to go fine, but no z600 in the list of models or drivers.

I have the same problem - does anyone have a fix? I'm using Edgy rather than Breezy

---

### Post by troorl on 2007-02-12
In my list doesn't present my z600 :(
What i'm doing wron?

P.S. Feisty...

---

### Post by elric.vh on 2007-02-27
Got the same issue as well, all follows through ok... but then on the "Add a Printer" screen, I get a "Lexmark  Lexmark Z600 Series" as well as a "Lexmark Z600 Series" printer, and when I select it, there is no matching driver. Anyone got a clue? I'm using Edgy

---

### Post by josno on 2007-02-28
Well, I've got Edgy to actually install the printer - when I get to the driver selection stage the Z600 driver isn't listed, so I click 'Install Driver', browse to /usr/share/cups/model and select Lexmark-Z600-lxz600cj-cups.ppd. This adds Z600 V1.0-1 to the drivers list which I can select. However, it won't print a test page - it'll think about it and then just say "Stopped: job stopped" in the 'State' column of the jobs window. This is the same whether I add the "Lexmark Z600 Series" printer or the "Lexmark Lexmark Z600 Series". Any ideas?

---

### Post by smilliken on 2007-03-01
I tried the instructions from this post for a Z65. There two small problems.

1. sudo /etc/rc2.d/S19cupsys restart
sudo: /etc/rc2.d/S19cupsys: command not found

there is no file S19cupsys in the directory

K13isdnactivecards  K20mysql      K25mdadm         S12915resolution  S20sysfsutils
K14ppp              K20rsync      K30squid         S12dbus           S21aumix
K15bind9            K20samba      K50dansguardian  S13capiutils      S25powersaved
K19spamassassin     K20spampd     K50proftpd       S19hplip          S50splashy90
K20bluez-utils      K20ssh        K99kdm           S19splashy70      S89cron
K20clamav-daemon    K20tftpd-hpa  S05vbesave       S20lisa           S90binfmt-support
K20cupsys           K20webmin     S10acpid         S20makedev        S99rc.local
K20dhcp3-server     K20xinetd     S10sysklogd      S20nvidia-kernel  S99rmnologin
K20inetd            K21dovecot    S11klogd         S20splashy80      S99splashyZ

2.direct z65:/dev/usb/lp0 "Lexmark  Lexmark Z65 Series" "Lexmark Printer", stated "bash: direct: command not found"

I ran thru the install for the printer ..... MEPIS>Setup>Peripherals>Ptinter>SMB thru windows and the Z65 was listed and installed wihtout any problems. Printed a test OK.

Do the above errors cause me any conerns?

Any help would be appreciated.

---

### Post by srwalter on 2007-03-07
Hey

A friend of mine has a Lexmark printer, so I went ahead and make an Edgy deb for the Z55 driver.  I based it off the "Lexmark Printer DDK" and sample code, which is all I could find on their site at this point.  You need to install the DDK, which you can do by downloading the RPM from [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668523_676599624_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668523_676599624_en,00.html)

Once you download the RPM, you can "fakeroot alien z55llpddk_2.0-1_i386.rpm" to get a debian package that you can install.  Once you have that out of the way, you can install [http://dasbrennen.isa-geek.org/~srwalter/lexmark-z55-1.0-1_i386.deb](http://dasbrennen.isa-geek.org/~srwalter/lexmark-z55-1.0-1_i386.deb)

The source is available at [http://dasbrennen.isa-geek.org/~srwalter/lexmark-z55-1.0.tar.gz](http://dasbrennen.isa-geek.org/~srwalter/lexmark-z55-1.0.tar.gz) since it is based on the Z55 Sample Driver, which is GPL.

---

### Post by nifocmike on 2007-03-11
> **tapH20guru said:**
> Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```


Okay, going through this list of commands I get:

mike@mike-linux:~/Desktop$ sudo alien -t z600llpddk-2.0-1.i386.rpm
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated

Continuing on further down the command list I get:

mike@mike-linux:~/Desktop$ sudo tar xvzf z600cups-1.0.tgz -C /
tar: z600cups-1.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mike@mike-linux:~/Desktop$ sudo ldconfig
mike@mike-linux:~/Desktop$ cd /usr/share/cups/model
mike@mike-linux:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
gunzip: Lexmark-Z600-lxz600cj-cups.ppd.gz: No such file or directory
mike@mike-linux:/usr/share/cups/model$ sudo /etc/rc2.d/S19cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
mike@mike-linux:/usr/share/cups/model$ /usr/lib/cups/backend/z600
bash: /usr/lib/cups/backend/z600: No such file or directory

Any help would be appreciated!

---

### Post by grusifix on 2007-03-11
So your z600llpddk-2.0.tgz was generated OK using alien.
Did you generate z600cups-1.0.tgz using alien also? I believe not because of "Cannot open: No such file or directory"

---

### Post by Pikestaff on 2007-03-14
Just tried this method on my Kubuntu Dapper... worked perfectly the first time, thank you to the person who wrote the tutorial :)

---

### Post by THEBIGEYE on 2007-03-24
i have installed this driver before i reinstalled now i have this problem
after i install the driver and run
ian@ian-desktop:~$ /usr/lib/cups/backend/z600
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
ian@ian-desktop:~$ 
i go to system>administrator>printer and try to find the driver its no where it should be i goto install the driver on the cups interface and it tells me it needs a ppd file. i can find the z600 file but it wont let me open it saying its not a ppd file as i say this is very anoing as i had my printer up and running fine before so if anyone has any ideas assistance would be greatly appreated

---

### Post by jonick on 2007-04-23
> **mattycoze said:**
> *QUOTES*
johonbravo  	I Installed the driver without issues, then restarted cups without issue, then did this:

Code:

jon@jon-ubuntu:~$ /usr/lib/cups/backend/z600 direct z600:/dev/usblp0 "Lexmark Lexmark X1100 Series" "Lexmark Printer"

Things seemed to be working however I went to add the printer and under "lexmark" there is no z600 driver. I restarted cups again, rebooted, and still no driver viewable.

I have a Lexmark x1195

What could be causing this as there were no apparent install errors?

*END QUOTE*

Yeah you know i get the same problem, i have a feeling after careful reading that it points to "/dev/usblp0" rather than "/dev/usb/lp0", anyone know how to change this? I've followed both instructions and both return the same thing, and you can't see either driver appear in the cups frontend wizard. That makes 4 people that i'm aware of with this problem, and yet nobody's done anything about it or at least put up a post about it. 

](*,)   PLEASE? 

Preety please with sugar on top... common i'll be your friend *starts acting like a child* lol

 Matty+C

Dare I say, me too.... Help!!:(

---

### Post by josno on 2007-04-23
> **mattycoze said:**
> 
Things seemed to be working however I went to add the printer and under "lexmark" there is no z600 driver. I restarted cups again, rebooted, and still no driver viewable.
I had this problem - when it got to the choosing z600 driver bit I clicked on the install driver button and browsed to /usr/share/cups/model selecting the z600 ppd file.
> **mattycoze said:**
> Yeah you know i get the same problem, i have a feeling after careful reading that it points to "/dev/usblp0" rather than "/dev/usb/lp0", anyone know how to change this?
I have my Z605 working fine like this, so I don't think that's the problem.

---

### Post by mills on 2007-05-01
> **josno said:**
> I had this problem - when it got to the choosing z600 driver bit I clicked on the install driver button and browsed to /usr/share/cups/model selecting the z600 ppd file.

I have my Z605 working fine like this, so I don't think that's the problem.

hey josno,

that did the trick, maybe you should try and get that put in the howto, would save ppl like me  alot of time:)

---

### Post by TheRingmaster on 2007-05-01
are there any fixes for the Lexmark X75?

---

### Post by Priscilla on 2007-05-11
What worked for me:

1 -> use -- scripts  option in alien

2 -> use the find driver button if no Z600 is showing up to you (choose the pdd file you extracted in the Shell)

3 -> play with cups [http://localhost:631](http://localhost:631)  (I think one should add the printer to the cups, by this interface also, but I’m a newbie)

What is still not working for me:

4 -> The job stays in the printer queue without being printed with status “job-stopped”

Can anyone help me ?

---

### Post by bluevoodoo1 on 2007-05-15
Guide still works perfectly in Feisty. Thanks!

---

### Post by Mirandacc on 2007-06-16
Thanks for the tip.  This worked excellently!

---

### Post by Sale on 2007-07-29
> **Priscilla said:**
> What worked for me:

1 -> use -- scripts  option in alien

2 -> use the find driver button if no Z600 is showing up to you (choose the pdd file you extracted in the Shell)

3 -> play with cups [http://localhost:631](http://localhost:631)  (I think one should add the printer to the cups, by this interface also, but I’m a newbie)

What is still not working for me:

4 -> The job stays in the printer queue without being printed with status “job-stopped”

Can anyone help me ?

I got to this same point... :(

Is there a solution?

I'm running 64bit Feisty.

---

### Post by altonbr on 2007-08-16
I'm in Feisty too. Is there an updated HOW-TO by any chance?

---

### Post by Pauly Psychotic on 2007-08-19
Thanks a lot for posting this! Works with no problem on our Lexmark z605! Which I have been trying to get to work for little over a month now! :)

---

### Post by altonbr on 2007-09-13
```
~$ cd /usr/lib/cups/backend 
```
```
/usr/lib/cups/backend$ ./z600
```
> direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"

Judging by this, the printer should work. However, whenever I print to it, it always says "Held" or "Pause".

When I go to [http://localhost:631/printers](http://localhost:631/printers), my Lexmark Z605 says:
> Lexmark_Z605 (Default Printer) "/usr/lib/cups/backend/z600 failed"

How do I test that the printer failed and why? It was able to print a test page, but not from OpenOffice.org

---

### Post by Manasia on 2007-11-28
I have tried everything under the sun and my Dell Photo printer 720 does not work.

When I do ./z600 I get no output. 

When I change the uri to z600://usb/dev/lp0 (Nothing)

I have been working with this for a while with no success. Anyone came into this problem?

Also when I do an ldd /usr/lib/cups/backend/z600 all the proper libraries are linked. 

Cups just sits there and says it cannot connect to the printer.

Thanks.

---

### Post by Manasia on 2007-11-28
One thing I notice is that my usb backend seems to be automatically attached to the printer, and not z600 backend. 

When I do ./usb I get the same output as one would get when they do ./z600. 

Does anyone know how to change this? I have tried using z600://dev/usb/lp0 in the configuration file and that does not help.

---

### Post by Hawk__0 on 2008-01-31
> **altonbr said:**
> ```
~$ cd /usr/lib/cups/backend 
```
```
/usr/lib/cups/backend$ ./z600
```


Judging by this, the printer should work. However, whenever I print to it, it always says "Held" or "Pause".

When I go to [http://localhost:631/printers](http://localhost:631/printers), my Lexmark Z605 says:


How do I test that the printer failed and why? It was able to print a test page, but not from OpenOffice.org

I'm having the same problem :(
on my x6150.
lexmark = lame.

anybody know how to fix this???????????

---

### Post by MRCeltic on 2008-02-07
> **tapH20guru said:**
> Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```

1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```
3. Now we run:
```
/usr/lib/cups/backend/z600 
```
You should be something like: 
```
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```
4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)

At the end of step 2 I had issues with installing printer, I ended up having to use the GUI Printer Installer and point to the PPD file with the /usr/share/cups folder.  That was the only way i could get the printer to work.  Is there a way to Embed this PPD file within the new release of Ubuntu?  Or for that matter all the lexmark printers?  If they are that east to get the PPD file from the Lexmark Drivers for Red Hat and so forth, just a thought.

---

### Post by MRCeltic on 2008-02-07
Also found this for those that are still having problems. not sure but this might be worth a shot for those that are still stuck.

[http://forums.openprinting.org/list.php?29](http://forums.openprinting.org/list.php?29)

---

### Post by oldHat on 2008-02-29
I hope I'm not repeating any previous content with this.

This howto is good.  I used it and it worked.  However, I always felt a little uncomfortable using the "hands-on" approach to install drivers on a Ubuntu system. 

After I trashed my system, along with my bookmark to this HOWTO, I found a different HOWTO.  I prefer this method:

[http://finebushpeople.net/LexmarkZ600]("http://finebushpeople.net/LexmarkZ600")

[LIST=1]
[*] untar the script
[*] run it, specifying the output directory with "-target"
[*]  alien  to convert the rpms to debs
[*] dpkg to install the debs
[/LIST]

(of course, you shouldn't take advice anyone who admits trashing a Ubuntu system)

---

### Post by bageh on 2008-04-03
I did work to me until the 

$ sudo tar xvzf  z600llpddk-2.0.tgz -C

and 
 
$ sudo tar xvzf z600cups-1.0.tgz -C 

then I got an error message telling me that the tar option requires an argument -- C
(each one the same error)
I tried to skip that, but at the end nothing works!

Help me, please!!!!

---

### Post by GarethA on 2008-05-27
Works fine on hardy with my Z605 - thanks!



> **bageh said:**
> I did work to me until the 

$ sudo tar xvzf  z600llpddk-2.0.tgz -C

and 
 
$ sudo tar xvzf z600cups-1.0.tgz -C 

then I got an error message telling me that the tar option requires an argument -- C
(each one the same error)
I tried to skip that, but at the end nothing works!

Help me, please!!!!


bageh - think you're missing a /
should be 
sudo tar xvzf  z600llpddk-2.0.tgz -C /

---

### Post by cristian.vulpe on 2009-03-29
Hi!

  Worked perfectly for me as well: Lexmark z615 on Ubuntu 8.10.

Thanks a lot!
  cristi

---

### Post by kwesiamoako on 2009-05-14
[quote=tapH20guru;451162]Ubuntu Hardy Heron with a lexmark z617
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy.

It did something small at the end

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/init.d/cupsys restart #The driver is now installed. Restart the cups daemon.
```3. Now we run:
/usr/lib/cups/backend/z600You should be something like(IMPORTANT): 
 4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)
5. Your printer should be turned on, you'd find the Lexmark printer there, choose, and click on the forward
6. Provide the ppd file which can be found in /usr/share/cups/model/
7. Click forward and you're done

Enjoy using your printer

---

### Post by DrBubba on 2009-08-09
Worked like a charm on my Dell E6500 for remote printing to a Lexmark Z515.

---

### Post by felipebm on 2009-08-19
beautiful solution!

thanks a lot!

---

### Post by baltadt on 2009-10-17
awesome. Got my Z611 to work perfectly from OOo. Thank you so much.

---

### Post by crjim on 2009-11-02
thank you tapH20guru... just upgraded to 9.10 and the lexmark z645 that had been working in 9.04 quit working... new installation of the drivers following your instructions worked like a charm...

---

### Post by meddle84 on 2009-11-07
hey guys! i`m trying to print with z605 lexmark on ubuntu 9.10. but i cant use the way to install driver described here because libstdc++5. in karmic there is only libstdc++6. with that lib driver dose not works.
can somebody help me to solve this problem?
update: i solve it. i`ve install libstdc++5 from debian etch with all dependences (nearly 5 packages) good luck to all!

---

### Post by kpuz on 2011-08-01
Excellent tutorial! Got my old dusty z611 to work on Ubuntu 12.04.

---

### Post by Geezanansa on 2011-10-17
> **tapH20guru said:**
> Ubuntu Breezy with a lexmark z605
Modified HOWTO from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) to work with breezy

Dependencies:
```
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (breezy come with v6 but you need v5 for compatibility)
```1. Download the driver from lexmark's site (CJLZ600LE-CUPS-1.0-1.TAR.gz)

2. Run though the following commands
```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```3. Now we run:
```
/usr/lib/cups/backend/z600 
```You should be something like: 
```
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```4.Now simply set up your printer using the new z600 driver. (ie: in GNOME: System->Administration->Printing)


Big Thank You to tapH2Oguru.  
Running oneiric and this tutorial got my lexmark X1270 printing (not tested scanner yet....)
Only got as far as ```
sudo /etc/rc2.d/S19cupsys restart 
```which i didnt know the oneiric default folder or equivalant so just exited and rebooted system then plugged in printer and then z600 was in list of drivers to install.  Printer now printing.

This is the first time that i managed to install the drivers from lexmark.  The drivers are from [http://support.lexmark.com]("http://support.lexmark.com/index?startover=y&question=CJLZ600LE-CUPS-1.0-1.TAR.gz") and try using **redhat** as keyword for searching.  Know it sounds obvious but I didn't easily find files even with full name.  Looking at support pages on lexmark.com is different than at support.lexmark.com :lolflag:

Here is link on how to use terminal [https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands](https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands).

Ubuntu rocks and thanks to folks like tapH2Oguru noobuntuists can successfully tell their machine what to do.  :guitar:

---

### Post by ddursma on 2012-01-16
Ok, I have the same problem. Downloaded the driver. I am not a programmer, and gedit would not open the driver text. where do I go to enter the suggested commands and where do I save all that stuff to?

Just found out Ctrl - Alt - T opens a terminal for code entry. Just guessing this is where I am supposed to enter these commands, not downloading GNU emacs and editing the driver, maybe. oops.

---

### Post by ddursma on 2012-01-17
Sorry, this did not work for me. ubuntu 11.10 Dell 720. 
Downloaded the driver from Lexmark, but at the first tar command to extract the driver I get 'No such file or directory'.

So this issue has been floating around here for 8 years and no one has just posted a driver?

Guess I'm printer shopping. Crap, and I just bought toner.

Still trying to make this work. no luck. file is in Archive manager. Terminal still returns file does not exist.
Extracted to desktop folder manually.
Terminal returns file does not exist.
How do I get the folder to a location the Terminal can find to run the:
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.and then maybe I can run the second command line.

Got it! Thank you to the Forum posters!

---

### Post by Geezanansa on 2012-05-17
Anybody got their old lexmark working with 12.04?:lolflag:

---

