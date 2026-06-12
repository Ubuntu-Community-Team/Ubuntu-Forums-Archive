---
title: "Samba Help"
date: 2008-08-14
forum: Server Platforms
---

### Post by kubapl on 2008-08-14
Hey I just finished following this [How-To]("http://ubuntuforums.org/showthread.php?t=202605") on setting up samba so I'd have a shared folder available to my windows computers. I see the light at the end of the tunnel but unfortunately I am having a problem trying to access the actual "shared" folder. It appears that I can access the DVD-Rom drive and the printers (it opens a blank folder with no errors and it makes sense and I have no printers installed yet on the server). Now whenever I try to access the shared folder I get an error:
```

\\SERVER\MyFiles us not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The user name could not be found.

```

And here is the screenshot: [IMG]http://kubapl.ath.cx/images/networking.jpg[/IMG]

Any ideas?

---

### Post by devonps on 2008-08-15
Can you provide a snippet of your SAMBA config file, something like this:

```

[movies]
        writable = yes
        path = /home/samba/movies
        public = yes
        only guest = yes
        printable = no
        comment = my movie collection
        create mode = 0644
        directory mode = 0755

```

This is one of my "public" shares that ALL users can access.

I don't profess to be an expert on SAMBA but I've got public shares working quite easily using the above.

Steve.

---

### Post by windependence on 2008-08-15
This post has a good basic config for a home file server. Only use this behind a good firewall as it's not the most secure config but fine for LAN use.

[http://ubuntuforums.org/showpost.php?p=5457470&postcount=14](http://ubuntuforums.org/showpost.php?p=5457470&postcount=14)

-Tim

---

### Post by kubapl on 2008-08-15
I updated my smb.config file to look like this:

```

[global]
        workgroup = domek
        server string = shared folder
        security = share
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = yes
        wins support = yes
        create mask = 0644
        directory mask = 0755
        guest ok = yes
        store dos attributes = yes
        dos filemode = yes

[shared]
        comment = shared
        path = /home/shared
        read only = no

```

Now its asking for a username and password each time I double click the computer in the networks folder. I've tried every user and pass that I can think of.

---

### Post by windependence on 2008-08-15
Change these lines:

```
security = user
map to guest = bad user

```

Then restart samba

-Tim

---

### Post by kubapl on 2008-08-15
Thanks man. Everything's working I can browse copy and paste files threw the network.

---

### Post by windependence on 2008-08-15
No problem goad to help. Hit the little star button on the lower right hand corner of my post. <shameless plug>. ;)

-Tim

---

### Post by kubapl on 2008-08-15
If I want to set up a printer also how do I install the printers drivers. I have the cd but I've never installed things off a cd. The printer in question is a HP laserjet p1005.

---

### Post by windependence on 2008-08-15
You can install the HP drivers from the repositories. HP is real good about linux. The drivers from the CD will be prompted for you when you connect a printer from a Windoze box. More later, I have to get some sleep before work. ;)

-Tim

---

### Post by kubapl on 2008-08-16
So have you waken up yet?

---

### Post by windependence on 2008-08-16
OK the drivers are already loaded in linux. If you are printing from a winows machine and have the printer attached to the Linux box, no problem, Windows will prompt you for the driver CD when you add the printer. CUPS will take care of it on the Linux side.

Here is some more info:

[http://www.freesoftwaremagazine.com/articles/printing_ubuntu](http://www.freesoftwaremagazine.com/articles/printing_ubuntu)

[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

Let me know if you need more help.

-Tim

---

