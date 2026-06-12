---
title: "proftpd Problem"
date: 2011-10-12
forum: Server Platforms
---

### Post by dingdongsilver on 2011-10-12
Ubuntu 11.04

Installed and configured proftpd.  Use two folders, Upload and Download.  From a ftp client, google chrome and windows explorer everything works fine and displays correctly.  Internet explorer, however, displays the entire root folder structure of the linux server.  Anybody experience this before or have any ideas on where to start troubleshooting?  Thanks.

---

### Post by Dangertux on 2011-10-12
This is actually an Internet Explorer 6/7 issue, you can read more about it and workarounds here : [http://support.microsoft.com/kb/941896](http://support.microsoft.com/kb/941896)

---

### Post by Jonathan L on 2011-10-12
> **dingdongsilver said:**
> Ubuntu 11.04

Installed and configured proftpd.  Use two folders, Upload and Download.  From a ftp client, google chrome and windows explorer everything works fine and displays correctly.  Internet explorer, however, displays the entire root folder structure of the linux server.  Anybody experience this before or have any ideas on where to start troubleshooting?  Thanks.

Hi Dingdong

From the description of the bug at Microsoft, it sounds to me as though you might be able to work around this by a chroot on the ftp server, instead of patches to the client which perhaps aren't under your control.  Perhaps have /somewhere/upload and /somewhere/download, do a chroot to /somewhere.  I'm guessing the Microsoft bug would put you with the listing of /somewhere.

[http://www.proftpd.org/localsite/Userguide/linked/chroot.html#AEN715](http://www.proftpd.org/localsite/Userguide/linked/chroot.html#AEN715)

Just a thought.

Kind regards
Jonathan

---

### Post by dingdongsilver on 2011-10-14
Thanks for the replies.  Can't to anything to the client browsers since I have no access to them.  

Jonathon I looked at doing chroot.  The command I tried to issue was:

```
$chroot --userspec=userftp:userftp /home/FTP-shared
```

I get an invalid user response.  I looked in /etc/passwd and userftp is there.  Did ```
$groups userftp
``` and got a group for it.  Any idea about that?

Also, if I do the chroot for the user will I have to have a /dev /etc /bin and other such directories under /home/FTP-shared?

---

### Post by Jonathan L on 2011-10-25
> **dingdongsilver said:**
> Thanks for the replies.  Can't to anything to the client browsers since I have no access to them.  

Jonathon I looked at doing chroot.  The command I tried to issue was:

```
$chroot --userspec=userftp:userftp /home/FTP-shared
```I get an invalid user response.  I looked in /etc/passwd and userftp is there.  Did ```
$groups userftp
``` and got a group for it.  Any idea about that?

Also, if I do the chroot for the user will I have to have a /dev /etc /bin and other such directories under /home/FTP-shared?

Hi ...

I was thinking of the <virtualhost ...> command inside proftp, per the link I gave, rather than the chroot command at the shell prompt (which will be difficult for a number of reasons).

The example there seemed exactly what you wanted to do:
[FONT=Arial][SIZE=1]```
[/SIZE][/FONT][FONT=Arial][SIZE=1]<VirtualHost myhost.mynet.foo>
DefaultRoot ~
</VirtualHost>[/SIZE][/FONT][FONT=Arial][SIZE=1]
```[/SIZE][/FONT]

Any use?

Kind regards,
Jonathan.

---

