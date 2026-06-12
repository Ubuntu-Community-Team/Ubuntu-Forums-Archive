---
title: "Username and password in login screen"
date: 2016-02-29
forum: Server Platforms
---

### Post by kambiz2 on 2016-02-29
Hi everybody,
I've installed Ubuntu 14.04.02 LTS server. I want to write username and password in the login screen.
I'm trying to know with desktop I have to install:
- i've tested with gnome: I haven't found how to do it
- I've tested with lightdm: it says that username and password are not correct. It's a loop
- I've tested with gdm: same thant lightdm
- finally I've tested gnome + lightdm. The first time it says that username and password are incorrect. But you execute mv .Xauthority .Xauthority.bak and then it works.

My question is: is there anyway to install only one desktop?
Thanks very much

---

### Post by MAFoElffen on 2016-02-29
Ubuntu Server has no gui (XServer), no desktop manager (so no Unity, KDE nor Gnome), and since none of that, no graphical Login Manager (not lightdm, xdm, nor gdm). It is console based.

Do you want a graphical desktop? If so, curiosity prompts me to ask why you didn't start off with installing a desktop edition?

To install a desktop onto Ubuntu core...

For Unity
```

sudo apt-get install ubuntu-desktop

```
For Gnome: 
```

sudo apt-get install gnome-shell ubuntu-gnome-desktop

```
For Xubuntu
```

sudo apt-get install xubuntu-desktop gksu leafpad synaptic

```
For Lubuntu
```

sudo apt-get install lubuntu-desktop

```
For Mate
```

sudo apt-get install mate-desktop

```

Any of those would install a full (heavy) suite of the desktop flavor you want, and all their related suite applications.

Now if you wanted to just install a minimal desktop, then you would install XServer, your choice of desktop environment, and your choice of graphical login manger (in that order).
There are many choices. (way more choices than what I listed above...) That is what Linux is about.

---

### Post by kambiz2 on 2016-03-01
Thanks very much for your answer. I only work under Windows environment, because of my knowlegde easier to begin than Linux. But one year ago I configurated Owncloud under Windows Server, but nowadays there is no support. For this reason we decided to configurate a Linux Server and install Owncloud here.
Now, the server is working fine but I want to arrange some the details I dont'l like. One of this is to remove the list users of the login screen. I've installed gnome desktop and kde-plasma-desktop, for remot desktop. I don't like the idea of installing a desktop in the server, but it's possible to use remote desktop and owcloud without desktop?
Thanks again MAFoElffen

---

### Post by SeijiSensei on 2016-03-01
Do you want just to remove the users from the login screen, or do you want to remove them entirely?  For the latter, use SSH to connect to the server, then run

```
sudo nano /etc/passwd
```

and delete the lines corresponding to the users you want to remove.

---

### Post by MAFoElffen on 2016-03-02
@SeijiSensei 

Wait ... Really? There is a shadow file that sync's with that file... wouldn't that get out of sync, besides messing with permissions that had that user as owner?

I've always used the command "userdel" (in Debian branch Linux) or "deluser" (rhel branches)... Which deletes the whole account and handles directories and other background wiring.

You say just manually deleting one line from one file causes no orphans / no problems?

...Just asking.

EDIT--
@ the OP:
My son followed me and his grandfather into IT. He is a System Engineer who manages  Server Farm of over 200 Windows Servers via using ssh with them, all Windows Server Core (no GUI). Even M$ now realizes that a GUI takes resources and sometimes opens up vulnerabilities. (especially in a remote desktop) If you do need a GUI, have you considered a instance load of a minimal X through an ssh tunnel?

Does your server have a BMC console interface?

---

### Post by mastablasta on 2016-03-03
> **kambiz2 said:**
> 
Now, the server is working fine but I want to arrange some the details I dont'l like. One of this is to remove the list users of the login screen. I've installed gnome desktop and kde-plasma-desktop, for remot desktop. I don't like the idea of installing a desktop in the server, but it's possible to use remote desktop and owcloud without desktop?


there is no need for remote desktop. if you want to administer the server via GUI then use a web GUI instead. Have a look at Zentyal or the very light Ajenti for that. Many also use Webmin. There are also many others available around in the web.

---

### Post by MAFoElffen on 2016-03-03
+1. I agree with mastablasta.

Especially with a "Server." there is a difference between remote administration and Remote Desktop. IMHO- Remote desktop adds a layer of vulnerabilities to a server that needs to be handled. You say it is okay for your server to be remote controlled. Now how to protect that. 

It also adds quite a network load in how RDP transfers the graphics of the desktop. Not that his network is going to be max'ed out, but most then complain about the lag and response time. I do. When I am forced to, I notice my network load goes way up and the effects are far reaching (affecting other nodes). I'm used to lag in remote app's, but when it affects the performance of other nodes, then I have to think about that.

But-- The way the OP worded his original post, I answered, but ... I had to ask him to clarify what he wanted and why he did not just originally install a desktop edition. The one main question left unanswered is "what Server Services he needs provided?" Basically, what job it is going to have in what environment... Some people do not know that you can install server services to desktop edition. (If that is it's main purpose/role.) Because if they are not familiar with Linux, then that is a new concept.

---

### Post by SeijiSensei on 2016-03-03
> **MAFoElffen said:**
> @SeijiSensei 

Wait ... Really? There is a shadow file that sync's with that file... wouldn't that get out of sync, besides messing with permissions that had that user as owner?


The user accounts reside in /etc/passwd.  Back in the hoary Unix past that file would also contain the encrypted passwords.  Since /etc/passwd needs to be readable by all users, that was an obvious security hole.  So the passwords themselves now reside in a file called /etc/shadow.  Active users are ones with an entry in /etc/passwd, so you can delete inactive users from there.  There will still be the encrypted password hashes in /etc/shadow for these users, but they won't be able to log in since they don't have an account in /etc/passwd.

If you want to delete all traces of a user you'd need to delete the record from /etc/shadow and use "sudo rm -rf /home/username" as well.  I have a number of entries in /etc/shadow that do not correspond to any active users.  Linux doesn't care.

---

### Post by MAFoElffen on 2016-03-04
Just me... I mentioned the sync of the shadow file and my other concerns of ownerships. Maybe you are right, just showing my age...[URL="http://manpages.ubuntu.com/manpages/hardy/man8/deluser.8.html"]

Ubuntu man deluser[/URL]:
> 
**      deluser** and **delgroup** remove users and groups from the system according to command line options and configuration information in _[/etc/deluser.conf]("file://etc/deluser.conf")_ and _[/etc/adduser.conf]("file://etc/adduser.conf")_. They are friendlier front ends to the **userdel** and **groupdel** programs, removing the home directory as option or even all files on the system owned by the user to be removed, running a custom script, and other features.  **deluser** and **delgroup** can be run in one of three modes...

Good to know your way works for you.

---

### Post by SeijiSensei on 2016-03-04
I use utilities like adduser, but I often edit /etc/passwd and /etc/group directly to make changes to the user accounts.

---

