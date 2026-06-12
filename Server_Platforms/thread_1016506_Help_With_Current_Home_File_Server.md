---
title: "Help With Current Home File Server"
date: 2008-12-20
forum: Server Platforms
---

### Post by falconed7 on 2008-12-20
Hey everyone!

I have just installed Ubuntu server (8.04.1) onto a cheap build and am going to be using it as a home file server.

I am following [this guide click here (from howtoforge)]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") and am using PuTTY to access the server.

I get up to this bit:

```

echo server1.example.com > /etc/hostname
/etc/init.d/hostname.sh start
```

I type in the top line and it says:

```
-bash: /etc/hostname: Permission Denied.
```

My /etc/network/interfaces looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.17
 netmask 255.255.255.0
 gateway 192.168.0.1
```

And my /etc/hosts looks like this:
```
127.0.0.1  localhost
192.168.0.17    wrongserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts#
```

I know they have domains in the example, however, I don't recall setting a domain. Do I just make this up now?

Any Help will be great!

I can assure you there will be more to come so I'll use this thread.

---

### Post by lykwydchykyn on 2008-12-20
Unless you actually have a domain (or, more to the point, a DNS server with a record for your server), there isn't much point setting a domain.  /etc/hostname is the file that contains the hostname information for your server, so whatever you put in that file is the hostname of the machine.  If you use a fully qualified domain name, it also sets the domain of the machine.

Any file outside of your home directory is probably owned by root (or some other system user), so you need to use sudo when writing to it, e.g.

```

sudo echo mycomputer.somedomain.not > /etc/hostname

```

---

### Post by falconed7 on 2008-12-20
> **lykwydchykyn said:**
> Any file outside of your home directory is probably owned by root (or some other system user), so you need to use sudo when writing to it, e.g.

```

sudo echo mycomputer.somedomain.not > /etc/hostname

```

Sorry I should have said; I did write it with sudo and still get the same error message.

EDIT: I have 2 HDDs: 1 80GB which the server is installed on, and a 750GB with I would like my data stored on. However, I used "guided - Use whole disk" When in installation and chose the 80GB drive. So I now think I have the 750GB drive installed but it's not formatted. Would this be right?

---

### Post by lykwydchykyn on 2008-12-20
> **falconed7 said:**
> Sorry I should have said; I did write it with sudo and still get the same error message.

Ah yes... you are correct.  I forgot that redirecting with sudo is a bit tricky.  I can't remember how to do it correctly. 

The cheating way is to just do "sudo -s" and get a root prompt, then you can redirect as you wish.

The other way is to just edit the file ("sudo nano /etc/hostname") and type what you need into it.

---

### Post by falconed7 on 2008-12-20
> **lykwydchykyn said:**
> Ah yes... you are correct.  I forgot that redirecting with sudo is a bit tricky.  I can't remember how to do it correctly. 

The cheating way is to just do "sudo -s" and get a root prompt, then you can redirect as you wish.

The other way is to just edit the file ("sudo nano /etc/hostname") and type what you need into it.

Okay editing sounds easiest, would I just write:
```
echo wrongserver > /etc/hostname
```
into it?

Also what does this command actually do?

---

### Post by lykwydchykyn on 2008-12-20
No, you'd just type "wrongserver" (without quotes).

echo merely repeats back whatever argument you give it.  Try it -- type "echo blah" at the console.

The ">" is called a redirect, it takes whatever the output of your command would have been and sticks it into a file (the file named after the redirect).

So "echo wrongserver > /etc/hostname" is the same as opening /etc/hostname in a text editor and typeing "wrongserver" into it.  It's just faster, and people can copy & paste it into the terminal.

---

### Post by falconed7 on 2008-12-20
Thank you for the explanation.

I checked the file and it already had "wrongserver" in it, so I didn't have to do anything, haha.

Sorry for all of the questions but onto my next one.

I have installed 2 HDDs in the PC and using the "Guided - Use entire disk" option, I installed the OS onto the 80GB. I have a feeling I should have done something else (ie. use "Manual" partition) as now I think my 750GB (for data) is unformatted. Would this be right?

For this section I am not following the guide because I didn't want to format in NTFS as I wouldn't be accessing it from Windows or placing it in a Windows machine.

Am I right in saying that what I need to do now is format and mount the data HDD?

I'll post my fstab if it helps:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f0b9914d-5cc3-4d80-b6dd-23f5918fc932 /               ext3    relatime,erro$
# /dev/sda5
UUID=2f1c486b-6b1f-4e14-9b11-385aa558ada5 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by lykwydchykyn on 2008-12-20
You did fine, though 80 GB will mostly go to waste as the system drive (for a server with no GUI, 10 GB is more than you'll ever use for at least a few years).

You can easily format the 750 GB drive after the fact and mount it whereever you want.

 - First, you need to create a partition.  I recommend using cfdisk, it's pretty easy.  If you have a GUI gparted is a good choice.
 - Next, you need to format the partition.  You can do this in gparted if you're using that, or with the mkfs command.  I would recommend using ext3 to format the partition, so the command would be:
```

sudo mkfs.ext3 /dev/sdb1

```
(that's assuming your drive is /dev/sdb and you only have one partition -- make sure you KNOW what the drive is before you issue this command).

 - Then, you need to mount the drive to a directory.  If this is shared server data, and you care to comply with the [FHS]("http://www.pathname.com/fhs/"), I would recommend mounting it to /srv.  The fstab line would read:
```

/dev/sdb1    /srv    ext3    defaults,acl,noatime   0   0

```
The "acl,noatime" bit is optional.  (acl gives you the ability to use more complex permissions setups, and noatime speeds things up a bit by not recording access times)  Note there are no spaces between those items.

Once you've done that, just issue "mount /srv" and it should be up.  You may want to reboot to make sure it gets mounted properly when the server reboots.

---

### Post by falconed7 on 2008-12-20
Thanks guys! I'm getting there!

I have formatted, partitioned and mounted my HDD.

I am following this to setup samba sharing.
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I have configured my samba.conf file like so:
```
[global]
    ; General server settings
    netbios name = wrongserver
    server string =
    workgroup = WRONGGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBU$

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

[share]
    path = /media/share/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = jamie
    force group = jamie
```

I have also added two users "jamie" (me) and "family" and enabled them.

I can currently see "wrongserver" in my network on my Windows Vista machine, however, I cannot connect or map a network drive as it gives me this error:
[http://img367.imageshack.us/img367/339/capture1kt0.jpg](http://img367.imageshack.us/img367/339/capture1kt0.jpg)

Supposedly it cannot find the share.

Is there something wrong with my smb.conf?

---

### Post by lykwydchykyn on 2008-12-20
You would connect to \\192.168.0.17\share, not \\192.168.0.17\media\share.

[share] is the name of your share, that's the folder you'd see if you browsed to the server.

/media/share is the local path to where you're sharing.  The clients don't see that.

---

