---
title: "problem with installing Celtx"
date: 2012-10-26
forum: Ubuntu Studio
---

### Post by koya30 on 2012-10-26
Hi guys,

I'm quite new to Ubuntu but I love its speed in comparison to windows...
I'm trying to install Celtx program.
I downloaded it, unpacked onto desktop and followed the instructions from thread [http://ubuntuforums.org/showthread.php?t=1639175](http://ubuntuforums.org/showthread.php?t=1639175)

when I double-click on Celtx icon, I can see that something is trying to mount as an app but it stops...it's unable to mount itself (I presume that's what's supposed to happen?)
I also can't seem to be able to create the launcher...

HELP ](*,)

---

### Post by CrocoDuck on 2012-10-26
Hi. Open a Terminal and go in the directory where you unpacked celtx, then type ./celtx and repost the output of the terminal.

---

### Post by koya30 on 2012-10-26
> **CrocoDuck said:**
> Hi. Open a Terminal and go in the directory where you unpacked celtx, then type ./celtx and repost the output of the terminal.

It tells me it IS a directory... what am I supposed to repost please? :-)

---

### Post by CrocoDuck on 2012-10-26
So sorry... I'm not a native speaker... In the unpacked directory we should see an executable file called celtx (this is what I read in the page that you linked). To execute celtx we are supposed to double click on it. But to know what happens when we launch the program we have to run the executable from terminal and not by double clicking on it. To run a exectubla file called "name" we have to type in the terminal, once we have get in the directory where it is stored,

```
./name
```So: go in the unpacked directory and type "./ "followed by the name of the executable file. Repost the output of this action (I hope I was clear this time:oops:).

---

### Post by koya30 on 2012-10-28
> **CrocoDuck said:**
> So sorry... I'm not a native speaker... In the unpacked directory we should see an executable file called celtx (this is what I read in the page that you linked). To execute celtx we are supposed to double click on it. But to know what happens when we launch the program we have to run the executable from terminal and not by double clicking on it. To run a exectubla file called "name" we have to type in the terminal, once we have get in the directory where it is stored,

```
./name
```So: go in the unpacked directory and type "./ "followed by the name of the executable file. Repost the output of this action (I hope I was clear this time:oops:).

I'm not a native speaker myself so not to worry ;-)

I'm afraid I'm still not very clear how to install this damned thing...

this is what I get in the terminal

user@user-OptiPlex-GX620:~$ /home/user/Desktop/celtx
bash: /home/user/Desktop/celtx: Is a directory
user@user-OptiPlex-GX620:~$ ./celtx
bash: ./celtx: Is a directory
user@user-OptiPlex-GX620:~$ /home/user/Desktop/celtx
bash: /home/user/Desktop/celtx: Is a directory
user@user-OptiPlex-GX620:~$ /home/user/Desktop/celtx: Is a directory
bash: /home/user/Desktop/celtx:: No such file or directory
user@user-OptiPlex-GX620:~$ /home/user/Desktop/celtx/celtx
bash: /home/user/Desktop/celtx/celtx: Permission denied
user@user-OptiPlex-GX620:~$ /home/user/Desktop/celtx/.celtx
bash: /home/user/Desktop/celtx/.celtx: No such file or directory
user@user-OptiPlex-GX620:~$ 

so...not sure what am I to do next...
it tells me 'Permission denied' or no such directory...

I'm lost :confused:

---

### Post by CrocoDuck on 2012-10-28
Uhm... I suspect you do not know how to get into directories using the terminal... Is very easy (probably is harder to say how to do it than actually do it...). We have to use the command "cd" to go where we want in the filesytem. You said that you unpacked the celtx archive onto desktop. So:

```
cd Desktop/
```

in a terminal will put us into the desktop folder. You will notice the change of directory by the change of the string of the prompt. You can also type

```
ls
```

to view the directory content.

Then, assuming that the unpacked celtx folder is called celtx (as I guess watching your reposts):

```
cd celtx/
```

to enter the directory. Remeber that everything in linux is case sensitive, so typing Celtx is different from typing celtx. As above the command ls will give to you the directory content. The executable files should be green coloured. If the executable is called celtx then we have to run

```
./celtx
```

and the terminal will give to us information about the program launching.

As I'm not so good at explain myself, I'll do an example:

```

user@computer:~$ cd Desktop
user@computer:~/Desktop$ ls
AnalogHarmonizer.ZIP  **[COLOR=Navy]Folder[/COLOR]**            SuperOctaver.ZIP
EH-Guitar-Synth.ZIP   Guitar Synth.pdf

```

You see: there is a directory called Folder, then:

```

user@computer:~/Desktop$ cd Folder/
user@computer:~/Desktop/Folder$ ls
**[COLOR=SeaGreen]Script.h[/COLOR]**
user@computer:~/Desktop/Folder$ ./Script.h 

```

If you need help type man followed by the command name, for example:

```
man ls
```

---

### Post by koya30 on 2012-10-30
Thank you for understanding my lack of ubuntu knowledge :P
So, I typed everything according to your notes and unfortunately, it still tells me 'permission denied'... 
perhaps I'm not the system dmin? but when I go to users, it tells me I AM the system administrator...confusing as hell :(

user@user-OptiPlex-GX620:~$ cd Desktop/
user@user-OptiPlex-GX620:~/Desktop$ ls
[COLOR="Navy"]celtx[/COLOR]  libflashplayer.so  readme.txt  [COLOR="navy"]usr[/COLOR]  xfce4-session-logout.desktop
user@user-OptiPlex-GX620:~/Desktop$ cd celtx/
user@user-OptiPlex-GX620:~/Desktop/celtx$ ./celtx
bash: ./celtx: Permission denied
user@user-OptiPlex-GX620:~/Desktop/celtx$ 




> **CrocoDuck said:**
> Uhm... I suspect you do not know how to get into directories using the terminal... Is very easy (probably is harder to say how to do it than actually do it...). We have to use the command "cd" to go where we want in the filesytem. You said that you unpacked the celtx archive onto desktop. So:

```
cd Desktop/
```

in a terminal will put us into the desktop folder. You will notice the change of directory by the change of the string of the prompt. You can also type

```
ls
```

to view the directory content.

Then, assuming that the unpacked celtx folder is called celtx (as I guess watching your reposts):

```
cd celtx/
```

to enter the directory. Remeber that everything in linux is case sensitive, so typing Celtx is different from typing celtx. As above the command ls will give to you the directory content. The executable files should be green coloured. If the executable is called celtx then we have to run

```
./celtx
```

and the terminal will give to us information about the program launching.

As I'm not so good at explain myself, I'll do an example:

```

user@computer:~$ cd Desktop
user@computer:~/Desktop$ ls
AnalogHarmonizer.ZIP  **[COLOR=Navy]Folder[/COLOR]**            SuperOctaver.ZIP
EH-Guitar-Synth.ZIP   Guitar Synth.pdf

```

You see: there is a directory called Folder, then:

```

user@computer:~/Desktop$ cd Folder/
user@computer:~/Desktop/Folder$ ls
**[COLOR=SeaGreen]Script.h[/COLOR]**
user@computer:~/Desktop/Folder$ ./Script.h 

```

If you need help type man followed by the command name, for example:

```
man ls
```

---

### Post by koya30 on 2012-10-30
I also looked this up:
[http://ubuntuforums.org/showthread.php?t=2077625&highlight=permission+denied](http://ubuntuforums.org/showthread.php?t=2077625&highlight=permission+denied)

and tried to change permissions just in case...

that's what I came up with:

user@user-OptiPlex-GX620:~$ cd Desktop/
user@user-OptiPlex-GX620:~/Desktop$ ls
celtx  libflashplayer.so  readme.txt  usr  xfce4-session-logout.desktop
user@user-OptiPlex-GX620:~/Desktop$ cd celtx/
user@user-OptiPlex-GX620:~/Desktop/celtx$ ./celtx
bash: ./celtx: Permission denied
user@user-OptiPlex-GX620:~/Desktop/celtx$ 
user@user-OptiPlex-GX620:~/Desktop/celtx$ sudo chown -R user:user celtx
[sudo] password for user: 
user@user-OptiPlex-GX620:~/Desktop/celtx$ ./celtx
bash: ./celtx: Permission denied
user@user-OptiPlex-GX620:~/Desktop/celtx$ 

permission is still denied... ;-(

---

### Post by CrocoDuck on 2012-10-30
Uhm... Interesting. Please, repost the output of this:

```
ls -l Desktop/celtx/
```

---

### Post by koya30 on 2012-10-30
> **CrocoDuck said:**
> Uhm... Interesting. Please, repost the output of this:

```
ls -l Desktop/celtx/
```

Hi,

this is what I got:

user@user-OptiPlex-GX620:~$ ls -l Desktop/celtx/
total 19708
-rw------- 1 user user     1952 Mar 30  2012 application.ini
-rw------- 1 user user     3893 Mar 30  2012 celtx
-rwxrwx--x 1 user user 15034648 Mar 30  2012 [COLOR="Olive"]celtx-bin[/COLOR]
drwx------ 3 user user     4096 Oct 26 16:43 [COLOR="Blue"]chrome[/COLOR]
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]components[/COLOR]
drwx------ 5 user user     4096 Oct 26 16:43 [COLOR="blue"]defaults[/COLOR]
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]dictionaries[/COLOR]
drwx------ 6 user user     4096 Oct 26 16:43 [COLOR="blue"]extensions[/COLOR]
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]greprefs[/COLOR]
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]icons[/COLOR]
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]js[/COLOR]
-rw------- 1 user user      478 Mar 30  2012 libfreebl3.chk
-rw------- 1 user user   272060 Mar 30  2012 libfreebl3.so
-rw------- 1 user user    67084 Mar 30  2012 libjemalloc.so
-rw------- 1 user user  1188420 Mar 30  2012 libmozjs.so
-rw------- 1 user user   221752 Mar 30  2012 libnspr4.so
-rw------- 1 user user   956024 Mar 30  2012 libnss3.so
-rw------- 1 user user   303664 Mar 30  2012 libnssckbi.so
-rw------- 1 user user   120676 Mar 30  2012 libnssdbm3.so
-rw------- 1 user user    79652 Mar 30  2012 libnssutil3.so
-rw------- 1 user user    13880 Mar 30  2012 libplc4.so
-rw------- 1 user user     9748 Mar 30  2012 libplds4.so
-rw------- 1 user user   121740 Mar 30  2012 libsmime3.so
-rw------- 1 user user      478 Mar 30  2012 libsoftokn3.chk
-rw------- 1 user user   178612 Mar 30  2012 libsoftokn3.so
-rw------- 1 user user   502052 Mar 30  2012 libsqlite3.so
-rw------- 1 user user   158680 Mar 30  2012 libssl3.so
-rw------- 1 user user   787736 Mar 30  2012 libxpcom_core.so
-rw------- 1 user user    13760 Mar 30  2012 libxpcom.so
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]modules[/COLOR]
-rwxrwx--x 1 user user    13972 Mar 30  2012 [COLOR="Green"]mozilla-xremote-client[/COLOR]
-rw------- 1 user user       45 Mar 30  2012 platform.ini
drwx------ 2 user user     4096 Oct 26 16:43 [COLOR="blue"]plugins[/COLOR]
-rw------- 1 user user    15689 Mar 30  2012 removed-files
drwx------ 6 user user     4096 Oct 26 16:43 [COLOR="blue"]res[/COLOR]
-rw------- 1 user user    11410 Mar 30  2012 run-mozilla.sh
user@user-OptiPlex-GX620:~$

---

### Post by CrocoDuck on 2012-10-31
So, as you know the issue is on permissions. On unix-like os, as linux is, files can be configured in order to let just to some chosen users the ability to perform just a core of chosen actions on them. There is an user, called the superuser, that can do everything he wants. If you didn't configured the superuser your user can get superuser's privileges for a task by typing sudo before the command for that task (remember that a user with **superuser** privileges** can really do everything, even if he is ruining the system**; so be **very careful** when you obtain this privileges). We can probe what users can do with files using ls -l. Here we see:

```
-rw------- 1 user user     3893 Mar 30  2012 celtx
```it means that the user called user owns the regular file called celtx. Also we see that the user called user has the right of read and write that file, but not to execute it. We also see that other users (if any) doesn't have rights on this file.

I downloaded celtx too, in order to understand how things should be. Here my permissions:

```

total 26972
-rw-r--r-- 1 user user     1952 2012-03-30 19:12 application.ini
-rwxr-xr-x 1 user user     3893 2012-03-30 19:12 celtx
-rwxr-xr-x 1 user user 21218448 2012-03-30 19:12 celtx-bin
drwxr-xr-x 3 user user     4096 2012-03-30 19:12 chrome
drwxr-xr-x 2 user user    4096 2012-03-30 19:12 components
drwxr-xr-x 5 user user     4096 2012-03-30 19:12 defaults
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 dictionaries
drwxr-xr-x 6 user user     4096 2012-03-30 19:12 extensions
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 greprefs
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 icons
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 js
-rw-r--r-- 1 user user      478 2012-03-30 19:12 libfreebl3.chk
-rwxr-xr-x 1 user user   383584 2012-03-30 19:12 libfreebl3.so
-rwxr-xr-x 1 user user    84360 2012-03-30 19:12 libjemalloc.so
-rwxr-xr-x 1 user user  1231616 2012-03-30 19:12 libmozjs.so
-rwxr-xr-x 1 user user   286432 2012-03-30 19:12 libnspr4.so
-rwxr-xr-x 1 user user  1173256 2012-03-30 19:12 libnss3.so
-rwxr-xr-x 1 user user   434688 2012-03-30 19:12 libnssckbi.so
-rwxr-xr-x 1 user user   142288 2012-03-30 19:12 libnssdbm3.so
-rwxr-xr-x 1 user user   109392 2012-03-30 19:12 libnssutil3.so
-rwxr-xr-x 1 user user    18824 2012-03-30 19:12 libplc4.so
-rwxr-xr-x 1 user user    14656 2012-03-30 19:12 libplds4.so
-rwxr-xr-x 1 user user   156552 2012-03-30 19:12 libsmime3.so
-rw-r--r-- 1 user user      478 2012-03-30 19:12 libsoftokn3.chk
-rwxr-xr-x 1 user user   213072 2012-03-30 19:12 libsoftokn3.so
-rwxr-xr-x 1 user user   609856 2012-03-30 19:12 libsqlite3.so
-rwxr-xr-x 1 user user   184864 2012-03-30 19:12 libssl3.so
-rwxr-xr-x 1 user user  1189664 2012-03-30 19:12 libxpcom_core.so
-rwxr-xr-x 1 user user    18752 2012-03-30 19:12 libxpcom.so
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 modules
-rwxr-xr-x 1 user user    18984 2012-03-30 19:12 mozilla-xremote-client
-rw-r--r-- 1 user user       45 2012-03-30 19:12 platform.ini
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 plugins
-rwxr-xr-x 1 user user    15689 2012-03-30 19:01 removed-files
drwxr-xr-x 6 user user     4096 2012-03-30 19:12 res
-rwxr-xr-x 1 user user    11410 2012-03-30 19:12 run-mozilla.sh


```In my system celtx works like a charm, but you can see that the permissions on files are different for a lot of files. I suggest you to unpack again the Celtx archive and have a look with permissions with ls -l. If the result is the same then you have to modify the permissions of every file by hand until they looks like mine in order to run properly the program. You can do it by by right clicking on a file and going to properties, but I suggest you to carefully read this page first:

[http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

Trust on me: knowing a little of shell can let you to save a lot of time (or the university project of your friends;)) using just some command insted of gazilions of clicks. As linux is multiuser, learning how to manage permissions is not a waste of time. Here an example that shows how to setup permissions like mine for the celtx file:
```
chmod 755 celtx

```

---

### Post by evilsoup on 2012-11-01
This is so bizarre, celtx works perfectly on my machine, and I don't see why the permissions would be messed up like that...

How did you unpack the .tar.bz2 archive? You didn't use sudo of gksudo or something, did you? That can mess up permissions on some things - those are commands to run a program as root - but if you don't know then you probably didn't.

The easiest way to properly extract an archive is to right-click on the .tar and select 'extract here'. You can then move the celtx directory wherever you want

Also, most of the things listed there are libraries, they probably don't need to be executed, so before you spend ten minutes changing all the permissions by hand, you could try just setting the file 'celtx' to be executable (right-click --> Properties --> Permissions tab --> check the 'allow executing file as program' box).

As for creating a launcher... yeah, that thread you linked to is nearly two years old, and unfortunately things have changed significantly since then. Now, you need to create a .desktop file. Copy this:

```
[Desktop Entry]
Type=Application
Name=Celtx
Exec=/path/to/celtx
Comment=Write movie and television scripts
Categories=Applications
StartupNotify=true
Icon=/path/to/celtx/icon.png
```

into a text editor. You'll need to change '/path/to/celtx' with the absolute path to your celtx executable (I think /home/user/celtx/celtx in your case), and you'll need to do the same for the '/path/to/celtx/icon.png'. The Directory called 'icons' in the celtx directory has a few good ones, I use 'default48.png'.

Then, save it in ~/.local/share/applications as 'celtx.desktop', and if you logout & in again, celtx should show up in your dash & you can add it to the launcher. Of course, you should only do that once you've got it working in the first place.

---

### Post by koya30 on 2012-11-01
Hi Evilsoup,

thanks for the tips. When I wanted to save the file as celtx.desktop I got a message that I couldn't save it because I have no permission to do that... so IT MUST BE my permissions that cause all the hassle... ](*,)


> **evilsoup said:**
> This is so bizarre, celtx works perfectly on my machine, and I don't see why the permissions would be messed up like that...

How did you unpack the .tar.bz2 archive? You didn't use sudo of gksudo or something, did you? That can mess up permissions on some things - those are commands to run a program as root - but if you don't know then you probably didn't.

The easiest way to properly extract an archive is to right-click on the .tar and select 'extract here'. You can then move the celtx directory wherever you want

Also, most of the things listed there are libraries, they probably don't need to be executed, so before you spend ten minutes changing all the permissions by hand, you could try just setting the file 'celtx' to be executable (right-click --> Properties --> Permissions tab --> check the 'allow executing file as program' box).

As for creating a launcher... yeah, that thread you linked to is nearly two years old, and unfortunately things have changed significantly since then. Now, you need to create a .desktop file. Copy this:

```
[Desktop Entry]
Type=Application
Name=Celtx
Exec=/path/to/celtx
Comment=Write movie and television scripts
Categories=Applications
StartupNotify=true
Icon=/path/to/celtx/icon.png
```

into a text editor. You'll need to change '/path/to/celtx' with the absolute path to your celtx executable (I think /home/user/celtx/celtx in your case), and you'll need to do the same for the '/path/to/celtx/icon.png'. The Directory called 'icons' in the celtx directory has a few good ones, I use 'default48.png'.

Then, save it in ~/.local/share/applications as 'celtx.desktop', and if you logout & in again, celtx should show up in your dash & you can add it to the launcher. Of course, you should only do that once you've got it working in the first place.

---

### Post by koya30 on 2012-11-01
Hey,

thanks a lot for the link! It made me understand much more of what you can actually do and how in Linux...
Unfortunately, when I typed su command into terminal, I get this message:

user@user-OptiPlex-GX620:~$ su
Password: 
su: Authentication failure
user@user-OptiPlex-GX620:~$ 

I'm sure I typed in the correct password... oh dear... this thing is getting progressively more and more of a pain in the hole... 

:(

> **CrocoDuck said:**
> So, as you know the issue is on permissions. On unix-like os, as linux is, files can be configured in order to let just to some chosen users the ability to perform just a core of chosen actions on them. There is an user, called the superuser, that can do everything he wants. If you didn't configured the superuser your user can get superuser's privileges for a task by typing sudo before the command for that task (remember that a user with **superuser** privileges** can really do everything, even if he is ruining the system**; so be **very careful** when you obtain this privileges). We can probe what users can do with files using ls -l. Here we see:

```
-rw------- 1 user user     3893 Mar 30  2012 celtx
```it means that the user called user owns the regular file called celtx. Also we see that the user called user has the right of read and write that file, but not to execute it. We also see that other users (if any) doesn't have rights on this file.

I downloaded celtx too, in order to understand how things should be. Here my permissions:

```

total 26972
-rw-r--r-- 1 user user     1952 2012-03-30 19:12 application.ini
-rwxr-xr-x 1 user user     3893 2012-03-30 19:12 celtx
-rwxr-xr-x 1 user user 21218448 2012-03-30 19:12 celtx-bin
drwxr-xr-x 3 user user     4096 2012-03-30 19:12 chrome
drwxr-xr-x 2 user user    4096 2012-03-30 19:12 components
drwxr-xr-x 5 user user     4096 2012-03-30 19:12 defaults
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 dictionaries
drwxr-xr-x 6 user user     4096 2012-03-30 19:12 extensions
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 greprefs
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 icons
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 js
-rw-r--r-- 1 user user      478 2012-03-30 19:12 libfreebl3.chk
-rwxr-xr-x 1 user user   383584 2012-03-30 19:12 libfreebl3.so
-rwxr-xr-x 1 user user    84360 2012-03-30 19:12 libjemalloc.so
-rwxr-xr-x 1 user user  1231616 2012-03-30 19:12 libmozjs.so
-rwxr-xr-x 1 user user   286432 2012-03-30 19:12 libnspr4.so
-rwxr-xr-x 1 user user  1173256 2012-03-30 19:12 libnss3.so
-rwxr-xr-x 1 user user   434688 2012-03-30 19:12 libnssckbi.so
-rwxr-xr-x 1 user user   142288 2012-03-30 19:12 libnssdbm3.so
-rwxr-xr-x 1 user user   109392 2012-03-30 19:12 libnssutil3.so
-rwxr-xr-x 1 user user    18824 2012-03-30 19:12 libplc4.so
-rwxr-xr-x 1 user user    14656 2012-03-30 19:12 libplds4.so
-rwxr-xr-x 1 user user   156552 2012-03-30 19:12 libsmime3.so
-rw-r--r-- 1 user user      478 2012-03-30 19:12 libsoftokn3.chk
-rwxr-xr-x 1 user user   213072 2012-03-30 19:12 libsoftokn3.so
-rwxr-xr-x 1 user user   609856 2012-03-30 19:12 libsqlite3.so
-rwxr-xr-x 1 user user   184864 2012-03-30 19:12 libssl3.so
-rwxr-xr-x 1 user user  1189664 2012-03-30 19:12 libxpcom_core.so
-rwxr-xr-x 1 user user    18752 2012-03-30 19:12 libxpcom.so
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 modules
-rwxr-xr-x 1 user user    18984 2012-03-30 19:12 mozilla-xremote-client
-rw-r--r-- 1 user user       45 2012-03-30 19:12 platform.ini
drwxr-xr-x 2 user user     4096 2012-03-30 19:12 plugins
-rwxr-xr-x 1 user user    15689 2012-03-30 19:01 removed-files
drwxr-xr-x 6 user user     4096 2012-03-30 19:12 res
-rwxr-xr-x 1 user user    11410 2012-03-30 19:12 run-mozilla.sh


```In my system celtx works like a charm, but you can see that the permissions on files are different for a lot of files. I suggest you to unpack again the Celtx archive and have a look with permissions with ls -l. If the result is the same then you have to modify the permissions of every file by hand until they looks like mine in order to run properly the program. You can do it by by right clicking on a file and going to properties, but I suggest you to carefully read this page first:

[http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

Trust on me: knowing a little of shell can let you to save a lot of time (or the university project of your friends;)) using just some command insted of gazilions of clicks. As linux is multiuser, learning how to manage permissions is not a waste of time. Here an example that shows how to setup permissions like mine for the celtx file:
```
chmod 755 celtx

```

---

### Post by evilsoup on 2012-11-01
> **koya30 said:**
> Hi Evilsoup,

thanks for the tips. When I wanted to save the file as celtx.desktop I got a message that I couldn't save it because I have no permission to do that... so IT MUST BE my permissions that cause all the hassle... ](*,)

Are you sure you are trying to save it to the right place? Open up a filemanager in your home folder and hit ctrl+h - a bunch of folders with dots in front of them should appear (if you put a . in front of any folder or file in linux, it will be hidden). There should be a folder called '.local'; within there should be a folder 'share', and within there a folder called 'applications'. That is where you should be saving that 'celtx.desktop' file.

Of course, all that will be useless until you get the actual celtx program working.

---

### Post by CrocoDuck on 2012-11-01
First of all try to change permissions for the celtx file (the main goal is to execute it), then try to make sure if you can write in the ~/.local/share/applications  directory following the last instructions by evilsoup. I want to ask to  you the output of other two commands, even if I'm quite sure it will be  trivial...

```
groups
``````
whoami
```

---

### Post by evilsoup on 2012-11-01
Ubuntu doesn't use su, it uses sudo. [This]("https://help.ubuntu.com/community/RootSudo") will explain the difference.

But I think that's a red herring so far as your problem is concerned. Don't bother messing around with sudo for this. Definitely **don't** try doing anything with su, until you really know what you're doing (and once you know what you're doing, you probably won't find any time that you need to use su over sudo).

Get into your celtx folder. Based on what you've written so far in this thread,
```
cd ~/celtx
```
 should bring you there. Then use
```
chmod u+x celtx
```
This will allow you to execute the file as a program. Then use
```
./celtx
```

---

