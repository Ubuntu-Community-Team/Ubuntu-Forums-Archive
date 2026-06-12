---
title: "need easy File Server"
date: 2008-05-10
forum: Server Platforms
---

### Post by miesnerd on 2008-05-10
I was looking for a project to make good use of this old computer (1.2 ghz, 256 MB of ram) comcrap that I have laying around. I have ubuntu server installed, and no GUI.

All I want is to be able to log in from any web broswer (with a login/password) and get certain files I have stored there at any time. I thought it would be awesome to be doing work somewhere and say "oh, I'll just log into my server and get that file".

Anyways, its behind a router, and its connected 24/7.

I would prefer to not install a GUI unless I need to.
Im pretty decent at the command line, limited experience in setting up FTP's though.
And I'll probably need to be walked through this.
Thanks.

Also, I have webmin already installed and working, if that'll help me any.

---

### Post by miesnerd on 2008-05-10
ok, i figured out how to upload one file at a time through webmin.
And that's cool, but I was hoping there was a way that I could have it kinda streamlined.
IE- the FTP server backs up a folder on my desktop (also running ubuntu 8.04) and makes it where I can access that folder via the web.

Thanks in advance.

---

### Post by cdtech on 2008-05-11
[[COLOR="DarkRed"]Proftpd[/COLOR]]("http://www.proftpd.org/")

You can apt-get install it. Thats what I use when I'm at a Windows desktop. I use slogin from my Ubuntu desktop to access my server. With proftp you can access using the browser via [ftp://yoursite.com](ftp://yoursite.com).

---

### Post by windependence on 2008-05-11
You could install Samba if you are serving to Windows machines, and even linux boxes will see the shares. 

A little reading on wget would be in order too. 

-Tim

---

### Post by hyper_ch on 2008-05-11
I'd go the ssh/sftp route....

---

### Post by miesnerd on 2008-05-11
where I am at now is that I have the majority of the files on the server.. 

Now, Im looking for the coolest graphical way to access files. 
It needs to be able to be done from both linux and windows machines.
Since Im sure I'll at some point use university machines, It'll need to be where I dont have to install any extra software, so I think I'll have to set up something where even the crappiest software (read: IE) can get me there.

Any ideas?
Please give specifics, as this is out of my area of general knowledge.

---

### Post by gavin2u on 2008-05-11
proftpd is the best choice, in my opinion.

[www.proftpd.org](www.proftpd.org)

---

### Post by hyper_ch on 2008-05-11
install openssh-server and get for
- windows:  winscp
- linux: konqueror or whatever supports ssh/sftp

or you can install samba... then you can mount the remot directory

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **gavin2u said:**
> proftpd is the best choice, in my opinion.

+1 proftpd.

---

### Post by miesnerd on 2008-05-11
i am staying away (for the time being) from proftpd because I was having problems getting it to work.

I might try it at a later date.
Anyways, in case I need to know (i have a graphical way of doing it already set up, how would I copy a file from the ssh'd computer to my computer. Let's say I wanted to copy a file from the ssh'd computer's home/miesnerd/desktop to the other computer's desktop.

Thanks.

---

### Post by hyper_ch on 2008-05-11
well, use a client that supports ssh/sftp... konqueror does so... not sure if the default gnome filemanager supports it also.. but you also have a few ftp clients available that support sftp.

---

### Post by .rdg on 2008-05-11
I'd go with sshd (for scp capabilities) or vsftpd (instead of proftpd). The first one is easy to configure and you get two in one. On Windows you can download a couple of scp clients (pscp or winscp), which doesn't require admin rights or installation. Don't forget to secure your ssh daemon if you choose to go that road. The ftp server, vsftpd, is a good choice if you chroot users in their home directories - it's a little easier to make it safe (to some point) than ssh and you still get what you need.

---

### Post by cdtech on 2008-05-11
> **miesnerd said:**
> how would I copy a file from the ssh'd computer to my computer. Let's say I wanted to copy a file from the ssh'd computer's home/miesnerd/desktop to the other computer's desktop.

Thanks.

```
scp user@remoteip:/dir/fromremote/whatever.txt .
```

This copies the whatever.txt file to the current (".") directory you are in now.

```
scp whatever.txt user@remoteip:/dir/fromremote/whatever.txt
```

This copies the whatever.txt from the local computer to the "/dir/fromremote/" remote computer.

---

### Post by mbarak on 2008-05-11
To copy a file from you're server to your computer (or vice versa) with ssh just in nautilus type in:

ssh://ip.of.server/ or
sftp://ip.of.server/

or you can click places > connect to server and select "ssh" as the server type

I agree .rdg
ssh and vsftpd is a good way to go (it's what i have on my server :))
vsftpd is in ubuntu's main repository, so is well supported and the configuration file is very well documented (/etc/vsftpd.conf i think) just go through that file, read the descriptions of the different options and uncomment what you want/comment what you don't
ftp can be used in any web-browser and (of course) nautilus

---

### Post by windependence on 2008-05-12
> **hyper_ch said:**
> well, use a client that supports ssh/sftp... konqueror does so... not sure if the default gnome filemanager supports it also.. but you also have a few ftp clients available that support sftp.

This works really slick. You can browse files just like they were on your local machine.

-Tim

---

