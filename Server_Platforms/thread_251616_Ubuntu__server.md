---
title: "Ubuntu  server"
date: 2006-09-05
forum: Server Platforms
---

### Post by dareofficer on 2006-09-05
Hello, I have Ubuntu installed on a computer  I have only for files share.  I can access that fine with my ubuntu box.  How do I use this to file share with my PC/Mac systems?  I want to save all my documents/files/music to the server.  I can http into it fine with Apache, but I can't connect via ssh like I do with my Ubuntu desktop.

Thanks

---

### Post by kidders on 2006-09-05
Why can't you SSH into your Ubuntu box? Can you even ping it?

Filesharing with OSX *and* Windows leaves you with only one option: Samba.

---

### Post by dareofficer on 2006-09-06
How do I connect via ssh with OSX???  I can with Linux no problem.  I can't with Windows or OSX, nor do I know how.  I have tried some SSH clients, but they are no good.  I can move small files but not large ones.

---

### Post by kidders on 2006-09-06
The sizes of the files shouldn't make any difference, unless your network connection is faulty.

Gaining SSH access to a computer is done the same way on every operating system, with the exception of windows ... **ssh hostname** or **ssh user@hostname**.

On Windows, puTTY is a perfectly good (and very small) SSH client. Of course, you could always throw on Cygwin (or a similar app) and emulate a full-blown Linux environment in Windows if you prefer.

One observation worth making is that SSH is an abominably inefficient way of transferring data around a private LAN. All that encryption and decryption *really* takes its toll on throughput!

---

### Post by dareofficer on 2006-09-06
I have noticed that the internet speed is very weak on the switch at this station.  I bet I have a bad cable. 

I do have putty, can I use that in s gui format?  If not how would I move a file from PC to Linux?  Sorry I'm still new to this but I print off all the things all of you help me with.  Thanks again for the help.  I'm just a dumb cop, trying to learn.

Berlin

---

### Post by kidders on 2006-09-06
No worries :-) I think I'd better explain my last post a bit better though!

Basically, SSH is intended to allow users to log into a machine remotely, in a highly secure way. Other uses include doing advanced tricks with things like file transfers or encrypted tunnelling of services such as X. It is **not** suitable for filesharing on a private LAN.

When possible, people prefer to use more flexible protocols that are designed specifically for the purpose of sharing files. Windows filesharing and AFS (Apple filesharing) are two examples.

So, unless you have a very specific reason for using SSH the way you describe, I would use Samba, a Windows filesharing app for Linux. (Macs also use it for Microsoft compatibility.) Involving SSH in any way very dramatically affects performance, and should only be considered where security is a big issue.

Is there a reason why you wouldn't like to use Windows' and OSX's built-in features for filesharing?

---

### Post by dareofficer on 2006-09-07
No, I would rather use samba.  I have tried, and failed.  How do I use samba?  It does not show the linux server.  I have Linux Ubuntu 6 server installed.  I want to be able to use a gui to connect to it.  I can connect in terminal, but I have no clue as to moving files in terminal.

Thanks

---

### Post by Iowan on 2006-09-07
Is Samba server installed/running?  **ps ax** should show one or more instances of **smbd** (and/or **nmbd**)
Perhaps it would help to post the **/etc/samba/smb.conf** file.

---

### Post by LeeVee on 2006-09-08
What I would suggest is the following;

Firstly, get the latest modules and compiling software;
1) apt-get update
2) apt-get upgrade
3) apt-get install build-essential
Then, get a great Remote GUI control panel called Webmin, with which you can setup your whole server/services/networking/file-sharing, etc from a remote terminal on your network;
4)apt-get install ssh
5)wget [http://prdownloads.sourceforge.net/webadmin/webadmin-1.290.tar.gz](http://prdownloads.sourceforge.net/webadmin/webadmin-1.290.tar.gz)
6)gzip -cd webmin-1.290.tar.gz | tar xvf -
7)apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
8)cd webmin-1.290
9)./setup.sh

It's now all setup!

You can navigate to your webmin page on the server from any PC on the network, by going to [https://xxx.xxx.xxx.xxx:10000](https://xxx.xxx.xxx.xxx:10000) in your internet browser, where xxx.xxx.xxx.xxx is your IP address of your cubit server.

Now you have full control and easy setup for all your server functions.
To share files on your Windows network, just go to servers, and then samba. If it says you don't have samba installed, it can be installed from there. It's easy to setup and find your way around - just remember to make the workgroup name the same as your windows workgroup and set up users and shared folders for the users.

Hope that helps - have fun!

-Lee

---

### Post by dareofficer on 2006-09-09
Thanks, I have it installed now. Could you give me a quick reference on how to set it up to file share?

---

### Post by kidders on 2006-09-09
Great news :-)

Assuming you've done an **apt-get install samba**, take a peek inside your **/etc/samba/smb.conf**.

The first thing to note is that samba treats shares called "homes" differently. Having a **[homes]** section in your smb.conf will let each user on your Ubuntu box access his home directory via **\\servername\username** from a windows box.

Global shares are done similarly ... start a section called, say, "movies" and add some directives that reflect how you'd like it to work. There are hundreds to choose from, but you can learn about all that once you're up and running!

```

[movies]
writable=no
path=/opt/movies
comment=My Movie Collection
browseable=yes
guest ok=yes
write list=root

```

Now, restart your samba service, wait a few minutes for your network to realise your Ubuntu box is there, and open your network neighbourhood for a look around.

In theory, it *should* be that simple!

---

### Post by dareofficer on 2006-09-14
I have it showing up, however when I try to enter a name and password, it does nothing.  Is there a default password?:roll:

---

### Post by kidders on 2006-09-15
Nope. Perhaps I should explain:

Samba can do all sorts of things with authentication. You *could* for instance install an LDAP server and set up an Active Directory sort of thing to control authentication on several samba installs for extremely large numbers of users. However you probably won't be interested in doing anything complicated.

The most straightforward thing to do is to provide samba with its own list of users and passwords. Many people find that kinda stupid, since your Linux box already has a nice, secure user/password list stored elsewhere ... but this way is just easier :-P

If memory serves, pick a username and type:
```
sudo smbpasswd username
```

Type your "sudo" password, then one for samba (twice). You should then be able to use that user to access fileshares. It's usually smart to keep samba's usernames consistent with those of "real" users on your system, so they can access their home directories more easily. If you don't do so, you'll only wind up having to map fake usernames to real ones later.

I hope that helps.

---

### Post by mike3k on 2006-09-15
I find NFS to be the best option for file sharing between Macs & Linux. File copying speed to NFS volumes are much faster than SMB, and NFS is more robust. NFS shares will automatically reconnect when your machine wakes up from sleep, but SMB shares won't.

---

### Post by hkgonra on 2006-09-15
Is there a way to set samba uo to where it doesn't need any type of login ? I would love to set it up at home with just simple file sharing like windows has. I don't want everyone in the house to have to login to access the family's shared files.

---

### Post by kidders on 2006-09-16
> Is there a way to set samba up to where it doesn't need any type of login ? I would love to set it up at home with just simple file sharing like windows has. I don't want everyone in the house to have to login to access the family's shared files.

Samba works exactly the same way as "real" Windows filesharing does ... if you protect a share with a password, one will be asked for.

*Not* setting passwords is not to be recommended, but there's no reason your users can't cache them in their password managers, so they *appear* to have password-free access. If you really do want to remove fileshare protection, you can tell samba to make your shares public.

> I find NFS to be the best option for file sharing between Macs & Linux

Perhaps Apple's own filesharing protocol is worth considering, too? It has some nice features that appeal to some people, like mDNS-based share advertising and virtual server support.

---

