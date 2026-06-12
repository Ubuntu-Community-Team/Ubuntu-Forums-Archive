---
title: "Restricted FTP access"
date: 2010-01-12
forum: Server Platforms
---

### Post by alexlaban on 2010-01-12
If it's to much to read only read the following 3 rows.

I want to share a folder in my home directory and the subdirectories of that folder but nothing more and I only want to allow read access to the folder.

I want it as secure as possible so even if the password and the username would end up in the wrong hands they wouldn't be able to do anything other then downloading what's in that single directory and the subdirectories. I've been searching some on the forums and google and have found some basic information about vsftpd, wu-ftp and ProFTPD but I haven't found any information about doing what I want to do. I do not want to use the ftp server for anything but this single purpose. I've been thinking a lot about sftp but I don't really need encryption that bad and I'm way more afraid of unauthorized ssh access then someone actually getting the hands on the files in that folder.

Also one other thing, is it possible to in some way run the ftp on port 80 even tho I run a web-server on that port cause the thing is one of the places where I want to access these files only allow data through port 80, if not it's not the world but it would be nice if it were possible to get it work.

I believe that is everything for now. Thanks for your help and I'm grateful for any help I can get even if you only can solve a little part of my problems, as they say, many streams small becomes a big river.

---

### Post by pricetech on 2010-01-12
You say you don't want secure ftp, but that means the password is transmitted in the clear and is therefore easy to sniff out, nullifying your authentication scheme.

Yes you can put your SFTP server on port 80, but you'll have to move your web server to another port first.

I'd look at using SSH based options such as SCP and SFTP.

---

### Post by alexlaban on 2010-01-12
Yeah well I would kinda need both on that port in that case and separate them with hostname or something but if it's not possible it's cool I can manage without from there. However what I'm afraid of when using SSH is someone gaining access to my system being able to alter stuff, I don't know how to get SSH that restricted and I'm not that afraid of someone getting my files I mainly just don't want them to be able to mess with my server or alter anything.

---

### Post by pricetech on 2010-01-12
Any form of access comes with some risk.  I don't know of anything more secure than SSH when it comes to remote access of any kind.

Maybe I'm not understanding what you want to do.  Are you trying to set up a server where other folks can access files or download them or do you need access for yourself ??

You may need to look at a more than one solution.

---

### Post by alexlaban on 2010-01-12
Both for me and some of my friends to access, however I don't want them to be able to login with the account over ssh and mess with my stuff executing commands and stuff. Even tho they are my friends I'm kinda paranoid and risk is someone get the userdetails from them somehow. However I don't want it totally public so I won't for instance put as a folder for apache. I know ssh is secure cause it's encrypted but if the wrong person get the details to a ssh login for your server they can really mess up a lot on the server. See the biggest problem is not keeping the files from unauthorized access but keeping people from being able to mess with my server and as long they can only read and download the files in that folder my server is safe.

---

### Post by phr0ze on 2010-01-12
[http://www.ubuntu-howto.info/howto/how-to-install-and-configure-pure-ftpd](http://www.ubuntu-howto.info/howto/how-to-install-and-configure-pure-ftpd)

Install Pure-FTP. Make a virtual user with the same group and home directory for that folder or make a real system user with the same group.

Make sure the group has read only to that folder.


Make sure you have the server setup to chroot. this keeps the user only in their home folder. Since its a virtual user you can give them a 'virual' home folder to a subfolder in your home path.

---

### Post by BobVila on 2010-01-12
> **alexlaban said:**
> Both for me and some of my friends to access, however I don't want them to be able to login with the account over ssh and mess with my stuff executing commands and stuff. Even tho they are my friends I'm kinda paranoid and risk is someone get the userdetails from them somehow. However I don't want it totally public so I won't for instance put as a folder for apache. I know ssh is secure cause it's encrypted but if the wrong person get the details to a ssh login for your server they can really mess up a lot on the server. See the biggest problem is not keeping the files from unauthorized access but keeping people from being able to mess with my server and as long they can only read and download the files in that folder my server is safe.

Why not create a separate account on the box and set the shell to sftp server? SSH authentication without shell access seems like it would suit you.

[http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94)

---

### Post by Lars Noodén on 2010-01-13
> **alexlaban said:**
> 
I want to share a folder in my home directory and the subdirectories of that folder but nothing more and I only want to allow read access to the folder.

That can be done with SFTP and chroot.  

```

# example
mkdir --mode=1755 -P /home/alexlaban/Public/sftp/

```

Then set sshd to force certain users into sftp and chroot them to your directory:

```

# from /etc/ssh/sshd_config
Subsystem sftp internal-sftp

Match Group *sftp-visitors*
	ChrootDirectory */home/alexlaban/Public/sftp/*
	AllowTCPForwarding no
	X11Forwarding no
	ForceCommand internal-sftp

```

Then make a user and set the default shell following the notes @BobVila pointed to:
 [http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94)
set the group of that user to be that which you specified in sshd_config, such as *sftp-visitors* above.

---

### Post by alexlaban on 2010-01-13
> **Lars Noodén said:**
> That can be done with SFTP and chroot.  

```

# example
mkdir --mode=1755 -P /home/alexlaban/Public/sftp/

```

Then set sshd to force certain users into sftp and chroot them to your directory:

```

# from /etc/ssh/sshd_config
Subsystem sftp internal-sftp

Match Group *sftp-visitors*
	ChrootDirectory */home/alexlaban/Public/sftp/*
	AllowTCPForwarding no
	X11Forwarding no
	ForceCommand internal-sftp

```

Then make a user and set the default shell following the notes @BobVila pointed to:
 [http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94)
set the group of that user to be that which you specified in sshd_config, such as *sftp-visitors* above.

Woah thanks, just one last thing if I'm going to use sftp I will still need to access the server via ssh locally as before so how would only allow to use this from the internet but still use all users from 192.168.0.*? Since it's my only way to access the server without going to the server room I kinda still need it.

---

### Post by Lars Noodén on 2010-01-13
> **alexlaban said:**
> Woah thanks, just one last thing if I'm going to use sftp I will still need to access the server via ssh locally as before so how would only allow to use this from the internet but still use all users from 192.168.0.*? Since it's my only way to access the server without going to the server room I kinda still need it.

Well one way would be to use an account that is not a member of **sftp-visitors**

Depending on how recent the version of OpenSSH you are running, 
you can set [sshd_config](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config) to use **Match Host**


```

# from /etc/ssh/sshd_config
Subsystem sftp internal-sftp

# first 'Match' to match, takes effect
# others are ignored

Match Address *192.168.0.0/24*
        ChrootDirectory /

Match Group *sftp-visitors*
	ChrootDirectory */home/alexlaban/Public/sftp/*
	AllowTCPForwarding no
	X11Forwarding no
	ForceCommand internal-sftp

```

If **Match Address** does not work, post the version of sshd that you are using and we'll work from that, and if necessary file a request with backports.  

  apt-cache policy openssh-server

---

### Post by alexlaban on 2010-01-13
So can I use Match to only allow the sftp-visitors to connect from the net and let anyone connect from 192.168.0.0/24?
My version is 1:5.1p1-6ubuntu2 according to that command.

You're really nice to help me who's a nobody here.

---

