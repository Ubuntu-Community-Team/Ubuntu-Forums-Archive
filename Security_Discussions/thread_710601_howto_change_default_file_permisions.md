---
title: "howto change default file permisions"
date: 2008-02-28
forum: Security Discussions
---

### Post by azelter on 2008-02-28
I wondered if anyone could tell me how I change the default file permissions from -rw-r--r-- to -rw-rw-r-- for new files created by all users on my computer. It seems the Ubuntu default is to give user read/write permission, group read-only and all read-only. I would like all new files created by all users on my system to have user and group read/write permissions and leave all as read-only.
chmod will change files already in existence, but I can't run this every single time a new file is created.
Thanks!
Alex

---

### Post by bodhi.zazen on 2008-02-28
set a umask in ~/.bashrc 

[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

### Post by k_grdn on 2008-02-28
Hi,

Change the umask value in /etc/profile or ~/.bashrc for specific.

r=4,w=2,x=1

default 022 = 755 dirs, 644 files

rw-rw-r

umask = 002

Subtract the uumask value from the actual permission value.

Regards,

k_grdn

---

### Post by azelter on 2008-02-28
Thanks for the fast answers. Doesn't umask apply just to programs that use shells? Will this affect files created in other applications (openoffice, gimp, whatever)?

---

### Post by Mr. C. on 2008-02-29
> **azelter said:**
> Thanks for the fast answers. Doesn't umask apply just to programs that use shells? Will this affect files created in other applications (openoffice, gimp, whatever)?

Let's clarify.  When a program creates a new file or directory, it specifies the permissions (the mode) for that new object.  In the case where the programmer doesn't specify specific modes, the default full permission mode is used, which is then subjected to the current processes umask setting.  Every process has a umask value, which affects every file system object created.  The umask does not affect any existing object.

By setting the umask in your shell, *all* processes created from that shell inherit this value.  Each process will use its inherited umask, unless it changes the umask for itself (and its sub-processes).

Shells are just programs, and as such, they are forced into the same rules.

MrC

---

### Post by azelter on 2008-02-29
Thanks for the clarification and everyone for the suggestions. It did indeed work. Somehow, I always thought that programs that are started from the gnome panel (or some other way that bypasses typing the command in a terminal) would not be aware of what was in .profile or .bashrc - hence I wasn't sure that changing the umask in those files would help. After all, if I look at the pstree output of my currently running system - firefox (which I started via my gnome panel) seems to stem directly off init: 
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;{NetworkManager}
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;acpid
     &#9500;&#9472;anacron&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;run-parts&#9472;&#9472;&#9472;slocate&#9472;&#9472;&#9472;updatedb
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;bubblemon-gnome
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dd
     &#9500;&#9472;dhcdbd&#9472;&#9472;&#9472;dhclient
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;run-mozilla.sh&#9472;&#9472;&#9472;firefox-bin&#9472;&#9472;&#9472;10*[{firefox-bin}]
     &#9500;&#9472;gconfd-2

etc, etc. 

So I was wondering when that program would become aware of /etc/profile. I guess in truth gdm must read it at login or something like that. Anyway - it works - so thanks very much.

---

### Post by Mr. C. on 2008-02-29
You are confusing many layers.  If you want some overview of *nix processes, read the Process slides here:

Week 3, "Special Files, Accounts and Processes" at:

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by azelter on 2008-03-05
Well it seems editing umask in /etc/profile and /etc/bashrc helped almost everything except the program I wanted. Files created on the command line have the right permissions. Files created using openoffice and knoqueror file browser have the right permissions. The relevant lines of  /etc/csh.cshrc and /etc/bashrc now look like:
if [ "`id -gn`" = "`id -un`" -a `id -u` -gt 99 ]; then
        umask 002
else
#       umask 022
        umask 002
fi

--------- and ----------

[ "`id -gn`" = "`id -un`" -a `id -u` -gt 99 ]
if $status then
        #umask 022
        umask 002
else
        umask 002
endif


/etc/profile now has the line:
umask 002

at the bottom.

However, the program I want to use to create folders makes them with group read-only permissions. I have no idea how to get this to change.

Mr. C. - without giving a full tutorial of linux processes, at what stage do various programs get to read/inherit from /etc/profile or /etc/bashrc? I guess the program I am trying to use does not do this...any more ideas?

---

### Post by Mr. C. on 2008-03-05
Every process inherits from its parent.  A process may choose to override some inherited object, such as umask.

Shell options, process settings and environment variables can be set immediately on the command line.  Exported environment variables, adn process-related settings will affect all subsequent child processes.

Think of the shell's startup files as simply conveniences - a place to set values for login and/or interactive shells, such that you don't have to reiterate those commands each shell; they are not magical.  So, get things to work via command line, and then you can place your settings in the various dot files.  Other programs *do not read* from the shell's startup files: rather, the shell sets the options when it runs, and exported environment variables and various process-control settings are passed along when the shell fork/exec's your programs.

Why your program creates files and directories with certain permissions is probably explained somewhere its documentation.  Certain programs desire to control permissions with their own settings, so that default permissions and a user's umask do not affect their operation. Consult the documentation for the program (do we know its name... nope, don't see it).  It may also be poor programming.  But rest assured, umask *is* inherited by your program from its parent (like the shell, or its own parent control process).

---

### Post by azelter on 2008-03-06
Mr.C
Thank you very much for the detailed response. That was exactly what I needed. I will contact the makers of the software (which is softworx by appliedprecision - I didn't name it before as it probably won't mean anything to most people). Unfortunately In general they have unbelievably poor software support. My experiences with such companies constantly make me lament the almost entirely closed nature of scientific software applications designed to control hardware (in this case a microscope). If only the companies that control the hardware would be content to profit from that, and their service contracts instead of insisting on building poorly programed closed source software applications to run their hardware and trying to profit from those too.
Anyway, thank you for your help.
Alex

---

### Post by Mr. C. on 2008-03-06
You're welcome.

Something to consider for your support call to the company.

Run the program under **strace**, and look for any **open**, **creat** (yes, without a final 'e'), **umask**, or **chmod**.   Strace is a program that shows you the system calls made by an application.  It provides the arguments passed to the system call, so that you can see exactly what the program is doing re: creating new files.  There may be many **open** calls with read-only modes, so you can ignore those.  You're looking for **open**s in create mode, **creat**, etc. which affect the files in question with the wrong permissions.

You can run it like this:

```
strace yourprogram | tee output.txt
```

which will dump the output both to STDOUT (the terminal) and to the file named output.txt.  Note, if your program is called via some shell script (eg. a "wrapper", you'll have to edit that shell script and add the strace in front of the call to the actual program.

See the man page for **strace**, and the various system calls mentioned above to learn about each system call's arguments.

---

### Post by bsmith1051 on 2008-03-08
I made the changes mentioned in this discussion -- both /etc/profile and my personal .profile files specify 'umask 002' -- but I'm still having a similar problem.  If I take the memory card from my camera and mount it in my USB adapter, then copy (or move) the files to the hard drive, the resulting files are all marked Group = No Access.

Maybe I need to restart for the changes to take effect?

---

### Post by Mr. C. on 2008-03-08
Are you using the GUI to perform the copy ?

Changing the umask in the current shell cannot ever affect the part process.  If you're using the GUI, log out and back in.  No need to restart.

---

### Post by bsmith1051 on 2008-03-08
yes, I'm using the default (Nautilus?) desktop.  I tried logging-off and back in but it didn't help.  I checked the Permissions of the files on the memory card and they're Group=No Access, too.  So maybe the problem here is that the default 'assigned' Permissions for FAT32 files (which I assume is what my memory card uses) is Group=No Access ?  I say 'assigned' because FAT32 has no Group permissions property to begin with so Ubuntu is 'assigning' one.

---

### Post by Mr. C. on 2008-03-08
> **bsmith1051 said:**
> yes, I'm using the default (Nautilus?) desktop.  I tried logging-off and back in but it didn't help.  I checked the Permissions of the files on the memory card and they're Group=No Access, too.  So maybe the problem here is that the default 'assigned' Permissions for FAT32 files (which I assume is what my memory card uses) is Group=No Access ?  I say 'assigned' because FAT32 has no Group permissions property to begin with so Ubuntu is 'assigning' one.

Ah, FAT32 is a different story.  You can't squeeze blood out of a turnip, and you'll not get permissions on a file system that does not support them.

---

### Post by bodhi.zazen on 2008-03-10
Permissions aer set on a FAT or NTFS file system at the time of mounting.

They are set for teh entire file system, not file-by-file.

See : 

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Mr. C. on 2008-03-10
Duplicate thread: see also: [http://ubuntuforums.org/showthread.php?p=4489509#post4489509](http://ubuntuforums.org/showthread.php?p=4489509#post4489509)

---

