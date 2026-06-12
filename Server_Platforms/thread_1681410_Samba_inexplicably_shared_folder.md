---
title: "Samba: inexplicably shared folder"
date: 2011-02-04
forum: Server Platforms
---

### Post by ceb on 2011-02-04
Hi,

I have a puzzling samba problem!

If I connect to my Ubuntu 10.04 LTS machine from a windows machine (i.e. type "\\ubuntu-machine-name" into Windows Explorer), I see a folder called "abc" (i.e. \\ubuntu-machine-name\abc). This is a real folder on my Ubuntu machine (/mnt/xyz, which I created and use), but I do not remember ever sharing it. I was surprised, because I was not expecting any shares on this machine.

In fact, if I look in \etc\samba\smb.conf, the folder is not mentioned (there is no mention of "/mnt/xyz" or "abc" or in fact any other shares, as expected). It is also not listed in the Samba Server Configuration Tool (no shares are listed, as expected). Further, if I right click on the /mnt/xyz folder, I see the "Share this folder" option is not selected.

Anyone got any ideas how this folder might be being shared?

Thanks!

Chris

---

### Post by luvshines on 2011-02-06
What does following say```

# List the shares
smbclient -L locahost -U%
```

---

### Post by ceb on 2011-02-06
Thanks for the help!

> **luvshines said:**
> What does following say```

# List the shares
smbclient -L locahost -U%
```


Here it is:

```
$ smbclient -L localhost -U%
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (ubuntu-machine-name server (Samba, Ubuntu))
        abc             Disk      No comment
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

        Server               Comment
        ---------            -------
        DEF                  A comment
        GHI                  Another comment
        UBUNTU-MACHINE-NAME  ubuntu-machine-name server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            DEF



```

(I'm replacing actual machine names with fake ones; in the above, mine is ubuntu-machine-name.)

The share abc is not listed in /etc/samba/smb.conf (no shares are listed, in fact). If I add a share to smb.conf and restart smbd, the new share does appear (and disappears when I remove it from smb.conf). I'm really puzzled! Is there some other mechanism I could have used to share the folder? As I said, right clicking on the folder also indicates that it's not shared.

In case it's important, this machine first had 8.04 LTS and was upgraded to 10.04 LTS at some point in the past. 


Chris

---

### Post by luvshines on 2011-02-06
smbclient output shows that it is shared :)
Maybe it was shared with 'net usershare'. Does the following show anything```

sudo net usershare list --long

sudo ll /var/lib/samba/usershares
```

---

### Post by ceb on 2011-02-06
> **luvshines said:**
> smbclient output shows that it is shared :)
Maybe it was shared with 'net usershare'. Does the following show anything```

sudo net usershare list --long

sudo ll /var/lib/samba/usershares
```


```
$ sudo net usershare list --long
abc
$ sudo ls /var/lib/samba/usershares
abc
```


I didn't know about this. Following the advice at [http://www.experts-exchange.com/Software/Server_Software/File_Servers/Samba/Q_24065850.html](http://www.experts-exchange.com/Software/Server_Software/File_Servers/Samba/Q_24065850.html) (scroll right to the bottom of the page if you want to see it), I deleted /var/lib/samba/usershares/abc, and now the mysterious share has vanished.

I'm the only user of this machine. While I can believe I created a share somehow and forgot about it, I don't understand why right clicking on the folder indicated that it wasn't shared. In any case, my problem is solved.

Thanks for your help!

Chris

---

