---
title: "HOWTO: Easy, simple GUI setup of smb file server"
date: 2011-02-11
forum: Tutorials
---

### Post by Cracklepop on 2011-02-11
You want to share files between computers on your LAN?
This is the easiest setup of a file server in ubuntu 10.10 that you will find ;)  (smb for windows compatibility). 

There are tons of other posts and web pages on this, but IMHO most newbies will hate them: they're long, complex, and full of terminal commands and file edits. 

This guide has NO editing of files, and only 1 (one) single OPTIONAL line to type into a terminal. Every single step is spelt out, for the sake of absolute newcomers.  Other users may want to read only the sub-headings.  

Step 1: the core HOWTO - setting up the file server
Step 2: giving your server a static IP address 
Step 3: connecting an Ubuntu client
Step 4: connecting a Windows client




 [SIZE=3]**_ Step 1. Creating an Ubuntu File Server _**[/SIZE]

**1.1: Make a shared folder on the server**
 - locate or create the folder you will be placing your shared files in
 - right-click it, select ''Sharing Options''
 - tick ''Share this folder''
 - I suggest you make the ''Share name'' the same as the folder name
 - tick ''Allow others to create...'' if you want clients to be able to put files onto the server
 - tick ''Guest Access'' to create an insecure server that doesn't need a password (not recommended)
 - ''Create Share''

 Note during step 1.1 you may be asked to allow Samba to be installed, and to allow Nautilus to ''Add the permissions automatically''.  You should allow these if asked.  

**1.2: Create a share user account on server (optional)**
This step is to create a user account on the server.  Clients will use this account when they access the file server.
Note this step can be skipped if you ticked ''Guest Access'' in step 1.1, or if you want to let clients use an already existing user account.
 - go to System > Administration > Users and Groups, click Add
 - give the user account a name (I will use ''sharer'' in this guide), click ok
 - give the user a password, click ok

 **1.3: Create a samba password**
Skip this step if you ticked ''Guest Access'' in step 1.1
 - type this into a terminal: **sudo smbpasswd -a sharer** (note ''sharer'' can be any existing Ubuntu user on the server)
 - you will be prompted for YOUR password (because of sudo) then twice for a new samba password for sharer. 

Note this password does not have any relationship with the Ubuntu password for the ''sharer'' user! You can use the same password if you want, although it would be more secure to use a different one

 That's it. The server is finished.


 [SIZE=3]**_ Step 2. Giving the Server a Static IP Address (optional but recommended)_**[/SIZE]

The server will work fine as is, but if it disconnects and reconnects to your router it may end up with a new IP address, which could be annoying... 
Follow the steps below to give your server a static IP address that won't ever change.

  - to get your gateway's IP address rightclick the network/connection icon in your Notification Area (i.e. ''Task Bar'' for Windows users) and select ''Connection Information'' 
  
You now know your gateway address, which is probably 192.168.1.1  

 You will also need to choose a new permanent IP address for your server.
 It will look like 192.168.1.X, where the first three numbers separated by dots are the same as the first 3 of your gateway and the X is a number between 2 and 254. 
 Your LAN is probably only using a handful of the smaller numbers, so just choose a large number up to 254 that's easy to remember, to insert where the X is. 
 I'm going to use 192.168.1.222 in this example - you can use this too if you like. 

 - go to System > Preferences > Network Connections
 - find the server's active connection to the router, in the appropriate tab, select it and click ''Edit''
 - go to the IPV4 tab
 - change the Method to ''manual''
 - click ''Add'' next to the ''Addresses'' box
 - type your chosen server IP address (''192.168.1.222'') in the Address column
 - type ''24'' (no speech marks) in the Netmask column
 - type the gateway address from above in the Gateway column, and again in the ''DNS Servers'' text box 
 - Apply the changes

 Your server now has a static IP address.


 [SIZE=3]**_ Step 3. Connecting an Ubuntu Client_**[/SIZE]

  - go to Places > Network 
 - you should see the server here and, if you double-click it, the share folder inside it 
 - to open the folder you must enter the username of a user account on the server that has had a samba password created for it (sharer, in this example) and the *samba* password for sharer (NOT sharer's Ubuntu password) 
 - to add the server's share folder to your Places menu for easier access next time, click Bookmarks > Add Bookmark at the top of the window when you are inside the share folder  

**If** you could not see the server in the Network window, do the following: 
[I] - Places > Connect to Server 
 - set Service Type to ''Windows share'' 
 - in the Server field type the server IP address (if you don't know it, then on the *server* rightclick the network/connection icon in your Notification Area and select Connection Information) 
 - click Connect 
 - a window with all the share folders on the server will open; doubleclick the one you want, then bookmark it as above    [/I]

You now have working file sharing between your server and an Ubuntu client on your LAN. 


   [SIZE=3]**_ Step 4. Connecting a Windows Client_**[/SIZE]
  

 XP: Start > MyComputer > MyNetworkPlaces > the shared folder  

 Win7: Start > Computer > rightclick > Add Network Location > follow the wizard prompts

---

### Post by qingpool on 2011-02-14
Uh, thank You! I was wandering when someone would surprise us with a simple to follow guide for 10.10, now that Ubuntu has come a long way and is more Windowsuser friendly..

Additional question - let's say i do this with guest access allowed, but i move my server to another network - what should i change? I remember vaguely that there was a subnet to be specified in smb.conf. Am i right?

---

### Post by pricetech on 2011-02-14
In your step 2 you recommend assigning the IP that you found in the previous step.  This will cause an IP address conflict when the router assigns that IP to another device.  Therefore you need to assign an IP that is outside the pool.

My preferred method is to reserve IPs in my router, which most routers support.

---

### Post by Centaur5 on 2011-02-14
Thanks for posting this howto!  I feel as though file sharing has been easy ever since they had the Shared Folders application that used to exist in Hardy under System -> Administration.  Now sharing is even easier now since it's just a matter of right clicking on the desired folder.  My question is after all these years why is it still required to do a command line smbpasswd -a?  Is there really no other way around this?  I've wondered if there is a GUI way to do that and I just haven't found it.  Right now it's just easier to use guest access and not worry about it.

---

### Post by edwardLS on 2011-02-14
This is great!  This information has answered many of my questions and issues.  However, I have a Ubuntu Server (no GUI) running which I would like to share a folder from to all other Desktops on my home network.  How do I accomplish what is performed in step 1.1?

Thanks for a great post!

---

### Post by Morbius1 on 2011-02-14
> **edwardLS said:**
> However, I have a Ubuntu Server (no GUI) running which I would like to share a folder from to all other Desktops on my home network.  How do I accomplish what is performed in step 1.1?
If you have Ubuntu Server you probably don't want to use Nautilus-share but you can create a usershare ( usershare is what Samba calls it ) from the command line.
[http://ubuntuforums.org/showpost.php?p=10316901&postcount=2](http://ubuntuforums.org/showpost.php?p=10316901&postcount=2)

The only thing it won't do is the modification of the Linux file permissions that nautilus shares does so you will have to do a chmod on the target directory.

I've used this on a number of different distros that don't run Gnome but they were all geared for the desktop. I've never run it against a Server oriented distro so I'm not sure if there are dependencies that a Server may not have by default. Usershare itself is part of Samba not part of Gnome so it should work but ....

---

### Post by treadlove on 2011-02-14
Will this work with a USB drive?  I've tried experimenting with a thumb drive.  It let's me create the share folder; and I can see it on the client side; but I can never mount the network location.  (aka the shared folder on the ubuntu box.)

---

### Post by Cracklepop on 2011-02-15
Ok guys, I'm not a linux newb (although I never stop learning new stuff) but this is actually the first time I've ever had a server on my LAN or used samba, so I won't be much help for anything outside the scope of the howto...  > **pricetech said:**
> In your step 2 you recommend assigning the IP that you found in the previous step.  This will cause an IP address conflict when the router assigns that IP to another device.  Therefore you need to assign an IP that is outside the pool.

Doh! Yes, thanks for that - I didn't follow my own advice when I did it, I just used an easy to remember IP instead. Fixed now.  > **treadlove said:**
> Will this work with a USB drive?  I've tried experimenting with a thumb drive.  It let's me create the share folder; and I can see it on the client side; but I can never mount the network location.  (aka the shared folder on the ubuntu box.)

You need to enter the drive into /etc/fstab, instead of letting Ubuntu mount it for you.
There's tons of posts on fstab around, but you'll end up putting a line similar to this one (but not the same) into fstab:
 /dev/sdb1    /mnt/VerbtmExternNTFS    ntfs-3g    user,noatime,umask=022,auto,noexec,rw,async,dev,suid    0    0      > **qingpool said:**
>  Additional question - let's say i do this with guest access allowed, but i move my server to another network - what should i change? I remember vaguely that there was a subnet to be specified in smb.conf. Am i right?

Don't know. First time samba user ;)  > **Centaur5 said:**
> My question is after all these years why is it still required to do a command line smbpasswd -a?  Is there really no other way around this?  I've wondered if there is a GUI way to do that and I just haven't found it.  Right now it's just easier to use guest access and not worry about it.

Sorry, I don't know (If I did I'd have put it in the howto).   > **edwardLS said:**
> This is great!  This information has answered many of my questions and issues.  However, I have a Ubuntu Server (no GUI) running which I would like to share a folder from to all other Desktops on my home network.  How do I accomplish what is performed in step 1.1?

Thanks for a great post!

Thanks :)
Sorry, I can't help you.  Follow Morbius' advice, or read some of the material on samba floating around the web.

---

### Post by Morbius1 on 2011-02-15
> **treadlove said:**
> Will this work with a USB drive?  I've tried experimenting with a thumb drive.  It let's me create the share folder; and I can see it on the client side; but I can never mount the network location.  (aka the shared folder on the ubuntu box.)
With Cracklepop's permission I would like to offer an alternative. The problem with external USB drives ( if formatted with NTFS or FAT32 ) is that they automount with your-user-name as owner and permissions of 700 meaning only your-user-name has access. One way as explained above is to add an entry into fstab but you can also use Samba itself to work around this problem. It does however violate the premise of this HowTo in that it requires a non-GUI remedy:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section:
```
force user = your-user-name
```[COLOR=Blue]*Change "your-user-name" to your actual login user name on that box.*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```After the remote user passes Samba authentication ( be that guest or with a username and password ) his identity will be converted to "your-user-name" as far as those shares are concerned.

---

### Post by Ben604 on 2012-06-29
Just a quick thank you for this thread.  Very helpful.

---

### Post by sdowney717 on 2012-11-10
nothing shows up in windows7.

What are you supposed to type into the empty entry box??
you can click server example, also drop down box is empty.

bust using 12.10

---

### Post by Kangarooo on 2013-01-13
I had problem Windows 7 doesnt see in network places anything.
FIX:
My Computer-> Right Click "Network" -> Properties -> Opens Network And Sharing Center -> Change advanced sharing settings -> Choose your profile and select Network discovery to Turn ON.

---

### Post by Eirhead on 2013-04-09
> **Morbius1 said:**
> With Cracklepop's permission I would like to offer an alternative. The problem with external USB drives ( if formatted with NTFS or FAT32 ) is that they automount with your-user-name as owner and permissions of 700 meaning only your-user-name has access. One way as explained above is to add an entry into fstab but you can also use Samba itself to work around this problem. It does however violate the premise of this HowTo in that it requires a non-GUI remedy:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section:
```
force user = your-user-name
```[COLOR=Blue]*Change "your-user-name" to your actual login user name on that box.*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```After the remote user passes Samba authentication ( be that guest or with a username and password ) his identity will be converted to "your-user-name" as far as those shares are concerned.

Thanks for this... I'm running a fileserver with the OS running off a solid state drive and my file server data being located on a 2TB raid 1 drive. So I followed these instructions and it fixed my issue with not being able to connect to the server remotely. Unfortunately, whenever I restart my server, it forgets permissions!!! :( Does anybody have any idea what's going on and why it might be doing this? Thanks muchly

---

