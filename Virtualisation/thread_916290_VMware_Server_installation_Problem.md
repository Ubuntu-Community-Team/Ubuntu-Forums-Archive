---
title: "VMware Server installation Problem"
date: 2008-09-10
forum: Virtualisation
---

### Post by Brian vs Shark on 2008-09-10
I've been following instructions here:

[https://help.ubuntu.com/community/VMware/Server#Installation%20and%20Quick%20Start](https://help.ubuntu.com/community/VMware/Server#Installation%20and%20Quick%20Start)


When I get to number 4. unzip and run vmware-install.pl  and click the Run button, nothing happens.  Even when I click the Run in terminal button, a terminal session pops up not even for a second and disappears.  

Can anyone assist with this issue?


Thanks, 

Brian

---

### Post by veloce on 2008-09-10
Best to run it in a terminal.  It's probably because it's not running as root but you don't see the error message.

Open a terminal, cd to the directory where vmware-config.pl has been unzipped to, then enter:

sudo ./vmware-config.pl


BTW: The instructions in the sticky part of this forum are better than those you are using. [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by Brian vs Shark on 2008-09-10
Im not sure how to cd to a directory. Im very new to linux.

---

### Post by veloce on 2008-09-11
That could be a problem.  While most simple things can be done using a gui, you will run into things that need you to be able to use the command line.

Open gnome terminal and try out a few commands.

ls lists the files in the current directory
cd [dir] changes the directory to the named directory

There are two "special" directory names that are useful:
. the current directory
.. the directory one level up.

Have a play, then have a go at the instructions I referenced in my last post.

---

### Post by Brian vs Shark on 2008-09-12
First off Thank you for the help above. Much appreciated.


OK. I finally got the VMware Server to install through terminal.  I got to the part where it asked for the serial number, I put that in and then Step. 5> [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) I copied the code and it said, 
The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

brian@brian-laptop:~/src/vmware-server-distrib$ sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
cp: cannot create regular file `/usr/lib/vmware/lib/libgcc_s.so.1': No such file or directory

Also, when I click o the icon from the drop down Application drop down menu, I get an ERROR message - Could not Launch... Failed to execute child process "vmware" (No such file or directory)



Im so close.. any suggestions?

---

### Post by Brian vs Shark on 2008-09-13
...

---

### Post by Brian vs Shark on 2008-09-14
bump

---

### Post by veloce on 2008-09-14
You are getting close.  That error is strange.  The code:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1

```

Is just trying to copy a link from one directory to another.  In a terminal, try:

```
cd /usr/lib/vmware/lib

```

If that works then the directory you are copying to exists. Then try:

```
ls

```
If the copy worked then the file libgcc_s.so.1 will be in the list.

If not, try:

```
cd /lib
ls libgcc*
```

Should show the file libgcc_s.so.1 if not, is there another file with a similar name?

---

### Post by Brian vs Shark on 2008-09-15
I tried this: cd /usr/lib/vmware/lib

it came back with no such file or directory;

then i cd /lib;  
ls

and it had the file libgcc_s.so.1


I then typed locate myfile libgcc_s.so.1 to get the full path, but since ive deleted and downloaded so many times, this is wha comes up and i hve no clue which is the right one.  

brian@brian-laptop:~$ locate myfile libgcc_s.so.1
/home/brian/.local/share/Trash/files/vmware-server-distrib/lib/lib/libgcc_s.so.1
/home/brian/.local/share/Trash/files/vmware-server-distrib/lib/lib/libgcc_s.so.1/libgcc_s.so.1
/home/brian/.local/share/Trash/files/vmware-server-distrib.2/lib/lib/libgcc_s.so.1
/home/brian/.local/share/Trash/files/vmware-server-distrib.2/lib/lib/libgcc_s.so.1/libgcc_s.so.1
/home/brian/src/vmware-server-distrib/lib/lib/libgcc_s.so.1
/home/brian/src/vmware-server-distrib/lib/lib/libgcc_s.so.1/libgcc_s.so.1
/lib/libgcc_s.so.1
/lib/vmware/lib/libgcc_s.so.1
/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
brian@brian-laptop:~$ 

should I give up on this?

---

### Post by veloce on 2008-09-15
Giving up is always an option but it's not very satisfying!

What seems to have happened is that your vmware installation has installed the file into:

/lib/vmware/lib/

instead of:

/usr/lib/vmware/lib/

Did you alter any of the installation directories when running the installer? If so, try uninstalling and reinstalling using the defaults.

Otherwise you could create the directory and copy the files there.

```
cd /usr/lib
sudo mkdir vmware
cd vmware
sudo mkdir lib
cd lib
sudo cp /lib/vmware/lib/* .
```

Problem is that there are likely to be other issues related to this.

---

