---
title: "Actual &quot;ubuntu&quot; session issues"
date: 2020-03-03
forum: Ubuntu Development Version
---

### Post by dino99 on 2020-03-03
Since a few days, some applets and app have troubles:

- synaptic now only loads via 'sudo' command line, icon click now loop. Previous version has also the same problem with the latest gnome upgrades.
- some chromium urls not  displaying all the icons: get instead some rectangles (can be the site fault indeed, but there is nothing logged to solve that problem) 
- gnome-shell-extension weather icon fails to load
- gnome-shell-extension-system-monitor cant run (lot of js errors)
- gnome-shell-extension-top-icons-plus is not compatible with actual gnome version (cant be installed on 3.35+ version)

Quite usual issues met at freeze times :mad:

---

### Post by mc4man on 2020-03-03
synaptic is fine here, using the current non-proposed package (  0.84.6ubuntu3

---

### Post by ajgreeny on 2020-03-03
Also seems fine here, though I am not using ubuntu but Xubuntu; same synaptic version so I think this may be something other than a general OS problem; perhaps more gnome related.

---

### Post by mc4man on 2020-03-03
> **ajgreeny said:**
> Also seems fine here, though I am not using ubuntu but Xubuntu; same synaptic version so I think this may be something other than a general OS problem; perhaps more gnome related.
There is a new synaptic in proposed that's not ready for use...

---

### Post by ajgreeny on 2020-03-03
> **mc4man said:**
> There is a new synaptic in proposed that's not ready for use...
Even when using a development version I keep away from "proposed" unless there's a good reason to use it. I will however now install that newer version of synaptic and see if I get the same problem.

---

### Post by mc4man on 2020-03-03
On a throwaway install just had issue where no libreoffice app would open except as root. Resolved that with a sledgehammer of
sudo rm -rf /tmp/*

---

### Post by dino99 on 2020-03-04
Good idea about the sledgehammer , now synaptic loads by clicking his icon  :P

---

### Post by dino99 on 2020-03-04
Agrrrr; one reboot later, get again the same loop issue and the previous solution does not works  ](*,)](*,)

 pkexec[1926]:  Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/oem] [COMMAND=/usr/sbin/synaptic]

---

### Post by ajgreeny on 2020-03-04
All still seems well with my Xubuntu 20.04 install after adding the "proposed" version of synaptic, so again, it looks as if this may be something related to the default gnome desktop.

I wonder if any other DE versions, ie, Kubuntu, Ubuntu-Mate, etc, etc, have seen the problem?

---

### Post by fthx on 2020-03-04
I run GNOME and latest Synaptic and I've not experienced any issue.

---

### Post by mc4man on 2020-03-04
> **dino99 said:**
> Agrrrr; one reboot later, get again the same loop issue and the previous solution does not works  ](*,)](*,)

Maybe try this. 
Open a terminal & go
```
journalctl -f > 1.log
```
Then try to open synaptic normally, when it fails back in terminal go ctrl+c to quit.
Then check out 1.log in home folder for any errors.
(- may be apparmor issue..

---

### Post by dino99 on 2020-03-04
nothing special from systemctl -f
but journalctl has logged:

pkexec: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/oem] [COMMAND=/usr/sbin/synaptic]

---

### Post by ajgreeny on 2020-03-04
Looking back at your original post you said> - synaptic now only loads via 'sudo' command line, icon click now loop. Previous version has also the same problem with the latest gnome upgrades.
Did you really start it with a simple ***sudo synaptic*** command or did you perhaps use ***sudo -H synaptic***?

I hope it was the latter as using sudo for a GUI application can cause a number of problems for a user with their home files and folders becoming root owned.

---

### Post by mc4man on 2020-03-04
> **dino99 said:**
> nothing special from systemctl -f
but journalctl has logged:

pkexec: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/oem] [COMMAND=/usr/sbin/synaptic]

Sorry, was on phone which is a hassle to post, meant journalctl which you figured out..
The key part above is Not authorized. I'd assume you're in the sudo and admin groups so not sure what the issue is. 
There used to be a startup app for pkexec but don't believe it's used anymore.

So what happens if you use pkexec directly, i.e
```
pkexec synaptic
```
Do you get the auth pop up?

---

### Post by dino99 on 2020-03-05
Same issue:

 pkexec synaptic
Error executing command as another user: Not authorized

This incident has been reported.

Going to "System Settings Users" then click on Unlock, i also get a loop and stay locked indeed.

---

### Post by corradoventu on 2020-03-05
I have Ubuntu 20.04 with Gnome - NO proposed - and synaptic works finel.
```
corrado@corrado-x4-ff-0303:~$ inxi -Sx
System:
  Host: corrado-x4-ff-0303 Kernel: 5.4.0-14-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.35.91 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
corrado@corrado-x4-ff-0303:~$ apt policy synaptic
synaptic:
  Installed: 0.84.6ubuntu3
  Candidate: 0.84.6ubuntu3
  Version table:
 *** 0.84.6ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-x4-ff-0303:~$ 
```

Edit: both with X11 and Wayland session

---

### Post by dino99 on 2020-03-05
'proposed' is always activated on my side, as i like riding on the wild edge :p

if i can grab some free time to dig around that issue, maybe i will find the faulty update(s): deactivating 'proposed' then downgrading to non proposed package version.
I have also read some devs talks about the current known problems, and some fix upgrades are already pending; so there is no hurry with that testing install.

---

### Post by ajgreeny on 2020-03-05
I'll repeat my query from post #13 related to your statement about using ***sudo synaptic***.

Was that the command you used or did you use a variation of it, eg ***sudo -H synaptic***

The warning about > Error executing command as another user: Not authorized makes me wonder if you did actually use ***sudo synaptic*** which may have changed ownership of your home files and folders to root.

---

### Post by dino99 on 2020-03-06
yes, i have always used 'sudo' without alternative nor trouble, at least until now.

---

### Post by ajgreeny on 2020-03-06
OK, so now let's see the output of ***ls -la*** in terminal; I suspect there may be some files and/or folders owned by root instead of your user which can cause all sorts of problems.

You should NEVER use sudo alone in order to open a GUI application; see **RootSudo** in my signature below for info about this.

---

### Post by dino99 on 2020-03-07
Here is the output:

```
oem@focal64:~$ ls -la
total 104
drwxr-xr-x 20 oem oem 4096 mar.   4 18:53 .
drwxr-xr-x  3 root  root  4096 jan. 31 14:47 ..
-rw-------  1 oem oem 4261 mar.   6 20:57 .bash_history
-rw-r--r--  1 oem oem  220 jan. 31 14:47 .bash_logout
-rw-r--r--  1 oem oem 3771 jan. 31 14:47 .bashrc
drwx------ 20 oem oem 4096 mar.   5 10:50 .cache
drwx------ 23 oem oem 4096 feb. 29 16:33 .config
drwx------  3 oem oem 4096 feb. 28 12:19 .dbus
drwxr-xr-x  2 oem oem 4096 feb.  5 10:04 Desktop
drwxr-xr-x  2 oem oem 4096 mar.   5 10:51 Documents
drwxr-xr-x  3 oem oem 4096 mar.   4 15:21 Downloads
drwx------  3 oem oem 4096 feb.  1 08:11 .gnupg
drwx------  3 oem oem 4096 jan. 31 15:51 .local
drwx------  5 oem oem 4096 feb.  2 20:47 .mozilla
drwxr-xr-x  2 oem oem 4096 feb.  5 10:04 Music
-rw-r--r--  1 oem oem  357 feb.  5 10:03 .pam_environment
drwxr-xr-x  2 oem oem 4096 feb.  5 10:04 Pictures
drwx------  3 oem oem 4096 jan. 31 18:46 .pki
-rw-r--r--  1 oem oem  807 jan. 31 14:47 .profile
drwxr-xr-x  2 oem oem 4096 jan. 31 15:51 Public
drwxr-xr-x  3 oem oem 4096 jan. 31 17:28 snap
drwx------  2 oem oem 4096 feb.  1 08:11 .ssh
-rw-r--r--  1 oem oem    0 jan. 31 15:09 .sudo_as_admin_successful
drwxr-xr-x  2 oem oem 4096 feb.  2 21:17 Téléchargements
drwxr-xr-x  2 oem oem 4096 feb.  5 10:04 Templates
drwxr-xr-x  2 oem oem 4096 feb.  5 10:04 Videos
```

---

### Post by ajgreeny on 2020-03-07
Well in the list you have shown of ls -la output you appear to have managed to get away with using command ***sudo synaptic*** or other GUI applications, though are you sure that was the full list of output you saw as there appear to be a few files missing in your list, eg .Xauthority, .xsession-errors, .ICEauthority.
Are you using wayland instead of xorg?  That may account for the lack of .Xauthority and .xsession-errors.

I also note the username oem and I wonder if you have performed an oem installation, though I admit I'm not sure what that means regarding running a normal user session so we must wait someone who know about OEM installations if that is how you installed.

---

### Post by dino99 on 2020-03-07
It is a default 'ubuntu' session, and the output above is complete; no matter what the user name is (dont be disturbed by it :P)

Compared to an other install '.dbus' here is owned by 'user' instead of 'root' on the other install.

---

### Post by corradoventu on 2020-03-07
On my Ubuntu 20.04 synaptic works fine clicking on the icon and desktop file is as follows:
```
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=synaptic-pkexec
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
X-Ubuntu-Gettext-Domain=synaptic
StartupNotify=true
StartupWMClass=synaptic

```

---

### Post by mc4man on 2020-03-07
This has nothing do do with synaptic, it's about pkexec.
The ~/.dconf folder is useless, generally created in the past by sudo gedit or similar. Normally also would see ~/.cache/dconf which also is useless. Both folder and contents can be deleted.

To check $HOME for root owned files better to run
```
ls -lA -R  |grep "root root"
```

At this point in _Gnome (Ubuntu session) _one can again run sudo gedit without consequence.
Also now there is no ~/.Xauthority file with gdm3.

To confirm it's just your user you could create a new user with admin rights and see.. Currently you can't do that but you can change the policy so no need to auth user-accounts.
Open /usr/share/polkit-1/actions/org.gnome.controlcenter.user-accounts.policy file as root, change the <allow_active>auth_admin</allow_active> line to yes as in screen.
Then if the new user can use pkexec for synaptic maybe you can find a file in ~/ that needs to be removed/redone/whatever.

A fresh install will certainly solve.

If you wanted to remove auth on opening synaptic normally then do the above edit on 
/usr/share/polkit-1/actions/com.ubuntu.pkexec.synaptic.policy

---

### Post by ajgreeny on 2020-03-07
Is the lack of .Xauthority a gnome case only, as I certainly have that file in my home in Xubuntu 20.04.

I have not used gnome for a long time now and have no way to find out if this is so or not.

---

### Post by mc4man on 2020-03-07
> **ajgreeny said:**
> Is the lack of .Xauthority a gnome case only, as I certainly have that file in my home in Xubuntu 20.04.

I have not used gnome for a long time now and have no way to find out if this is so or not.
I suspect so. A fresh install about 10 days ago had none, a fresh install today the same.

Edit:
It's the display manager. gdm3 doesn't create/use .Xauthority file, lightdm does and maybe other display managers.

---

### Post by ajgreeny on 2020-03-07
Thanks for that mc4man.

---

### Post by dino99 on 2020-03-11
Latest gnome upgrades from proposed now let sysnaptic be opened via its icon; so self upgrade fix :D

---

### Post by him610 on 2020-03-12
```

$ apt list synaptic
Listing... Done
synaptic/focal,now 0.84.6ubuntu3 amd64 [installed]

```

---

### Post by jefflpearsonii on 2020-03-13
The only real problem I am having with 20.04 is network proxy.  Just doesn't work.  I have installed Unity DE so logged into Gnome doesn't work there either

---

