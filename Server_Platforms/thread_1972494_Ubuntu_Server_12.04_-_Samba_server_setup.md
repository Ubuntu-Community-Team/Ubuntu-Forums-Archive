---
title: "Ubuntu Server 12.04 - Samba server setup"
date: 2012-05-03
forum: Server Platforms
---

### Post by ranger12 on 2012-05-03
Hello everyone, I just downloaded and installed Ubuntu 12.04 server to play around with and have created a home network with the server, my desktop system which is running 12.04 Desktop edition and a wireless 4 port router(Westell 7500). Both machines are wired into the router - not wireless. I had no problem installing the server. I am trying to learn how to set up samba on the server so I can just have a user logon and go to their home directory setup for them on the server. Creating a user account and samba account was not a problem. I just have not been able to figure how to set up the smb.conf file to have them logon and see their particular home directory on the server. I can logon to the server just fine using SSH and I don't need to do by Samba but I would like to learn how to configure it to do so. I have figured out how to create a single share on the server and make it accessible to anyone from within nautilus on my dekstop - what about user logins on my desktop for user's home directories on the server? I will attach what I have butchered in my smb.conf on the server. I made a copy of it to smb.txt so I could attach it. Apparently *.conf files as post attachments are a no-no.:) I wonder if someone can point me to a really good tutorial somewhere I can look at myself. I have been poking around various places on the internet.

---

### Post by bab1 on 2012-05-03
You have everything set up.  This is what you have (minus the # comments)```
[homes]
   comment = Home Directories
   browseable = no [COLOR="Red"]<- you can't browse to the share[/COLOR]
   read only = no [COLOR="Red"] <-- This makes the share capable of rw[/COLOR]
   create mask = 0700    [COLOR="Red"]< -- this makes the the files rwx[/COLOR]
   directory mask = 0700 [COLOR="Red"]<-- This makes the directory traversable and rw[/COLOR]
   valid users = %S  [COLOR="Red"]<-- The user must have a Ubuntu and a Samba account[/COLOR]
```

You should be able to use [COLOR="Red"]**cntl+l (ell)**[/COLOR] in nautilus to open a location bar.  In hat bar can use smb://server/user_name and the home directory for that user should appear.  [COLOR="Red"]*(I Edited the part in red part as I mistyped it earlier).* [/COLOR]

If the share is not browsable you must know your login and the server name (you can substitute the IP address for the server name).

[COLOR="Blue"]Edit: [/COLOR]This assumes that the username on the client is the same as the user on the server (and the samba user).

---

### Post by drdos2006 on 2012-05-03
Have a look here
[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)

and 


Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by ranger12 on 2012-05-03
Bab1 - thanks! That worked perfectly with the location bar. I have a follow up question - is there a way when a user logs on to the desktop client to login to the server and than mount their user directory automatically in nautilus with a login script placed in the appropriate place or is that not supported?

---

### Post by bab1 on 2012-05-03
> **ranger12 said:**
> Bab1 - thanks! That worked perfectly with the location bar. I have a follow up question - is there a way when a user logs on to the desktop client to login to the server and than mount their user directory automatically in nautilus with a login script placed in the appropriate place or is that not supported?
It should be able to be scripted, but you might try bookmarking it first.  The command from the terminal is ```
nautilus smb://server/user_name
```

On second thought; what type of client are we talking about.  Linux or Windows or...

If this was a Linux client I would mount the share at bootup using *fstab*.  No muss or fuss.  The directory is available transparently when the user clicks on an icon.  This I have written a script for.  The user is even prompted via the GUi.

---

### Post by ranger12 on 2012-05-03
It is Ubuntu 12.04 Desktop on the client.

---

### Post by ranger12 on 2012-05-03
Can you script when a user logs in to their account on the desktop to dynamically mount their share and I supply their server user name and password to log in to that share transparently? The logon script would than be stored in the home directory on the desktop client. Doable or not? I need to do some research on login scripting.

---

### Post by bab1 on 2012-05-03
> **ranger12 said:**
> Can you script when a user logs in to their account on the desktop to dynamically mount their share and I supply their server user name and password to log in to that share transparently? The logon script would than be stored in the home directory on the desktop client. Doable or not? I need to do some research on login scripting.

Sure it's doable.  The login script is the easy part.  You need to create a mount point and prepare fstab to create a mount the CIFS file system when asked to.  Then the script just invokes a command similar to```
mount -t cifs //server/login /mount/point
```

Things to read```

man fstab
man mount
man mount.cifs
```

Google for bash scripting to get a feel for that.

I assume you are using local users on both hosts (computers).  It would be nice for you to keep the username=uid consistent across both hosts.  You can check what you have with ```
getent passwd
getent group
```

Of course you can read about getent with```
man getent
```

---

### Post by ranger12 on 2012-05-04
Thanks for the ideas. I will do some research on bash scripting. I am planning on keeping the usernames the same on the client and the server. I will check out those manuals as well. As a side note, I also have setup and configured NFS on both machines which gives me now 3 ways to access the server from the desktop - SSH,NFS and Samba. It will be a great learning tool for basic Linux networking.

---

### Post by bab1 on 2012-05-04
> **ranger12 said:**
> I am planning on keeping the usernames the same on the client and the server. The username needs to be paired with the uid.  For example, here the user ***egb*** uid is 1004.  If on another host the user is 1002 there are problems ```
egb:x:[COLOR="Red"]1004[/COLOR]:1004:,,,:/home/bab:/bin/bash
```

For small networks you can manually control this.  In larger networks user management should be centralized (e.g LDAP or NIS).

---

### Post by ranger12 on 2012-05-05
Okay. I misunderstood. I will check that but I believe they do match.

---

### Post by ranger12 on 2012-05-09
I have just decided to bookmark it in nautilus and told it to remember the password forever. I did the same thing with the user accounts for my 2 nephews and niece on the workstation. The bookmark says smb when they first logon to their acount on the workstation until they click it and then it connects to their home directory on the server and t hen says "xxxx" on "xxxxx". I explained that to them so I believe I will stick with that instead of trying to dynamically login/map their server home directories when they logon to the workstation. I am content with that since right now their is only one workstation on this network.

---

### Post by ranger12 on 2012-05-11
Okay I have finally stumbled onto the solution and it works pretty well so far - autofs. I have it setup and working on the client machine and mapping their home directories off the server. :)

---

