---
title: "Monitoring utility for IBM ServeRAID"
date: 2007-10-30
forum: Server Platforms
---

### Post by honigbluete on 2007-10-30
On my IBM x3550 I use a hardware RAID (IBM ServerRAID) at level 1 for two harddisks. The CD-ROM that comes with it says that the software can be installed on various Linux versions but Ubuntu is not listed. Is it recommended to install one of these versions or is there an alternative? I want to monitor the RAID status, rebuild status and the like.

EDIT:
Oh, and btw the disc says "minimum system requirements: 256 color video driver". Is it possible to ru nthe tool with that on the IBM as I have just a non-graphical system?

---

### Post by honigbluete on 2007-10-31
Well the supported platforms use rpm for packet managing, Ubutu uses apt. I know I can install rpm packages but the question is if I have to do so because no other way exists or if somebody knows a better solution.

---

### Post by waveform on 2008-03-06
If you're still interested in this, I've just managed to get IBM ServeRAID 9.00 working with a ServeRAID 8k (SATA) adapter in an x3500 on Gutsy 64-bit. I haven't tried out the GUI interface because, like you, I'm using a no-X server setup. However, I did manage to configure it (e.g. e-mail notification) by using the ServeRAID manager I had installed on a Windows box to remotely configure the Ubuntu box.

Anyway, if you're interested let me know and I'll write up the instructions and post 'em here. A brief warning though: it's not exactly a simple procedure (quick overview: tweak alien to ignore arch differences, use alien to convert rpm to deb, extract the deb, tweak incompatible stuff like lib32 locations and postinst/rm scripts, repackage and install the deb ... urgh). Still, it's probably worth it (automatic e-mail notification of a failed drive has likely saved my bacon a few times in the past!)

---

### Post by kb9szx on 2008-03-06
Well, I for one would be interested in some direction .  I've overcome so much so far to get gutsy on my IBM x330 :)  what's a little more to manage my serveRAID 4lx controller......Thanks in advance !!

---

### Post by waveform on 2008-03-07
As promised:

[size="5"]**Acknowledgements:**[/size]

Much of this procedure is based on Andrew Kutz's article, [Managing hardware RAIDs with Adaptec Storage Manager and Ubuntu](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1296399,00.html). IBM's ServeRAID cards and software (or at least, all the ones I've worked with) are just rebadged versions of the Adaptec kit. Andrew's article covers the original Adaptec kit on Feisty. I found I needed a couple of extra tweaks to get the rebadged stuff working on Gutsy (whether this is down to differences between the Adaptec and IBM rebadged versions, or differences between Feisty and Gutsy, I'm not sure).


[size="5"]**Pre-Requisites:**[/size]

Below is the list of hardware and software I'm using. I'm reasonably confident that these steps should work on other versions of ServeRAID hardware and software (e.g. the ServeRAID 8.40 software), but for reference this is the kit I used:

[list]
[*]**Machine:** IBM System x3500 7797-G2G
[*]**OS:** Ubuntu 7.10 Gutsy Gibbon amd64
[*]**Software:** IBM ServeRAID 9.00 for Linux x86_64
[*]**RAID Card:** IBM ServeRAID 8k (SATA/SAS)
[/list] 


[size="5"]**Obtaining the ServeRAID Software:**[/size]

Your server should have shipped with one or two ServeRAID CDs (e.g. "ServeRAID Support" and "ServeRAID Application"). The Support CD is usually a bootable live CD which you can use to configure the RAID setup prior to installing an OS. The Application CD (sometimes labelled "ServeRAID Management") contains the software for installation. However, it's probably wise to check the [IBM System x Support](https://www-304.ibm.com/systems/support/supportsite.wss/brandmain?brandind=5000008) site to check for the latest versions of these CDs, and any firmware updates for your card. Select your product family, type, model, and a Linux OS from the lists and filter the results for RAID. For example, [this](https://www-304.ibm.com/systems/support/supportsite.wss/supportresources?categoryind=5051463&brandind=5000008&familyind=5310496&typeind=5310692&modelind=5348137&osind=5166079&taskind=2&news=N&parts=N&pubs=N&matrix=N&selectedButton.x=16&selectedButton.y=3) is the page for my particular box (an x3500 7797-G2G). I strongly recommend you check for any firmware updates, especially if they're labelled "Critical update" (for example, on my box the latest firmware update labelled critical, "fixed a problem where a reboot would occur when all drives would spin up at the same time" ... ouch!)


[size="5"]**Procedure for 64-bit users:**[/size]

[list=1]
[*]As ServeRAID is distributed in RPMs we'll obviously need **alien** and **fakeroot** for conversion, so install these packages:

```
$ sudo apt-get install alien fakeroot
```
[*]We also need the **ia-32** compatibility libraries as the x86_64 / amd64 version of ServeRAID is still a 32-bit application:

```
$ sudo apt-get install ia32-libs
```
[*]Something in the ServeRAID agent expects **sort** to be in /bin. However, in Ubuntu it's only in /usr/bin, so we'll create a symbolic link to fix this:

```
$ sudo ln -s /usr/bin/sort /bin/sort
```
[*]From the ServeRAID Application CD (aka the ServeRAID Management CD), copy the RPM containing the software for your architecture to your home directory. For example:

```
$ cp /media/cdrom/linux_x86_64/manager/RaidMan-9.00.x86_64.rpm .
```
[*]Even though the RPM is allegedly for x86_64 / amd64, internally it appears to be for i386. Therefore, alien will refuse to convert it for us due to the different architectures. So, we need to tweak alien to make it think the architecture of the RPM is really amd64. Open /usr/share/perl5/Alien/Package/Deb.pm in your favourite editor with root privileges:

```
sudo vim /usr/share/perl5/Alien/Package/Deb.pm
```

On (or near) line 351 you should find the following line:

```
print OUT "Architecture: ".$this->arch."\n";
```

Copy and comment out the original line with a # prefix, so you can switch it back easily later, and change the copied line as follows:

```
# print OUT "Architecture: ".$this->arch."\n";
print OUT "Architecture: amd64\n";
```

[*]Now, use alien in a fakeroot to convert the RPM package to a debian package:

```
$ fakeroot alien -c RaidMan-9.00.x86_64.rpm
```
[*]You should get a message stating [font=courier]raidman_9.00-1_i386.deb created[/font], however the resulting file will actually be called [font=courier]raidman_9.00-1_amd64.deb[/font] (this discrepancy is due to the tweak we made earlier)
[*]Next, we need to tweak some of the scripts inside the package to work properly on Ubuntu. Make a directory structure to extract the debian package into, and extract the package along with its control scripts:

```
$ mkdir -p raidman_9.00-1_amd64/DEBIAN
$ dpkg -x raidman_9.00-1_amd64.deb raidman_9.00-1_amd64/
$ dpkg -e raidman_9.00-1_amd64.deb raidman_9.00-1_amd64/DEBIAN
```
[*]Open the post-install (postinst) script with your favourite editor:

```
$ vim raidman_9.00-1_amd64/DEBIAN/postinst
```

Remove the following line

```
chkconfig --add raid_agent
```
[*]Open the post-remove (postrm) script with your favourite editor:

```
$ vim raidman_9.00-1_amd64/DEBIAN/postrm
```

Remove the following line

```
chkconfig --del raid_agent
```
[*]Now we need to make sure the Java launchers can find the correct 32-bit libraries. The existing scripts assume 32-bit libraries live under /usr/lib, which is incorrect on Ubuntu (they live under /usr/lib32 here). Open the agent launcher script with your favourite editor:

```
$ vim raidman_9.00-1_amd64/usr/RaidMan/RaidAgnt.sh
```

Duplicate the following lines (they should start at or near line 141) and change the second copy to reference /usr/lib32 instead of /usr/lib:

```
if [ -f /usr/lib/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib/libstdc++.so.5
fi
```

For example, these should become:

```
if [ -f /usr/lib/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib/libstdc++.so.5
fi
if [ -f /usr/lib32/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib32/libstdc++.so.5
fi
```
[*]Now the same for the manager launcher script:

```
$ vim raidman_9.00-1_amd64/usr/RaidMan/RaidMan.sh
```

Duplicate the following lines (they should start at or near line 141 again) and change the second copy to reference /usr/lib32 instead of /usr/lib:

```
if [ -f /usr/lib/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib/libstdc++.so.5
fi
```

For example, these should become:

```
if [ -f /usr/lib/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib/libstdc++.so.5
fi
if [ -f /usr/lib32/libstdc++.so.5 ]
then
   LD_PRELOAD=/usr/lib32/libstdc++.so.5
fi
```
[*]Now repackage the extracted content back into the debian package:

```
$ dpkg -b raidman_9.00-1_amd64/ raidman_9.00-1_amd64.deb
```
[*]Install the new package:

```
$ sudo dpkg -i raidman_9.00-1_amd64.deb
```
[*]With a bit of luck the install should go smoothly and the background RAID agent ought to start automatically. You can control the RAID agent with the /etc/init.d script like so:

```
$ sudo /etc/init.d/raid_agent stop
$ sudo /etc/init.d/raid_agent start
```
[*]Should you need to perform this installation on any other servers, simply copy and re-use the debian package.
[/list]

[size="5"]**Procedure for 32-bit users:**[/size]

[list=1]
[*]As ServeRAID is distributed in RPMs we'll obviously need **alien** and **fakeroot** for conversion, so install these packages:

```
$ sudo apt-get install alien fakeroot
```
[*]We also need the **libstdc++** compatibility libraries:

```
$ sudo apt-get install libstdc++5
```
[*]Something in the ServeRAID agent expects **sort** to be in /bin. However, in Ubuntu it's only in /usr/bin, so we'll create a symbolic link to fix this:

```
$ sudo ln -s /usr/bin/sort /bin/sort
```
[*]From the ServeRAID Application CD (aka the ServeRAID Management CD), copy the RPM containing the software for your architecture to your home directory. For example:

```
$ cp /media/cdrom/linux/manager/RaidMan-9.00.i386.rpm .
```
[*]Now, use alien in a fakeroot to convert the RPM package to a debian package:

```
$ fakeroot alien -c RaidMan-9.00.i386.rpm
```
[*]Next, we need to tweak some of the scripts inside the package to work properly on Ubuntu. Make a directory structure to extract the debian package into, and extract the package along with its control scripts:

```
$ mkdir -p raidman_9.00-1_i386/DEBIAN
$ dpkg -x raidman_9.00-1_i386.deb raidman_9.00-1_i386/
$ dpkg -e raidman_9.00-1_i386.deb raidman_9.00-1_i386/DEBIAN
```
[*]Open the post-install (postinst) script with your favourite editor:

```
$ vim raidman_9.00-1_i386/DEBIAN/postinst
```

Remove the following line

```
chkconfig --add raid_agent
```
[*]Open the post-remove (postrm) script with your favourite editor:

```
$ vim raidman_9.00-1_i386/DEBIAN/postrm
```

Remove the following line

```
chkconfig --del raid_agent
```
[*]Now repackage the extracted content back into the debian package:

```
$ dpkg -b raidman_9.00-1_i386/ raidman_9.00-1_i386.deb
```
[*]Install the new package:

```
$ sudo dpkg -i raidman_9.00-1_i386.deb
```
[*]With a bit of luck the install should go smoothly and the background RAID agent ought to start automatically. You can control the RAID agent with the /etc/init.d script like so:

```
$ sudo /etc/init.d/raid_agent stop
$ sudo /etc/init.d/raid_agent start
```
[*]Should you need to perform this installation on any other servers, simply copy and re-use the debian package.
[/list]

[size="5"]**Configuration with RAID manager (local and remote):**[/size]

If you have an X environment installed on your server you should be able to launch the RAID manager interface by using something like this (I haven't tried this as I don't have X on any servers, although I have tried something similar on a 32-bit Gentoo client and it worked nicely):

```
$ gksu /usr/RaidMan/RaidMan.sh
```

**NOTE:** The RAID manager *must* be run as root (hence the gksu in the command above), even if you're running it on a separate client. You can also use RAID manager on a separate machine to configure the agent on the server. For this to work you must ensure that TCP ports 34571 to 34575 are open if you're running a firewall (the RAID manager only listens on 34571 and 34572 for connections, but for some reason it's necessary to have the others open after a connection is established - I'm not sure why yet).

When using the RAID manager on a separate client to configure the server (e.g. if you don't have X on your server) you'll find you can't alter most settings unless you logged into the server as root (from within the RAID manager interface). Unfortunately, for this to be possible you'll have to give your root user a password:

```
$ sudo passwd root
```

To re-disable the root account after you've finished the configuration, use the following:

```
$ sudo passwd -l root
```

See the excellent [RootSudo](https://help.ubuntu.com/community/RootSudo) page for more information on these commands and why you should generally leave the root account disabled. Some other things to note when trying to use RAID manager on a separate machine:

[list]
[*]When adding a new server to the managed list (from the menu: Remote | Add) it can take a _very_ long time to appear. If it's still sat on the hourglass after 2 or 3 minutes, don't worry - that seems to be perfectly normal!
[*]In Andrew Kutz's article (see top) he walks through the process of running the manager on the server and forwarding the display to a different client. This is another good method of remote management but I'd only recommend it for clients with a very fast low-latency link to the server. The "pretty" (aka downright silly) interface needs an awful lot of network roundtrips to draw / update / etc. A simple mouse click on a button, or selecting a menu took 5 or more seconds to register when I tried this over a reasonably high-speed (8Mbit down, 800Kbit up) broadband connection with SSH. In the end I got so annoyed with it I just used the RAID manager on a Windows server via remote desktop to configure it.
[*]Sometimes it seems that the results of an operation don't immediately appear in the interface. For example, when adding new entries for e-mail notification of errors the users didn't appear in the list until I closed and re-opened the configuration window (not the whole application mind). This only seems to apply when using RAID manager on a separate machine to the server (i.e. not with a forwarded display, but by using the remote configuration facility).
[/list]



Please let me know about any errors or corrections!


Cheers,

Dave.

---

### Post by xnoxpx on 2008-03-10
I'm working on converting a Mandrake 9.5 file server to a ubuntu 7.10(not 64-bit) domain/file server (I have an IBM xSeries 345 type 8670 with LSI 1030 raid controller)
I have RaidMan_8.40-1_i386.rpm on my CD

Except for my habit of pasting "....raidman_9.00-1_i386....." instead of typing the commands out manually, Every thing went perfectly

gksu /usr/RaidMan/RaidMan.sh does work in X

---

### Post by waveform on 2008-03-10
I'm glad to hear it! Is there anything you think could be improved in the instructions? I'm not too hapy with the last section at the moment; it probably needs splitting into different chunks, as it's not entirely clear where I'm talking about running the manager app on the server, on the server with a forwarded display, or remotely on a different machine.

Also, one thing to watch out for: on one of our machines using ServeRAID 8.40 (a Win2k machine), it constantly adds stuff to a RaidDP.log file under the installation directory. If left unchecked, this grows to hundreds of megs in a fairly short time (few months). Apparently it's a known error in 8.40 (fixed in later versions) that only affects some environments (it doesn't happen on a similar box we've got which runs 8.40 on Win2k3).

The simple workaround is to delete RaidDP.log if it gets too large (the agent will simply recreate it and start filling it again).


Cheers,

Dave.

---

### Post by xnoxpx on 2008-03-11
Thanks for the heads up, we just bought a x3550(7978) to install our first M$ (terminal) Server (1 of our vendors is kicking in to help purchase it because they require Active X), thats where I got ServerRaid 8.4.
We will be running Win2k3 But I will probablly just install the newest version to play it safe.

---

### Post by 1stwiz on 2008-05-13
thx2 waveform, great job
32bit instructions work great for ubuntu 8.04 LTS (hardy heron) as well :)
with the agent running in ubuntu 8.04 I can now monitor from win ServeRAID mgr my controllers (8k, 4L) and everything seems working

---

