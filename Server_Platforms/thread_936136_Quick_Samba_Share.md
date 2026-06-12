---
title: "Quick Samba Share"
date: 2008-10-02
forum: Server Platforms
---

### Post by Vegan on 2008-10-02
Is there a quick and brief way to get samba to share a folder, public read/write

I wanted to be able to open the web files directly.

Then I wanted to chown the /web folder to whatever user Apache uses. So I can dump the need to chmod 777 all the time.

---

### Post by Krupski on 2008-10-02
> **Vegan said:**
> Is there a quick and brief way to get samba to share a folder, public read/write

I wanted to be able to open the web files directly.

Then I wanted to chown the /web folder to whatever user Apache uses. So I can dump the need to chmod 777 all the time.

Hopefully this will help you...

Here's my smb.conf file that I use with my in-home file server.

[COLOR="Red"]**Note that this configuration TOTALLY lacks any security.**[/COLOR] ANY Windows user can connect to the server and has full read / write / create / delete privileges. Since this is a family intranet, and since I'm behind a hardware firewall, I have no problem with security.

You should easily be able to edit a few lines to suit your needs.

My SMB.CONF file:


```

#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#
#======================= Global Settings =======================

[global]
        server string = Storage Drive
        security = SHARE
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = Yes
        wins support = Yes
        create mask = 0644
        directory mask = 0755
        guest ok = Yes
        store dos attributes = Yes
        dos filemode = Yes

[shared]
        comment = storage
        path = /home/shared
        read only = No

```


Hope this helps!

-- Roger

---

### Post by lykwydchykyn on 2008-10-02
Totally wide open:

 - change ownership of /var/www to nobody and nogroup:
```

chown -R nobody:nogroup /var/www

```
 - Makes sure everyone can party with these files:
```

chmod -R 777 /var/www

```
 - add the following to /etc/samba/smb.conf
```

[www]
path = /var/www
writeable = yes
force create mode = 0777
force directory  mode = 0777
force user = nobody
force group = nobody
guest ok = yes

```

 - Restart samba
```

invoke-rc.d samba restart

```

Just make sure if you have your web site open to the net... on second thought, don't have it open to the net.

---

### Post by Vegan on 2008-10-02
Thanks, had to tweak a tad but I have Windows able to map the share as a drive so I can more easily work with the web pages. The linux machine is hiding behind a linksys wrt54g so i am exploiting its abilities.

---

