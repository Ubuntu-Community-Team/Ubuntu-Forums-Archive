---
title: "Setting up a shared storage server."
date: 2009-07-31
forum: Server Platforms
---

### Post by Alexanderfoto on 2009-07-31
Hello.
We just bought a Dell Poweredge 2900 iii to use as a shared storage server. We run a small office with three macs, and our plan is very basic, we want them all to use the server as shared storage for projects. 

We also want to have external access so we can work from home. 

How would you recommend setting this up? FTP? 

I do have some experience with Ubuntu Desktop, but no experience with the server edition what so ever. I've been Googling my eyes red for two days now, and I'm getting wiser. The main problem is that there are endless possibilites and I need some help narrowing them down to something thats good for me. 

Can anyone help me?
Thank you :)

---

### Post by TwiceOver on 2009-07-31
God I love the 2900 III we have at work.  What a beast.

I've never used a Mac so I can't be positive on any of this.

Set up Samba on your ubuntu server for file sharing.  Or if OSX supports NFS use that rather than Samba.

As for connection from the internet, you could go with FTP, or look into OpenVPN and have your users do a VPN connection.

So you have experience with desktop, but not server?  The server is command line only.  That may sound like a daunting task, but using the command line, you learn a lot.  There are also some web based tools that you can install to help manage the system visually (webmin specifically).  This way you get a "Best of both worlds" where you still have some nice GUI tools without having to install the full desktop.

---

### Post by Macchi on 2009-07-31
Samba is a quite simple and practical way to  share files between Windows, Mac and Linux clients.

For remote access to the file shares I would recommend sshfs on a high non-standard port (such as 12345). It works great on GNU/Linux and Mac OSX.
Remember though to close the standard ssh port 22 on your firewall in order to increase the security of the server.

Regarding servers I am not dogmatic about the command line. With a graphical user interface you can set up an excellent server intuitively in a few minutes. This is a better alternative for less experienced users.

---

### Post by hrod beraht on 2009-07-31
sshfs. It's dirt-simple to set up (requires nothing extra on a server that already has ssh), and it provides an encrypted connection for using it over the internet, and you can use it locally the exact same way, so it provides continuity without the need for separate local and distance solutions. You can use it to mount the server as any other drive, and it will be transparent to the user, showing up just like any other directory.

Bob

---

