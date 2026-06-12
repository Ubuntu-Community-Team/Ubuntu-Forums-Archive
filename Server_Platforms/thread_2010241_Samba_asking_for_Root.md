---
title: "Samba asking for Root"
date: 2012-06-25
forum: Server Platforms
---

### Post by boab2791 on 2012-06-25
I have just taken my first steps in setting up my new 40th Birthday Pressie, an HP Proliant Micro-server to run Ubunut Server 12.04 Server.

My main aim is to replace my slow ReadyNas DUO with this new server running predominantly as a File server.

I have installed the server cd and chose the File Server Package. I have installed the Graphical Samba Component using Terminal. I have also installed the Unity Desktop as command line stuff is still a bit beyond me.

When I access the Samba GUI it asks me for a password, it does not like my one and only user password and also does not like it being blank. If I understand correctly what I have been reading doing various Google searches the root user is locked on Ubuntu and has either no password or one unknown to the system admin!

I have reinstalled the server from scratch with no change, samba keeps asking for a password from the GUI and I have no idea how to try it from command line.

Any help for this complete noob would simply be astounding and gratefully accepted.

---

### Post by bab1 on 2012-06-25
> **boab2791 said:**
> I have just taken my first steps in setting up my new 40th Birthday Pressie, an HP Proliant Micro-server to run Ubunut Server 12.04 Server.

My main aim is to replace my slow ReadyNas DUO with this new server running predominantly as a File server.

I have installed the server cd and chose the File Server Package. I have installed the Graphical Samba Component using Terminal. I have also installed the Unity Desktop as command line stuff is still a bit beyond me.
From a practical standpoint you are better off installing Ubuntu 12.04 Desktop.  In small LAN installations you won't see any difference, It appears the hardware you are using is good enough to run the desktop anyway.

I run Ubuntu 12.04 server on an old P3 with 256MB of RAM with Samba and it works fine.  I also run Samba on my Desktop which is a Core 2 Duo with 8GB of RAM.  I don't see any appreciable difference.  The real load is disk I/O and both of my machines have fast SATA II hard drives.  
> 

When I access the Samba GUI it asks me for a password, it does not like my one and only user password and also does not like it being blank. If I understand correctly what I have been reading doing various Google searches the root user is locked on Ubuntu and has either no password or one unknown to the system admin!
This could be due to applying the Desktop environment on the Server distro.  I'm not saying this is 100% the reason, but others have complained enough for me to recommend installing the Desktop from the start> 

I have reinstalled the server from scratch with no change, samba keeps asking for a password from the GUI and I have no idea how to try it from command line.

Any help for this complete noob would simply be astounding and gratefully accepted.
Once you have the Desktop version installed its really quite simple.  You can follow [**_[COLOR="RoyalBlue"]this howto[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590") for the basics.  I don't recommend placing the shares in a home directory in a NAS situation.  I will help you set up the basics and also the shares correctly if you wish.

---

### Post by jlittle on 2012-06-25
> **boab2791 said:**
> 
I have installed the server cd and chose the File Server Package. I have installed the Graphical Samba Component using Terminal. I have also installed the Unity Desktop as command line stuff is still a bit beyond me.

When I access the Samba GUI it asks me for a password, it does not like my one and only user password and also does not like it being blank. If I understand correctly what I have been reading doing various Google searches the root user is locked on Ubuntu and has either no password or one unknown to the system admin!


Never bothered with a gui to setup samba the config file it not to difficult and well commented. But if your account is an admin then that should be the one to use. Yes you do not need to enable root, that is what  the command 'sudo' is for.

Again the config file is pretty simple: From a terminal window:
[B]
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup[/B]

(Enter your password at the prompt for **sudo.**Just in case you screw something totally you now have a backup!)

**sudo nano /etc/samba/smb.conf **

You can add a simple share like this at the end of the file
[B]
[sample]
comment = A sample test share
path = /some/path/on/this/server
# This is a comment because of the leading '#'
# Make share browseable from Window's explorer
browseable = Yes
# Allow Windows user write access
writeable = Yes[/B]

(**CTRL + X** to save the file)

For each Windows user add them with their password with command

**sudo smbpasswd *TheUserName***

(TheUserName's password enter for the two prompts)

After add all your users you need to reload the new configuration with your changes:

**sudo service smbd reload**

That's all there is to it. Plenty of good how tos online as well.

HTH

-- 
Jonathan

---

