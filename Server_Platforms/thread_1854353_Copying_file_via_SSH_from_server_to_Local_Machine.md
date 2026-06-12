---
title: "Copying file via SSH from server to Local Machine"
date: 2011-10-04
forum: Server Platforms
---

### Post by Mistertuxedopants on 2011-10-04
Helllo Forum,

I have a ubuntu (File) server setup

I have OpenSSH-Server installed Via (apt-get)

I have the LAN IP assigned by the router port forwarded to 22

I can connect outside of my LAN

I just don't know how to copy files down from my server to the Local Machine 

any help would be great,

Thanks
MTP

---

### Post by matt_symes on 2011-10-04
Hi

Have a look at secure copy.

```
man scp
```

There are loads of examples of the net.

This is just one.

[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

Kind regards

---

### Post by Mistertuxedopants on 2011-10-04
that doesn't show how to copy to from the server to a local windows machine. Its shows from server to server. I might miss something but i think i looked at that last night

---

### Post by Jonathan L on 2011-10-04
> **Mistertuxedopants said:**
> Helllo Forum,

I have a ubuntu (File) server setup

I have OpenSSH-Server installed Via (apt-get)

I have the LAN IP assigned by the router port forwarded to 22

I can connect outside of my LAN

I just don't know how to copy files down from my server to the Local Machine 

any help would be great,

Thanks
MTP

Hi Mr TP

I'll confess I found the quantity of information about ssh/scp to make it difficult to find the simple examples!
```
ssh farname@farserver.com pwd
ssh farname@farserver.com ls -l
scp farname@farserver.com:farfilename localfilename
scp farname@farserver.com:/etc/motd .
```If your far username is the same as your local one,
```
ssh farname@farserver.com:farfilename localfilename
...
```If the far system doesn't have a DNS entry and you just know the IP address:
```
scp 212.1.2.3:farfilename localfilename
...
```Hope that helps

Regards
Jonathan

---

### Post by matt_symes on 2011-10-04
Hi

> **Mistertuxedopants said:**
> that doesn't show how to copy to from the server to a local windows machine. Its shows from server to server. I might miss something but i think i looked at that last night

Have you tried it yet ;) Try it from your client, connecting to your server, and copy a file to your client. Ignore the fact it just talks about servers.

Kind regards

---

### Post by collisionystm on 2011-10-04
> **Mistertuxedopants said:**
> Helllo Forum,

I have a ubuntu (File) server setup

I have OpenSSH-Server installed Via (apt-get)

I have the LAN IP assigned by the router port forwarded to 22

I can connect outside of my LAN

I just don't know how to copy files down from my server to the Local Machine 

any help would be great,

Thanks
MTP


Easy. Just use rsync to copy it.

Make a folder on your Local Machine to copy files into. 

mkdir /home/username/files

You can invoke the rsync command from either direction, however the easiest is probably to do it from the server.

Login to the server.

> rsync -ra --progress SOURCE DESTINATION

```
rsync -ra --progress /directory/filesyouwant username@localmachine:/home/username/files
```

You will see your stuff copy over and voila. You are done.

Earlier I said you can copy from either direction. In order to copy without logging into your server, you just need to know the absolute path and file name. Just use the template of source and destination.
```

rsync -ra --progress username@server:/directory/files /home/username/files
```

---

### Post by collisionystm on 2011-10-04
> **Mistertuxedopants said:**
> that doesn't show how to copy to from the server to a local windows machine. Its shows from server to server. I might miss something but i think i looked at that last night


Oh, you have a windows machine? Alright, hold on.

---

### Post by Jonathan L on 2011-10-04
> **collisionystm said:**
> Easy. Just use rsync to copy it.
...

... ah yes as Collissiony says, if you want to copy all your files, from time to time, rsync is an excellent way to do this.  If this is what you're doing, you could also consider git.

Jonathan.

---

### Post by collisionystm on 2011-10-04
Here,

You want WinSCP

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

You just punch in your servers SSH credentials and it gives you a 'Windows Explorer' Interface to browse your files and just drag them onto your desktop.

Enjoy.

---

### Post by Lars Noodén on 2011-10-04
SFTP is a good solution.  You can use graphical clients like Nautilus or Filezilla if you want.

---

### Post by ~!geek!~ on 2011-10-04
> **collisionystm said:**
> Here,

You want WinSCP

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

You just punch in your servers SSH credentials and it gives you a 'Windows Explorer' Interface to browse your files and just drag them onto your desktop.

Enjoy.

  +1 to this!  The explorer interface winscp provides, makes it easy to browse the directory at server and copy files from them to local machine intuitive to a windows user!

---

### Post by collisionystm on 2011-10-04
I just tried Filezilla. Filezilla works, however WinSCP gives you the option to Move Folders and files, as well as copy, delete and rename. It seems to outperform filezilla in this category.

---

### Post by matt_symes on 2011-10-04
Hi

As i completely missed the fact you want to scp to a windows boxen - must get my eyes checked - i would also suggest WinSCP.

You can, of course, also use putty.

Kind regards

---

### Post by Mistertuxedopants on 2011-10-04
> **collisionystm said:**
> Here,

You want WinSCP

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

You just punch in your servers SSH credentials and it gives you a 'Windows Explorer' Interface to browse your files and just drag them onto your desktop.

Enjoy.

worked amazing. very nice interface, very easy to you. Thank you!

Also thanks to everybody else that helped

---

