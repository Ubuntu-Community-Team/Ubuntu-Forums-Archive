---
title: "I'm Having Trouble Logging On to Linux..."
date: 2005-12-06
forum: The Cafe
---

### Post by Kregel on 2005-12-06
Hello,

I've been using linux for almost a year now, but this is my first experience with the ubuntu forums, however i have heard that it is a very helpful place.

Here is my problem: my linux computer was working just fine.  I restarted it for one reason or another(i don't even remember why) and when it booted back and i tried to log in i got this message:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator."

To be honest i have no idea what to do. Can someone help me PLEASE? i'm starting to go into linux withdrawl because i've had to use our windows computer for a week now.

Any help or suggestions would be greatly appretiated

---

### Post by aysiu on 2005-12-06
Is your /home folder, in fact, full?

---

### Post by Kregel on 2005-12-06
I didn't think so. How would I check that?

---

### Post by erikpiper on 2005-12-06
Is your /home a seperate partition?
If so "df"

---

### Post by Kregel on 2005-12-06
[QUOTE=erikpiper]Is your /home a seperate partition?
If so "df"[/QUOTE]

I'm sorry, but I don't know what that means...while I've been using Linux for almost a year now, I'm still pretty new to all the technical stuff, and to me, what you just said is technical...

---

### Post by erikpiper on 2005-12-06
Type df into a console and paste the contents here

(Can u log in at all? As root even?)

---

### Post by erikpiper on 2005-12-06
PS: You can hit ctrl-alt-f1 (or f2 or up to f6) to go to a virtual terminal, and try logging in there (command line)

---

### Post by Kregel on 2005-12-06
Again I'm sorry for my linux illiteracy, but...

1. i don't really know what it means/how i would "type df into a console"

and 2. i don't think i can log in at all...its just at the ubuntu log in sceen where it asks for my user name and password. i put them in and it gives me the message in my first post. the only option is to click okay, and when i do it just takes me back to the log in screen

---

### Post by Kregel on 2005-12-06
[QUOTE=erikpiper]PS: You can hit ctrl-alt-f1 (or f2 or up to f6) to go to a virtual terminal, and try logging in there (command line)[/QUOTE]

also, becuase i've used nothing but windows my whole life up until now i don't really know how to use the command line a ton...such as loggin in in the command line

---

### Post by aysiu on 2005-12-06
Presumably, you don't have a graphical environment working right now, right? That means you have something that looks like a command-line prompt. Type ```
df -h
``` there. See what pops up...

---

### Post by aysiu on 2005-12-06
[QUOTE=Kregel]also, becuase i've used nothing but windows my whole life up until now i don't really know how to use the command line a ton...such as loggin in in the command line[/QUOTE] Press Control-Alt-F1. What happens?

---

### Post by Kregel on 2005-12-06
[QUOTE=aysiu]Presumably, you don't have a graphical environment working right now, right? That means you have something that looks like a command-line prompt. Type ```
df -h
``` there. See what pops up...[/QUOTE]

well i had a graphical environment, then i pushed *ctrl+alt+f1* and it took me to some kind of command line, the last line reading "andrew login:"

i typed df -h

it then said "password"

i typed in my password

it responed "login incorrect"

---

### Post by aysiu on 2005-12-06
At **login:** you should log in. Type your username.

Then you'll be asked for your password at **password:**

Only after you've logged in should you type ```
df -h
```

The computer assumed your username was df -h. That's why it asked for your password.

This is what I get, so you get an idea of what it looks like ```
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              20G  2.2G   17G  12% /
tmpfs                 221M     0  221M   0% /dev/shm
tmpfs                 221M   13M  209M   6% /lib/modules/2.6.12-10-386/volatile
**/dev/hda5              97G   45G   48G  49% /home**
/dev/hda1              15G  6.0G  8.7G  41% /windows
``` From this, I know that I do, in fact, have a separate /home partition and that it's 97 GB, 45 GB of it used, and 48 GB of it free.

---

### Post by Kregel on 2005-12-06
[QUOTE=aysiu]At **login:** you should log in. Type your username.

Then you'll be asked for your password at **password:**

Only after you've logged in should you type ```
df -h
```

The computer assumed your username was df -h. That's why it asked for your password.

This is what I get, so you get an idea of what it looks like ```
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              20G  2.2G   17G  12% /
tmpfs                 221M     0  221M   0% /dev/shm
tmpfs                 221M   13M  209M   6% /lib/modules/2.6.12-10-386/volatile
**/dev/hda5              97G   45G   48G  49% /home**
/dev/hda1              15G  6.0G  8.7G  41% /windows
``` From this, I know that I do, in fact, have a separate /home partition and that it's 97 GB, 45 GB of it used, and 48 GB of it free.[/QUOTE]

alright so i got that...but i don't have anything that says /home...under the "mounted on" part i have these four:

/
/dev/shm
/.dev
/dev

---

### Post by aysiu on 2005-12-06
Hm. No separate /home partition.
Okay. You have a few options. The first I know how to do. The others are possible in theory, but I don't know how to do them.

1. Get a live CD like Ubuntu's live CD or, better yet, Knoppix. This can mount your current installation, and you can browse around to see how full a folder is (your /home folder in this case).

2. Somehow, via the command-line, enable the root user, and allow it to log in graphically. Then, once logged in, poke around and see how big the /home folder is and how full it is.

Of course, if you don't have a separate /home partition, then it can't be that your /home folder is full... it must be that your entire hard drive is full... or that, as the original warning stated, GDM can't write to your authorization file. I'm wondering if that's the .ICEauthority people kept talking about last week.

Sorry I can't be more help.

---

### Post by Kregel on 2005-12-06
[QUOTE=aysiu]Hm. No separate /home partition.
Okay. You have a few options. The first I know how to do. The others are possible in theory, but I don't know how to do them.

1. Get a live CD like Ubuntu's live CD or, better yet, Knoppix. This can mount your current installation, and you can browse around to see how full a folder is (your /home folder in this case).

2. Somehow, via the command-line, enable the root user, and allow it to log in graphically. Then, once logged in, poke around and see how big the /home folder is and how full it is.

Of course, if you don't have a separate /home partition, then it can't be that your /home folder is full... it must be that your entire hard drive is full... or that, as the original warning stated, GDM can't write to your authorization file. I'm wondering if that's the .ICEauthority people kept talking about last week.

Sorry I can't be more help.[/QUOTE]

okay so i have a live cd, so i just put that in and restart my computer, then when it comes up just delete stuff off my hard drive to open it up some?

---

### Post by aysiu on 2005-12-06
[QUOTE=Kregel]okay so i have a live cd, so i just put that in and restart my computer, then when it comes up just delete stuff off my hard drive to open it up some?[/QUOTE] Is it a live Ubuntu or Knoppix?

---

### Post by Kregel on 2005-12-07
[QUOTE=aysiu]Is it a live Ubuntu or Knoppix?[/QUOTE]

live ubuntu

---

### Post by aysiu on 2005-12-07
Okay. It'll take a few more steps, then.

1. Boot it up.

2. When you get to the live session, open a terminal. 
In Breezy, this is Applications > Accessories > Terminal.
In Hoary, it's Applications > System Tools > Terminal.

3. Once you're in the terminal type ```
sudo fdisk -l
``` and post the output here. We'll work from there on mounting your partition to be read.

---

### Post by Kregel on 2005-12-07
well shoot...i just realized that i've lost my live disk...is there anything i can do without it or not really?

---

### Post by aysiu on 2005-12-07
[QUOTE=Kregel]is there anything i can do without it or not really?[/QUOTE] Yes, but I don't know how (see above about letting root log in).

---

### Post by Kregel on 2005-12-07
alright

well like i said in my first post this is my first time using ubuntu forums, so i'm not really sure what to do at this point...if i do find my live cd would i then just try and conctact you again, or open up a new thread or what?

and by the way, thank you for your help

---

### Post by aysiu on 2005-12-07
[QUOTE=Kregel]if i do find my live cd would i then just try and conctact you again, or open up a new thread or what?[/QUOTE] Just post in this thread and say "I found it!" It's better to keep it to one thread because if, for some reason, I'm not around, someone else can help out and see what the context of the problem is and what you've tried already.

To find the thread again, click on Search (at the top-right) and select "Find All Your Threads."

In the meantime, I'll poke around and see if there's an easy way to enable graphical root login from the terminal.

---

### Post by arphe_el on 2005-12-07
here's my situation the bootloader loads but after sometime the computer floppy disk lit on and i see my hardisk light is on as well but on the screen it's totally black no ubuntu graphical greeter and no terminal either to log-in.

what to do? thank you in advance and hope to hear from you. GODspeed!

---

### Post by Brunellus on 2005-12-07
[QUOTE=Kregel]well shoot...i just realized that i've lost my live disk...is there anything i can do without it or not really?[/QUOTE]
Yes, you can solve your problem.

You are getting the same gnome error as I described in [this thread](http://www.ubuntuforums.org/showthread.php?t=98738").  The solution is probably the same.

PROBLEM:  ~/.ICEauthority cannot be read during GNOME startup.

SOLUTION:

1) Hit CTRL + ALT + F1 to get to a text console.  You will be prompted for your username and password.  

2) Change the owner of ~/.ICEauthority back to your username.  To do this, type

```
sudo chown USERNAME .ICEauthority
```

where USERNAME is replaced by your username.  You will be prompted for your password.

3) Hit CTRL + ALT + F7 to get back to the GDM graphical login screen.  Enter your username and password as prompted to log into GNOME.  Problem (hopefully) solved.

---

### Post by Kregel on 2005-12-07
alright so i pushed *ctrl + alt + F1*, then entered my user name and password. it brought up the prompt or whatever you want to call it like i was in the terminal : USERNAME@USERNAME~:

at this point i typed in the "sudo chown USERNAME .ICEauthority" and pushed enter

the first time i did it it asked for my password, i put it in and pressed enter, then pushed *ctrl + alt + F7*

it took me back to the log in screen, i tried logging in and go the same message as i did originally(i my first post)

i tried one more time, the same thing happened except this time after i typed the "sudo chown USERNAME .ICEauthority" it didn't ask me for my password. instead it just brought up a new line with the "USERNAME@USERNAME~:" prompt. i pushed *ctrl + alt + F7* again to exit, tried logging on and again got the same message

---

### Post by WildTangent on 2005-12-07
Is it really saying "USERNAME@USERNAME~:" at the prompt? Because if it is...I don't think thats good...

-Wild

---

### Post by Kregel on 2005-12-07
[QUOTE=WildTangent]Is it really saying "USERNAME@USERNAME~:" at the prompt? Because if it is...I don't think thats good...

-Wild[/QUOTE]

no...replace USERNAME with my username, for example "bob@bob~:"

---

### Post by Kregel on 2005-12-08
I found my Ubuntu Live CD! What do I do now?

---

### Post by aysiu on 2005-12-08
[QUOTE=Kregel]I found my Ubuntu Live CD! What do I do now?[/QUOTE] Boot from it. Then open a terminal and type ```
sudo fdisk -l
df -h
cat /etc/fstab
``` and post the output here.

---

### Post by Kregel on 2005-12-08
this is what i got:

warty@ubuntu:~ $ sudo fdisk -l

Disk /dev/hda: 13.6 GB, 13676544000 bytes
16 heads, 63 sectors/track, 26500 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       25507    12855496+  83  Linux
/dev/hda2           25508       26500      500472    f  W95 Ext'd (LBA)
/dev/hda5           25508       26500      500440+  82  Linux swap

warty@ubuntu:~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on

warty@ubuntu:~ $ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
# Added by Morphix
/dev/hda1 /mnt/hda1 ext3 noauto,users,exec 0 0
# Added by Morphix
/dev/hda5 /mnt/hda5 auto noauto,users,exec 0 0
# Added by Morphix
/dev/cloop0 /mnt/cloop0 auto noauto,users,exec 0 0
/dev/sda1 /mnt/sda1 auto noauto,users,exec,umask=000,uid=warty 0 0
/cdrom1 /cdrom1 supermount auto,user,fs=auto,dev=/dev/cdrom1

---

### Post by aysiu on 2005-12-08
Try this: ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
``` Control-L
/recovery/home/kregel

I'm assuming your username is kregel. Go to whatever your real home folder is. 

Press Control-H (to see hidden directories).

Right-click on the file called .ICEauthority and select **Properties**.
Do you own it? What are the permissions on that file?

---

### Post by Kregel on 2005-12-08
under the permissions tab it says that the owner is warty

---

### Post by aysiu on 2005-12-08
[QUOTE=Kregel]under the permissions tab it says that the owner is warty[/QUOTE] Is Warty your username?

It should be Owner: kregel
Group: kregel
Owner: read (check), write (check)
everything else not checked.

---

### Post by Kregel on 2005-12-08
no, "andrew" is

---

### Post by Kregel on 2005-12-08
[QUOTE=aysiu]
It should be Owner: kregel
Group: kregel
Owner: read (check), write (check)
everything else not checked.[/QUOTE]

i didn't see that part before. let me switch it real quick

---

### Post by aysiu on 2005-12-08
Sorry, then owner should be andrew and group andrew.

---

### Post by Kregel on 2005-12-08
it won't let me change it to andrew...there's just a drop down menu with different things to choose from, such as "root"..stuff like that, but no andrew..and it won't just let me type it in

---

### Post by aysiu on 2005-12-08
[QUOTE=Kregel]it won't let me change it to andrew...there's just a drop down menu with different things to choose from, such as "root"..stuff like that, but no andrew..and it won't just let me type it in[/QUOTE] Hm. This may not be the cleanest workaround, but maybe you can try checking all the boxes (i.e., giving every user full access to the file).

Presumably that will then allow you to log in without the live CD now that anyone has read/write access to the /home/andrew/.ICEauthority file. Once you're logged in you can uncheck the appropriate boxes (leaving only owner read and owner write checked).

Hopefully that'll work.

Initially, I thought your /home partition might be full, but you don't have a /home partition. So the .ICEauthority file is the only thing I can think of.

---

### Post by Kregel on 2005-12-09
i checked all the boxes, restarted my computer, this time taking out the live cd, tried logging in and it gave me the same message that i put in my first post

---

### Post by aysiu on 2005-12-09
Damn.

So you're at the command-line, right?

Can you try typing this? ```
sudo chown andrew:andrew /home/andrew/.ICEauthority
startx
```

---

### Post by Kregel on 2005-12-09
first press ctrl + alt + F1 from the login screen?

---

### Post by aysiu on 2005-12-09
[QUOTE=Kregel]first press ctrl + alt + F1 from the login screen?[/QUOTE] Yes. Control-Alt-F1, then what was in my previous post. Sorry.

**Edit**: If that doesn't help, [this](http://ubuntuforums.org/showthread.php?t=76866) might.

---

### Post by Kregel on 2005-12-09
alright this is what happened when i typed it in:


"/usr/bin/X11/startx: line 132: cannot create temp file for here document: No space left of device
/usr/bin/X11/startx: line 132: cannot create temp file for here document: No space left of device

fatal server error:
Server is already active for display
         if this server is no longer running, remove /tmp/.X0-lock and start again

Please contact the The X.Org Foundation support
                  at [http://wiki.X.Org](http://wiki.X.Org) for help

Xlib: Connection to "0.0" refused by server

Xlib: No protocol specified


giving up
xinit: unable to connect to X serve
xinit: No such process (errno 3): server error.
andrew@andrew:~$"

---

### Post by aysiu on 2005-12-09
[QUOTE=Kregel]
andrew@andrew:~$"[/QUOTE] Can you type ```
df -h
``` here? It'll show how much disk space you have left.

---

### Post by Kregel on 2005-12-09
it looks like this:


Filesystem   Size   Used   Avail   Use%   Mounted on
/dev/hda1    13G    12G    0        100%        /
tempfs         126M   0      126M    0%        /dev/shm
/dev            13G     12G    0       100%     /.dev
none             5.0M   2.8M  2.3M    36%      /dev

---

### Post by aysiu on 2005-12-09
[QUOTE=Kregel]it looks like this:
```

Filesystem   Size   Used   **Avail**   Use%   Mounted on
/dev/hda1    13G    12G    **0**        100%        /
tempfs         126M   0      126M    0%        /dev/shm
/dev            13G     12G    0       100%     /.dev
none             5.0M   2.8M  2.3M    36%      /dev
```[/QUOTE] Well, that's the problem, then. Available for /dev/hda1 is 0. You have no space left on your hard drive. You have to delete some files.

---

### Post by Kregel on 2005-12-09
[QUOTE=aysiu]Well, that's the problem, then. Available for /dev/hda1 is 0. You have no space left on your hard drive. You have to delete some files.[/QUOTE]

alright so i've used windows up until a short while ago but since switching to linux have really liked it, however i still know how to do pretty much nothing with it besides check my email and play games(which i can do with windows). i would love to learn as much as i can about all the stuff you can do with linux though, so could you explain to me how to do that?

---

### Post by aysiu on 2005-12-09
Well, there's the easy way, and then there's the point-and-click way.

The easy way is to use the command-line to delete files.
Let's say, for example, that you have a bunch of mp3s in /home/andrew/music that you want to get rid of. You type this in: ```
cd /home/andrew/music
ls
rm *.mp3
``` *cd* changes directories. *ls* lists the files in the directory (so you can see what you're about to delete). *rm* removes files.

If you wanted to delete an entire folder, say your pictures folder, you would do ```
rm -R /home/andrew/pictures
```

The point-and-click way, you'll need the live CD again for.
Follow the instructions I gave you before, except forget about the right-clicking on .ICEauthority--just delete the files you don't want any more.

---

### Post by sami83 on 2005-12-09
Ctrl + Alt + F1
login with your username and password
```

cd /home/USERNAME (replacing username with yours)
```
list the contents
```
ls -l
```
it should list something like: 

```

drwxr-xr-x   4 sami sami   4096 2005-11-27 06:17 downloads
drwxr-xr-x   5 root sami   4096 2005-12-05 00:13 encryptions
-rwxrwxrw-   1 root root    517 2005-11-28 14:38 initGroups.sh
-rw-r--r--   1 sami sami  20480 2005-12-08 07:04 logs.txt
-rw-r--r--   1 sami sami     24 2005-12-05 00:26 passwd.txt
drwxr-xr-x   6 sami sami   4096 2005-12-07 22:33 pptpd-1.2.3
-rwxr--r--   1 root sami 185721 2005-12-07 22:28 pptpd-1.2.3.tar.gz
-rwxr--r--   1 sami sami 829440 2005-12-07 22:20 pptpd-1.3.0.tar
drwxrwxr-x  13 sami sami   4096 2005-11-29 17:02 profile
-rwxr-----   1 sami sami   7722 2005-11-27 04:26 smb.conf
drwxr-xr-x   2 root root   4096 2005-11-29 05:02 test
-rwxrwxrwx   1 sami sami     38 2005-11-28 15:24 test.sh
-rw-r--r--   1 sami sami   2155 2005-12-05 09:58 trace.txt
drwxr-xr-x   2 sami sami   4096 2003-09-28 17:46 udp-broadcast-relay-0.3
-rwxr--r--   1 sami sami  71680 2005-12-07 21:28 udp-broadcast-relay-0.3.tar
```
find files you wish to delete to make some room, for an instance some downloaded files. Lets say you have a directory called downloads under your home folder.
```
cd downloads
```
now list its contents
```
ls -l

drwxr-xr-x  2 sami sami 4096 2005-11-27 06:17 samba
drwxr-xr-x  3 sami sami 4096 2005-11-27 06:20 webmin
drwxr-xr-x  4 sami sami 8096 2005-11-27 06:50 testfile
```
Lets say i want to delete a single file, in this case the testfile
```
rm testfile
```
Now lets say i see a useless folder that i just extracted some install files
```
rm -r samba
```
This would remove the whole directory

*edit* Uups, was a bit too slow on the typing :)

---

### Post by Kregel on 2005-12-09
i have a folder with music in it called "Andrew's Music"

i don't want to delete the whole folder, just some of the songs/folders in it

whenever i try cd /home/andrew/Andrew's Music 

the next line that comes up looks like this : >

and then it won't let me do anything

---

### Post by aysiu on 2005-12-09
Can you try ```
cd /home/andrew
ls
``` How does Andrew's Music appear?

---

### Post by Kregel on 2005-12-09
[QUOTE=aysiu]How does Andrew's Music appear?[/QUOTE]

its a blueish-purpleish color

---

### Post by aysiu on 2005-12-09
[QUOTE=Kregel]its a blueish-purpleish color[/QUOTE] Sorry. I wasn't specific enough. What's the name of the folder? Does it appear as ```
Andrew's Music
``` or something else? Keep in mind it's case-sensitive...

---

### Post by Kregel on 2005-12-09
that is correct, it appears as "Andrew's Music" in a purplish-blueish font color

---

### Post by sami83 on 2005-12-09
[QUOTE=Kregel]i have a folder with music in it called "Andrew's Music"

i don't want to delete the whole folder, just some of the songs/folders in it

whenever i try cd /home/andrew/Andrew's Music 

the next line that comes up looks like this : >

and then it won't let me do anything[/QUOTE]

do:
```
cd "/home/andrew/Andrew's Music"
```

---

### Post by Kregel on 2005-12-09
okay, so after i've deleted some stuff what do i do? exit the comand line and try logging back in from the graphical login screen?

---

### Post by sami83 on 2005-12-09
[QUOTE=Kregel]okay, so after i've deleted some stuff what do i do? exit the comand line and try logging back in from the graphical login screen?[/QUOTE]

startx should do the trick allso.

---

### Post by Kregel on 2005-12-09
YAY!! It let me log on! So would the next step now to make sure this doesn't happen again be to get a bigger hard drive, or what?

---

### Post by sami83 on 2005-12-09
[QUOTE=Kregel]YAY!! It let me log on! So would the next step now to make sure this doesn't happen again be to get a bigger hard drive, or what?[/QUOTE]

Well, bigger hard drive would do the trick. But if you arent in dire need of the additional space i'd suggest you just keep an eye out for the space left on your current hard drive and do cleanups on it on regular basis (as in delete un-needed files)

---

### Post by aysiu on 2005-12-09
[QUOTE=Kregel]YAY!! It let me log on! So would the next step now to make sure this doesn't happen again be to get a bigger hard drive, or what?[/QUOTE] Yes.

---

### Post by Kregel on 2005-12-09
Thank you all for all of your help

---

### Post by arphe_el on 2006-02-27
i forgot to drop by and say thank you. GODspeed!

---

### Post by nalmeth on 2006-02-27
wow excellent effort and persistence by helpee's and helper's

---

