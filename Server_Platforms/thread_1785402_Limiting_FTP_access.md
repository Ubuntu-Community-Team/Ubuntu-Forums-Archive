---
title: "Limiting FTP access"
date: 2011-06-18
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-06-18
I recently started dabbling with a ubuntu web server.
I have it configured ok and its working.

My brother has asked if I can host his website.

I have said yes.

I want to be able to give him ftp access to the folder on the server where his website will be stored.
I dont want him to have access to anything else. Its not that I dont trust him, more that I dont want the risk of him accidentally deleting or changing something he shouldnt.

For clarity I want him to have access to /var/www/trentrc  and nothing else.

How do I create a user for him and limit his access.
I've never done any user creation in linux except for the menu driven one setup at install time

---

### Post by Lars Noodén on 2011-06-18
> **bigmonmulgrew said:**
> For clarity I want him to have access to /var/www/trentrc  and nothing else.

How do I create a user for him and limit his access.


If you drop insecure FTP and [use SFTP instead](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads), limiting becomes very easy because chroot is built into SFTP.  So you limit his access by setting the chroot directory to /var/www/trentrc

---

### Post by Lars Noodén on 2011-06-18
> **bigmonmulgrew said:**
> How do I create a user for him... ?


The way I would do it would be 
```

sudo useradd

```

But there is also a [graphical way to add users](http://www.liberiangeek.net/2011/03/addremove-users-ubuntu-11-04-natty-narwhal/), if that's what you want.

---

### Post by bigmonmulgrew on 2011-06-18
Thanks for the replies. Ill take a look later.
This is on ubuntu server so a graphical method not required

---

### Post by brent1975 on 2011-06-18
I believe this is what you are wanting to do. Just change the directory of home to the web directory that you create for your brother. 
[http://forums.iso-world.com/viewtopic.php?f=3&t=35](http://forums.iso-world.com/viewtopic.php?f=3&t=35)

---

### Post by bigmonmulgrew on 2011-06-21
I'm already using some form of sftp. Must be whatever is default in ubuntu server 11.04. I can access the server but I cant access it using no security. I've not tried all the methods but I'm using sftp.
Currently I have access (although not necessarily write access) to everything which is normal I expect as I am the only user

So I thought I'd start by creating a new user to trial with.

```
sudo useradd -d /var/www/trentrc trcadmin
sudo passwd trcadmin
```

The first line creates a user "trcadmin" and sets its home directory the second command sets the users password. It is possible to set this with useradd but I prefere this way. I also came accross the "adduser" command which prompts you for each piece of user data.

I'm going with the example from brent first (and only if it works) as it seems much less long winded. I did have to lookup certain commands like how to add groups though.

First I created a group. As This is for a website administrator I called it "webadmins"

```
sudo addgroup webadmins
```
If you want to see a list of your groups use
```
cat /etc/group | more
```

Then to add my new test user trcadmin to the new group
```
sudo adduser trcadmin webadmins
```

You should get this output 
```
Adding user `trcadmin' to group `webadmins' ...
Adding user trcadmin to group webadmins
Done.

```

Next come the bit I had to labour over for a while before it sunk in.
We need to add a Match directive to sshd's configuration file.
This can be found at /etc/ssh/sshd_config
You need to add the following to the end of the file
```
Subsystem sftp internal-sftp

Match Group webadmins
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
```
Obviously substitute webadmins for whatever group you have created.

---

### Post by bigmonmulgrew on 2011-06-21
and now disaster
After following the above I am now no longer able to connect to the PC via ssh or ftp. 
I can access the website thats hosted on this machine but as its a VPC and my only way of managing it was via SSH, I'm now stuck. any ideas anyone?

---

### Post by Dry Lips on 2011-06-21
> **bigmonmulgrew said:**
> and now disaster
After following the above I am now no longer able to connect to the PC via ssh or ftp. 
I can access the website thats hosted on this machine but as its a VPC and my only way of managing it was via SSH, I'm now stuck. any ideas anyone?

What version of Ubuntu do you have on your server? If you run 8.04 LTS you would
lock yourself out, because OpenSSH 4.7 (which comes with 8.04) doesn't support ChrootDirectory.

I did try to do this for an entire day on my old "server" running 8.04 before finding out that the version of SSH I was running was too old. But luckily I had physical access to my box, so it was not a big problem at all. 

If you're running a VPC, I guess you could ask your host to fix it for you. (edit sshd_config and remove the lines you inserted or perhaps do a reinstall).

---

### Post by bigmonmulgrew on 2011-06-21
Im running ubuntu server 11.04.
I am my host
The vpc is hosted on a physical server sitting in my spare room.
The host is 11.04 also.
I have physical access to the host as well as ssh access.
I cant access the guest via ssh, i dont even get a login page.
Currently the only way i know of to access the guests terminal is via ssh. Im sure theres another way since i have physical access but i dont know how.

---

### Post by bigmonmulgrew on 2011-06-21
I think i remember reading its openssh v 5.8

---

### Post by Dry Lips on 2011-06-21
> **bigmonmulgrew said:**
> After following the above I am now no longer able to connect to the PC via ssh or ftp. 

Do you mean ftp or sftp?

---

### Post by bigmonmulgrew on 2011-06-21
> **Dry Lips said:**
> Do you mean ftp or sftp?


Yes to be clear i mean sftp

---

### Post by Dry Lips on 2011-06-21
> **bigmonmulgrew said:**
> Yes to be clear i mean sftp

  	 	 	 	 	 	  The reason why I asked this is obvious, if you had vsftpd installed you would have an easy way out of this...
 

 So if I understand you right, you run a 11.04 server host with a 11.04 server guest. And you cannot access your guest, right? I must admit I'm no expert on virtualization, as I've only used VirtualBox myself, but isn't there a way of logging directly into your guest account from your host?

---

### Post by bigmonmulgrew on 2011-06-21
Yes your right there both 11.04

I expect there is a way to connect from the host but i dont really know it.

---

### Post by Dry Lips on 2011-06-21
> **bigmonmulgrew said:**
> Yes your right there both 11.04

I expect there is a way to connect from the host but i dont really know it.

  	 	 	 	 	 	  Frankly I think that would be the only way of accessing your VPC if really you have locked yourself out. My guess is that you probably could sort this out if have access to your host. Perhaps you could ask for help at the Virtualization subforum?
 

 I guess the alternative would be to delete the current VPC and create a new one.
 
Good luck!

---

### Post by bigmonmulgrew on 2011-06-22
> **brent1975 said:**
> I believe this is what you are wanting to do. Just change the directory of home to the web directory that you create for your brother. 
[http://forums.iso-world.com/viewtopic.php?f=3&t=35](http://forums.iso-world.com/viewtopic.php?f=3&t=35)
After some difficulty I rebuilt the server and then followed these instructions to limit my new user.

The home directory is now /var/www/trentrc

when I login with user "trcadmin" it now shows me this directory automatically.

Thats only half the problem though. This user can still navigate around the server at will and as far as I can tell they have the same access I have.
I want to limit this users access to this folder (and its subfolders) so that they cant see whats above it. Is there a way to do this

---

### Post by Lars Noodén on 2011-06-22
> **bigmonmulgrew said:**
> I want to limit this users access to this folder (and its subfolders) so that they cant see whats above it. Is there a way to do this

Yes.  Use [SFTP and chroot](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads).  Chroot is built into SFTP and will allow you to restrict access to a particular directory very, very easily.  Forget FTP.

---

### Post by bigmonmulgrew on 2011-06-22
> **Lars Noodén said:**
> Yes.  Use [SFTP and chroot](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads).  Chroot is built into SFTP and will allow you to restrict access to a particular directory very, very easily.  Forget FTP.

Well I've just followed that link just like last time and again had the same problem.
I cant access the server via ssh or sftp.
I can however access the server via ftp but I cant change any files to rectify the problem. I can only browse and open files.

---

