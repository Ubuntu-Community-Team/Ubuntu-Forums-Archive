---
title: "how to Recover encrypted home folder"
date: 2009-11-25
forum: Security
---

### Post by Ceiber Boy on 2009-11-25
When Ubuntu 9.10 was released i was pleased to see that their was an option in the install process to encrypt the home folder. post installation my encryption pass key was displayed which i noted.

as an academic exercise i'm trying to recover my home folder via a live CD, in preparation that in the unlikely event that things do go wrong i would be able to recover my data, however things don't seem to be straight forward! can anyone please explain in simple terms how this is done or direct me to some offical documentation where this is clearly explained.

Regards

---

### Post by bodhi.zazen on 2009-11-25
See these links

General : [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

And to answer your question : [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by shane2peru on 2009-12-22
> **bodhi.zazen said:**
> See these links

General : [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

And to answer your question : [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Ok, I'm not just doing this for fun.  Lightning struck very close to home, and my computer went belly up.  I have rsynced my data to an external hdd just the day before, and the encrypted folder was mounted (I believe).  Anyrate I have encrypted data on my external hdd under .Secured_encfs and a .encrypted folder.   When I tried to mount it following the instructions in the first link, it mounted, however all the directories and files are mumble jumble.  They are letters, but make no sense, thus making files unrecognizable.  Why is it like that?  Is there any way for me to recover this data?  There is a possibility that my internal hdd is still good, and perhaps I can get data off it, but I have not had the opportunity to try that.  Any help on this would be greatly appreciated!  I used the cryptkeeper to set it up, access.  I don't know if that is different or the same.  I'm a total noob to encryption.

Shane

---

### Post by shane2peru on 2009-12-22
a BIG SIGHHHHHHH!  Got it, I had to install cryptkeeper.  Then I just copied the .encrypt and .Secured_encfs folder to my other computer, opened up cryptkeeper and imported the encrypted folder.  Apparently it uses a different format than described in the restore processes noted above.  

Shane

---

### Post by bodhi.zazen on 2009-12-22
Sweet, glad you got it sorted.

---

### Post by shane2peru on 2009-12-22
> **bodhi.zazen said:**
> Sweet, glad you got it sorted.

Me too!!!  Very important data was at stake!  

Shane

---

### Post by shane2peru on 2009-12-23
> **bodhi.zazen said:**
> Sweet, glad you got it sorted.

Hey you may think about including cryptkeeper in your tutorial.  The advantage is that it has a GUI front end, and is easy to use.  ```
sudo apt-get install cryptkeeper
``` or find it in Synaptic searching for that name.  Then **Applications -> System Tools -> Cryptkeeper**  At start up it should ask you what folder to encrypt or something like that I don't remember now. Then it puts an icon by the clock and it is point and click to mount and unmount it.  Of course it asks for your passphrase as well.  Very simple to use, and very user friendly.  I mount it when I make my backups, and the data is all moved, and still encrypted, then I copied it here, and had to import the folder and it was all in good shape to use on a new box!  

Shane

---

### Post by bodhi.zazen on 2009-12-23
I agree, I included it by default in Zenix :

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

### Post by MorganJarl on 2010-05-10
I have a similar problem.

I have followed the instructions on this blog post:  [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
 Dustin asked that we ask for support here, so here I am.
 I followed all the steps and can now see all my files in the terminal, but not copy them.
 The only step I am not sure it actually worked is the last one where I get this message: 



> 
morgan@ubuntu:~$ cat .profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.
 # the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
 # if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
 . "$HOME/.bashrc"
    fi
fi
 # set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


I am running from a LiveCD of 9.10 and trying to copy my encrypted /home folder and I get this message when I am trying to do it even if I follow the above steps:
 

> morgan@ubuntu:~$ cp /home/morgan /media/OneTouch4
cp: omitting directory `/home/morgan'
 
Any ideas?

---

### Post by bodhi.zazen on 2010-05-10
You simply need the -r flag

see man cp

```
sudo cp -r cp /home/morgan /media/OneTouch4/
```
You may not need sudo, depending on permissions, but can't hurt

---

### Post by MorganJarl on 2010-05-12
The CP command now work I think, but I try to mount my external drive too - so I can copy to it - which seems to work. Only when I try to copy the stuff I get a long line of these messages:
cp: cannot create directory `/media/OneTouch4/Videos/Webcam': No space left on device

But I know for sure I have 200 GB and am only trying to move max 70 GB. So i guess me trying to mount it does not work? What command should I use to mount my external? This is what I used:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - morgan
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

morgan@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [8f01ae7b2db4a64d] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/morgan

morgan@ubuntu:~$ cd $HOME
morgan@ubuntu:~$ ls -alF
total 2280
drwx------ 69 morgan morgan  20480 2010-05-08 19:53 ./
drwxr-xr-x  4 root   root     4096 2010-02-04 00:24 ../
drwx------  3 morgan morgan   4096 2010-02-06 20:07 .adobe/
-rw-r--r--  1 morgan morgan     24 2010-05-07 11:07 .aspell.en.prepl
-rw-r--r--  1 morgan morgan     22 2010-05-07 11:07 .aspell.en.pws
-rw-------  1 morgan morgan   2258 2010-05-11 12:59 .bash_history
-rw-r--r--  1 morgan morgan    220 2010-02-04 00:24 .bash_logout
-rw-r--r--  1 morgan morgan   3180 2010-02-04 00:24 .bashrc
drwx------ 11 morgan morgan   4096 2010-03-24 19:01 .cache/
drwxr-xr-x  2 morgan morgan   4096 2010-05-03 22:57 cbt/
drwx------  3 morgan morgan   4096 2010-02-04 19:15 .compiz/
drwxr-xr-x 20 morgan morgan   4096 2010-04-07 01:00 .config/
drwx------  3 morgan morgan   4096 2010-02-04 18:46 .dbus/
drwxr-xr-x  5 morgan morgan   4096 2010-03-17 22:47 democracy2/
drwxr-xr-x  6 morgan morgan  12288 2010-05-07 15:43 Desktop/
-rw-r--r--  1 morgan morgan     56 2010-05-08 09:22 .dmrc
drwxr-xr-x  7 morgan morgan   4096 2010-04-29 19:48 Documents/
drwxr-xr-x  2 morgan morgan  24576 2010-05-07 01:01 Downloads/
drwxr-xr-x  3 morgan morgan   4096 2010-05-08 09:23 .dropbox/
drwxr-xr-x  6 morgan morgan   4096 2010-04-10 18:44 Dropbox/
drwxr-xr-x  4 morgan morgan  12288 2010-03-23 23:16 .dropbox-dist/
-rw-r--r--  1 morgan morgan    983 2010-03-29 11:26 EBJKS.ebjkeystore
-rw-r--r--  1 morgan morgan      0 2010-03-29 11:26 EBJKS.ebjkeystoreBAK
lrwxrwxrwx  1 morgan morgan    124 2010-02-04 00:24 .ecryptfs -> /home/.ecryptfs/morgan/.ecryptfs/
-rw-------  1 morgan morgan     16 2010-02-04 18:46 .esd_auth
drwxr-xr-x  8 morgan morgan   4096 2010-04-08 10:30 .evolution/
-rw-r--r--  1 morgan morgan    167 2010-02-04 00:24 examples.desktop
drwx------  2 morgan morgan   4096 2010-04-29 20:25 .filezilla/
drwxr-xr-x  2 morgan morgan  12288 2010-05-08 20:20 .fontconfig/
drwx------  3 morgan morgan   4096 2010-03-15 01:33 .FontForge/
drwxr-xr-x  2 morgan morgan   4096 2010-03-10 01:11 .fontmatrix/
-rw-r--r--  1 morgan morgan    598 2010-03-15 01:23 .fontmatrix.data
drwxr-xr-x  2 morgan morgan  12288 2010-03-22 00:38 .fonts/
-rw-r--r--  1 morgan morgan    130 2010-03-10 01:11 .fonts.conf
drwxr-xr-x  2 morgan morgan   4096 2010-05-07 10:31 .freemind/
drwx------  5 morgan morgan   4096 2010-05-08 21:26 .gconf/
drwx------  2 morgan morgan   4096 2010-05-08 22:46 .gconfd/
drwx------  4 morgan morgan   4096 2010-02-22 14:57 .gegl-0.0/
drwxr-xr-x 22 morgan morgan   4096 2010-05-06 01:47 .gimp-2.6/
-rw-r-----  1 morgan morgan      0 2010-05-08 19:37 .gksu.lock
drwx------  3 morgan morgan   4096 2010-02-04 20:21 .gnome/
drwx------ 10 morgan morgan   4096 2010-05-08 04:23 .gnome2/
drwx------  2 morgan morgan   4096 2010-02-04 18:46 .gnome2_private/
drwx------  2 morgan morgan   4096 2010-05-08 09:22 .gnupg/
drwxr-xr-x  2 morgan morgan   4096 2010-05-08 09:22 .gstreamer-0.10/
-rw-r--r--  1 morgan morgan    291 2010-05-08 09:34 .gtk-bookmarks
drwx------  2 morgan morgan   4096 2010-02-04 18:46 .gvfs/
drwxr-xr-x  2 morgan morgan   4096 2010-02-25 13:39 .helix/
-rw-r--r--  1 morgan morgan     34 2010-05-06 01:01 .httrack.ini
-rw-------  1 morgan morgan  34254 2010-05-08 09:22 .ICEauthority
drwxr-xr-x  2 morgan morgan   4096 2010-02-04 20:59 .icons/
drwxr-xr-x  4 morgan morgan   4096 2010-04-14 02:20 .java/
drwxr-xr-x  2 morgan morgan   4096 2010-04-29 19:20 .jftp/
drwxr-xr-x  3 morgan morgan   4096 2010-02-19 19:55 .kde/
drwx------  3 morgan morgan   4096 2010-03-22 00:08 .kompozer.net/
drwxr-xr-x  3 morgan morgan   4096 2010-02-04 19:36 .local/
drwx------  3 morgan morgan   4096 2010-02-06 20:07 .macromedia/
-rw-r--r--  1 morgan morgan   3146 2010-02-25 13:40 .mailcap
drwx------  3 morgan morgan   4096 2010-02-04 20:26 .mission-control/
drwxr-xr-x  3 morgan morgan   4096 2010-02-19 15:43 .mouseTrap/
drwx------  4 morgan morgan   4096 2010-02-15 15:01 .mozilla/
drwx------  3 morgan morgan   4096 2010-02-15 15:02 .mozilla-thunderbird/
drwxr-xr-x 98 morgan morgan  28672 2010-04-18 14:07 Music/
drwx------  5 morgan morgan   4096 2010-05-06 01:38 .mysqlgui/
drwxr-xr-x  2 morgan morgan   4096 2010-02-04 18:46 .nautilus/
drwxr-xr-x  3 morgan morgan   4096 2010-02-05 12:34 .openoffice.org/
drwx------  4 morgan morgan   4096 2010-05-04 00:24 .personal/
drwxr-xr-x 12 morgan morgan  12288 2010-05-07 15:42 Pictures/
drwx------  3 morgan morgan   4096 2010-02-04 19:36 .pki/
lrwxrwxrwx  1 morgan morgan    104 2010-02-04 00:24 .Private -> /home/.ecryptfs/morgan/.Private/
-rw-r--r--  1 morgan morgan    675 2010-02-04 00:24 .profile
drwxr-xr-x  2 morgan morgan   4096 2010-02-04 18:46 Public/
drwx------  2 morgan morgan   4096 2010-05-08 09:22 .pulse/
-rw-------  1 morgan morgan    256 2010-02-04 18:46 .pulse-cookie
drwxr-xr-x  2 morgan morgan   4096 2010-03-14 23:38 .qt/
drwxr-xr-x  3 morgan morgan   4096 2010-05-05 19:25 .rapache/
-rw-------  1 morgan morgan  35112 2010-05-05 20:33 .recently-used
-rw-------  1 morgan morgan 621115 2010-05-08 19:34 .recently-used.xbel
drwxr-xr-x  3 morgan morgan   4096 2010-03-15 01:25 .schoolsplay.rc/
drwxr-xr-x  3 morgan morgan   4096 2010-03-12 15:46 .scribus/
drwx------  3 morgan morgan   4096 2010-05-02 22:24 .Skype/
drwx------  2 morgan morgan   4096 2010-02-04 18:46 .ssh/
-rw-r--r--  1 morgan morgan      0 2010-02-04 19:00 .sudo_as_admin_successful
drwxr-xr-x  2 morgan morgan   4096 2010-02-04 18:46 Templates/
-rw-r--r--  1 morgan morgan 449169 2010-03-15 02:00 TeutonicNo1-DemiBold.sfd
-rw-r--r--  1 morgan morgan 447706 2010-03-15 01:56 TeutonicNo1-DemiBold.sfd~
drwxr-xr-x  2 morgan morgan   4096 2010-02-04 20:59 .themes/
drwxr-xr-x  5 morgan morgan   4096 2010-02-04 20:59 .thumbnails/
drwxrwxr-x  2 morgan morgan   4096 2010-02-19 15:58 Ubuntu One/
drwxr-xr-x  2 morgan morgan   4096 2010-02-05 12:14 .update-manager-core/
drwx------  2 morgan morgan   4096 2010-02-04 18:49 .update-notifier/
drwxr-xr-x  7 morgan morgan   4096 2010-02-06 20:01 Videos/
drwxr-xr-x  2 morgan morgan   4096 2010-03-24 15:00 .wapi/
drwxr-xr-x  4 morgan morgan   4096 2010-03-22 06:43 .wine/
drwxr-xr-x  4 morgan morgan   4096 2010-02-04 23:52 .wine_old/
-rw-------  1 morgan morgan   8185 2010-05-08 21:12 .xsession-errors
-rw-------  1 morgan morgan  27151 2010-05-08 04:23 .xsession-errors.old
morgan@ubuntu:~$ cat .profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
morgan@ubuntu:~$ sudo mount /dev/sdb1 /mnt
sudo: unable to resolve host ubuntu
[sudo] password for morgan: 
morgan@ubuntu:~$ sudo cp -r /home/morgan /media/OneTouch4/
sudo: unable to resolve host ubuntu
cp: writing `/media/OneTouch4/Videos/Film/': No space left on device

```

---

### Post by bodhi.zazen on 2010-05-12
I think you are confusing paths and what is mounted where and your chroot.

After you decrypt your old home, exit the chroot.

Then you will 

sudo cp -R /mnt/home/morgan/* /media/OneTouch4/

---

### Post by MorganJarl on 2010-05-12
Hmmm... Ok, I tried this after following the instruction from Kirklands blog:

> morgan@ubuntu:~$ sudo mount /dev/sdb1 /mnt
sudo: unable to resolve host ubuntu
[sudo] password for morgan: 
mount: according to mtab, /dev/sdb1 is already mounted on /mnt

morgan@ubuntu:~$ exit
logout

root@ubuntu:/# sudo cp -R /mnt/home/morgan/* /media/OneTouch4/backup/
sudo: unable to resolve host ubuntu
cp: cannot stat `/mnt/home/morgan/*': No such file or directory
root@ubuntu:/# 


What is wrong now? I might sound a bit more knowledgeable then I am. I had to google about how to exit chroot (which I am not even sure what it is to be honest, though I am starting to understand a bit more). Am I doing something wrong or is there something wrong with my stuff?

---

### Post by MorganJarl on 2010-05-12
How do I mount my external HDD as my morgan user? 
I don/t have the permission to look at the external HDD or something:

> morgan@ubuntu:/media$ cd /media/OneTouch4
-su: cd: /media/OneTouch4: Permission denied


When I try to find the /mnt as my morgan user I get this (that is an empty dir):

> morgan@ubuntu:~$ cd /mnt
morgan@ubuntu:/mnt$ dir
morgan@ubuntu:/mnt$


If this helps...

---

### Post by MorganJarl on 2010-05-16
Didn't manage to mount my External Hdd, but I managed to move bits out of my encrypted folder to a non encrypted on the same HDD and then move them to the external by using the LiveCD root user. So now it is fixed. Thanks.

---

### Post by lamadredelsapo on 2010-09-26
I have a similar problem, I followed Dustin Kirkland's howto and thus I can list my files within my terminal.
Now I want to copy them to my external hdd so from another terminal (outside chroot) I did the follwing:

```
sudo cp -r /mnt/home/fernando/* /media/LACIE\ FPH/
cp: cannot stat `/mnt/home/fernando/*': No such file or directory
```

I don't understand why it cannot find any files...

---

### Post by kswix on 2011-11-15
What I must do if after mount I see files (ls) in my home directory like this:

ECRYPTFS_FNEK_ENCRYPTED.FWZ62j6-MK5SESESo8Tnpl1............. ?

---

