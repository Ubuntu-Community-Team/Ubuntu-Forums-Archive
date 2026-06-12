---
title: "File sharing solution (anything BUT WebDAV)"
date: 2009-08-21
forum: Server Platforms
---

### Post by Mark20 on 2009-08-21
Hi all,

I've given up trying to use WebDAV as a file sharing solution.  It kind of works, but it's not stable (copying files into shared folder fail the majority of the time, it's glitchy, etc.), and it's gotten so bad that I've decided to use SVN until I can find something better :| Yes. SVN for file sharing :(

Essentially I would like to share directories from my server to remote clients.  The clients will then be able to access those directories from XP/Vista/Linux.  One of my Windoze users explicitly asked to be able map this directory as a network drive - so that would be nice if possible.

Does anyone know of an alternative to WebDAV that I could set up on my server?

Thanks,
Mark

---

### Post by hessiess on 2009-08-21
> **Mark20 said:**
> Hi all,

I've given up trying to use WebDAV as a file sharing solution.  It kind of works, but it's not stable (copying files into shared folder fail the majority of the time, it's glitchy, etc.), and it's gotten so bad that I've decided to use SVN until I can find something better :| Yes. SVN for file sharing :(

Essentially I would like to share directories from my server to remote clients.  The clients will then be able to access those directories from XP/Vista/Linux.  One of my Windoze users explicitly asked to be able map this directory as a network drive - so that would be nice if possible.

Does anyone know of an alternative to WebDAV that I could set up on my server?

Thanks,
Mark

sftp, can function as a file system, at least on Linux (sshfs)

---

### Post by bear24rw on 2009-08-21
use samba if you wanna be able to mount as a network drive in windows, google ubuntu samba server or something and youll get tons of hits

---

### Post by Mark20 on 2009-08-21
OK, I'll give Samba a shot - I've used it on local networks in the past so it shouldn't be too tough to set up.  I'm a little hesitant to use SFTP due to client side issues.  For example, it looks like my XP users would need to buy a program like [ExpanDrive]("http://www.expandrive.com/windows/") to be able to mount a network drive :(

Thanks for the feedback!

Mark

---

### Post by HermanAB on 2009-08-21
Uhmm, just don't run Samba over the public internet.  

I vote for SSH server.  Every self respecting machine should have a SSH Daemon running.

---

### Post by Mark20 on 2009-08-21
I've done some research, and to allow remote samba shares I'm going to need to open ports 137-139 on my router.  This is suicide :(  Does anyone know of any way to safely run a samba share which can be connected to from a remote machine?  Or if that's not possible, is there an alternative to Samba that I can use?

Thanks,
Mark

---

### Post by cwaidelich on 2009-08-21
I installed [Hamachi]("https://secure.logmein.com/products/hamachi/vpn.asp?lang=de"). It creates VPN tunnels all over the red (On Linux and Win). Then I share the files with a good configured Samba Server...

How many computers will be sharing the files?

---

### Post by HermanAB on 2009-08-21
You can tunnel Samba over SSH.  You only need to forward port 139/TCP or 445/TCP.

---

### Post by Mark20 on 2009-08-21
@HermanAB

Yeah I've been [_looking into Samba over SSL_]("http://lists.samba.org/archive/samba/2004-May/085358.html") but client side configuration is going to be brutal.  Essentially for Samba over SSL the XP clients will need to 
1) configure  a Loopback Adapter
2) set up an SSH tunnel to be able to access port 139.

This isn't a problem for me, but it's kind of a big hassle for everybody else.  There's gotta be an easier way.

@cwaidelich
Hamachi looks really useful.  I don't mean to be cheap...but I don't like the idea of paying for it, unless I absolutely need to.  I'm still a student, so I tend to try to find free solutions :)
I will have 4 people accessing the files on my server.  Sometimes they'll be at school or at home or at work.  Which is why Samba over SSL is kind of a drag because then they're gonna need to configure loopback adapters on each of their PCs, it's just too much of a hassle...

Mark

---

### Post by cwaidelich on 2009-08-21
> **Mark20 said:**
> 
@cwaidelich
Hamachi looks really useful.  I don't mean to be cheap...but I don't like the idea of paying for it, unless I absolutely need to.  I'm still a student, so I tend to try to find free solutions :)


Im using it on 15 diferent systems and we havnt payed a dime (Im a student too). It has two licences: comercial and non-comercial. Unless they stopped doing the non-comercial. (Just looked, they still do the non-comercial.)

But I get ur point :)

> I will have 4 people accessing the files on my server.  Sometimes they'll be at school or at home or at work.  Which is why Samba over SSL is kind of a drag because then they're gonna need to configure loopback adapters on each of their PCs, it's just too much of a hassle...

I wouldn't know to solve this, if they are always on diferent PCs (some of them public as I understood)...

---

### Post by Mark20 on 2009-09-02
Thanks for the suggestion cwaidelich, I ended up installing Hamachi on a couple of computers, and it works really well.  The only problem is that at my school we are only given regular user accounts on the XP desktops (non-admin).  Meaning that Hamachi is unable to install since it doesn't have the privileges to setup the virtual network interface.  We can still use Hamachi on all our home computers, but yeah it's too bad you gotta be admin to install it in XP :(

Mark

---

