---
title: "Samba &amp; Swat - Swat not loading pages"
date: 2012-09-03
forum: Server Platforms
---

### Post by Woolfenstien on 2012-09-03
First of all - sorry if I have posted this in the wrong support category.

OS: Ubuntu Server 12.04.1 (64-bit)

I would like to use Swat to administrate my Samba shares, printers, etc. I followed the instructions on [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat) however I have a problem that's really throwing me for a loop - pages aren't loading fully. It seems like something is making it stop dead. As such, I can't do anything with Swat.

Example: [http://i.imgur.com/l7p4K.png](http://i.imgur.com/l7p4K.png)
The HTML: [http://i.imgur.com/qF6li.png](http://i.imgur.com/qF6li.png)

The Ubuntu Server install is brand new (done today) and apart from setting up some services like SSH otherwise untouched.

My /etc/xinetd.d/swat file is as follows:
```
service swat
{

   port            = 901
   socket_type     = stream
   protocol        = tcp
   wait            = no
   user            = root
   server          = /usr/sbin/swat
   log_on_failure  += USERID
   disable         = no
   #only_from       = localhost

}

```

I have tried loading the Swat pages locally (using Lynx) and from another computer on the LAN (Using Firefox Nightly and IE9) - all show that the page is being truncated for whatever reason.

If you'd like/need more information, please ask and I'll (try) to provide.

Thanks if you can help me get to the bottom of this.

---

### Post by redmk2 on 2012-09-04
> **Woolfenstien said:**
> First of all - sorry if I have posted this in the wrong support category.

OS: Ubuntu Server 12.04.1 (64-bit)

I would like to use Swat to administrate my Samba shares, printers, etc. I followed the instructions on [https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat) however I have a problem that's really throwing me for a loop - pages aren't loading fully. It seems like something is making it stop dead. As such, I can't do anything with Swat.

Example: [http://i.imgur.com/l7p4K.png](http://i.imgur.com/l7p4K.png)
The HTML: [http://i.imgur.com/qF6li.png](http://i.imgur.com/qF6li.png)

The Ubuntu Server install is brand new (done today) and apart from setting up some services like SSH otherwise untouched.

My /etc/xinetd.d/swat file is as follows:
```
service swat
{

   port            = 901
   socket_type     = stream
   protocol        = tcp
   wait            = no
   user            = root
   server          = /usr/sbin/swat
   log_on_failure  += USERID
   disable         = no
   #only_from       = localhost

}

```

I have tried loading the Swat pages locally (using Lynx) and from another computer on the LAN (Using Firefox Nightly and IE9) - all show that the page is being truncated for whatever reason.

If you'd like/need more information, please ask and I'll (try) to provide.

Thanks if you can help me get to the bottom of this.

You are viewing the SWAT output for a user.  SWAT administration needs the root user to make changes.  The login shows the user **uiharu**.

If you understand what SWAT will provide, you should be able to edit the smb.conf file directly using any text editor.  A few examples could be```

gksudo gedit /etc/samba/smb,conf

sudo nano /etc/samba/smb,conf

sudo vim /etc/samba/smb,conf
```

... The first example uses a basic GUI based text editor while the next two are terminal based text editors.

---

### Post by Woolfenstien on 2012-09-04
That user is in the sudoers, is part of the administrators group and has read and write permissions to the smb.conf, and has access to the administrator functions of Swat (only four icons show if a regular user logs in).

However I did try running as root ('sudo -i; passwd' to set a password then logged in via the web GUI), and exactly the same thing happens. I've since returned the root account to the state it was in before this.

I'm aware I can manually make my own smb.conf, but I'd prefer to have a program do it and check it for me. As it's a part of Samba I don't see why I shouldn't be able to use it to make a good configuration file quickly - it's only for a home network. More importantly, if this isn't a problem with Swat but instead with another package then I'd like to know what's going wrong still, in case this affects anything else.

---

### Post by redmk2 on 2012-09-04
> **Woolfenstien said:**
> That user is in the sudoers, is part of the administrators group and has read and write permissions to the smb.conf, and has access to the administrator functions of Swat (only four icons show if a regular user logs in).

However I did try running as root ('sudo -i; passwd' to set a password then logged in via the web GUI), and exactly the same thing happens. I've since returned the root account to the state it was in before this.

I'm aware I can manually make my own smb.conf, but I'd prefer to have a program do it and check it for me. As it's a part of Samba I don't see why I shouldn't be able to use it to make a good configuration file quickly - it's only for a home network. More importantly, if this isn't a problem with Swat but instead with another package then I'd like to know what's going wrong still, in case this affects anything else.

I have to admit I haven't used SWAT for quite a few years.  My impression is that it is not really current.  Something for you to think about is the notes from synaptics view of SWAT```
SWAT is **no longer actively maintained**, and its default configuration is
not secure for use over an untrusted network.  [B]SWAT will also rewrite
smb.conf, rearranging the entries and deleting all comments as well as
include= and copy= options[[/B], so is not suitable for use in conjunction
with hand-edited smb.conf files or the default package-managed
configuration.
```

If you do decide to edit the smb.conf file with text editor you can test your changes with ```
testparm 
```...If you want a reference to all the parameters you can see them [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") or at ```
man smb.conf
```

---

### Post by Woolfenstien on 2012-09-04
If Swat is indeed not maintained anymore, then that would probably explain the problems I was having. Thanks for that, and for the testparm recommendation. I'll have a look at the man pages and roll my own smb.conf.

---

### Post by redmk2 on 2012-09-04
> **Woolfenstien said:**
> If Swat is indeed not maintained anymore, then that would probably explain the problems I was having. Thanks for that, and for the testparm recommendation. I'll have a look at the man pages and roll my own smb.conf.

I would say that is a good idea.  One thing you should be aware of: The defaults that are used are only modified by the smb.conf file.  By that I mean there are more parameters than are shown by the smb.conf file.  Try running the following to see entire set of defaults```
testparm -v
```

Very few of the parameters need changing (via smb,conf).  For a small network I would start by just adding a share to the end of the smb.conf file.  See here for a [**_[COLOR="Blue"]basic[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=3781") set up.

The only thing I do differently is I make all my shares at /smb/[some_share] rather than in my home directory.  Either way will work though.

---

