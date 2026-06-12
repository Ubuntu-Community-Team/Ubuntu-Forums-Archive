---
title: "Basic commands - This is my list what can you add?"
date: 2006-10-11
forum: The Cafe
---

### Post by jameswhite1979 on 2006-10-11
Guys,

I am brand new to Linux and Ubuntu this is my second day and I am starting to collect a list of basic commands:

su : Super User rights from within the terminal
sudo : super user run this command
ls : list directory contents
ls -lis : list directory content is list view
cd : change directory
cd /dirname : jump change a directory
apt-get install : gets app from web and installs
apt-get remove : uninstalls app
apt-get update : updates the DB
clear : clears screen
./filename : processes a install command
mkdir : creates a directory
chmod 777 dirname : resets access rights to directory
kill 999 : kills process at high level
reboot : reboots system
exit : exits from terminal or moves back a userlevel
make : comlies package code
make install : installs the compiled code
uname -r : gives you the kernel version

Can you add to this list and have I made any mistakes. Go easy this is all very new for me!

---

### Post by NoTiG on 2006-10-11
you can give someone a fish, or teach them to fish ... :P

so basically i think its pointless to teach all the different options for every command. The main thing is to learn how to figure out commands yourself. A couple of good pointers

man ls            # will give you information about ls

also by pressing tab you can auto complete a command or see all available possibilities ... so if you type gre ... and cant remember that what you need is grep, then just hit tab a couple of times. 

Also the history helps remember commands you have used before.

---

### Post by PatrickMay16 on 2006-10-11
tar -xf

Extracts the contents of most tar.** archives.

apt-cache search ****

Searches the apt database for packages with names or descriptions similar to ****

apt-cache show ****

Shows information on package ****, for example "apt-cache show unzip".

df -h 

Shows mounted filesystems and space usage infomation for them.

du -hs /path/to/directory/

Shows the size of the contents of the specified directory.


Let me know if this helped. I could list some more if you'd like.

---

### Post by yasoumalaka on 2006-10-11
I'll join you on this mission. I was thinking of doing the same thing. Maybe someone could go through all the different sudos. for example sudo sudo -s gksudo su and so on. Thanks to anybody that does it  would be a big help. Hopefully they get posted to the top.

---

### Post by henriquemaia on 2006-10-11
Having an **&** at the end of the command line sends this process to the background (you regain the prompt to type more commands). If you type a command followed by **&& **and then another command (i.e. $command1 && command2) the second command will only be started when the first one is finished

---

### Post by dannyboy79 on 2006-10-11
su : Super User rights from within the terminal
sudo : super user run this command
ls : list directory contents
ls -lis : list directory content is list view
cd : change directory
cd /dirname : jump change a directory
apt-get install : gets app from web and installs [NOTE from dannyboy: I would use aptitude, it keeps track of dependencies and when you uninstall stuff it takes the dependencies with it, apt-get DOESN'T do this!]
apt-get remove : uninstalls app [same here]
apt-get update : updates the DB [same here]
clear : clears screen
./filename : processes a install command
mkdir : creates a directory
chmod 777 dirname : resets access rights to directory [i don't know what you mean by resets access right, chomd will make the dir readable, writable, and executable i thought?]
kill 999 : kills process at high level
reboot : reboots system
exit : exits from terminal or moves back a userlevel
make : comlies package code
make install : installs the compiled code
uname -r : gives you the kernel version
dir : will list all directories within your current location
cat filenamehere : will display it's contents
pwd : will show you your current location (very important if you're usincli ftp)
cp oldfilename newfilename : copies a file
mv oldfile newfile : will overwrite the oldfile with the newfile
chown usernamehere dirnamehere : changes the dir owner to whoever you put
chgrp groupnamehere dirnamehere : changes the group who owns the dir

Thats it from me, you're best off reading a linux command website.

---

### Post by anaconda on 2006-10-11
su   doesn't work in ubuntu!
instead we have to use:
sudo su

and if you have mkdir then you should also have rmdir  to remove a directory..


Thanks for the && -didn't know it And just happen to need it!

---

### Post by John.Michael.Kane on 2006-10-11
This may help
[An A-Z Index of the Linux BASH command line]("http://www.ss64.com/bash/")

[Alphabetical Directory of Linux Commands]("http://www.linuxdevcenter.com/linux/cmd/")

[Linux Shortcuts and Commands:]("http://www.unixguide.net/linux/linuxshortcuts.shtml")

---

### Post by dannyboy79 on 2006-10-11
> **anaconda said:**
> su   doesn't work in ubuntu!
instead we have to use:
sudo su

You really should be more specific. I'll update the statement for you. su doesn't come enabled in Ubuntu by default, you need to set it up yourself. You would type 'sudo passwd' and when it asks you for a password, enter in a root password. now whenever you want to log in as root, you would hit su then the password you chose or you could simply login that way by entering root as the username and the password you chose.

---

### Post by cacharreo on 2006-10-11
[http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)

---

### Post by PatrickMay16 on 2006-10-11
> **anaconda said:**
> su   doesn't work in ubuntu!
instead we have to use:
sudo su

Nah, instead, just do:

sudo -s

---

### Post by yasoumalaka on 2006-10-11
There is many sites with commands. I don'tthink it would hurt to have ubuntu applications for the commands since its a little different. I'd really like to see someone detail the differences in the uses of sudo. ETC gksudo, sudo -s, sudo. Anybody????

---

### Post by UltraMathMan on 2006-10-11
Just a quick note on apt-get.

```
apt-get remove --purge
``` removes a program and purges any configuration files associated with it.

---

### Post by ciscosurfer on 2006-10-11
Allow me to add to this, with this caveat echoed by other users on this thread: learning *how to use* these commands is essential; rote memorization is fine provided you are learning how these commands function for you.  

And now for two additional links >>
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by Epperly on 2006-11-04
> **UltraMathMan said:**
> Just a quick note on apt-get.

```
apt-get remove --purge
``` removes a program and purges any configuration files associated with it.

Is that the same thing as aptitude remove?
One command not listed I like to use sometimes is:
**gksudo nautilus**, add/edit root folders and such

---

### Post by EdThaSlayer on 2006-11-04
Well...pressing "cal" gives you a calendar...

---

### Post by picpak on 2006-11-04
pkill program-name - Kills a command
free -m - shows free space
sudo apt-get clean - Clear apt archives
sudo dpkg -i filename.deb - Install *.deb file
sudo apt-get build-dep program-name - Get dependencies for source packages
cd ~ - go to home folder
cd .. - go to previous folder
tar -cvf file-or-folder - Make tar archive
tar -cvjf file-or-folder - Make tar.bz2 archive
tar -cvzf file-or-folder - Make tar.gz archive
tar -xvf file-or-folder - Untar tar archive
tar -xvjf file-or-folder - Untar tar.bz2 archive
tar -xvzf file-or-folder - Untar tar.gz archive
nano - Text editor
wget [http://internet-address.com](http://internet-address.com) - Download manager
rm -r file-or-folder - Forcefully remove file/folder
ls --color=auto - List directory contents, colour-coded
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade - Get information about broken packages when getting dependency problems

---

### Post by kuja on 2006-11-04
> **anaconda said:**
> su   doesn't work in ubuntu!
instead we have to use:
sudo su

and if you have mkdir then you should also have rmdir  to remove a directory..


Thanks for the && -didn't know it And just happen to need it!
Not true. su works fine in Ubuntu. You can switch to any user, with the exception of locked accounts, such as root.


Anyway, I might as well list a few nice ones

cut - cuts up strings at the specified delimiter, displaying only what you want to have displayed.
sed - complicated, but powerful
`` - enclose a command between these to allow its output to be the input of another command, or similar. 
killall - kill commands by the binaries name rather than by PID
music123 - My best friend when I break my GUI :P

---

### Post by Sef on 2006-11-04
> 
Quote:
Originally Posted by UltraMathMan View Post
Just a quick note on apt-get.

Code:

apt-get remove --purge

removes a program and purges any configuration files associated with it.
Is that the same thing as aptitude remove?

Yes, if you did 'sudo aptitude remove --purge', it would be the same.  The difference between aptitude  and apt-get is that if you install with aptitude when you remove with aptitude, it will remove the dependencies as well.

---

### Post by chaosgeisterchen on 2006-11-04
I would strongly recommend to solely use **aptitude** instead of **apt** for packet managing issues. It has proven superiority to me.

---

### Post by vinaygeorgian on 2009-04-13
> **jameswhite1979 said:**
> Guys,

I am brand new to Linux and Ubuntu this is my second day and I am starting to collect a list of basic commands:

su : Super User rights from within the terminal
sudo : super user run this command
ls : list directory contents
ls -lis : list directory content is list view
cd : change directory
cd /dirname : jump change a directory
apt-get install : gets app from web and installs
apt-get remove : uninstalls app
apt-get update : updates the DB
clear : clears screen
./filename : processes a install command
mkdir : creates a directory
chmod 777 dirname : resets access rights to directory
kill 999 : kills process at high level
reboot : reboots system
exit : exits from terminal or moves back a userlevel
make : comlies package code
make install : installs the compiled code
uname -r : gives you the kernel version

Can you add to this list and have I made any mistakes. Go easy this is all very new for me!

even i am facing the same problem.......help me out.........

---

