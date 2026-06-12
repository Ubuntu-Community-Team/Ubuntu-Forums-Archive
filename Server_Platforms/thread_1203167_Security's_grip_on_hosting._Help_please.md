---
title: "Security's grip on hosting. Help please"
date: 2009-07-03
forum: Server Platforms
---

### Post by mentorkyrom on 2009-07-03
So I am uber noob with ubuntu and pretty much with linux too, but every couple of years I try to mess with a new distro to see whats changed, and I really like ubuntu. Anyways I run a forum and we've decided to look into the possability of hosting one out of a box of our own and stick on friends businesses t1 line.

Onto my problems, 

1) I decided to go with Ubuntu-Server (latest version) 32 bit and installed the EHCP hosting control panel. I really like it and it makes it really easy but I'm running into some security problems. For instance the FTP users EHCP makes seem to have no permissions, I can connect via FTP but I cannot CHMOD files or directories, nor can I create new ones. In fact I couldn't do a manual install of SMF (forums) until I manually (server side) logged in and changed the properties on the files and folders that I needed too. which leeds me to my next question.

2) Is there a way to create an FTP user outside of the EHCP control panel that could have access to the entire hosting root (/var/www/) ?

3) other than using sudo commands, and gksudo nautilus; is there any way to graphicly be logged into as root so that I can change and modify files freely?

I am a mostly a windows user (sorry) so please speak lin-noob for me. I appreciate all the work done here at Ubuntu and you guys have made a fantastic and pretty user friendly distro of linux, and I understand the strict security but it just seems a little overwhelming at first I suppose. 

Thanks for any help provided.

-Brandon

---

### Post by doas777 on 2009-07-03
1/2) is it you, or your clients that will be accessing the ftp? how about using ssh/sftp instead of ftp? then you can get secure access to the entire file system if you like. you can connect to sftp with winSCP ( [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) ) from windows, or just put 'ssh://server' into a nautilus address bar to access it. ssh is a pretty simple install, if you can deal with a touch of CLI.

3) you won;t find instructions for running as root on these [forums]("http://ubuntuforums.org/showthread.php?t=716201"). I urge you to check this out: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), as sudo really is an elegant solution to the problem at hand.

---

### Post by mentorkyrom on 2009-07-03
appreciate the quick response.

In response to your question it is me and only me that will be accessing anything either on the control panel or FTP, or even the server itself for that matter. 

Regarding 1) I will look into that winscp. I assume SFTP is already part of ubuntu? Or is it something I would have to install on the server. Is it something that I need to configure?


Thanks again!

---

### Post by windependence on 2009-07-03
There should be nothing for you to set up for sftp. WinSCP connects to your server just like an ssh connection. 

I would suggest even though you say you are a "windoze" guy, that you learn at least some command line as it could save you from much trouble at some point. Linux is a command line driven OS, and especially with the server version, it's essential you know at least some CLI even if you load a GUI.

-Tim

---

### Post by mentorkyrom on 2009-07-03
right on I just figured out the winscp thing just now. Its funny cuz you think "Wait, it cant be this easy..." but it is :)

and I am trying to learn, in the past 48 hours i've learned

sudo 
gksudo 
get-apt
mk
mkdir
rm
rmdir

. Googles pretty cool about helping me search on linux commands. I appreciate your responce, and using that winscp will be great now!

---

### Post by mentorkyrom on 2009-07-03
actually that didn't work


So I'm logged  through winSCP and Im trying to make a new folder with permissions 0755. (another question can I even set things to 777?)

But I get an error message when trying to make the folder "temp"
Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 14

---

### Post by windependence on 2009-07-03
Good deal. The more you use the commands, the easier it will be to remember them.

You can also use sftp in a Linux browser such as Konqueror. Just use sftp://xxx.xxx.xxx where the x is the IP of the server you want to connect to. You will be able to browse the other system if you have the proper permissions.

BTW, it's great to see someone new to the OS enthusiastic about learning the CLI instead of spurning it. Linux is command driven, and you know what they say, when in Rome, do as the Romans do. 

Good luck!

-Tim

---

### Post by windependence on 2009-07-03
> **mentorkyrom said:**
> actually that didn't work


So I'm logged  through winSCP and Im trying to make a new folder with permissions 0755. (another question can I even set things to 777?)

But I get an error message when trying to make the folder "temp"
Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 14

The user you are logged on as probably doesn't have the authority to what you are trying to do. You can change that in the sudoers file.

-Tim

---

### Post by mentorkyrom on 2009-07-03
Ok, dont make fun of me but I think I know why.

In the bad habbit of "rushing to do things" I changed the owner of the folder "Packages" in my hosting directory to www- rather than root as the owner. Would this be why I dont have permissions to do that now?


EDIT:

Yea, changing the owner back to root resolved that issue.


But Im still having problems with my SMF forums saying I do not have permissions.

I noticed the packages and what not that I upload using SMF get save under the user www- and I cannot change them using sFTP even?

I just wanna set the directory /var/www/vhosts/...folders.../packages to be 777 and have that hold dir be 777 no matter who uploads it. 

It seems like every time something else makes a folder or file Ubuntu locks it down?

Again, I appreciate the help.

---

### Post by mentorkyrom on 2009-07-03
Although it's fun learning, I'd almost pay to have something set this **** up for me../:lolflag:

---

### Post by mentorkyrom on 2009-07-03
shamless bump...

---

### Post by doas777 on 2009-07-03
> **mentorkyrom said:**
> Ok, dont make fun of me but I think I know why.

In the bad habbit of "rushing to do things" I changed the owner of the folder "Packages" in my hosting directory to www- rather than root as the owner. Would this be why I dont have permissions to do that now?


EDIT:

Yea, changing the owner back to root resolved that issue.


But Im still having problems with my SMF forums saying I do not have permissions.

I noticed the packages and what not that I upload using SMF get save under the user www- and I cannot change them using sFTP even?

I just wanna set the directory /var/www/vhosts/...folders.../packages to be 777 and have that hold dir be 777 no matter who uploads it. 

It seems like every time something else makes a folder or file Ubuntu locks it down?

Again, I appreciate the help.


I don;t see any reason that you couldn;t set it to 777 with chmod, and leave the owner as is. doesn't that work? also what user is your hosting daemon running as? 
```
ps -ef | grep <processname>
```

overall it doesn't seem like a good idea to use 777 on a web accessible directory (or really any other). does your forum software have any instructions?

one peice of advise, is to create a new thread for the specific issue you are encountering now. you have a much better chance of attracting a knowledgable person with experience on the software in question, if your thread title includes it.

good luck

---

### Post by windependence on 2009-07-04
SMF requires certain files to be 777 but my experience is you can get by with 775 which is much better. I would avoid making any file world writable if you can avoid it.

-Tim

---

### Post by windependence on 2009-07-04
> **mentorkyrom said:**
> Ok, dont make fun of me but I think I know why.

In the bad habbit of "rushing to do things" I changed the owner of the folder "Packages" in my hosting directory to www- rather than root as the owner. Would this be why I dont have permissions to do that now?


EDIT:

Yea, changing the owner back to root resolved that issue.


But Im still having problems with my SMF forums saying I do not have permissions.

I noticed the packages and what not that I upload using SMF get save under the user www- and I cannot change them using sFTP even?

I just wanna set the directory /var/www/vhosts/...folders.../packages to be 777 and have that hold dir be 777 no matter who uploads it. 

It seems like every time something else makes a folder or file Ubuntu locks it down?

Again, I appreciate the help.

Well this is not all bad at all. Locking down is good, especially on a forum. If you want to change perms on a file and you have access to the physical box, use sudo to gain enough access like this:

```
chmod 775 filename
```

-Tim

---

