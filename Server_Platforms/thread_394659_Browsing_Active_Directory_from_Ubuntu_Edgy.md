---
title: "Browsing Active Directory from Ubuntu Edgy"
date: 2007-03-27
forum: Server Platforms
---

### Post by Basotang on 2007-03-27
I have problems browsing an Active Directory of a Windows 2003 Server. (Kerberos is not used.)

The strange thing is that using smbclient, everything is fine. However, with Nautilus or trying to mount the share I am running into problems.

With smbclient, the following works fine, I can browse the share properly:

```
smbclient //server/myshare --user=username%password --workgroup=mydomain

```

When I do

```
sudo mount -t cifs //server/myshare /mountpoint -o username=username,password=password,domain=mydomain,file_mode=0777,dir_mode=0777

```
it does not report any problem. When I ls /moutpoint, it gives me the correct list of directory of the share, so far so good. However, when I try to ls /montpoint/dir1 (a valid directory on the share) then I get the same list of directory which is not correct. I can cd to /mountpoint/dir1 but ls still gives the same output than on the top level (i.e. same as ls /mountpoint).

I have read many posts and tried many different things, but it still does not work. 
First I used smbs instead of cifs, and the difference was that instead of giving the same list of top level directory of the share, it returned an input/output error when doing ls /mountpoint/dir1. 

Any help would be greatly appreciated, thanks in advance.

Seb.

---

### Post by ifeldt on 2007-03-27
I'm sure you have already tried this, but I'll do what I can.

This seems to be about connecting samba to Active Directory.  You can probably ignore the kerberos part of it. They use something called ads, which sounds promising.

**[http://www.enterprisenetworkingplanet.com/netos/article.php/3487081]("http://www.enterprisenetworkingplanet.com/netos/article.php/3487081")**

If that works, there is a single sign on using PAM that could greatly improve lifer for your linux users.

**[http://www.enterprisenetworkingplanet.com/netos/article.php/3502441]("http://www.enterprisenetworkingplanet.com/netos/article.php/3502441")**

If this didn't help at all let me know.

Ian Feldt

---

### Post by Basotang on 2007-03-27
Thanks for your quick reply Ian.
It is a much simpler setup that explained in these links: it is not about a samba server, just a simple connect from Ubuntu (as a client, not a server) to a windows share (served by a Windows 2003 server).
I am surprised that it works when I use smbclient but not with mount.cifs!

Seb.

---

### Post by ifeldt on 2007-03-27
Alright.

Here they describe using the mount.cifs command.

**[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html]("http://www.die.net/doc/linux/man/man8/mount.cifs.8.html")**

To install it, do a ```
sudo apt-get install smbfs
```

I'm not sure if this will be any help to you, but the syntax seems different enough that it looks to be worth checking out.

Ian Feldt

---

### Post by Basotang on 2007-03-29
A few more trials and internet searching later, it seems that mount.cifs does not currently support Microsoft DFS. 

I found someone with the same problems: [http://lists.samba.org/archive/linux-cifs-client/2007-March/001879.html]("http://lists.samba.org/archive/linux-cifs-client/2007-March/001879.html")

And here a post saying it is not supported: [http://lists.samba.org/archive/samba/2006-December/127890.html]("http://lists.samba.org/archive/samba/2006-December/127890.html")

Therefore the only workaround right now is to mount the shares of the DFS individualy...

Seb.

---

