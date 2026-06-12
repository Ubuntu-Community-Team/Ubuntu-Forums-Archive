---
title: "[samba] delete share using script or command"
date: 2008-05-06
forum: Server Platforms
---

### Post by nulele on 2008-05-06
Hi,
I want to delete a Samba share from the smb.conf file through a script or command.
I checked on the internet and found this command:

*net share delete sharename*

Nice and easy, but doesen't work. Nothing happens. I'm asked for a password that I leave blank and that's all.

I also tried this one:

*net share sharename /D*

but it definitely does not seem to be a command the shell likes!
The weird thing is that if I only enter

*net share*

the command works and I see the list of all Samba shares...

Can anyone help me? Thanks

---

### Post by cdenley on 2008-05-06
I don't think there is a command that will edit smb.conf for you. I think the "net share delete sharename" option is there for windows servers. If you created a usershare through nautilus, then you can delete that.

```
net usershare delete share_name
```

---

### Post by njparton on 2008-05-06
The samba config file is quite easy to read and all your shares are normally appended to the bottom.  I'd edit it manually, unless of course you don't have access or root privelidges?

---

### Post by nulele on 2008-05-07
> **cdenley said:**
> I don't think there is a command that will edit smb.conf for you. I think the "net share delete sharename" option is there for windows servers. If you created a usershare through nautilus, then you can delete that.

```
net usershare delete share_name
```

Doh!! 
So I have to find another way to remove shares automatically... I'll read up on usershare as you suggest.
Thank you!

---

### Post by njparton on 2008-05-07
Don't be afraid of editing config files if you have access to them!

---

### Post by nulele on 2008-05-07
> **njparton said:**
> Don't be afraid of editing config files if you have access to them!

Yes I have total access to the server ad smb.conf... but I need to edit it automatically because I've been developing a PHP web user interface for creating/updating/deleting ftp users.

---

### Post by jimbo99 on 2008-11-15
As of Hardy Heron and up, not all shares are listed there.  It depends on how you created the share.  With Hardy Heron/Intrepid Ibex they put in a hodgepodge of ways to create shares and they are extremely confusing to most.

I would not recommend telling everyone that all their answers are in a config file.  And, it is important that these shares be under the roof of one program.  That program should find all shares and allow full modification of the shares with a few clicks of a mouse.  The world of networking has been made a little more difficult by Canonical.

---

### Post by noletolucas on 2010-06-01
> **jimbo99 said:**
> As of Hardy Heron and up, not all shares are listed there.  It depends on how you created the share.  With Hardy Heron/Intrepid Ibex they put in a hodgepodge of ways to create shares and they are extremely confusing to most.

I would not recommend telling everyone that all their answers are in a config file.  And, it is important that these shares be under the roof of one program.  That program should find all shares and allow full modification of the shares with a few clicks of a mouse.  The world of networking has been made a little more difficult by Canonical.

applause. totally agree.

if you create the share using Nautilus through right-clicking the folder and 'Share folder' this sharing doesn't go to this file.

least not for me on Ubuntu 9.04

---

### Post by noletolucas on 2010-06-01
The info may be in /var/lib/samba/usershares diretory.

It holds all my shares.

---

### Post by Ryan Dwyer on 2010-06-01
This thread was made over two years ago. Please don't post in old threads.

---

### Post by zerin on 2010-09-09
hey! this old thread was useful for me just now. i found it on top of the list cause i had the same problem, fixed it in a jiffy. i used nautilus to creaet my share and quickly deleted it with 

"sudo net usershare delete share_name"

---

