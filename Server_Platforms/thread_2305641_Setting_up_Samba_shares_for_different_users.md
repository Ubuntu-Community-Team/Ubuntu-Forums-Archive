---
title: "Setting up Samba shares for different users?"
date: 2015-12-07
forum: Server Platforms
---

### Post by biggyk on 2015-12-07
I have been testing out a few different os options to mainly run a media server and Murmur with a older system I put together with parts from my older gaming pc. AMD Phenom 2.

I was going to use freenas but with an older system and no ecc memory and thought it wasnt the best option. I have a bit of experience with linux and figured I would give Ubuntu server a try. Right now, im testing it within virtualbox and have installed webmin.

I installed murmur easily with no issues and I have also set up a media samba share that has guest permissions. Now I want to create two more shares with their own user login. Im not sure exactly how im suppose to go about setting up a user and password. Do I do it in samba settings or make a user in ubuntu? 

Im sure this is a straight forward task but if anyone can send me in the right direction, even post a link that I can read up that would be great.

Thanks

---

### Post by bab1 on 2015-12-07
> **biggyk said:**
> ... I want to create two more [Samba] shares with their own user login. Im not sure exactly how im suppose to go about setting up a user and password. Do I do it in samba settings or make a user in ubuntu? 

Im sure this is a straight forward task but if anyone can send me in the right direction, even post a link that I can read up that would be great.

Thanks
For each user you need to create a Linux user (adduser) and a Samba user (smbpasswd -a).  If you want these user shares to be private you can use the [homes] share.  This share will allow you to create one share that accepts the users login to authenticate to that users private share.  If you want a share the allows both users to authenticate to and jointly use that share you can do that with a common user group that both users are part of.

You can start your reading with with [this]("https://help.ubuntu.com/community/Samba/SambaServerGuide").   I use the terminal to configure shares. Everything for Samba is configured in the /etc/samba/smb.conf file.  

I see the steps as this :
[LIST=1]
[*]Add the users (adduser <user>)
[*]Add the Samba user (smbpasswd -a <user>)
[*]Configure permissions and ownership of the directory you are going to share  
[*]Configure the share (see: man smb.conf)
[/LIST]

The [homes] share is the easiest.  When you add the user, the system creates a home directory (/home).  The [homes] share makes the logged in users home directory available as a private share.

---

### Post by biggyk on 2015-12-08
Great il check it out, thanks

What if I wanted to have private folders on my 2nd hard drive that will be going in instead of using the home folder? Basically the above steps?

---

### Post by bab1 on 2015-12-08
> **biggyk said:**
> Great il check it out, thanks

What if I wanted to have private folders on my 2nd hard drive that will be going in instead of using the home folder? Basically the above steps?
You can define where the "home" directory is located when you use the ***adduser*** command.  One some servers I have placed the users home dir at /srv/share/home.  This was a separate disk with 1 partition for all the home directories.  See the man page for adduser```
man adduser
```

[COLOR="#0000FF"]Edit:  Specifically this[/COLOR]```
      --home **DIR**
              Use **DIR** as the user's home directory, rather than the default specified by the
              configuration file.  If the directory does not exist, it is created and skele&#8208;
              ton files are copied.

```

---

