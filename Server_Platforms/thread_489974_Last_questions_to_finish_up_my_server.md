---
title: "Last questions to finish up my server"
date: 2007-07-01
forum: Server Platforms
---

### Post by notaloafer on 2007-07-01
Thanks so much for the great support I've received on this forum!
Anyways I have a few questions left in regard to securing up my server:

**1: Lock session in Gnome**
How do I do this? Every time I click on lock screen all I have to do is move the mouse and my session is back. I would like it to password protect my session.

**2: vsftpd Support**
I've looked all over through google for good guides to this, I have it installed with my preferences setup but I have no idea how to add/remove users or a good way to manage them (perhaps through a MySQL database? That would be convenient!)

**3: Hanging Startup Issue**
I made a previous thread on this already but we couldn't find a solution. We came up with that it has something to do with USB because whenever I turn on my computer it hangs at that checkpoint for 30-60 seconds trying to boot (it still does eventually boot). If you'd like to help me on this please [view this thread.]("http://ubuntuforums.org/showthread.php?t=488624")

**4: Permissions Issue** **FIXED!!**
I had copied over my WWW folder from my previous Windows 2000 Server. However I want to set the owner as "root" and the group as "users". When I do this it only applies to that one directory (even if I select copy permissions to subdirectories). How come it won't change the owner and group permissions on the sub directories? (I'm still a newbie to linux permission systems).

Thanks so much for the support you can offer!
-Eric.

Added after: **5: Configuring Logins**
What I want for a permission system is to have my root account, and then a general use account (the account is called general-lee). The root account has all permissions, but I want the general use account to not be able to administer the board without acting as root (alternate temp login). For example if I want to restart apache2, I would run a restart command as root and once it's restarted I would be back to my normal permissions (not being able to restart unless you are acting as root). If you have any suggestions for a better way to do this or a more secure way please tell!

---

### Post by scxtt on 2007-07-01
1. i'm sure there's an option for whatever screen saver prog. you're using to lock the screen ... otherwise, there are X-lock programs
2. are you looking for something that's not usual linux users?  just create new accounts on your box for them to use [ useradd <username>; passwd <username> ] ...
3. what do you have plugged into usb?
4. did you try: **chown -R root:root /var/www** -- generally root isn't in "users", it has its own group ...

---

### Post by notaloafer on 2007-07-01
> **scxtt said:**
> 1. i'm sure there's an option for whatever screen saver prog. you're using to lock the screen ... otherwise, there are X-lock programs
2. are you looking for something that's not usual linux users?  just create new accounts on your box for them to use [ useradd <username>; passwd <username> ] ...
3. what do you have plugged into usb?
4. did you try: **chown -R root:root /var/www** -- generally root isn't in "users", it has its own group ...

1: I'm just talking about the screen lock gnome provides. The one where you hit the shutdown icon in the top right corner and select "lock screen" which is supposed to password protect your session. 
2: About vsftpd; are you saying all I have to do are create general users to use with the FTP? I'm sorry, I'm just so used to the way my old ftp server used to work on windows (I would create a seperate user account only applied to the FTP). So I can use general user accounts to work with the FTP?
3: The only thing plugged into my USB is my KVM (as described in that thread). However I know this to not be the problem because I used my Dads generic keyboard/mouse and I still got the exact same errors.
4: I'm kinda messed up mentally on linux permissions. I was using gnome right click then viewing permissions and trying to change it from there. How would I use chown?

I don't know if its against forum ToS but if I can and someone wants to help me I'd be happy to give out my MSN/AIM addresse(s) if you wanted to help me touch up on my server.

Thanks!
-Eric.

---

### Post by scxtt on 2007-07-01
1. i don't personally use screen locks (or a screensaver), my cat doesn't touch my computer and he's the only one there when i'm not ... i was using xlock but it seemed pointless ...
2. you can create normal linux user accounts and when a person who knows the creds for one of those accounts accesses your FTP, they use that ... you can make it so it doesn't use a valid shell, so they can't log in (i.e. SSH) ... at least that's how it is for proftpd ...
3. can't really help on that one, don't have USB probs myself ...
4. you'd run the chown command, as root, in a terminal window ...

---

### Post by notaloafer on 2007-07-01
> **scxtt said:**
> 1. i don't personally use screen locks (or a screensaver), my cat doesn't touch my computer and he's the only one there when i'm not ... i was using xlock but it seemed pointless ...
2. you can create normal linux user accounts and when a person who knows the creds for one of those accounts accesses your FTP, they use that ... you can make it so it doesn't use a valid shell, so they can't log in (i.e. SSH) ... at least that's how it is for proftpd ...
3. can't really help on that one, don't have USB probs myself ...
4. you'd run the chown command, as root, in a terminal window ...

1: So screen locking doesn't really matter? Sounds good to me.
2: I don't know much about SSH (I have heard of it) how would I go about doing that?
3: Ok :P
4: Issue fixed. Thanks!

---

### Post by scxtt on 2007-07-01
1. well, it only matters if there's physically someone there you don't want on your box ...
2. ssh is "secure shell" - basically telnet v2, at least conceptually - you can securely log onto any box running an SSH server and remotely administer it ... it's great :) ... you can install it via **sudo aptitude install openssh-server**.
3. ;)
4. awesome :D

---

### Post by notaloafer on 2007-07-01
> **scxtt said:**
> 1. well, it only matters if there's physically someone there you don't want on your box ...
2. ssh is "secure shell" - basically telnet v2, at least conceptually - you can securely log onto any box running an SSH server and remotely administer it ... it's great :) ... you can install it via **sudo aptitude install openssh-server**.
3. ;)
4. awesome :D

1: Well I was thinking of it as a extra layer of security with VNC, it's not too important at the moment (Trying to launch my server! :P). I'll just disable VNC for now until I can secure it.
2: I installed it... now what do I do.... *dumbfounded* lol.

I also know that SSH is a great layer of security to add to VNC's crappy authentication, I just have no idea where to start.

---

### Post by scxtt on 2007-07-02
1. i'm not sure if screensavers start when using VNC ... the point of a screensaver is to save your physical screen, which is now controlled by the computer you're sitting at ... if you want to lock a vnc session, either lock your current computer or close the client, you can connect to it later just as you left it ... you can use x11vnc which will share your :0 connection, but you're probably spawning new :1, :2, :3, etc. connections ...
2. well, if you're sitting at your physical box, you don't need to do anything ... if you're (far) away from your box, even in the other room w/ another PC, you can now connect to your box ... so when i'm at work, i can ssh into my box in my apt and do whatever i choose ... you just need a ssh client (installed by default in *buntu, can use putty in windows) ...

you can also use VNC+SSH to create an encrypted tunnel for VNC to travel over ...

---

### Post by notaloafer on 2007-07-02
Also with vsftpd can I have multiple user directories? Before with my old server a single login could point to say
/var/www/public

and also
/var/private/

All with just a single login... does that sound like it could work with vsftpd?

---

### Post by scxtt on 2007-07-03
standard linux permissions should apply ... i've not used vsftp, just proftpd, but you'll probably be more concerned w/ locking people OUT of directories (ones that "other" have read permissions on) then letting them in ... most likely your users will login w/ their accounts on your box, then be in /home/$USER ... from there they'd navigate to where your files are - i'm sure you could even use symbolic links in their home directories to make it easier on them ... but any standard GUI ftp client should be able to navigate things ...

actually, you can use SSH (also includes sFTP [secure FTP]) to allow people to get/put files on your box ... they'd just need a client that can make connections like that --> filezilla can, and i'm sure a bunch of others can too - putty even offers one ...

so if you don't have a specific reason to use FTP, other than you want to get/put files - sFTP might be an easier option for you ...

---

### Post by notaloafer on 2007-07-03
> **scxtt said:**
> standard linux permissions should apply ... i've not used vsftp, just proftpd, but you'll probably be more concerned w/ locking people OUT of directories (ones that "other" have read permissions on) then letting them in ... most likely your users will login w/ their accounts on your box, then be in /home/$USER ... from there they'd navigate to where your files are - i'm sure you could even use symbolic links in their home directories to make it easier on them ... but any standard GUI ftp client should be able to navigate things ...

actually, you can use SSH (also includes sFTP [secure FTP]) to allow people to get/put files on your box ... they'd just need a client that can make connections like that --> filezilla can, and i'm sure a bunch of others can too - putty even offers one ...

so if you don't have a specific reason to use FTP, other than you want to get/put files - sFTP might be an easier option for you ...

sFTP does sound nicer. I'm not looking for anything fancy for FTP servers; all I need is the ability to have multiple users having permissions to certain directories ONLY! (I don't want them to be able to browse the entire system :P). All I use FTP for right now is so the people hosted on my sites can update their files. nothing more nothing less... would you suggest sFTP? I installed SSH before so I should already have it right?

THanks
-Eric.

---

### Post by notaloafer on 2007-07-03
Oh! I'm starting to like the FTP server you mentioned that you used.. (proftpd). I found a alternate called GPROFTPD that looks like it gives me EXACTLY what I want with a graphical user interface... sound good?

Thanks
-Eric.

PS- I installed it and I LOVE IT! As far as creating user accounts for every person I want to be able to FTP and setting them to the right "home" directory, is that going to be a security risk at all? I can't browse the files of my system remotely (except the ones that the permissions applied to). So does that mean that's set? Basically I don't want these user accounts (The FTP accounts) to be able to login to the local machine at all! That's the security risk I'm talking about.

Double thanks
-Eric.

---

### Post by scxtt on 2007-07-03
if you can't "trust" your ftp users,  then it's a "security risk" any way you slice it ... you can use the UNIX permission structure to keep people out of directories/files you don't want  them in ...

as an example,

d[color=red]rwx[/color][color=green]rw-[/color][color=blue]r--[/color] = directory; [color=red]read/write/execute permissions for owner[/color]; [color=green]read/write permissions for those in the same group as the file[/color]; [color=blue]read permissions for "others" (i.e. anyone who's not the owner or in the group)[/color] ...

you can use this structure to allow/disallow any users you want ... if you want, make an "FTP group" and assign users to it then give them the permissions you want ... all you really have to "worry" about is the permissions for "other" ...

honestly, using FTP is just another layer of configuration if you've got sFTP (via SSH) installed, running if you don't want them getting a shell login, you can set their shell to /bin/false ... i think the only real advantage you'd have w/ FTP is that there are a lot of connect clients available since it's kind of a legacy protocol ...

---

### Post by notaloafer on 2007-07-03
so as far as /bin/false I'd set this as their shell directory via user manager? I'm going to go with that :P

Thanks so much for all your help, its not that I don't trust my FTP users its just I don't want them tempted to mess with system configuration. Just making sure they don't have access to do that :P

-Eric.

---

### Post by scxtt on 2007-07-03
they really shouldn't anyway ... your system will be pretty locked down by default ... nothing "system configuration" wise can be **edited/saved** by anyone w/o root access (either directly or via sudo) ... people may be able to look @ the files, but they can't do anything to them ...

basically, if you've got a txt file that has REALLY IMPORTANT info in it, make sure your user is the only one w/ read/write/execute permissions, then you don't have to worry ... unless you've got an A-hole of an admin who isn't trustworthy ...

just make sure their entry in /etc/passwd is something like:
```
postfix:x:110:119::/var/spool/postfix:/bin/false
```

---

### Post by notaloafer on 2007-07-03
Well I sure hope I'm not a A-Hole then :P:P

---

