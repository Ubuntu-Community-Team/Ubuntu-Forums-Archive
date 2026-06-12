---
title: "Allow a single folder to be accessed remotely?"
date: 2010-04-18
forum: Server Platforms
---

### Post by FeverNK on 2010-04-18
I recently set up a computer running Ubuntu 9.10 Desktop for use as a server, and successfully have it hosting game servers.

I'm relatively new to Ubuntu, so I'm not sure how to go about this, but ideally I would like a user to be able to access a single folder on the server over the internet, and be able to upload and download files from it.

It would be nice to set up multiple folders like this, so different people would have access to their own personal folder, but not anyone else's.

Please let me know if this is possible, and if so how to do it.

Thanks,
--
Niko

---

### Post by romeroc24 on 2010-04-18
You can use Samba that is compatible with windows and linux you can start installing the samba server.

```

$sudo apt-get install samba

```

The key is configure the /etc/samba/smb.conf file 

```

$sudo vim /etc/samba/smb.conf

```

Find the next lines, modify or add:

```

workgroup = WORKGROUP

[samba-share]
   comment = Shared Files
   path = /srv/
   public = yes
   read only = no

```

The /srv/ directory need access privilegies:
```

$sudo chmod -R 777 /srv/

```

Next restart your samba server

```

$sudo /etc/init.d/samba restart

```

And access from a windows client with the same WORKGROUP and see on Shared Files or Network. And you can write and see files.
:guitar:

---

### Post by FeverNK on 2010-04-18
Sorry I forgot to mention that it had to be accessed over the internet, not on the same LAN.  I'll edit my post.

---

### Post by samosamo on 2010-04-18
I can't think of a more simple task. Nothing out of the ordinary needs to be done here.  Just instruct your users to use SFTP.

---

### Post by SRST Technologies on 2010-04-18
Actually samba is relatively useless in WAN applications since the routers at almost every ISP on the planet block this type of thing for security of the end user.

---

### Post by FeverNK on 2010-04-19
I'm starting from scratch without a lot of knowledge, samosamo.  What will I need to set up on my server?

---

### Post by lykwydchykyn on 2010-04-19
> **FeverNK said:**
> I'm starting from scratch without a lot of knowledge, samosamo.  What will I need to set up on my server?

SFTP services are part of openssh-server, so you could just install that and create normal user accounts for all your people.  That has some nasty side effects, though, like giving everyone console login to your server, and pretty much the same access as they'd have sitting down at the machine.

A more secure way to approach it is to restrict them to SFTP only, and to **chroot** them (so that they can only access the initial login directory and what's below it).

Instructions for that are here:
[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

Windows users would need to use something like WinSCP to connect, Windows doesn't ship with a native ssh/scp/sftp client last time I checked.

---

### Post by FeverNK on 2010-04-19
Ok I followed the instructions on that thread, but can't seem to connect from my other computer with WinSCP.  I created  a user with the given code, and I have port 21 forwarded to my server for FTP.

In WinSCP I enter the username and password I chose, port 21, and the external IP address of my server under host name.  Is this correct?

It says unable to connect, is there something other than scponly that I should have installed on my server?

---

### Post by FeverNK on 2010-04-21
Can anyone help me with this?  I think I must be missing something simple, because I have everything set up that the page said.

---

### Post by HermanAB on 2010-04-21
Wrong port.

Port 21 is FTP, which is insecure.

Port 22 is SSH and SFTP, which are secure.

---

### Post by FeverNK on 2010-04-21
Thanks, now I can connect.  It isn't letting me paste files into the folder remotely though, how do I change that permission?

EDIT:  Never mind, I got it working.  Thanks for the help, guys.

---

