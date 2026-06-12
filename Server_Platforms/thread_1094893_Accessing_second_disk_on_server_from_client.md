---
title: "Accessing second disk on server from client"
date: 2009-03-13
forum: Server Platforms
---

### Post by Trekrider58 on 2009-03-13
I have installed a second disk on my 8.10 Server and followed the solution provided in the thread below to mount it from boot up:

[http://ubuntuforums.org/showthread.php?t=686042](http://ubuntuforums.org/showthread.php?t=686042)

My second disk now loads at boot and I can use it just like any other folder on the Server.

My problem is mounting the folder that links to the disk from my client.

For a regular folder I use NFS so the command is:

sudo mount [server name]:/[folder on server] [folder on client]

If I try this for the mounted folder on the Server I get an error message that I don't have permission to do this - I presume this is because mounting the second disk is carried out as root on the Server and hence my client can't do it.

Is there some way round this or another way of accessing the second disk on my Server from my client?

---

### Post by neilevan814 on 2009-03-13
Have you tried using SSH to connect the client to the server?  I just checked on my client using ssh to my server and I can just cd to the folder to which I mounted my second drive on my server.

---

### Post by Trekrider58 on 2009-03-13
> **neilevan814 said:**
> Have you tried using SSH to connect the client to the server?  I just checked on my client using ssh to my server and I can just cd to the folder to which I mounted my second drive on my server.
Yes, I can but unfortunately this doesn't help me.

I was using SSH to connect to the primary drive on the Server and it does work. The problem with this is that I can create folders and copy files etc. but I can't open documents or spreadsheets with Open Office.

If I double click on an Open Office file from the client (using Nautilus in the GUI) I get a message asking for my user name and password - I type these in (actually the user name is auto filled) and it just comes back and asks for them again - after a couple of tries it just rejects the request and shuts down the Open Office application. That's why I changed over to mounting the folder instead.

---

### Post by Trekrider58 on 2009-03-13
Incidentally, using Nautilus (and SSH) on the Client I can copy a file from the Server onto my Client, edit it, then copy it back to the Server - but I want to be able to edit directly on the Server.

---

### Post by neilevan814 on 2009-03-13
I see Trekrider.  Well, I hope someone does have a solution for this as it would be of interest to me too.  I really only edit things in terminal using nano. Did you say you actually got a folder from the server to mount to a directory on your client?  And then you tried to use a gui app to open a document on the client and was unable to access it?  Might this be a permissions problem?

---

### Post by Trekrider58 on 2009-03-13
> **neilevan814 said:**
> I see Trekrider.  Well, I hope someone does have a solution for this as it would be of interest to me too.  I really only edit things in terminal using nano. Did you say you actually got a folder from the server to mount to a directory on your client?  And then you tried to use a gui app to open a document on the client and was unable to access it?  Might this be a permissions problem?

I expect that you are correct that it is a permissions problem but I don't know why.

If I mount a folder from my server on my client I can then access the folders and files on the server through Nautilus just as if they were on my client.

If I select Places > Connect to Server from the GUI on my client I can access the files through Nautilus (using SSH) but I can't open 'Open Office' files (asks for password but won't accept it) - I guess this is where the permissions is a problem, although I have set RWX access for User, Group and Others on the server.

This is why I want to mount the second disk - hence my original question, but this also seems to be a permissions problem. Thanks for the suggestion though.

---

### Post by Trekrider58 on 2009-03-13
What I find really annoying is that Windows clients can see the folders and open the documents with no problems at all through Samba - I would have thought that a Ubuntu Client to the Ubuntu Server would be easier to set up.:(

---

### Post by Zack McCool on 2009-03-13
There are a few items to address here...

1) NFS connection: Did you add the new mountpoint to your /etc/exports file?  Because it is a separate disk, it does not inherit the export from the main fs...

2) SSH: You know you can mount a remote volume using sshfs, right?  Not only would this solve your issues with OpenOffice, but it also will work much faster for most files than NFS or Samba, as it uses compression.

3) Samba: Why does this work, while the NFS mount doesn't?  Configuration...

Hope it helps a little...

---

### Post by Trekrider58 on 2009-03-13
> **Zack McCool said:**
> There are a few items to address here...

1) NFS connection: Did you add the new mountpoint to your /etc/exports file?  Because it is a separate disk, it does not inherit the export from the main fs...

2) SSH: You know you can mount a remote volume using sshfs, right?  Not only would this solve your issues with OpenOffice, but it also will work much faster for most files than NFS or Samba, as it uses compression.

3) Samba: Why does this work, while the NFS mount doesn't?  Configuration...

Hope it helps a little...

You are a star Zack:D

1) Oops, I forgot to change the mountpoint in /etc/exports - have now done this and have full access.

2) I thought I was using sshfs through the GUI? Can you explain more?

3) Correct - some dummy forgot to change the mountpoint (see 1) - that must be me then;)

Thanks for the help

---

### Post by Zack McCool on 2009-03-14
> **Trekrider58 said:**
> You are a star Zack:D

Glad to be able to help...

> 
2) I thought I was using sshfs through the GUI? Can you explain more?


There is a mountable ssh file system.

```
sudo apt-get install sshfs
```

then, man sshfs.  If I am mounting a remote filesystem from another linux box, I always use sshfs, as the performance is about double (on average) what I get from nfs or samba...

---

### Post by neilevan814 on 2009-03-20
Wow!  sshfs  This is just what I was looking for.  Thanks Zack McCool!  Too Cool!

---

