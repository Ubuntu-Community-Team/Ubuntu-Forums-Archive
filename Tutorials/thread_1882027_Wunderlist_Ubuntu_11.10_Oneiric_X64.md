---
title: "Wunderlist Ubuntu 11.10 Oneiric X64"
date: 2011-11-16
forum: Tutorials
---

### Post by collisionystm on 2011-11-16
I just figured this out. Hope it helps someone.
 
 INSTALLING WUNDERLIST ON UBUNTU 11.10 ONEIRIC x64
 
 open a new Terminal
 
 ```
cd Downloads
```
 
 ```
wget http://www.6wunderkinder.com/downloads/wunderlist-1.2.4-linux-64.tgz
```
 
 ```
tar -xf wunderlist*
 
```
 ```
sudo mv Wunderlist* Wunderlist
```
 
 ```
sudo cp -R Wunderlist/ /opt
```
 
 ```
sudo chmod -R 770 /opt/Wunderlist
```
 
 ```
sudo chown -R YOURUSERNAME /opt/Wunderlist
```
 
 ```
sudo cp /opt/Wunderlist/Resources/wunderlist.png /usr/share/pixmaps/
```
 
 ```
gksudo gedit /usr/share/applications/wunderlist.desktop
```
 
 Paste this and save it
 
 > [Desktop Entry]
 Encoding=UTF-8
 Name=Wunderlist
 Exec=/opt/Wunderlist/Wunderlist
 Icon=/usr/share/pixmaps/wunderlist.png
 Terminal=false
 Type=Application
 Categories=Application;Office;
 StartupNotify=false
 
 
 ```
sudo apt-get install curl
```

```
sudo apt-get install libnotify4
```
 
 ```
sudo cp /usr/lib/x86_64-linux-gnu/libnotify.so.4.0.0 /usr/lib/libnotify.so.1
```
 
 ```
sudo apt-get install libffi6
```
 
 ```
sudo cp /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0 /usr/lib/libffi.so.5
```
 
 ```
sudo apt-get install libxss1
```
 
 You should now be able to open the Unity dash and type Wunderlist.
 
 Click and it should open.
 
 If it fails
 
 Open terminal and run it manually to see what errors you get
 ```

 cd /opt/Wunderlist/
```
 ```

 ./Wunderlist
```

---

### Post by rejven on 2011-11-19
works perfectly! thanks!

---

### Post by collisionystm on 2011-11-19
> **rejven said:**
> works perfectly! thanks!


Your welcome! :D

---

### Post by nttranbao on 2011-11-21
Thank you Collisionystm, It works properly on my Mint 11 64bit (Ubuntu). The default setup file does not work (encountered problems with font big or similar).

Best regards,
Bao

---

### Post by collisionystm on 2011-11-21
> **nttranbao said:**
> Thank you Collisionystm, It works properly on my Mint 11 64bit (Ubuntu). The default setup file does not work (encountered problems with font big or similar).

Best regards,
Bao

Oh.. It was only tested on 11.10 but I am glad you have it working :P

---

### Post by michael37 on 2011-11-23
a recommendation to avoid problems on future updates, 
replace copy with soft links.
e.g.

sudo ln -s /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0 /usr/lib/libffi.so.5

---

### Post by collisionystm on 2011-11-23
> **michael37 said:**
> a recommendation to avoid problems on future updates, 
replace copy with soft links.
e.g.

sudo ln -s /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0 /usr/lib/libffi.so.5


Good idea.
... just one question. Even if we use a *linking* feature, the link will only work when the original libffi.so.6.0.0 file is present, correct? So in a way, it is still the same effect? Am I wrong? I have never used soft links :P

---

### Post by reema1 on 2011-11-24
hey!
Thanks for this..
After trying so many ways of installing it...i finally see a Wunderlist file in the Dash.

But when i try running it using ```
./Wunderlist
```it shows this message - 
```
bash: ./Wunderlist: cannot execute binary file
```What shall i be doing now?? Please help.

I am new to Ubuntu, so kindly guide me through..

---

### Post by collisionystm on 2011-11-24
> **reema1 said:**
> hey!
Thanks for this..
After trying so many ways of installing it...i finally see a Wunderlist file in the Dash.

But when i try running it using ```
./Wunderlist
```it shows this message - 
```
bash: ./Wunderlist: cannot execute binary file
```What shall i be doing now?? Please help.

I am new to Ubuntu, so kindly guide me through..

If you click on the icon in the dash, does it work??

You shouldn't have to run that command for wunderlist. It is only if the clicking the icon in the dash fails.
To execute the command
cd /opt/Wunderlist
./Wunderlist

---

### Post by reema1 on 2011-11-24
> **collisionystm said:**
> If you click on the icon in the dash, does it work??

You shouldn't have to run that command for wunderlist. It is only if the clicking the icon in the dash fails.
To execute the command
cd /opt/Wunderlist
./Wunderlist


Yeah i did try clicking the icon from Dash, but it fails to open.. so i try opening from the terminal.. n it shows the error message - cannot execute binary files! :(
What should i next?

---

### Post by scarleo on 2011-11-28
Great guide. Just wanted to add that to get the icon working I had to also do chmod a+r /usr/share/pixmap/wunderlist.png

---

### Post by michael37 on 2011-11-28
> **collisionystm said:**
> Good idea.
... just one question. Even if we use a *linking* feature, the link will only work when the original libffi.so.6.0.0 file is present, correct? So in a way, it is still the same effect? Am I wrong? I have never used soft links :P

Nope, it will continue to point to the "libffi.so.6.0.0" file even if a file is updated with a newer version. This is very important and practical for future security updates.

---

### Post by khanx on 2011-11-30
:popcorn:

---

### Post by collisionystm on 2011-12-01
Your Welcome :)

---

### Post by Docaltmed on 2011-12-10
Thank you very much! Excellent guide, it worked like magic.

---

### Post by Majal on 2011-12-11
I've done everything in this page but still I get these errors, and after clicking RUN, the message "Segmentation Fault" prints out. Running the program using sudo, however, makes Wunderlist run. But of course, nobody's comfortable of always running the program in super user privileges.

bash print-out:

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 4

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 1

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 0

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 5

(installer:8111): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(installer:8111): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Segmentation fault

---

### Post by collisionystm on 2011-12-12
> **Majal said:**
> I've done everything in this page but still I get these errors, and after clicking RUN, the message "Segmentation Fault" prints out. Running the program using sudo, however, makes Wunderlist run. But of course, nobody's comfortable of always running the program in super user privileges.

bash print-out:

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 4

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 1

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 0

(process:8111): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 5

(installer:8111): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(installer:8111): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Segmentation fault




post the output of

sudo ls -lh /opt/Wunderlist

---

### Post by kkaland on 2011-12-12
For the record, this works in Mint 12 as well.

---

### Post by Majal on 2011-12-13
Dear collisionystm,

Here's the output:

maj@Emeth:~$ sudo ls -lh /opt/W*
[sudo] password for maj: 
total 212K
-rwxrwx---  1 maj root   95 2011-12-12 10:01 CHANGELOG.txt
drwxrwx---  2 maj root 4.0K 2011-12-12 10:01 installer
-rwxrwx---  1 maj root  577 2011-12-12 10:01 LICENSE.txt
-rwxrwx---  1 maj root  477 2011-12-12 10:01 manifest
drwxrwx--- 13 maj root 4.0K 2011-12-12 10:01 modules
drwxrwx---  8 maj root 4.0K 2011-12-12 10:01 Resources
drwxrwx---  3 maj root 4.0K 2011-12-12 10:01 runtime
-rwxrwx---  1 maj root  901 2011-12-12 10:01 tiapp.xml
-rwxrwx---  1 maj root 1.2K 2011-12-12 10:01 timanifest
-rwxrwx---  1 maj root 176K 2011-12-12 10:01 Wunderlist

Realizing that, I did this:

maj@Emeth:~$ sudo chown -R maj:maj /opt/W*
maj@Emeth:~$ sudo ls -lh /opt/W*
total 212K
-rwxrwx---  1 maj maj   95 2011-12-12 10:01 CHANGELOG.txt
drwxrwx---  2 maj maj 4.0K 2011-12-12 10:01 installer
-rwxrwx---  1 maj maj  577 2011-12-12 10:01 LICENSE.txt
-rwxrwx---  1 maj maj  477 2011-12-12 10:01 manifest
drwxrwx--- 13 maj maj 4.0K 2011-12-12 10:01 modules
drwxrwx---  8 maj maj 4.0K 2011-12-12 10:01 Resources
drwxrwx---  3 maj maj 4.0K 2011-12-12 10:01 runtime
-rwxrwx---  1 maj maj  901 2011-12-12 10:01 tiapp.xml
-rwxrwx---  1 maj maj 1.2K 2011-12-12 10:01 timanifest
-rwxrwx---  1 maj maj 176K 2011-12-12 10:01 Wunderlist

And I still got this:


maj@Emeth:~$ /opt/W*/Wunderlist

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 4

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 1

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 0

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 5

(installer:6210): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(installer:6210): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Segmentation fault

:(

---

### Post by collisionystm on 2011-12-13
> **Majal said:**
> Dear collisionystm,

Here's the output:

maj@Emeth:~$ sudo ls -lh /opt/W*
[sudo] password for maj: 
total 212K
-rwxrwx---  1 maj root   95 2011-12-12 10:01 CHANGELOG.txt
drwxrwx---  2 maj root 4.0K 2011-12-12 10:01 installer
-rwxrwx---  1 maj root  577 2011-12-12 10:01 LICENSE.txt
-rwxrwx---  1 maj root  477 2011-12-12 10:01 manifest
drwxrwx--- 13 maj root 4.0K 2011-12-12 10:01 modules
drwxrwx---  8 maj root 4.0K 2011-12-12 10:01 Resources
drwxrwx---  3 maj root 4.0K 2011-12-12 10:01 runtime
-rwxrwx---  1 maj root  901 2011-12-12 10:01 tiapp.xml
-rwxrwx---  1 maj root 1.2K 2011-12-12 10:01 timanifest
-rwxrwx---  1 maj root 176K 2011-12-12 10:01 Wunderlist

Realizing that, I did this:

maj@Emeth:~$ sudo chown -R maj:maj /opt/W*
maj@Emeth:~$ sudo ls -lh /opt/W*
total 212K
-rwxrwx---  1 maj maj   95 2011-12-12 10:01 CHANGELOG.txt
drwxrwx---  2 maj maj 4.0K 2011-12-12 10:01 installer
-rwxrwx---  1 maj maj  577 2011-12-12 10:01 LICENSE.txt
-rwxrwx---  1 maj maj  477 2011-12-12 10:01 manifest
drwxrwx--- 13 maj maj 4.0K 2011-12-12 10:01 modules
drwxrwx---  8 maj maj 4.0K 2011-12-12 10:01 Resources
drwxrwx---  3 maj maj 4.0K 2011-12-12 10:01 runtime
-rwxrwx---  1 maj maj  901 2011-12-12 10:01 tiapp.xml
-rwxrwx---  1 maj maj 1.2K 2011-12-12 10:01 timanifest
-rwxrwx---  1 maj maj 176K 2011-12-12 10:01 Wunderlist

And I still got this:


maj@Emeth:~$ /opt/W*/Wunderlist

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 4

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 1

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 0

(process:6210): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 5

(installer:6210): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(installer:6210): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Segmentation fault

:(

try

sudo apt-get install libglib2.0-0

---

### Post by Majal on 2011-12-14
maj@Emeth:~$ sudo apt-fast install libglib2.0-0
[sudo] password for maj: 
Working...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.

Thanks for your reply, but are there any other solution(s)?

---

### Post by cousteau on 2011-12-18
Hi there.

Thanks for sharing. Unfortunately it doesn't work on my machine. Here's the error message:

./Wunderlist: error while loading shared libraries: libffi.so.5: cannot open shared object file: No such file or directory

Any idea? Thanks again.

---

### Post by zygmurti on 2011-12-20
Same here. Is there a fix for this?

---

### Post by collisionystm on 2011-12-20
Code:
sudo apt-get install libffi6
Code:
sudo cp /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0 /usr/lib/libffi.so.5

---

### Post by whyDerrick on 2012-01-11
Collisionystm,

Thanks for a great guide to getting Wunderlist running. I'm pretty new to this, but I was able to get the application running. Unfortunately, I haven't been able to get the icon to appear properly in my pixmaps folder. After I enter the gksudo command to open gedit, I get the following list of error messages. 
[CODE] 
(gksudo:4972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:4974): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KHUF7V': No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8GSG7V': No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory [CODE]

I don't know what it all means or how to fix it. Is there any chance these directories can't be found because I'm running Ubuntu from a WUBI install and if so, how do I fix it? Any (further) help would be greatly appreciated, though this wholly a cosmetic issue.

---

### Post by collisionystm on 2012-01-11
> **whyDerrick said:**
> Collisionystm,

Thanks for a great guide to getting Wunderlist running. I'm pretty new to this, but I was able to get the application running. Unfortunately, I haven't been able to get the icon to appear properly in my pixmaps folder. After I enter the gksudo command to open gedit, I get the following list of error messages. 
[CODE] 
(gksudo:4972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:4974): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KHUF7V': No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8GSG7V': No such file or directory

(gedit:4974): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory [CODE]

I don't know what it all means or how to fix it. Is there any chance these directories can't be found because I'm running Ubuntu from a WUBI install and if so, how do I fix it? Any (further) help would be greatly appreciated, though this wholly a cosmetic issue.


Here is my guess.
When you sudo a command on an installed Ubuntu, you are running with root privileges but still under your user directory. So when you do something like gksudo gedit you are actually running out of the /home/username/.local/share ... etc.

However, on the live cd, it is hacked so there is no sudo passwd, and I am not sure how everythiing is run on there, but you probably need to create the folders its missing manually.

OR, if its a persistent live session, make your own user account instead of ubuntu. Put a password on it. It should function like normal.

but... try this and run gksudo again.

open terminal

sudo bash

cd /root      <<<< i would assume /root exists. If not, create it. mkdir /root

mkdir .local

cd .local

mkdir share

---

### Post by whyDerrick on 2012-01-12
Thanks for your help. Creating the new directories in the root got rid of most of the error messages. I just don't quite understand how to fix problems yet, so I didn't think to make the missing directories. Even after I created the directories though, the gksudo command still didn't work. I ended up copying the file out of the wunderlist/resources path and essentially using the command line to move the copy into the pixmaps directory. And that worked, so I'm all good now! 

Oh! This is slightly offtopic, but WUBI isn't a liveCD, at least not if I understand it correctly. Rather, it's a virtual disk that runs Ubuntu from within a Windows drive to make it such that green users like myself don't need to partition their hard drives to give Ubuntu a more substantial test run than a liveCD (or run it indefinitely that way).

Thanks for your help.

---

### Post by ricsi-pontaz on 2012-01-16
I tried it on Ubuntu 12.04 64 bit, but no luck. Error message:

ricsipontaz@ricsipontaz-desktop:/opt/Wunderlist$ ./Wunderlist 
[18:00:51:372] [Titanium.Host] [Information] Loaded module = tiapp
[18:00:51:373] [Titanium.Host] [Information] Loaded module = tifilesystem
[18:00:51:373] [Titanium.Host] [Information] Loaded module = tiplatform
[18:00:51:375] [Titanium.Host] [Information] Loaded module = tiui
[18:00:51:376] [Titanium.Host] [Information] Loaded module = ticodec
[18:00:51:377] [Titanium.Host] [Information] Loaded module = tidatabase
./Wunderlist: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0: undefined symbol: g_mutex_lock
ricsipontaz@ricsipontaz-desktop:/opt/Wunderlist$

---

### Post by Wallynm on 2012-01-20
Awesome!!! Worked perfectly!!!
Thank you!!!

---

### Post by pediatracancun on 2012-01-24
Ubuntu 11.10 64 bits with Unity.

I followed all the steps, but the program only shows the first screen where it informs the type of license; click on Run and the program clsoses.
I executed in terminal ./Wunderlist and got the following message:

(process:3939): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (32) on option of type 4 (also 0.1.4 and 5)

(installer:3939): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

Any suggestions?

---

### Post by CaptSaltyJack on 2012-02-14
Holy cow. I'll just say what others are thinking I'm sure: this is ridiculous. Wunderkinder needs to invest some time/$ into a proper Linux developer who knows how to put together a proper .deb package or something. This install process is absurd.

---

### Post by frogger78 on 2012-02-22
I get:

```
./Wunderlist: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0: undefined symbol: g_bytes_unref

```

Any ideas on what's causing that?  Is this a glib conflict?

---

### Post by collisionystm on 2012-02-28
Everyone should take a look at this.

[http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html](http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html)

This is a much better way of doing it.

---

### Post by abadr on 2012-05-01
Thanks for the howto...

---

### Post by Bucic on 2012-06-07
> **collisionystm said:**
> Everyone should take a look at this.

[http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html](http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html)

This is a much better way of doing it.
I followed it on my 12.04 x64 to no avail. it simply won't start. I get the welcome window (Wunderlist Installer) with Cancel and Run buttons. I press Run and it won't start. It's visible in Dash (program icon). Launching either from dash or by terminal command wunderlist or even by cd /opt/Wunderlist-1.2.4 and then Wunderlist returns 'Wunderlist: command not found' error.

---

### Post by lifelike27 on 2012-09-15
> **Bucic said:**
> I followed it on my 12.04 x64 to no avail. it simply won't start. I get the welcome window (Wunderlist Installer) with Cancel and Run buttons. I press Run and it won't start. It's visible in Dash (program icon). Launching either from dash or by terminal command wunderlist or even by cd /opt/Wunderlist-1.2.4 and then Wunderlist returns 'Wunderlist: command not found' error.

If you run it as root it should work.

---

### Post by agualdino on 2012-10-30
Hi,

I'm stuck with this error too. 
Anyone knows how to fix this issue?

> **frogger78 said:**
> I get:

```
./Wunderlist: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0: undefined symbol: g_bytes_unref

```

Any ideas on what's causing that?  Is this a glib conflict?

---

### Post by dklovedoctor on 2013-07-01
> **agualdino said:**
> Hi,

I'm stuck with this error too. 
Anyone knows how to fix this issue?

this did the trick for me
I updated libglib

---

