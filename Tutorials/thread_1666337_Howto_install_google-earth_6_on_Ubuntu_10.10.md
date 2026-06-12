---
title: "Howto install google-earth 6 on Ubuntu 10.10"
date: 2011-01-13
forum: Tutorials
---

### Post by WitchCraft on 2011-01-13
/opt/google/earth/free

[http://www.google.com/earth/index.html](http://www.google.com/earth/index.html)

Click on Download Google Earth 6


Click on 32 Bit Debian /ubuntu and click on Agree and download.


While it is downloading, install this dependency (won't be installed automagically):
```

apt-get install lsb-core

```

If you have a 64-Bit system, you also need the following:
```

ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32

```


Once you installed the google-earth.deb package, you need to give the executable execute permission:
```

chmod +x /opt/google/earth/free/googleearth-bin

```


Afterwards, it still won't work, because it misses the shared libaries, so you need to add them to ldconf.
```

gedit /etc/ld.so.conf.d/googleearth.conf

```

And add the following content
```

# Google-Earth needs you
/opt/google/earth/free

```

Afterwards, still have to update the changed ldconfig:
```

/sbin/ldconfig

```

alternatively you can do a
```

export LD_LIBRARY_PATH="/opt/google/earth/free"

```
every time 

From now on you can start google-earth via:
```

/opt/google/earth/free/googleearth-bin

```
or from 
```

Applications->Internet->Google Earth

```

---

### Post by Uwe907 on 2011-01-26
Excellent!!  I've tried and tried but didn't even get close, so for me this was a real lifeline.

I'm on 64bit Ubuntu 10.10 and it worked perfectly once I worked out that *I* needed to install the 64 bit version. For guys like me who haven't yet fully woken up, I suggest changing 

"Click on 32 Bit Debian /ubuntu and click on Agree and download."

to

"Click on either 32 or 64 Bit Debian /ubuntu as appropriate and click on Agree and download."

Oh yes, I did every command sudo.  I guess if I'd entered "sudo su" at the terminal then the code you supplied could have been used exactly as is.

Many, many thanks indeed for a magnificent effort.

Uwe

---

### Post by adeee on 2011-01-27
yup i try and its works perfect. am 32 bit user. well i just install google earth first time on ubuntu. i will tell you any bug if any appear.

thaxs and great :P

---

### Post by jocko on 2011-01-28
Here's an even easier way:

```
sudo apt-get install googleearth-package
make-googleearth-package --force
sudo dpkg -i googleearth*.deb
```

---

### Post by adeee on 2011-01-29
wrong post. correct is next.

---

### Post by adeee on 2011-01-29
> **jocko said:**
> Here's an even easier way:

```
sudo apt-get install googleearth-package
make-googleearth-package --force
sudo dpkg -i googleearth*.deb
```


i tried your instruction but this error occure. 

see and tell me the solution please.
```

adeee@adeee-desktop:~$ sudo dpkg -i googleearth*.deb
[sudo] password for adeee: 
(Reading database ... 222186 files and directories currently installed.)
Preparing to replace googleearth 6.0.1.2032+0.5.7-1 (using googleearth_6.0.1.2032+0.5.7-1_i386.deb) ...
Unpacking replacement googleearth ...
Setting up googleearth (6.0.1.2032+0.5.7-1) ...

Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-support ...
adeee@adeee-desktop:~$ googleearth
/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found
adeee@adeee-desktop:~$ 
```

---

### Post by paulysa1969 on 2011-03-08
Thanks for this info on installing Google Earth. I managed to install Google Earth 6.0.1.2032 beta onto my system running Ubuntu 10.10. :D

Virtual Box -4.0_4.0.4-70112 is also installed and was working on Friday 4 March but was not working today. :confused:

I need to restore my iPhone which I was going to do under VirtualBox/WindowsXP/iTunes -which worked quite well :D......until now :confused:.
Since I have recent iPhone backups and VirtualBox snapshots I removed Virtual Box  completely in Synaptic and restarted and reinstalled VirtualBox 4 but this has not  helped :confused:. 
I also removed it again and installed VirtualBox-3.2_3.2.12-68302 and this has also not helped :confused: :confused:.

I am uncertain where to start troubleshooting this. If there is a way to use Ubuntu to restore an iPhone from a recent backup without VirtualBox/WindowsXP/iTunes, I would appreciate any advice :KS.

Thanks is advance
Paul

---

### Post by Linearcraig on 2011-03-08
Beautiful. First stop New York to see the purty 3d buildings lol

Thanks a lot

---

### Post by afd on 2011-03-21
This seemed to install Google earth 32bit for me on Ubuntu 10.10 - nice to get back to playing with this app.

Unfortunately it also seems to have borked my Skype :( Can anyone help me fix Skype or uninstall Google Earth and restore my system to as it was (I need Skype, I can live without GE)

Thanks in advance.

---

### Post by rleck on 2011-03-24
I find myself in company with afd here. After the GE6 install, which went fine, Skype continued to work until a reboot. Now it won't start. (My VBox 4.0.4 install is still healthy) Reinstalling skype hasn't helped. With all else remaining the same, I'm stumped. Is there something in the gaggle of files that came with lsb-core that skype doesn't like? :confused:

skype(2.1.0.81-1ubuntu5) & google-earth-stable(6.0.1.2302-r0) on Ubuntu 10.10 - amd64

Unlike afd, I need both skype and GE!

---

### Post by rleck on 2011-03-25
Solved:

This was my skype error after installing google earth 6 using the instructions in this thread:
symbol lookup error: /usr/lib32/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

There are heaps of threads about this in the forums, but most are for an historical issue with getlibs and duplicate Qt installs, which didn't apply in my situation and have since been fixed in packages(nor did their fix work for me)

I tried all manner of re-installs, without success. This is what worked:

Used synaptic to do a 'completely remove' the new google earth 6 I installed using the instructions above. 
**Tested skype and it worked.** (To eliminate the possibility of other issues)


Then I followed the install instructions I found here:
[http://www.ubun2.info/2010/10/how-to-install-google-earth-in-ubuntu.html?showComment=1287937450936](http://www.ubun2.info/2010/10/how-to-install-google-earth-in-ubuntu.html?showComment=1287937450936)

googleearth-package creates the .deb from google's GoogleEarthLinux.bin specifically for your system. From the forums this skype killing seems to be most often but not exclusively an amd64 issue.

Open terminal: Applications > Accessories > Terminal
sudo apt-get install ia32-libs lib32nss-mdns
sudo apt-get install googleearth-package
make-googleearth-package --force  
#Ignore copious warnings

Double click resulting <googleearth.6.xx.x.x.x.x>.deb file (probably in your home folder if you didn't change terminal directory) and it will install with your password.
Open google earth: Applications > Internet > Google Earth
Open skype: Applications > Internet > Skype - both should work!
Good luck!

---

### Post by unit1 on 2012-01-07
Running 10.10 and I just double clicked on the .deb file and it installed automagically via Ubuntu Software Center.:D

---

### Post by Rebelli0us on 2012-01-08
Is google earth a trusted app?

---

