---
title: "Setting up a server for a classroom"
date: 2008-02-05
forum: Server Platforms
---

### Post by CreativeName5 on 2008-02-05
Hello I have a computer lab full of Macs at my school that the journalism class uses to put together their newspaper. The problem is they are not networked together at all so finding all the files to transfer over when when going to press is a nightmare.

What i would like to do is set up one computer to use as a server running with ubuntu that would have a folder for each person (two per computer) that they would only be able to access. I know i could probably do this with Samba, but i don't know how.

Also the computers are not connected to the internet so would i still be able to network them together to this computer without it? if not i can hook them up.

Also though it is not necessary it would be nice if this could also work as a print server.

Any help would be appreciated, thank you.

-Sean

---

### Post by HermanAB on 2008-02-05
Go to the Samba web site.  There is link to an Ubuntu specific howto guide right on the front page.  Also read the Official Howto Guide.

Cheers,

Herman

---

### Post by CreativeName5 on 2008-02-06
Yeah looking through all of that helped and gave me a general idea of what to do to get this up and running, but i don't know if i missed something but can anyone tell me how i would be able to when someone logs into the share they would see everyone's folder but they would only be able to write to their folder and only read the other ones because we have a problem with people messing with other people's files. Also there should be at least one administrator account that could acess all of them.

Thanks again
Sean

---

### Post by koenn on 2008-02-06
Probably the easiest would be to create 1 share, in which you have subdirectories for each user (eg by sharing /home). That means you only need to set up and manage 1 share - all access can be managed with filesystem permissions, 

here's a quick start. 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm)
Note that the default [homes] share in sambe only grants access to the owner - you probably want a create mask / file mode of 775 or 750 (depending on whether you want to manage read access throug group membership, or just allow 'others' to read

---

