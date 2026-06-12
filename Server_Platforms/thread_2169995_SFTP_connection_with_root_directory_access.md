---
title: "SFTP connection with root directory access"
date: 2013-08-24
forum: Server Platforms
---

### Post by Stefan_Luksch on 2013-08-24
Hi community,

Recently I set up a virtual machine on VMWare Workstation with Ubuntu 12.04.3 64bit.
It's running a teamspeak and a minecraft server on it.
Since I don't like the way of editing files in a Ubuntu terminal or in a telnet terminal,
I was looking forward to set up a SFTP connection with a user which has permissions on the whole server.
Well, that project pretty much failed to be honest.
So I was hoping you can give me a complete tutorial of 
"How to set up a SFTP connection with root directory access and grant all permissions".

Best Regards
Stefan

---

### Post by CharlesA on 2013-08-24
What files are you wanting to edit?

You can always login as root, but that is not sometime I would recommend.

As far as my setup goes, I created a user and gave them rwx permission on the folder I use for my website and uploads.

---

### Post by nerdtron on 2013-08-24
Set the root account password and use it to login. Or just like what CharlesA said, gice rwx permissions on the files you want to edit?

And may I know why you don't like to edit files using the terminal? It is faster and efficient since you don't have to download and reupload the files you edit.

---

### Post by CharlesA on 2013-08-25
> **nerdtron said:**
> 
And may I know why you don't like to edit files using the terminal? It is faster and efficient since you don't have to download and reupload the files you edit.

I totally agree with that. I've done it both ways and it is far easier (for me) to ssh in and mess with the files when I am testing stuff than it is to place the upload/download game.

---

