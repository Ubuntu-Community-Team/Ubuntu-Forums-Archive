---
title: "Filesystem causing programs not to work ( I think )"
date: 2012-03-28
forum: Server Platforms
---

### Post by marineco on 2012-03-28
So.. I am having troubles with microsoft access on our work PCs. The full post is [here]("http://www.utteraccess.com/forum/Partition-File-System-t1984638.html") on the office forums.

Short version: The back end of my database is on my new Ubuntu server. I can browse to it, edit it, delete if I wanted, so long as I do it directly. But, that's not how a split database is supposed to work. I'm supposed to connect to it through my front end.. When I try, it acts as if the back end is read only.

The best idea we have come up with so far is that Access doesn't like it's back end being put on a non-NTFS partition. (My guess, Microsoft trying to ensure more sales of their server software):evil::evil:

My solution (which I need help figuring out how to implement) is to make a small partition in the server, and set it to mount/share automatically. I'll put the backend there. But I need it to still be backed up by my dropbox, which I don't know how to change the directory.

Any help implementing this solution, or ideas for an easier one, would be very appreciated.

---

### Post by rubylaser on 2012-03-28
How are you sharing that directory (SMB/NFS) and what are the permissions on the directory?  It sounds like a file permissions issue.  You shouldn't need to use NTFS for this at all.

---

### Post by marineco on 2012-03-29
It's a SMB share. Pretty new to Linux, I haven't heard of NFS. The permissions are wide open. Everyone has complete access. When the file is accessed directly that is. It's only when we connect to this file via the front end (Client) that the problem starts.

Mini Microsoft Access lesson for any who don't know how it works, but might be able to help me if they did: 

I am working with a split database that has two parts. Somewhat of like SSH now that I think of it. It works fine on the server side, but when I go to the client side it's acting like a viewer, vs the remote control it's supposed to be. 

Innacurate, but I think it'll get the idea across. (While they coincide in this case, Server and Client in the above paragraphs refer to the files, not necessarily the machine.)

---

### Post by rubylaser on 2012-03-29
Are you sharing the SMB share as read and writeable, and does the user you're connecting with have permissions to read/write to the file?

---

### Post by marineco on 2012-03-29
Yes, I am the user. It is set to allow anybody and everybody on the network full read, write, create, delete access.

(I know, not the best for security, but I need it working first before I start tightening security)

---

### Post by marineco on 2012-04-02
It wound up being a Dropbox issue, best I can tell. I had to remove the file and folder from the Dropbox system, THEN change my permissions, and put it back in the Dropbox. For some reason, it wouldn't stick otherwise.

---

