---
title: "Regarding changing Hostname and Server name in Terminal"
date: 2018-03-28
forum: Server Platforms
---

### Post by dilip.h.n on 2018-03-28
Hello,
If i open a terminal i am getting as
```
dilip@Dilip:~$
```

where "dilip" is Server name and "Dilip" is Hostname (correct me if i am wrong....
I tried to change hostname by the command:
```
gksudo gedit /etc/hostname /etc/hosts
```

But i am unable to change the Server name ie., "dilip"

So, How can i change this server name...? What are the commands need to be given..??

Any suggestions are appreciated.

Thank you.

---

### Post by slickymaster on 2018-03-28
*Thread moved to **Server Platforms**.*

---

### Post by slickymaster on 2018-03-28
> **dilip.h.n said:**
> Hello,
If i open a terminal i am getting as
```
dilip@Dilip:~$
```

where "dilip" is Server name and "Dilip" is Hostname (correct me if i am wrong....
I tried to change hostname by the command:
```
gksudo gedit /etc/hostname /etc/hosts
```

But i am unable to change the Server name ie., "dilip"

So, How can i change this server name...? What are the commands need to be given..??

Any suggestions are appreciated.

Thank you.

**dilip** is the username for the current user
**Dilip** is the hostname of the server

After changing the server hostname you'll have to reboot it so the change takes effect

---

### Post by dilip.h.n on 2018-03-28
Sorry,
I want to change the username for the current user ie., "dilip".
I am able to change the hostname of the server but unable to change the username for the current user...

So, How do i change the username for the current user ie., "dilip"...???

Thank you.

---

### Post by slickymaster on 2018-03-28
```
sudo usermod -l newUsername oldUsername
```After that done rename your home folder```
sudo usermod -d /home/newHomeDir -m newUsername
```Log out and log in using your new username

---

### Post by springshades on 2018-03-28
You'll need to use the "usermod" command with the --login flag. Note that this may not be as simple as you think it is, since you may want to also change the location of your HOME directory as well to match. It's not entirely clear whether you want to do that or not.

Look at the manual page for the command to see if any of the other options are necessary for what you want to accomplish.

EDIT: The previous post is a better answer. We just happened to post at approximately the same time.

---

### Post by TheFu on 2018-03-28
There are a few other ways, but using usermod is probably safest.
I would sudoedit the /etc/passwd and /etc/shadow files. This will only change the username, not the HOME directory for that userid, which is also in the passwd file and it will leave the default groupname alone too. If you want, you can change those by editing the group and gshadow files in /etc/.

There is a manpage for each of these config files which explains what each field means. Section 5 is for config files, so **man -s5 passwd** will show information about the config and not the passwd command. manpages rock.

There is also a group-mod command - I'd have to look it up and read the manpage on it to get the correct options.

Also, editing these files only works for simple setups.  In a corporate environment with LDAP (or some other) userid/groupid controls, it may be necessary to use those other tools to rename a username.

---

### Post by dilip.h.n on 2018-04-06
If i give the following command in the terminal as:-
sudo usermod -l DILIP dilip

it shows the message as:-
usermod: user dilip is currently used by process 1365

How do i solve this issue..??

---

### Post by dilip.h.n on 2018-04-06
[COLOR=#000000]If i give the following command in the terminal as:-[/COLOR]
[COLOR=#000000]sudo usermod -l DILIP dilip[/COLOR]

[COLOR=#000000]it shows the message as:-[/COLOR]
[COLOR=#000000]usermod: user dilip is currently used by process 1365

How do i solve this..??[/COLOR]

---

### Post by TheFu on 2018-04-06
See post #7 for manual steps.

Or use a different account to make the changes.

---

### Post by dilip.h.n on 2018-05-01
Hello,
Now i have changed to the new  username and host name ie., Dilip@dilip. 
And i have renamed the home folder 
[COLOR=#000000][FONT=&amp]sudo usermod -d /home/Dilip -m Dilip
[/FONT][/COLOR]
Now in terminal if i type ll, i get as:-
total 1476
drwxr-xr-x 7 Dilip DILIP 4096 Apr 30 19:20 ./
drwxr-xr-x 29 Dilip DILIP 4096 May 1 22:59 ../
drwxrwxrwx 2 Dilip DILIP 4096 May 1 13:31 GKclW-0.

3rd column tells who is the owner of the file / directory (Dilip) and 
4th column tells who is the  group owner of the file / directory (DILIP) 

But how am i getting DILIP ..??
1] How can i change the group owner from DILIP to Dilip..??
2] How can i change the group owner for the whole system (actually group owner and owner should be same except in case of root permissions.) How do i do that..??
   I tried with chown {-R} [user]{:group} [file|directory], but in this case i need to give for every file/directory present in my system which is time consuming/cumbersome...

Any suggestions are appreciated.

Thank you.

---

### Post by TheFu on 2018-05-01
Did you read #7 above?

---

### Post by dilip.h.n on 2018-05-05
Yes, I followed #7, but what should i change there..?? 
I am unable to figure it out.
Any suggestions..??

---

### Post by LHammonds on 2018-05-05
If you installed Ubuntu Server 18.04 using the "live" ISO image rather than the "alternative" image, then you will need to make this additional change for the hostname to keep after a reboot:

Edit "/etc/cloud/cloud.cfg" and change "preserve_hostname" to "true"

[Reference Link](https://ubuntuforums.org/showthread.php?t=2390785)

LHammonds

---

### Post by TheFu on 2018-05-06
> **dilip.h.n said:**
> Yes, I followed #7, but what should i change there..?? 
I am unable to figure it out.
Any suggestions..??

You can manually edit the passwd, shadow, group and gshadow files. They are just text.  There are manpages which explain what each field is inside those files.  Post #7 explains how to read the manpage for these sections. 

If there are references inside those files to external locations, those need to "fit" and be correct.  Changing a group or userid (the names, extra info) is pretty bonehead actually.  Just ensure everything is consistent, if you change group information across all the files.  
Have a plan and execute that plan quickly for the least issues. After all, these files are live and used by the system for every command run.   Sometimes I'll have 4 terminals open with all the changes pre-made, just not saved with the SAVE command already typed, but not entered.  Then I'll quickly move from terminal to terminal writing the changes.

If you mess those files up, be certain to have a backup for each file and the skill to put them back from alternate boot media. Of course, you can make the changes slowly with alternate boot media, but testing it is a hassle whereas doing it on a live system is just a logout and login for GUI-based systems or opening a new session for servers.

For my home systems, I don't use the useradd/mod or groupadd/mod commands. Too hard to figure out what they do, when I can just edit the files directly and be done. If the manpages don't work for you, every Linux admin book has a chapter about these things. Feel free to use any of them.

---

### Post by lensman3 on 2018-07-01
> **dilip.h.n said:**
> If i give the following command in the terminal as:-
sudo usermod -l DILIP dilip

it shows the message as:-
usermod: user dilip is currently used by process 1365

How do i solve this issue..??

The login shell is running under process 1365 and has user dilip locked.  The kernel and "/sbin/init" won't let you change login files it controls.  It is a form of "you can teach an old dog new tricks".  

Research single user mode and rescue mode.  It involves catching your system before it boots and editing the boot commands by adding the word "single" to the end of  linux command in /boot/grub/grub.cfg.  

The boot will dump you to a root command line.  The machine will probably not even have a network and the screen will be a graphics terminal.  You will need to use "cd", "chown", "chgrp" and use the recusive options to change an entire directory tree at once. You will have to edit /etc/group file's line with dilip name on it from capitals to lower case.  Realize your are now "GOD" on the machine.

A cntl-d will log you out and finish booting the machine.  You will be logged in as "root" but your own password should work.  If your password doesn't work you will have to learn how to add a password for root.   

-or-
It might be simpler to add another user.  Give that person sudo prevledges from the old account. Login as the new user and make the changes using sudo. Reboot and log back into your old user and hope its fixed.

-or-
try "sudo init 1" and see if you get to runlevel 1 which is single user.  Make sure you do a couple of "sync" s before you do this.  (This command might be exciting since it could be like running "rm -frv /" and seeing when things stop working)!

---

