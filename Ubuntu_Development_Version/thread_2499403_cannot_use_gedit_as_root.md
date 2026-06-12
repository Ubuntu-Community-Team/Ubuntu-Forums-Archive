---
title: "cannot use gedit as root"
date: 2024-07-25
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-07-25
Hello,

trying under oracular to issue the command:
```
sudo gedit gnome-shell.css
```

the outcome is the following:
> mkdir: cannot create directory ‘/run/user/0’: Permission denied
Authorization required, but no authorization protocol specified

(gedit:3762): Gtk-WARNING **: 21:56:26.338: cannot open display: :0

the command:
```
sudo gnome-text-editor gnome-shell.css
```

is working fine.

Regards!

---

### Post by #&amp;thj^% on 2024-07-25
XFCE4 here with gedit installed:
```
 apt policy gedit
gedit:
  Installed: 46.2-3
  Candidate: 46.2-3
  Version table:
 *** 46.2-3 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```
It has to be in Gnome ie:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo gedit gnome-shell.css
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
And it saved my edit.
Also to note (no gnome-text-editor installed):
```
apt policy gnome-text-editor
gnome-text-editor:
  Installed: (none)
  Candidate: 46.3-1
  Version table:
     46.3-1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages

```

---

### Post by Claus7 on 2024-07-25
Hello,

thank you *1fallen* for your response. It seems that there is a different behavior between xfce and gnome then. Mine are:

> apt policy gedit
gedit:
  &#917;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;: (&#954;&#945;&#957;&#941;&#957;&#945;)
  &#933;&#960;&#959;&#968;&#942;&#966;&#953;&#959;:      46.2-3
  &#928;&#943;&#957;&#945;&#954;&#945;&#962; &#904;&#954;&#948;&#959;&#963;&#951;&#962;:
     46.2-3 500
        500 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) oracular/universe amd64 Packages


It's weird though. "&#917;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;: (&#954;&#945;&#957;&#941;&#957;&#945;)" above means "Installed: (none)", yet gedit is installed.

> 
apt policy gnome-text-editor
gnome-text-editor:
  &#917;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;: 46.3-1
  &#933;&#960;&#959;&#968;&#942;&#966;&#953;&#959;:      46.3-1
  &#928;&#943;&#957;&#945;&#954;&#945;&#962; &#904;&#954;&#948;&#959;&#963;&#951;&#962;:
 *** 46.3-1 500
        500 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) oracular/main amd64 Packages
        100 /var/lib/dpkg/status

I figured it out. The gedit version was a snap one. I checked synaptic and found out that gedit wasn't installed. After installing it, all were fine.

Regards!

---

### Post by vanadium on 2024-07-26
Using plain 'sudo' to launch a graphical application is a good way to break your account, as you should know. It is not without reason we used to have the "gksudo" tool back in the days.

A good way to edit system files is to use `sudoedit`, and specify the graphical editor to use. I have the script `sedit` in my ~/.local/bin directory:

```

#!/bin/sh
2>/dev/null SUDO_EDITOR="/usr/bin/gedit -s" sudoedit "$@"

```

Thus, a command `sedit <filename` will use `sudoedit` to edit a system file, specifying to use the graphical editor "gedit".

This is a safe way to edit system files. `sudoedit` creates a temporary copy that the user can edit with normal user priviledges. When the temporary copy is closed, `sudoedit` copies the changes over to the system file.

---

### Post by #&amp;thj^% on 2024-07-26
We are in the development sub forum, so most if not all us already know about "sudo any-gui" is not a good practice, so vanadium post above is a good reminder.
I'll use this as one more possibility:
```
export SUDO_EDITOR="/usr/bin/gedit"

```
All my permissions are just as expected:
```
 ls -la | grep root
drwxr-xr-x  3 root root          3 Jul 16 18:03 ..

```
```
ls -la /home/$USER
total 2338266
drwxr-x--- 29 me   me           58 Jul 26 10:06 .
drwxr-xr-x  3 root root          3 Jul 16 18:03 ..
-rw-rw-r--  1 me   me           41 Jul 25 16:21 .aspell.en.prepl
-rw-rw-r--  1 me   me           22 Jul 25 16:21 .aspell.en.pws
-rwxr-xr-x  1 me   me     99670660 May 26 18:00 balenaEtcher-1.18.11-x64.AppImage
-rwxr-xr-x  1 me   me     96000789 Nov  9  2022 balenaEtcher-1.9.0-x64.AppImage
-rwxr-xr-x  1 me   me          795 May 26 18:00 .bash_aliases
-rw-------  1 me   me        15380 Jul 26 10:06 .bash_history
-rw-r--r--  1 me   me           21 May 26 18:00 .bash_logout
-rw-r--r--  1 me   me           57 Jun  4 19:49 .bash_profile
-rw-r--r--  1 me   me         1272 Jul 17 17:06 .bashrc
drwxrwxr-x 31 me   me           34 Jul 25 12:21 .cache
drwxrwxr-x  2 me   me            8 Jul 17 10:17 cachyos-repo
drwxrwxr-x  4 me   me            9 Jul 17 10:12 .cargo
drwxrwxr-x  3 me   me            3 Jul 17 10:14 .cert
drwxr-xr-x 50 me   me           67 Jul 26 10:02 .config
drwxrwxr-x 80 me   me          223 Jul 17 10:37 .conky
-rw-------  1 me   me          508 May 26 18:00 dead.letter
drwxr-xr-x  2 me   me            2 Jul 16 18:22 Desktop
-rw-r--r--  1 me   me           26 Jul 25 10:23 .dmrc
drwxr-xr-x  2 me   me           61 Jul 25 16:32 Documents
drwxr-xr-x  3 me   me            4 Jul 26 08:34 Downloads
-rwxr-xr-x  1 me   me     48762856 May 26 18:00 ExtremeCooling4Linux-v0.3-x86_64.AppImage
drwxrwxr-x  2 me   me           76 Jul 17 10:15 .fonts
drwxrwxr-x  5 me   me            9 Jul 18 06:52 .gnupg
-rw-r--r--  1 me   me          559 May 26 18:00 .gtkrc-2.0
-rw-------  1 me   me            0 May  7 12:30 .ICEauthority
drwxrwxr-x  3 me   me            3 Jul 17 10:15 .icons
drwxrwxr-x  7 me   me            7 Jul 17 10:15 .kodi
drwx------  4 me   me            4 Jul 16 18:22 .local
drwxrwxr-x  4 me   me            4 Jul 17 10:15 .mozilla
drwxr-xr-x  5 me   me           10 Jul 17 10:19 Music
-rw-------  1 me   me         1934 Jun 11 13:53 nohup.out
drwxrwxr-x  4 me   me            5 Jul 17 10:15 .npm
drwxrwxr-x  3 me   me            3 Jul 17 10:16 .nv
-rw-r--r--  1 me   me       460088 May 13 16:22 nvidia-bug-report.log.gz
-rw-r--r--  1 me   me          662 Jun  6 09:25 .nvidia-settings-rc
-rw-rw-r--  1 me   me      1918810 Jul 25 13:40 os
drwxr-xr-x  2 me   me            8 Jul 17 10:20 Pictures
drwxrwxr-x  3 me   me            3 Jul 17 10:16 .pki
-rw-r--r--  1 me   me          874 May 26 18:00 .profile
drwxr-xr-x  2 me   me            2 Jul 16 18:22 Public
drwx------  2 me   me            3 Jul 16 18:04 .ssh
-rw-r--r--  1 me   me            0 Jul 16 18:22 .sudo_as_admin_successful
-rw-rw-r--  1 me   me         3280 Jul 17 10:34 surfshark-install.sh
-rw-r--r--  1 me   me   2147483648 May 26 18:00 temp.file
drwxr-xr-x  2 me   me            5 Jul 16 18:22 Templates
drwxrwxr-x 32 me   me           32 Jul 18 07:28 .themes
drwxrwxr-x  3 me   me            3 Jul 17 10:16 .var
drwxr-xr-x  2 me   me            2 Jul 16 18:22 Videos
-rw-r--r--  1 me   me          173 May 26 18:00 .wget-hsts
-rw-------  1 me   me           64 Jul 26 10:01 .Xauthority
-rw-r--r--  1 me   me         1600 Feb 23 05:17 .Xdefaults
-rw-r--r--  1 me   me           14 Feb 23 05:17 .xscreensaver
-rw-------  1 me   me       278591 Jul 26 10:29 .xsession-errors
-rw-------  1 me   me       704505 Jul 26 10:00 .xsession-errors.old
drwxrwxr-x  4 me   me           10 Jul 18 08:14 zc-master
-rw-r--r--  1 me   me           56 May 26 18:00 .zshrc

```
EDIT Whoops forgot:
```
stat /usr/bin/gedit
  File: /usr/bin/gedit
  Size: 14640     	Blocks: 18         IO Block: 14848  regular file
Device: 0,28	Inode: 726654      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-07-25 13:25:13.344962104 -0600
Modify: 2024-04-18 15:18:47.000000000 -0600
Change: 2024-07-25 13:24:42.591679932 -0600
 Birth: 2024-07-25 13:24:42.559662387 -0600

AND
ls -la  /usr/bin/gedit
-rwxr-xr-x 1 root root 14640 Apr 18 15:18 /usr/bin/gedit


```
But the warning on using "SUDO" with any GUI, should not be a good practice.

---

### Post by TheFu on 2024-07-26
I assuming anyone using the development version of any distro can handle the issues running a GUI under sudo can cause.  It used to be much more important before Ubuntu started allowing sudo to change to the HOME of the userid sudo switched into using, so any settings should be placed in that $HOME owned by the expected userid, not the user's HOME owned by a foreign userid, often root.

sudoedit **is** the solution around this, if Canonical doesn't want to consider it a bug and go out of their way to add corrections for yet another snap problem. Sigh.

Lastly, the EDITOR environment can be used and sudoedit will honor that setting happily.  Of course, we all know there's only 1 acceptable answer for which editor should be used. ;)

I'll go away now.

---

### Post by Claus7 on 2024-07-27
Hello,

just to mention that all changes were taking place under virtualbox using a testing ubuntu 24.10. Indeed in one case I had tampered with a theme file wrongly, yet the system "figured it out" and reverted back to default.

I "listen" to what you say, yet in some cases, using a file under the user, it provides duplicate results and I have to tamper with these files under root. I hope that I will have the time to mention that thoroughly.

Regards!

---

