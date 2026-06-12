---
title: "Personal file server"
date: 2009-11-23
forum: Server Platforms
---

### Post by blueyelabs on 2009-11-23
Hi all,

I just purchased one of Marvell's Sheeva Plugs in order to make it easy for me to back up all my files using OSX's Time Machine and also to access files at home from wherever I am. What I would like to do is firstly to be able to access an attached USB drive as NAS so I can backup directly to it and secondly I would like to be able to browse and download files at my own convenience without having to write my own web interface. On my Mac I have a programme called Papaya ([http://lightheadsw.com/papaya/](http://lightheadsw.com/papaya/)) which is brilliant and allows me to set passwords and stuff all from the application. It also has a gorgeous web interface and easy drag-and-drop to share.
So, anyone have any idea how I would go about those two tasks on Ubuntu?

Thanks in advance.

---

### Post by Lars Noodén on 2009-11-24
> **blueyelabs said:**
> I would like to be able to browse and download files at my own convenience without having to write my own web interface. 

This ought to be added to a FAQ somewhere.  You can do that with the SFTP subsystem built into the openssh server you have running.  

Members of the group sftp-only can log in and have only sftp access. 

```

Subsystem sftp internal-sftp

Match Group sftp-only
	ChrootDirectory %h
	AllowTCPForwarding no
	X11Forwarding no
	ForceCommand internal-sftp

```

For graphical, drag-and-drop sftp clients you have cyberduck, fugu, fetch, konqueror, dolphin, filezilla, and a few others.

---

### Post by Lars Noodén on 2009-11-24
A second way to take advantage of the sftp subsystem, using the above, is to use sshfs to mount the file system.  Then you just drag and drop to that folder.  

```

# create mount point 'server' in the home directory if none exists
test -e ~/server || mkdir --mode 700 ~/server

# mount the remote server
sshfs blueyelabs@server.example.org:. ~/server

# alternately, see if using compression is faster or slower
sshfs -C blueyelabs@server.example.org:. ~/server

```

---

### Post by blueyelabs on 2009-11-24
Thanks for the reply Lars.

I've been messing around with Ubuntu Server and managed to get afp working. What I meant more than using something like Cyberduck or Transmit et cetera is a system like Papaya which presents a web interface which is really nice.
In terms of afp, I'd like to use it simply so I can use Time Machine backup when I'm abroad and not carry around my backup drive (which is a silly thing to have to do). I'll look into sshfs with Snow Leopard (I found this article [http://www.5dollarwhitebox.org/drupal/node/97](http://www.5dollarwhitebox.org/drupal/node/97)) since OSX refuses to connect to sftp servers.
I did get afp running but I'm not sure if it's secure or not (so I don't know if TM will back up to it...)
I'm not entirely sure where that sftp configuration goes (sorry, ssh server setup is fairly new for me).
Thanks for replying :)

---

### Post by Lars Noodén on 2009-11-25
> **blueyelabs said:**
> Thanks for the reply Lars.

I've been messing around with Ubuntu Server and managed to get afp working. What I meant more than using something like Cyberduck or Transmit et cetera is a system like Papaya which presents a web interface which is really nice.
In terms of afp, I'd like to use it simply so I can use Time Machine backup when I'm abroad and not carry around my backup drive (which is a silly thing to have to do). I'll look into sshfs with Snow Leopard (I found this article [http://www.5dollarwhitebox.org/drupal/node/97](http://www.5dollarwhitebox.org/drupal/node/97)) since OSX refuses to connect to sftp servers.
I did get afp running but I'm not sure if it's secure or not (so I don't know if TM will back up to it...)
I'm not entirely sure where that sftp configuration goes (sorry, ssh server setup is fairly new for me).
Thanks for replying :)

cyberduck, fetch, fugu, filezilla aren't goofy web-apps.  They are fully functional sftp clients, plus a little more. 

For AFP you have to add netatalk.  It's one of the things left out of most linux distros, as is OpenAFS.  It's not hard to add if you have a recipe.  Here's a very old one, but it should still work for the newer kernels:
[http://www-personal.umich.edu/~lars/kernel_patching.html](http://www-personal.umich.edu/~lars/kernel_patching.html)

However you do it, make sure that you make your changes as a custom package and install that.  It makes life a *lot* easier.

See also pages like this:
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

### Post by blueyelabs on 2009-11-25
> 
cyberduck, fetch, fugu, filezilla aren't goofy web-apps. They are fully functional sftp clients, plus a little more.

I know the aren't, I use to use cyberduck all the time until I bought Coda which does all my SFTP for me. I still use it occasionally to connect to the servers at the company I'm working in. I was looking for something for the less technical members of my family to access files from wherever they are. Hence the desire for a web interface like that of Papaya.
I saw the kremalicious article and have bookmarked it. Thanks for the pointer to the netatalk patching. I'll look into it tomorrow if possible.

Thanks :)

---

