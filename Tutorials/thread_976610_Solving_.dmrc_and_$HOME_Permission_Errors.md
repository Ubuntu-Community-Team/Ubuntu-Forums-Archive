---
title: "Solving .dmrc and $HOME Permission Errors"
date: 2008-11-09
forum: Tutorials
---

### Post by drs305 on 2008-11-09
**[COLOR="DarkGreen"][SIZE="3"]In a Rush? Go Directly to #5 for the Quick Fix ...[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="3"]1. The Error Message:[/SIZE][/COLOR]**
[LIST]
[*]**[COLOR="DarkRed"]User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.[/COLOR]**
[/LIST]
**[COLOR="Navy"][SIZE="3"]2. What does it mean and how did it happen?[/SIZE][/COLOR] **
During boot or session start, the system detected an error in the ownership and/or permissions of the $HOME folder or the .dmrc file. You will still be able to gain access to your user account and have administrative (sudo) rights if you are in the *admin* group.

The most likely cause of this error was an inappropriate use of the '*chown*' or '*chmod*' command, possibly combined with the '*-R*' option. The '*-R*' switch adds the *recursive* option to a command, meaning that the command is executed not only on the specific file or folder, but all subfolders and files below it. Be very careful whenever applying the *-R* switch to a command. If you don't need it, don't use it.

An example of a command that would cause this to occur would be "*chmod -R 777 /home/username*" since this would both make the user's home folder writable by others and change the permissions of the .dmrc file to "777". Neither of these is acceptable by the system.

**[COLOR="Navy"][SIZE="3"]3. How do I fix it?[/SIZE][/COLOR] **

The following commands will restore the ownership and permissions to those acceptable by the operating system. If you perform the commands in order, the use of '*sudo*' is not required for the '*chmod*' commands. If, for some reason, you are running the livecd (not necessary) and have booted to a root prompt, '*sudo*' is not required for *any* command.

Items in [COLOR="DarkRed"]**dark red**[/COLOR] require changing to your specifics (e.g your user name). Items in [COLOR="Navy"]**dark blue**[/COLOR] are portions of the generated error message.

Open a terminal:
Applications, Accessories, Terminal, or
ALT-F2, type ***gnome-terminal*** in the window and hit "RUN" or
If you are at the normal login prompt, select *Options* in the lower left corner, *Failsafe Terminal* and enter your username and password. Enter the commands from this guide in the terminal window that opens.

*[COLOR="Navy"]**User's .dmrc file should be owned by user**[/COLOR]*:
```
sudo chown *[COLOR="DarkRed"]username[/COLOR]* /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc 
```
Example for a user with a logon of '[COLOR="DarkRed"]*john[/COLOR]*': sudo chown *[COLOR="DarkRed"]john[/COLOR]* /home/*[COLOR="DarkRed"]john[/COLOR]*/.dmrc


*[COLOR="Navy"]**and have 644 permissions**[/COLOR]*:
```
chmod 644 /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc
```
[COLOR="DarkRed"]Note 1[/COLOR]: If you look at the actual .dmrc permissions, you will see that the system defaults to "644". If you take a look at the actual permission after logging back in, you will find the system has changed the permissions to "600" ( -rw------- ). You can substitute "600" in this command if you wish.

*[COLOR="Navy"]**User's $HOME directory must be owned by user**[/COLOR]*. **Read [COLOR="DarkRed"]Notes 2 & 3[/COLOR] before executing this command:**
	```
sudo chown *[COLOR="DarkRed"]username[/COLOR]* /home/*[COLOR="DarkRed"]username[/COLOR]*
```
[COLOR="DarkRed"]Note 2[/COLOR]: I did not use the recursive *-R* switch. While all folders and files within the $HOME folder normally are owned by the user, the only folder which needs to have the ownership changed to eliminate this error is the $HOME folder itself. You may run this command as "sudo chown -R username:username /home/username" if you want to ensure the entire contents of your home folder belong to you and your usergroup.
[COLOR="DarkRed"]Note 3[/COLOR]: When this command is run you may get a message stating "*unable to access /home/user/.gvfs.*. This is not a problem and references the .gvfs is a virtual file system. The command should do what is necessary to fix the problem, but you can avoid this message by accomplishing these commands first.
```

umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs

```

*[COLOR="Navy"]**and must not be writable by others**[/COLOR]*:
```
chmod 755 /home/*[COLOR="DarkRed"]username[/COLOR]*
```
Other acceptable permissions include 750 or 700.

Log out and back in for the changes to take effect. Rebooting is not necessary.

**[COLOR="Navy"][SIZE="3"]4. What is the .dmrc file?[/SIZE][/COLOR]**
The .dmrc is an initialization file which the system checks during session logon. Specifically, gnome checks the file for any specific language or session information it hasn't located elsewhere. While often the file is blank except for the basic header data, it may contain a specific language to use at session startup. Below is an example. The plain text is the default entry, the bold text is what would be added to begin the session with a specific language.
```

[Desktop]
Session=gnome
**Language=cs_CZ.UTF-8**

```
For more information on the .dmrc file, refer to the [_[COLOR="DarkRed"]Gnome Display Manager Reference Manual[/COLOR]_]("http://www.gnome.org/projects/gdm/docs/2.20/configuration.html"), Configuration, Sections 6.1 and 6.3.

**[COLOR="Navy"][SIZE="3"]5. Solution Summary: No Frills[/SIZE][/COLOR]**
Depending on the problem, all of these steps may not be necessary. Running all of them will correct any of the issues addressed by the error message. They can be run in terminal in the current session or from the root prompt in recovery mode. If running from the root prompt, '*sudo*' is not required. These commands will not work from the LiveCD desktop without modification .
```

sudo chown *[COLOR="DarkRed"]username[/COLOR]* /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc
chmod 644 /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc
sudo chown *[COLOR="DarkRed"]username[/COLOR]* /home/*[COLOR="DarkRed"]username[/COLOR]* 	# if you get a ".gvfs" error message, see Section 3, [COLOR="DarkRed"]Note 3[/COLOR]
chmod 755 /home/*[COLOR="DarkRed"]username[/COLOR]*

[I]Log out of your current session and back in. 
Rebooting is not necessary but will accomplish the same thing.[/I]

```
For the last command, other acceptable permissions include 750 or 700.

Since you came to the "Quick Fix" you probably didn't read the preceeding sections. If you are *sure* you want all the files in your home folder to belong to you (which is normal), you can reduce the commands to:
```

sudo chown -R *[COLOR="DarkRed"]username[/COLOR]* /home/*[COLOR="DarkRed"]username[/COLOR]*  # if you get a ".gvfs" error message, see Section 3, [COLOR="DarkRed"]Note 3[/COLOR]
chmod 755 /home/*[COLOR="DarkRed"]username[/COLOR]*
chmod 644 /home/*[COLOR="DarkRed"]username[/COLOR]*/.dmrc
[I]Log out of your current session and back in. 
Rebooting is not necessary but will accomplish the same thing.[/I]

```

**[COLOR="Navy"][SIZE="3"]6. More Info[/SIZE][/COLOR]**
[_[COLOR="DarkRed"]FilePermissions[/COLOR]_]("https://help.ubuntu.com/community/FilePermissions")
[_[COLOR="DarkRed"]Gnome Display Manager Reference Manual[/COLOR]_]("http://www.gnome.org/projects/gdm/docs/2.20/configuration.html")
[_[COLOR="DarkRed"]dmrcErrors[/COLOR]_]("https://help.ubuntu.com/community/dmrcErrors") Same content in wiki formatting.

---

### Post by bodhi.zazen on 2008-11-12
Very nice post , this is obviously a FAQ.

Consider posting this information on the wiki :)

---

### Post by ajmorris on 2008-11-12
very nice tutorial :) You may like to consider adding the differences between sudo paramaters to the end though though, i.e. sudo -i and sudo -s  so that errors like this, do not occur :)
(obviously this is not the only reason it happens, but it is a big contributer)


AJ

---

### Post by kevdog on 2008-11-16
Congratulations on tutorial of the week.  Can't say that I've ever run across this error, however well written guide.  This from one tutorial of the week winner to the next :)

---

### Post by hackerlife on 2008-11-17
man, thanks so much!!!
this was such a well made How-to, definately one of the best ive ever seen!
i had this problem 'cuz i had to back up my /home (cuz hp wanted to reformat my hdd those bastards!!)

---

### Post by Melindrea on 2008-11-18
Thank you, thank you, thank you! (I don't know if it solved the problems yet - if not I'll come back and whine.) After reinstalling and backing up my home directory to another partition, I've been having that problem. Not really that much of an issue, but a bit annoying. It was on my "to-do" list. So, thank you very much for (hopefully) helping me fix it. =)

---

### Post by JEStone on 2008-11-19
works great! Very nice tutorial.

---

### Post by greyfox1 on 2008-11-29
I ran into this after moving my home directory to a different partition, re-installing Ubuntu and then mounting the partition at my home folder location.  Like everyone else, this worked for me.  Thanks and cheers!

---

### Post by jaypmcwilliams on 2008-12-23
:P AWESOME! totally worked. & worked well. I used 750. I HUGE help to us at Lin-U-Over.com

---

### Post by compgeek83 on 2008-12-24
I followed your directions to the letter and it fixed the login error message but caused another problem.

After logout - login I got an error "Nautilis encountered an error" with some garbage about bonobo

had to run 

"killall bonobo-activation-server"

after another logout-login all is well

---

### Post by jamesisin on 2009-01-01
Well, these instructions have fixed my .dmrc error message and they seem to have also fixed this freezing problem I was having:

[http://ubuntuforums.org/showthread.php?p=6472353](http://ubuntuforums.org/showthread.php?p=6472353)

However, Rhythmbox, Amarok (Xine), and Totem (Movie Player) are no longer able to play anything.  Totem says "GStreamer encountered a general stream error" and Amarok tells me xine could not find any audio drivers.

Anybody got an answer on this one?

---

### Post by jamesisin on 2009-01-08
Well, I was able to get all the audio back in order by running through the PA setup again (actually thrice, but who's counting?).

The thing is, for no apparent reason I keep losing this permission battle.  I have now run these four commands to correct my .dmrc & home directory ownership/permissions in the last three days.

Why does this keep getting hosed?  I am NOT using chown or chmod myself (nor the GUI version).  I have been ripping CD's using Sound Juicer, and I can't imagine it's f***ing with the permissions.

Any thoughts?

---

### Post by bodhi.zazen on 2009-01-08
Are you running graphical applications as root ? If so, use gksu.

Are you using sudo -s ? If so use sudo -i

---

### Post by jamesisin on 2009-01-08
I have created a separate thread for my issues:

[http://ubuntuforums.org/showthread.php?t=1034452](http://ubuntuforums.org/showthread.php?t=1034452)

I have answered your questions there and I hope you may be able to provide any additional insight there as well.

---

### Post by dimbulb1024 on 2009-01-13
A big thanks to you drs305.

This took care of my error message.

---

### Post by JBA2337 on 2009-01-16
sudo chown username /home/username/.dmrc  
sudo chown username /home/username

The above are the commands that you told us to use.

But in the summary, the commands are:

sudo chown username: /home/username/.dmrc
sudo chown username: /home/username 


Is the colon :  necessary or does it not matter?


JBA2337

---

### Post by jamesisin on 2009-01-16
No.  Use only your username.  (Unless of course your username has a : in it, which may not even be possible.)

---

### Post by drs305 on 2009-01-16
> **JBA2337 said:**
> Is the colon :  necessary or does it not matter?


The colon is not necessary and it doesn't matter in this case, but it does mean something. If you use "username", then the owner of a file or folder is changed to "username". Adding a colon ( : ) after the username is a shorthand way of writing "username:username", which changes the owner to "username" and the group to the group named "username".
Examples:
**sudo chown dave /home/dave** makes 'dave' the owner of /home/dave  The group to which /home/dave belongs does not change.
**sudo chown dave: /home/dave** makes 'dave' the owner of /home/dave and makes /home/dave part of the *group* 'dave'

For correcting the error, which group the .dmrc file or /home/*username* folder belongs to is not considered. However, the examples should be consistent. In keeping with the philosophy of changing as little as possible, I will remove the colon, although in most cases the /home/username folder would belong to the user's group as well.

Thanks for pointing out the differences between the examples and the summary.

---

### Post by col48 on 2009-03-01
As far as the "How did it happen", I think for me it coincided (twice) with mistyping my password at login. (Ubuntu 8.04).

---

### Post by mfdc1969 on 2009-03-06
Thank you very much drs305 for this How-to!

I have noticed that every time I copy my entire home directory (including hidden files) to an external hdd I get this error the very next time I boot up or restart.

It's nice to have such a concise solution.

---

### Post by Jacdeb6009 on 2009-03-11
> **mfdc1969 said:**
> Thank you very much drs305 for this How-to!

I have noticed that every time I copy my entire home directory (including hidden files) to an external hdd I get this error the very next time I boot up or restart.

Mmm, I have the same problem with the same cause (has happened a couple of times).  Can anyone explain why this happens when I copy to an external HDD and how this can be avoided?  I mean the "fix" is simple, but it is a nuisance.

Thanks!

---

### Post by bodhi.zazen on 2009-03-11
See man cp :twisted:

cp does not preserver permissions, and neither does FAT or NTFS file systems.

When you save (backup) $HOME you can use cipo or the -a flag or tar ...

If you archive the files (tar) you can save the archive to FAT/NTFS, but not with cp as these file systems do not preserve the permissions.

---

### Post by Misaru-Meep on 2009-03-12
I seem to be running into a problem. I tried what you asked, but I got this message in terminal:

[B]lizz@lizz-laptop:~$ sudo chown -R lizz:lizz /home/lizz
chown: cannot access `/home/lizz/.gvfs': Permission denied
lizz@lizz-laptop:~$ [/B]

---

### Post by bodhi.zazen on 2009-03-12
yea, that error is not uncommon ...

---

### Post by Misaru-Meep on 2009-03-12
Does anyone know what I should do?

---

### Post by bodhi.zazen on 2009-03-12
You should be good to go, keep following the tutorial and reboot.

---

### Post by Misaru-Meep on 2009-03-12
I did continue through with everything, and restarted my computer, and the warning stopped. But I am still getting the same *other* warning, and it not allowing me to access my home folder from the places menu. If anyone could help, I have my original thread here: 

[http://ubuntuforums.org/showthread.php?t=1093674](http://ubuntuforums.org/showthread.php?t=1093674)

---

### Post by Jacdeb6009 on 2009-03-13
> **bodhi.zazen said:**
> See man cp :twisted:

cp does not preserver permissions, and neither does FAT or NTFS file systems.

When you save (backup) $HOME you can use cipo or the -a flag or tar ...

If you archive the files (tar) you can save the archive to FAT/NTFS, but not with cp as these file systems do not preserve the permissions.

Thanks bodhi!! I have looked at the man page for cp and it doesn't quite explain the problem (maybe using nautilus is a further complication). One further question, if I may, why would the cp command (or Nautilus for that matter) change the permissions of the source files and directories? I can sort of understand that the permissions in the copy may not be preserved, but changing the permissions of the source doesn't quite make sense to me.

This may simple be "how it is", but it would be interesting to understand why it is implemented in this way...

Thanks for your patience,

---

### Post by bodhi.zazen on 2009-03-13
I do not know how to explain it to you better.

Neither FAT or NTFS preserve permissions. use cp to copy a file to a windows partition then copy it back.

See also :

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

and

[http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving](http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving)

That second link is a (brief) overview of the issues.

---

### Post by Jacdeb6009 on 2009-03-13
Once again, Thanks!!  I will take a look at the threads to gain a better understanding of this.

---

### Post by hype on 2009-04-08
Thanks, i dsperatly tried to set ownership to 644 on .dmrc, but without effect.

The >chmod 755 /home/user did the trick :D

---

### Post by agl on 2009-05-01
Thank you

---

### Post by lmcfadden on 2009-05-16
Once again the Ubuntu forum and knowledgeable users have come to my aid.  Had this problem since upgrading to Jaunty, however I was also doing some tests installing Wine, so I must have caused it, but all is well now.

Thanks again...

Lloyd.

---

### Post by sunil12 on 2009-05-23
started getting this message today on logon.
tried the above mentioned fix. I am new to ubantu... here is what i get on terminal, kindly guide

$ chown my username/home/ my username/.dmrc
chown: missing operand after `username/home/username/.dmrc'
Try `chown --help' for more information.

---

### Post by drs305 on 2009-05-24
> **sunil12 said:**
> started getting this message today on logon.
tried the above mentioned fix. I am new to ubantu... here is what i get on terminal, kindly guide

$ chown my username/home/ my username/.dmrc
chown: missing operand after `username/home/username/.dmrc'
Try `chown --help' for more information.

Let's use a username of sunil12. Of course, you would need to substitute your actual login name.  The commands would be:
```

sudo chown sunil12 /home/sunil12/.dmrc
chmod 644 /home/sunil12/.dmrc
sudo chown sunil12 /home/sunil12
chmod 755 /home/sunil12

```

---

### Post by rcayea on 2009-05-26
Thanks for the post. Much appreciated. :D

---

### Post by Bearly Able on 2009-06-01
Thanks for the great "How To".  Very easy to follow and well-explained.  I like to understand why I'm doing things and what each command is for.  After a frustrating week of problems with no apparent solution, it's been great to find one thing I can fix so easily!

---

### Post by frodon on 2009-06-02
> **lmcfadden said:**
> Once again the Ubuntu forum and knowledgeable users have come to my aid.  Had this problem since upgrading to Jaunty, however I was also doing some tests installing Wine, so I must have caused it, but all is well now.

Thanks again...

Lloyd.Yep i'm having this after installing a game through wine, i think wine and the install of games through it is what created the issue on my computer.

chmod 644 .dmrc wasn't enough as my /home/frodon had +w rights which seems to be the issue.

---

### Post by d3ngar on 2009-06-03
Hey,

My .dmrc file is not existent. Creating a blank file as a replacement doesn't cut it... Anyone got any idea what I could do?

Thanks,

Chris

---

### Post by d3ngar on 2009-06-03
Actually I might just create a new profile and copy it from there and change any ref to my username...

Watch this space <---


Uhh, just spilled the beans!

---

### Post by drs305 on 2009-06-03
> **d3ngar said:**
> Actually I might just create a new profile and copy it from there and change any ref to my username...

n3ngar,

This is the (entire) content of my .dmrc file. I am running the standard 64-bit jaunty install. Two blank lines for some reason, then the other two.
> 


[Desktop]
Session=gnome

However you get the file into your system, run this to get the correct permssions/owernship:
```

sudo chown *[COLOR="DarkRed"]yourusername[/COLOR]* ~/.dmrc
chmod 644 ~/.dmrc

```

---

### Post by d3ngar on 2009-06-03
Yup, the creation of a new user and logging in as the one, created a new .dmrc file. I since copied it over, made it mine, chmod to 644 and the problem is GONE.

Thanks for everyones help, btw!

Linux RoCKS!!

---

### Post by Julian David Pitt on 2009-06-16
Hi Everyone
I have been working on this error all day and following this tutorial, but the error refuses to leave me unfortunately. I have run all the commands in section 5 and they all appear to run ok. I even rebooted into recovery mode and ran them from a root shell, still no joy on logging out and then back in. I get the standard error message about $HOME/.dmrc being ignored as well as ```
Could not update ICEauthority file /home/julian/.ICEauthority
``` when I ok the first message. These are the permissions I have on the relevant files:

```
julian@julian-desktop:~$ ls -la /home
total 32
drwxr-xr-x  5 root   root    4096 2009-06-16 10:47 .
drwxr-xr-x 23 root   root    4096 2009-06-16 11:38 ..
drwxr-xr-x 31 julian julian  4096 2009-06-16 15:36 julian
drwx------  2 root   root   16384 2009-06-04 15:11 lost+found
drwxr-xr-x 23    999    999  4096 2009-06-05 14:33 ubuntu
julian@julian-desktop:~$ ls -la /home/julian/.dmrc
ls: cannot access /home/julian/.dmrc/..: Permission denied
ls: cannot access /home/julian/.dmrc/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
julian@julian-desktop:~$ ls -la /home/julian/.ICEauthority
total 8
drwxr-xr-x  2 julian julian 4096 2009-06-16 10:50 .
drwxr-xr-x 31 julian julian 4096 2009-06-16 15:36 ..
julian@julian-desktop:~$

```

If I run the commands again and check permissions afterwards I get this:

```
julian@julian-desktop:~$ sudo chown julian /home/julian/.dmrc
[sudo] password for julian:
julian@julian-desktop:~$ chmod 644 /home/julian/.dmrc
julian@julian-desktop:~$ sudo chown julian /home/julian
julian@julian-desktop:~$ chmod 755 /home/julian
julian@julian-desktop:~$ ls -la /home
total 32
drwxr-xr-x  5 root   root    4096 2009-06-16 10:47 .
drwxr-xr-x 23 root   root    4096 2009-06-16 11:38 ..
drwxr-xr-x 31 julian julian  4096 2009-06-16 15:36 julian
drwx------  2 root   root   16384 2009-06-04 15:11 lost+found
drwxr-xr-x 23    999    999  4096 2009-06-05 14:33 ubuntu
julian@julian-desktop:~$ ls -la /home/julian/.dmrc
ls: cannot access /home/julian/.dmrc/..: Permission denied
ls: cannot access /home/julian/.dmrc/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
julian@julian-desktop:~$ ls -la /home/julian/.ICEauthority
total 8
drwxr-xr-x  2 julian julian 4096 2009-06-16 10:50 .
drwxr-xr-x 31 julian julian 4096 2009-06-16 15:36 ..
julian@julian-desktop:~$

```

Many thanks if anyone can help me out.

---

### Post by drs305 on 2009-06-16
> **Julian David Pitt said:**
> ```
Could not update ICEauthority file /home/julian/.ICEauthority
``` when I ok the first message. These are the permissions I have on the relevant files:




Try running this command to set the proper ICE permissions:
```

sudo chmod 600 $HOME/.ICEauthority

```

---

### Post by Julian David Pitt on 2009-06-16
Hi drs305
I have dome as you suggested and logged out and back in, with the same 2 error messages I am afraid. My permissions now show as follows:

```
julian@julian-desktop:~$ ls -l /home/julian
total 32
drwxr-xr-x 2 julian julian 4096 2009-06-16 15:14 Desktop
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Documents
drwxr-xr-x 3 julian julian 4096 2009-06-16 15:16 folding
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Music
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Pictures
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Public
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Templates
drwxr-xr-x 2 julian julian 4096 2009-06-16 10:52 Videos
julian@julian-desktop:~$ ls -l ~/.ICEauthority
total 0
julian@julian-desktop:~$

```
Is it right that there is nothing in the ICEauthority file?

---

### Post by drs305 on 2009-06-16
> **Julian David Pitt said:**
> 
Is it right that there is nothing in the ICEauthority file?

When I run "ls -l .ICEAuthority" I get this:
> -rw------- 1 drs305 drs305 7652 2009-06-16 11:10 .ICEauthority


1. Make sure you are the owner. The commands I give in the first post are the minimum to get the .dmrc and /home ownership problems resolved. So:
```

sudo chown julian: /home/julian/.ICEauthority
chmod 600 /home/julian/.ICEauthority

```

If you can't change the permissions to 600, try moving the file to your Desktop. In actuality, if you delete it the file should be recreated correctly, but I prefer moving things as a less permanent solution so you can put it back if necessary.
```

sudo mv ~/.ICEauthority ~/Desktop

```
Restart and see if the file was recreated, is now owned by you, and has the correct permissions.

The .ICEauthority file gets messed up sometimes when certain graphical commands are run with "sudo" instead of "gksudo". I have no direct experience with this but there are numerous posts about it on various forums. The exact cause is often undetermined but there is a suspicion this is the cause.

---

### Post by Sarickjones21 on 2009-07-01
hi,im new to linux and programming. i get the same error msg but the solution dont seem to work. what i did wrong to get this msg was i went into user and group section and typed in /root in place of /home/sarickjones....sigh i know im an idiot but i was trying to get root permission lol......

so after reading this FAQ i typed this in recovery mode. 
> chown sarickjones:sarickjones /home/sarickjones
/.dmrc
chmod 644 /home/sarickjones/.dmrc
sudo chown sarickjones:sarickjones /home/sarickjones
chmod 755 /home/sarickjones[SIZE=2][SIZE=1]
[/SIZE][FONT=Verdana][SIZE=2]i also tried it without putting "sarickjones:" dont know if that matters...

[/SIZE][/FONT][/SIZE][FONT=Verdana][SIZE=2][SIZE=2]and i rebooted but i still get same msg.
[/SIZE]

[SIZE=2]i also get[/SIZE] [/SIZE][/FONT]> Could not update ICEauthority file /home/julian/.ICEauthority[FONT=Verdana]so i typed in what drs305 but it says[/FONT] > '/root/.iceauthority' : No such file or directory[SIZE=2]also typed chown sarickjones ~/.dmrc and i get no such file or directory.

thanks for the help![/SIZE]

---

### Post by drs305 on 2009-07-01
First, welcome to Ubuntu and the Ubuntu forums!

The *.ICEauthority* file is not root's. It should be in your home ($HOME) folder: /home/sarickjones/.ICEauthority

Edited: See sisco311's post below.

---

### Post by sisco311 on 2009-07-01
> **Sarickjones21 said:**
> hi,im new to linux and programming. i get the same error msg but the solution dont seem to work. what i did wrong to get this msg was i went into user and group section and typed in /root in place of /home/sarickjones....sigh i know im an idiot but i was trying to get root permission lol......


reboot in recovery mode and
change your home directory location back to /home/sarickjones:
```
usermod -d /home/sarickjones sarickjones
```

---

### Post by Sarickjones21 on 2009-07-01
thanks guys for the help! ```
usermod -d /home/sarickjones sarickjones
``` worked for me. didnt know it was that simple... lol

---

### Post by Julian David Pitt on 2009-07-02
I am still getting the same generic error about Home/.dmrc on start and when I run 
```
ls -l .ICEAuthority
```

I get

```
julian@julian-desktop:~$ ls -l .ICEAuthority
ls: cannot access .ICEAuthority: No such file or directory
```

I have now run all the commands you suggested and am at a loss to know what to do now ? Help please?

---

### Post by drs305 on 2009-07-02
> **Julian David Pitt said:**
> I am still getting the same generic error about Home/.dmrc on start and when I run 
```
ls -l .ICEAuthority
```

I get

```
julian@julian-desktop:~$ ls -l .ICEAuthority
ls: cannot access .ICEAuthority: No such file or directory
```

I have now run all the commands you suggested and am at a loss to know what to do now ? Help please?

Julian,

You have spelled the file incorrectly. The A is lowercase, and case matters in linux. So try "ls -l .ICEAuthority" and see if you get a return.

As for continuing to get the error, if you $HOME is back where it belongs ( ;-) ), let's try it from the top:

```

sudo chown julian /home/julian/.dmrc
chmod 644 /home/julian/.dmrc
sudo chown julian /home/julian
chmod 755 /home/julian

```
Then exit and re-login

---

### Post by Yleeyas on 2009-07-06
Thanks for this, solved more than one problem for me ;)

---

### Post by ace007 on 2009-07-18
Thank you for taking the time to write a coherent FAQ. I fubared my mom's computer with a fresh install, I knew permissions were the issue, but I didn't know off hand how to fix them.

Thanks,

---

### Post by Julian David Pitt on 2009-08-18
Hi All
I am still having this error on my system despite my best efforts at resolving it. I get the "User's $Home/.dmrc file is being ignored" message despite having run the commands to take ownership of the .dmrc file and set the correct permissions on my home directory. I should point out that home is situated on my sda3 partition as per my fstab file:
cat /etc/fstab gives me:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0   0
# /dev/sda1
UUID=2380d134-7025-4b70-b1ab-93ace576a52a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f2552b1e-c9f3-4024-b74c-800db20d546e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2
```
Please advise anything furtehr I am able to do to rectify this error. Thank you.

---

### Post by drs305 on 2009-08-18
Julian David Pitt,

Check the results when you run these commands. They should look similar to these, with your username instead of drs305.

**ls -la /home**
> 
drwxr-xr-x 34 drs305 drs305 4096 2009-08-18 08:03 drs305

**ls -la $HOME/.dmrc**
> 
-rw------- 1 drs305 drs305 2 2009-08-02 19:18 /home/drs305/.dmrc


---

### Post by Julian David Pitt on 2009-08-18
Hi drs305 
This is what i get :
```
julian@julian-desktop:~/folding$ ls -la /home
total 32
drwxr-xr-x  5 root   root    4096 2009-06-16 10:47 .
drwxr-xr-x 23 root   root    4096 2009-08-07 11:48 ..
drwxr-xr-x 41 julian julian  4096 2009-08-18 10:19 julian
drwx------  2 root   root   16384 2009-06-04 15:11 lost+found
drwxr-xr-x 23    999    999  4096 2009-06-05 14:33 ubuntu
julian@julian-desktop:~/folding$ ls -la $HOME/.dmrc
ls: cannot access /home/julian/.dmrc/..: Permission denied
ls: cannot access /home/julian/.dmrc/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
julian@julian-desktop:~/folding$

```
Thanks for your help.

---

### Post by drs305 on 2009-08-18
Julian,

The problem is, as you can see, the system won't let you access .dmrc. You can try to change the file properties (again) using the following commands.

Run these two commands to change the ownership to yourself and then set the permissions:
```

sudo chown julian /home/julian/.dmrc
chmod 644 /home/julian/.dmrc

```

Then log out and back in or reboot.

Are you using folding@home? I know a bit about the program but not enough about the specifics to know how that might interfere with your normal setup.

Added: We worked a bit on this via PM. See post #60.

---

### Post by Julian David Pitt on 2009-08-18
Hi Drs305
I have followed your instructions to the letter with the same result. I get the same error when I log in and the permissions appear to not have changed at all:
```
julian@julian-desktop:~$ ls -la /home
total 32
drwxr-xr-x  5 root   root    4096 2009-06-16 10:47 .
drwxr-xr-x 23 root   root    4096 2009-08-07 11:48 ..
drwxr-xr-x 41 julian julian  4096 2009-08-18 14:34 julian
drwx------  2 root   root   16384 2009-06-04 15:11 lost+found
drwxr-xr-x 23    999    999  4096 2009-06-05 14:33 ubuntu
julian@julian-desktop:~$ ls -la $HOME/.dmrc
ls: cannot access /home/julian/.dmrc/..: Permission denied
ls: cannot access /home/julian/.dmrc/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
julian@julian-desktop:~$
```
Thanks again.

---

### Post by Julian David Pitt on 2009-08-19
I have finally managed to resolve this by renaming the $HOME/.dmrc file. I then logged off and back on again. The system recreated the file, this time with the correct permissions, and now all is well. Thanks to drs305 for his help.

---

### Post by Hachi-Roku on 2009-11-27
Thanks for the how-to. Not only did it allow me to put my CFD program into its own user folder (done for reasons stipulated by the CFD program), it also sent me on one of those linux learning journeys about file ownership and modification etc.

in the end i just changed ownership via chown. lets see how it goes!!

found this really helpful... and simple too
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

cheers

---

### Post by malibusurfer2 on 2010-08-22
Thank you drs305! You provided a great tutorial with great explanations. The Ubuntu community is amazing.

---

### Post by drs305 on 2010-08-22
> **malibusurfer2 said:**
> Thank you drs305! You provided a great tutorial with great explanations. The Ubuntu community is amazing.

It's nice to know that old posts can still come in handy from time to time...

---

### Post by christ8 on 2012-01-13
Well, this proved to be very useful.  I recovered my system to a new partition, due to a crash caused by me.  I spent a whole day trying to track it down, and finally this helped.  Many thanks.

---

