---
title: "Samba NOT allowing access to folders"
date: 2006-10-31
forum: Server Platforms
---

### Post by cocotu on 2006-10-31
Hello all!, maybe we all can learn from this thread as I will write all the steps I have taken so far in order to set up Samba here at work for File server purposes. This is the first time I touch Samba, sorry for any misunderstandings.

I'm testing this in a computer lab with a workgroup called: Lab

This my smb.conf file:

#Global Parameters

workgroup= Lab
netbios name= Samba
security= SHARE
#encrypt passwords= yes

[homes]
read only= no
browseable= no

[music]
path= /data/mp3
browseable= yes
write list= xrgm, gts18,rguisbert

[everyone]
path= /data/everyone
read only= no
browseable= yes

[apps]
path= /data/apps
browseable= yes
valid users= @admins, root
write list= @admins, root

This is what happens with this command:
xrgm@XubuntuLab:/etc$ sudo netstat -plant | grep LISTEN
tcp        0      0 127.0.0.1:4228          0.0.0.0:*   LISTEN 4181/hpiod 
tcp        0      0 127.0.0.1:1638          0.0.0.0:*   LISTEN 4184/python 
tcp        0      0 0.0.0.0:139             0.0.0.0:*   LISTEN 5133/smbd 
tcp        0      0 0.0.0.0:1458            0.0.0.0:*   LISTEN 5182/nc 
tcp        0      0 127.0.0.1:631           0.0.0.0:*   LISTEN 4746/cupsd 
tcp        0      0 0.0.0.0:445             0.0.0.0:*   LISTEN 5133/smbd 
tcp6       0      0 :::22                   :::*        LISTEN 4506/sshd 

This is what happens when I add smbclient:
By using the command: smbclient -U rguisbert -L SAMBA

Domain=[LAB] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        music           Disk
        everyone        Disk
        apps            Disk
        IPC$            IPC       IPC Service (Samba 3.0.22)
        ADMIN$          IPC       IPC Service (Samba 3.0.22)
Domain=[LAB] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        LAB4                 Computer Lab
        SAMBA                Samba 3.0.22

        Workgroup            Master
        ---------            -------
        LAB                  LAB4

When I try to access the folder **apps** from my WinXP machine I get a prompt:

user: \\Samba\gwguest
password:

There is no username gwguest in my WinXP machine or in the Linux box! I tried many password and nothing

When I try to access the folders **everyone and music** from my WinXP machine I get:

\\Samba\music is not accessible. You might not have permission to use this network resource. Contact the network administrator of this server to find out if you have access permissions.

Same case for the **everyone** folder.

I did: 
1. Restart Samba
2. sudo useradd rguisbert
3. sudo smbpasswd -a rguisbert

And repeated this for all users. What is the problem?? We want to make a swicth to Linux but it seems very confusing!!

thanks...

---

