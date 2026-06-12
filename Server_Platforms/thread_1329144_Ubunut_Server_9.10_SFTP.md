---
title: "Ubunut Server 9.10 SFTP"
date: 2009-11-17
forum: Server Platforms
---

### Post by Jisamaniac on 2009-11-17
I've been researching the best way to click, drag, and drop my files on to my server on a client end. I've decided I want to use SFTP for security reasons, but not entirely sure how to go about doing this because I prefer to use Ubuntu Server 9.10 edition, and 9.10 Server doesn't accept a GUI. Do I need a GUI to be able to click and drop my files? Any suggestions?

---

### Post by scorp123 on 2009-11-17
> **Jisamaniac said:**
> I've been researching the best way to click, drag, and drop my files on to my server on a client end. Why don't you use your Nautilus file manager ????

***Places > Connect to Server > Service Type: SSH*** ...

(SFTP is a sub-protocol of SSH)

---

### Post by Jisamaniac on 2009-11-17
Didn't know that. I'll do that. Ty. Anything else i should know?

---

### Post by virtuoosi on 2009-11-17
> **Jisamaniac said:**
> I've decided I want to use SFTP for security reasons

If you want to add more security to your SSH connection, consider using a custom port instead of the default 22. You can do this by editing /etc/ssh/sshd_config. Change the Port from 22 to a custom, free port.

Also, using RSA keys instead of passwords adds even more security. Here's a how-to:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by scorp123 on 2009-11-17
> **virtuoosi said:**
> If you want to add more security to your SSH connection, consider using a custom port instead of the default 22.  Security by obscurity??

And what if a wannabe intruder port-scans the box and then starts hammering the other port you moved to? You're just moving the problem around, you're not solving it.

It would be better to consider real solutions, e.g. ***fail2ban*** or ***denyhosts*** ... Too many failed login attempts == BAM!! intruder gets banned and blocked by the built-in firewall and can never connect again, no matter which port you use.


> **virtuoosi said:**
>  Also, using RSA keys instead of passwords adds even more security. Here's a how-to:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) I agree on this part here. This is a good idea.

---

### Post by Lars Noodén on 2009-11-17
I second @scorp123 's comments about security through obscurity.  

> **Jisamaniac said:**
> I've been researching the best way to click, drag, and drop my files on to my server on a client end. I've decided I want to use SFTP for security reasons, but not entirely sure how to go about doing this because I prefer to use Ubuntu Server 9.10 edition, and 9.10 Server doesn't accept a GUI. Do I need a GUI to be able to click and drop my files? Any suggestions?

If you want a GUI, then Filezilla has been popular enough to warrant mentioning.

You have built-in to Konqueror the ability to open an sftp connection by entering the URL.  e.g. sftp://192.168.0.101/  That gives you the ability to drag and drop files.  

Another option is to use sshfs to mount the remote server as a folder on your computer.  

```

# create a mount point called 'server' if it doesn't exist
# the remote server will be accessible here when mounted
test -d  ~/server || mkdir --mode=700 ~/server

# login and mount the remote account
sshfs -C jisamaniac@192.168.0.101:. ~/server

```

---

### Post by scorp123 on 2009-11-17
> **Lars Noodén said:**
>  Another option is to use sshfs to mount the remote server as a folder on your computer.  Yeap, that's a nice solution too.

---

### Post by Jisamaniac on 2009-11-17
Do i need a GUI for all of this? I remember reading Ubuntu Server 9.10 would no longer provide access to a GUI.

---

### Post by scorp123 on 2009-11-17
> **Jisamaniac said:**
> Do i need a GUI for all of this? Real men don't use a GUI. Real men don't touch mice ....

Just kidding.

The GUI has nothing to do with this. You ***can*** use a GUI for SSH/SFTP. I think we all assumed that was what your question was about?

> **Jisamaniac said:**
>  I remember reading Ubuntu Server 9.10 would no longer provide access to a GUI. And so? A server by definition is a machine that sits in the server room together with all the other precious machines that work day and night. With the exception of the admin there will never ever be anyone sitting in front of it. So there won't be a keyboard. There likely won't even be a screen. There most likely won't ever be any mice. So what's the point of having a GUI on a server??? Some professional UNIX server systems (e.g. the really big machines from HP and SUN) don't even have graphics cards for this reason (you configure them via a serial port or via the network ...)

So you have an Ubuntu server. Fine. And you use it as SFTP server. Fine. And so ... what does the absence of any GUI have to do with this? Won't you have your own client machine? e.g. your own Ubuntu desktop or laptop somewhere so you'd connect to the server remotely ... via SSH and SFTP?

---

### Post by Jisamaniac on 2009-11-18
Ya i want to be able to click and drag the files to server and access them with a mouse, so yes if i don't need a gui that answers that question. 

I guess the other part of my question is setting this up. I've looking through tutorials and its all confusing as hell because it's like i can't get a straight answer. 

I still haven't looked into the suggestions yet that people have left me. 

And yes scorp123 real men don't need GUI.

---

### Post by scorp123 on 2009-11-18
> **Jisamaniac said:**
>  I guess the other part of my question is setting this up. What? SFTP?

> **Jisamaniac said:**
>  I've looking through tutorials and its all confusing as hell  Confusing?? ```
sudo apt-get install openssh-server
``` ... and BTW, on Ubuntu server it should be installed by default so above command is only necessary if you chose not to install SSH (last question during the Ubuntu server installation process, when the installer asks you what task sets it should install ... ). Voila. Done.

---

### Post by Lars Noodén on 2009-11-18
> **Jisamaniac said:**
> Do i need a GUI for all of this? I remember reading Ubuntu Server 9.10 would no longer provide access to a GUI.

The GUI is on your desktop and is used to access the server.  No GUI on the server, hopefully.

---

### Post by Jisamaniac on 2009-11-20
I'm sorry. I'd like to further state I'm an idiot. 

As I finally discoverd SFTP is already installed on Ubuntu Server 9.10 (thats what "sudo apt-get install openssh-server"). Use FileZilla to connect to server. That is all.

For further editing and understanding of SFTP. I found this site [http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html](http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html) 

Thanks everyone for their help and patience.

---

### Post by Spiritof76 on 2009-11-22
> **Lars Noodén said:**
> I second @scorp123 's comments about security through obscurity.  



If you want a GUI, then Filezilla has been popular enough to warrant mentioning.

You have built-in to Konqueror the ability to open an sftp connection by entering the URL.  e.g. sftp://192.168.0.101/  That gives you the ability to drag and drop files.  

Another option is to use sshfs to mount the remote server as a folder on your computer.  

```

# create a mount point called 'server' if it doesn't exist
# the remote server will be accessible here when mounted
test -d  ~/server || mkdir --mode=700 ~/server

# login and mount the remote account
sshfs -C jisamaniac@192.168.0.101:. ~/server

```

Is there anyway to supply the password automatically in the script?

---

### Post by cariboo on 2009-11-23
Setup private keys using [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") howto, and there is no need for a password.

---

### Post by Lars Noodén on 2009-11-23
> **cariboo907 said:**
> Setup private keys using [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") howto, and there is no need for a password.

That tail end bit could be expanded, since it is almost as important as the rest of the HowTo.

The keys stored in ~/.ssh/authorized_keys can be constrained as shown in the example.  Stronger emphasis is needed on the fact that **command="*program*"** must be used if safe operation is to be expected.

---

