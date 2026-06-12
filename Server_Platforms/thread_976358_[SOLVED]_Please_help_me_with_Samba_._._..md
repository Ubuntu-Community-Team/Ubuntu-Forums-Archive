---
title: "[SOLVED] Please help me with Samba . . ."
date: 2008-11-09
forum: Server Platforms
---

### Post by madhartigan on 2008-11-09
Hi there.

I've been quite successful dealing with building my Ubuntu server and getting it just the way I'd like it.

The problem I've run into is when I try to use Samba.

I'm trying to access the Ubuntu server from Vista Ultimate x64 and I'm simply unable to get to it.  I get to the Vista logon screen to access the remote drive and it won't let me through.

I've totally bunged up my smb.conf file so if someone could post a blank template of the default one, I'd appreciate that as a starting point.

Also, if anyone could "hand-hold" me through the troubleshooting of this, I'd really appreciate it.

I'd love to be able to "reset" my server's samba installation to what it would be like if I had just installed Samba so I can start from scratch.

TIA for any help.

-Darryl

---

### Post by Sef on 2008-11-09
Moved to server platforms.

---

### Post by NullHead on 2008-11-09
Have you tried ```
sudo dpkg-reconfigure samba
```

---

### Post by gpsmikey on 2008-11-09
You might want to check out "Samba 3 by Example" -- the pdf version of the book is at 
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
They have many examples in there and you can pick one that comes close to what you want and modify it for your use.  I have the paper copy I purchased from Amazon.com before I found the pdf version.  He explains why things work and why they don't ](*,)

I don't have Vista (neither Vista nor AOL are allowed in the house ! ), but XP seems to be able to talk to it fine here. You need to make sure the accounts match between Vista and Samba and that you added the account/password in Samba.

mikey

---

### Post by madhartigan on 2008-11-09
> **NullHead said:**
> Have you tried ```
sudo dpkg-reconfigure samba
```

I'll give that a shot.

I just did an "apt-get purge samba" so I'm hoping that removed everything.

EDIT: dpkg-reconfigure samba does not rewrite the smb.conf file.  It allows me to reset everything besides that file.

> **gpsmikey said:**
> You might want to check out "Samba 3 by Example" -- the pdf version of the book is at 
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
They have many examples in there and you can pick one that comes close to what you want and modify it for your use.  I have the paper copy I purchased from Amazon.com before I found the pdf version.  He explains why things work and why they don't ](*,)

I don't have Vista (neither Vista nor AOL are allowed in the house ! ), but XP seems to be able to talk to it fine here. You need to make sure the accounts match between Vista and Samba and that you added the account/password in Samba.

mikey


Thank you for the great link.  I'll read through that and see if it solves my problem.  I also found that with Vista there's an issue with how Vista does authentication and you have to edit the secpol.msc.

More on that once I solve my problem.  I don't want to expound on one thing that I've learned if it doesn't solve my problem in the long run.

Thanks again!!

---

### Post by oceallaighm on 2008-11-09
I just wanted to say that I have Samba running on Ubuntu Server 8.04 x86 and I was able to map network drives from both Windows XP Pro. and Vista Home Premium, obviously using Samba as a Workgroup.

Samba is all that I am running on the old AMD Athlon Thunderbird box. I found the following site [http://www.howtoforge.com/](http://www.howtoforge.com/) very helpful in both installing Ubuntu Server 8.04 and Samba. I just followed the instructions.

---

### Post by madhartigan on 2008-11-09
Well, as it turns out, my issue for letting Vista talk with the Samba share was simply following this fix:

[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)


In addition, I hadn't realized that the user I had created did not have ownership of the folder I was trying to share, so once I got to the folder through Vista, I was unable to create folders or paste things into it.


Once I did the chown, everything worked out great!!

Thanks for the tips!!

---

### Post by madhartigan on 2008-11-09
Well, as it turns out, my issue for letting Vista talk with the Samba share was simply following this fix:

[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)


In addition, I hadn't realized that the user I had created did not have ownership of the folder I was trying to share, so once I got to the folder through Vista, I was unable to create folders or paste things into it.


Once I did the chown, everything worked out great!!

Thanks for the tips!!

---

