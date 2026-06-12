---
title: "Remote User Write Privileges"
date: 2009-04-13
forum: Server Platforms
---

### Post by drsox1899 on 2009-04-13
I'm new to Servers, but I have built a home made NAS with Ubuntu 8.10 server in it to run my Music collection - OK so far !

Now I am adding Video and have setup a Netgear EVA8000 to access the Video share on the NAS by adding it as a Samba user.  Reads fine, but the EVA8000 also wants to write some library data every now and then.

I've set up a share for it to write to and chmod the share to 0777, but the message comes back "Unable to write to the share"

I haven't added the EVA8000 to the users list so can't login as it - is this what I should be doing ?  How do I do this in the Server version of 8.10 ?  In the GUI version of 8.10 I know how to do it.

Thanks.

---

### Post by cdenley on 2009-04-13
How did you configure the share? In order to write to the share, the share must be writable in samba, and the user must have write permission with the filesystem and the samba share.

---

### Post by drsox1899 on 2009-04-13
Thanks.

I did two things :

1. I made the share, in this case, /EVA8000, chmodded with 0777.

sudo mkdir /EVA8000
sudo chmod 0777 /EVA8000

2. Then I added the user with the following :

sudo useradd -s /bin/true newuser
sudo smbpasswd -L -a newuser
sudo smbpasswd -L -e newuser

This is following the HowTo in this forum thread :

[http://ubuntuforums.org/showthread.php?t=799712&highlight=Build+Headless+Remote+Bit+Torrent+BT+Azureus+NAS+Samba+Webserver+FTP](http://ubuntuforums.org/showthread.php?t=799712&highlight=Build+Headless+Remote+Bit+Torrent+BT+Azureus+NAS+Samba+Webserver+FTP)


That's all I did.  I'm sure there's some more steps I should be following though !

---

### Post by cdenley on 2009-04-13
If you could read /EVA8000 remotely, you must've edited /etc/samba/smb.conf or created a usershare in /var/lib/samba/usershares, or did I mis-read your post? Post your smb.conf file.

---

### Post by drsox1899 on 2009-04-13
Here's the smb.conf file :

[global]
    ; General server settings
    netbios name = Pippin
    server string = NSK1380
    workgroup = Felix
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

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
;    valid users = %S
;    create mode = 0600
;    directory mode = 0755
;    browseable = no
;    read only = no
;    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no


; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes



[UMusic]
    path = /Music/UMusic
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = yourlogin
;    force group = yourlogin

[UVideo]
    path = /Video/UVideo
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = yourlogin
;    force group = yourlogin


[EVA8000]
    path = /EVA8000
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = yourlogin
;    force group = yourlogin
;    force group = yourlogin

---

### Post by cdenley on 2009-04-13
```

[EVA8000]
path = /EVA8000
browseable = yes
read only = no
guest ok = no
[B]create mask = 0644
directory mask = 0755[/B]

```
According to the permissions you gave for the share, only the owner can write to anything. Either change those permissions, or login as the owner.

---

### Post by drsox1899 on 2009-04-13
So if I change 

        guest ok = no

to

        guest ok = yes

it should work OK ?

---

### Post by cdenley on 2009-04-13
> **drsox1899 said:**
> So if I change 

        guest ok = no

to

        guest ok = yes

it should work OK ?

That's not what I put in bold. If you want to allow all users who can currenty read the share to be able to write to the share, assuming your filesystem permissions permit this:
```

[EVA8000]
path = /EVA8000
browseable = yes
read only = no
guest ok = no
[B]create mask = 0666
directory mask = 0777[/B]

```

---

### Post by drsox1899 on 2009-04-13
Sorry, didn't see the emboldening.

I made the changes and still I can't get the EVA8000 to write to the location.

---

### Post by cdenley on 2009-04-13
> **drsox1899 said:**
> Sorry, didn't see the emboldening.

I made the changes and still I can't get the EVA8000 to write to the location.
Did you reload the configuration?
```

sudo /etc/init.d/samba reload

```

---

### Post by drsox1899 on 2009-04-13
Yes, I did that.  I also reset the Windows networking and that also seemed to solve the problem.

It seems that the EVA8000 can now write to that location. 

Thanks very much

---

