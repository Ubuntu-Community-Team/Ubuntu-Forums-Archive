---
title: "install Linux Guest Additions (VB)"
date: 2009-09-05
forum: Virtualisation
---

### Post by ssulaco on 2009-09-05
Vista (Host)
Ubuntu (Guest)
Nvidia Geforce 6100
I cannot seem to open up the guest addition iso file located at the desktop,I would like to be able to use 3D effects in Virtualbox,see screenshots,any help would be much appreciated.

---

### Post by dk06 on 2009-09-05
> **ssulaco said:**
> Vista (Host)
Ubuntu (Guest)
Nvidia Geforce 6100
I cannot seem to open up the guest addition iso file located at the desktop,I would like to be able to use 3D effects in Virtualbox,see screenshots,any help would be much appreciated.


If your update mgr is running at the same time it may cause an issue installing the guest add-ons, but you should be able to access the files on the mounted ISO.

Looks like you're running the command from your desktop, try right-clicking the mounted CD and select "Open in Terminal" then retry the command

______________________________________________________________________
[http://download.virtualbox.org/virtualbox/3.0.4/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.0.4/UserManual.pdf)
> 
  2. Mount the VBoxGuestAdditions.iso file as your Linux guest’s virtual CD-
      ROM drive, exactly the same way as described for a Windows guest in chapter
      4.2.1.1, Mounting the Additions ISO file, page 62.
  3. Change to the directory where your CD-ROM drive is mounted and execute as
      root:
      sh ./VBoxLinuxAdditions-x86.run
      In a 64-bit Linux guest, use VBoxLinuxAdditions-amd64.run instead.
  The VirtualBox Guest Additions contain several different drivers. If for any reason
you do not wish to install them all, you can specify the ones which you wish on the
command line - for example
sh ./VBoxAdditions.run x11
  to install the X Window graphic drivers. Type in the command
                                     
   4 Guest Additions
sh ./VBoxAdditions.run help


---

### Post by Perryg on 2009-09-06
That works but there is an easier way since you are already on the desktop with the mounted CD.  
[list]Dbl click the cd to open it.  
Then open a terminal window and type sudo -i (enter password)
now just drag the proper Image to the terminal and drop it.  
Hit enter and it will install if you have everything that you are supposed to have installed to compile modules.[/list]

---

### Post by ssulaco on 2009-09-06
Thanks...I did install the DKMS,before hand.....Its my wifes computer,and when shes on it,I cant get near it, Im trying to convert her:)but she has a hard enough time with windows....Thanks again.

---

### Post by andrew.46 on 2009-09-09
Hi ssulaco,

> **ssulaco said:**
> I cannot seem to open up the guest addition iso file located at the desktop,I would like to be able to use 3D effects in Virtualbox,see screenshots,any help would be much appreciated.

I see that others have already got you going but I can see where you have come unstuck with your original command. If you wish to run from the commandline you need to change to the iso first (as dk06 has mentioned) and *then* you will find your files:

```

andrew@skamandros:~$ **[COLOR="Red"]cd /media/cdrom[/COLOR]**
andrew@skamandros:/media/cdrom$ ls -l
total 29159
dr-xr-xr-x 3 root root     2048 2009-08-05 03:37 32Bit
dr-xr-xr-x 2 root root     2048 2009-08-05 03:37 64Bit
-r-xr-xr-x 1 root root      230 2009-07-01 01:28 AUTORUN.INF
-r-xr-xr-x 1 root root     3937 2009-08-05 03:36 autorun.sh
-r-xr-xr-x 1 root root  3057104 2009-08-05 03:29 VBoxLinuxAdditions-amd64.run
-r-xr-xr-x 1 root root  2770868 2009-08-05 03:37 VBoxLinuxAdditions-x86.run
-r-xr-xr-x 1 root root 12555776 2009-08-05 03:24 VBoxSolarisAdditions.pkg
-r-xr-xr-x 1 root root  5753600 2009-08-05 03:17 VBoxWindowsAdditions-amd64.exe
-r-xr-xr-x 1 root root   477712 2009-08-05 03:11 VBoxWindowsAdditions.exe
-r-xr-xr-x 1 root root  5233968 2009-08-05 03:12 VBoxWindowsAdditions-x86.exe

```

And then run the installation command...

Andrew

---

### Post by ssulaco on 2009-09-10
Andrew...Thankyou for the additional info....Im not yet real proficient with the command line yet,it might be a few days before i give it a try again.

---

### Post by andrew.46 on 2009-09-10
Hi ssulaco,

> **ssulaco said:**
> Andrew...Thankyou for the additional info....Im not yet real proficient with the command line yet,it might be a few days before i give it a try again.

Don't worry too much about it, the other posts in this thread have suggested perfectly workable methods using the gui. I am just completing the picture :).

Andrew

---

### Post by ssulaco on 2009-09-11
> **andrew.46 said:**
> 
```

andrew@skamandros:~$ **[COLOR="Red"]cd /media/cdrom[/COLOR]**
andrew@skamandros:/media/cdrom$ ls -l
total 29159
dr-xr-xr-x 3 root root     2048 2009-08-05 03:37 32Bit
dr-xr-xr-x 2 root root     2048 2009-08-05 03:37 64Bit
-r-xr-xr-x 1 root root      230 2009-07-01 01:28 AUTORUN.INF
-r-xr-xr-x 1 root root     3937 2009-08-05 03:36 autorun.sh
-r-xr-xr-x 1 root root  3057104 2009-08-05 03:29 VBoxLinuxAdditions-amd64.run
-r-xr-xr-x 1 root root  2770868 2009-08-05 03:37 VBoxLinuxAdditions-x86.run
-r-xr-xr-x 1 root root 12555776 2009-08-05 03:24 VBoxSolarisAdditions.pkg
-r-xr-xr-x 1 root root  5753600 2009-08-05 03:17 VBoxWindowsAdditions-amd64.exe
-r-xr-xr-x 1 root root   477712 2009-08-05 03:11 VBoxWindowsAdditions.exe
-r-xr-xr-x 1 root root  5233968 2009-08-05 03:12 VBoxWindowsAdditions-x86.exe

```

And then run the installation command...

Andrew
Thanks for the visuals.....installation went good,
What should I do with the mounted ISO image on the desktop,does it have to remain there for the GA to work?

Also if I installed Debian along with Ubuntu in VB,will the Linux GA that installed for ubuntu work for Debian also?

---

### Post by andrew.46 on 2009-09-11
Hi ssulaco,

> **ssulaco said:**
> Thanks for the visuals.....installation went good,
What should I do with the mounted ISO image on the desktop,does it have to remain there for the GA to work?

Excellent news :). The mounted iso image can be safely unmounted, if you have a cdrom drive you will see a setting that allows it to be used in place of this.

> Also if I installed Debian along with Ubuntu in VB,will the Linux GA that installed for ubuntu work for Debian also?

I have not run Debian as a guest system so I cannot answer this one, but I would imagine it would. 

Andrew

---

