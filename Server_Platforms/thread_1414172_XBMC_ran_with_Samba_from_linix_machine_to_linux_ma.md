---
title: "XBMC ran with Samba from linix machine to linux machine help please"
date: 2010-02-23
forum: Server Platforms
---

### Post by Shiloh Hawkesworth on 2010-02-23
I am trying to get XBMC (the program, not am Xbox) up and running and I am having some issues... 

I have Karmic installed on my home computer (the home computer is going to act as my server because it holds my files)... I also have Karmic installed on an Asrock nettop ([http://www.asrock.com/nettop/overview.asp?Model=ION%20330HT-BD](http://www.asrock.com/nettop/overview.asp?Model=ION%20330HT-BD))... 

My goal here is to be able to add the "source" location on my home computer to the Asrock machine... Both have XBMC installed on them... I have the Asrock hooked up to my TV as a media canter... 

I can not seem to get the home machine visible to the Asrock machine... I have Samba installed on the home machine... Here is a copy of my conf file:

[global]
    ; General server settings
    netbios name = shiloh
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

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
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = shiloh
    force group = shiloh


Am I supposed to have Samba installed on both machines or just the "server" machine?

The only hang up  can't seem to figure out is the sharing aspect of this... All the posts I have read seem to talk about how to share from a windows machine to a linux, but not from Linux machine to Linux machine... In playing with this I was able to add a server connection between the two with ssh, but that does not get me by because the XBMC machine can't see the ssh connection... It needs to be a SMB share...

Any help on this would be greatly appreciated...

---

### Post by Morbius1 on 2010-02-23
> [MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    [COLOR=Blue]guest ok = no[/COLOR]
    create mask = 0644
    directory mask = 0755
    force user = shiloh
    force group = shilohYou have that share set up to not allow guest access. That means the clients will have to provide a username and password. So the two big questions are:

(1) Have you set up a samba user on the server corresponding to the client user?

You can do that this way:

Open **Terminal**
Type **sudo useradd -s /bin/true *client-user-name***
[COLOR=Blue]*This will create a linux user on the server that has no server logon capability and no server home directory.*[/COLOR]

Type **sudo smbpasswd -a *client-user-name***
This will add AND enable a samba user and password for the client.

(2) Is the Asrock set up to provide to the server the username and password when requested?

---

### Post by gobbledigook on 2010-02-23
i would suggest installing samba on both machines if it is not already, then try connecting again. once you have a connection established to the folders you wish to share, its pretty straightforward to add them via  "add source" in the xbmc gui :)

---

### Post by Shiloh Hawkesworth on 2010-02-23
I was suggested by someone to install XBMC live as a stand alone and get away from the Ubuntu background OS... 

I am building this as a media canter... Would installing XBMC as a stand alone be better/easier?

---

### Post by gobbledigook on 2010-02-23
i've no experience with the standalone install, but it could be restrictive if you decide to use your server for something else at a later date.

Try the xbmc live cd for a while and see how you get on :)

---

### Post by Shiloh Hawkesworth on 2010-02-23
(2) Is the Asrock set up to provide to the server the username and password when requested?[/QUOTE]

It is my understanding XBMC provides that info when I create the link in XBMC... I have to give a username and password to connect to the SMB drive... 
Is that correct?

---

