---
title: "Samba shares not showing up in clients, but can access through IP"
date: 2017-08-31
forum: Server Platforms
---

### Post by jayj2291 on 2017-08-31
Hey all,

I am having a little trouble getting my LAN devices to see my samba share folder. Here is the setup:

I have a  server running ubuntu server 16.04 LTS (xenial) and Samba version 4.3.11-Ubuntu
My laptop running lubuntu desktop (ubuntu 17.04 zesty)
Another laptop running windows 8.1
and various other phones and tv's etc...

I can(not) access the folders in the following ways:

[Lubuntu] (using PCManFM)
[LIST]
[*]Navigating to smb://<server_ip>/share works. I have since bookmarked this folder. But i have to log in (even if anonymously without password)
[*]Browsing Network > Windows Network (only folder) > SMB:///. it is empty even after 15 minutes of loading and timing out.
[/LIST]

[Windows]
[LIST]
[*]Navigating to \\<server_ip> shows the shared folder. - no login prompt required
[/LIST]

Browsing to:
[LIST]
[*]Network > Computers = Windows PC ONLY
[*]Network > Media Devices = Router 1 & Router 2 (I have another router set up as a wifi repeater and ethernet switch which has never caused any problems for years)
[*]Network > Network infrastructure = Router 1 & Router 2
[/LIST]

[Android Phone] (using ES File Explorer)
[LIST]
[*]I can see both routers AND the samba server (although the routers have a FTP icon and the samba has an SFTP icon)
[/LIST]

[Smart TV]
[LIST]
[*]Can only see router 1 & Router 2 as media devices
[/LIST]


So I guess my question is: My samba server is working in terms of file sharing and permissions as i can access (directly) and create/ edit files. But is there a way where I can have my samba share detected and displayed in my devices (other than my android) such as my tv, windows and lubuntu laptop without having to directly type in an ip address? I want this folder to be fully open and accessible (I understand the risks of exposure to those on my LAN).

Note: smbtree command does nothing on either server or lubuntu laptop.

Many thanks in advance,

- Jay

---

### Post by darkod on 2017-09-01
Well, there are couple of different things here...

Whether some server will respond only by IP or also by name depends on DNS records. For small home LAN it usually makes little sense to run your own local DNS server, so what you can do is create records in the local hosts file on each client, that will make the server reachable by name. For example:
```
192.168.1.10   fileserver
```

Now, to have a share "detected and displayed", you probably mean automounted on boot. In linux that is easy by making an entry in /etc/fstab. There are literary million tutorials online for that. You can select (create) your own mount point, like for example /networkshare (but use something shorter :) ). Then after each boot the share content will be available in /networkshare.

On windows that is also quite easy, open the fileserver ( \\fileserver ) by name or IP, and when the shares display, do right-click, Map as network drive. There will be check box "reconnect on logon". With that, the share will map automatically on each boot to the letter you have selected.

For TVs unfortunately I'm not aware if these options exist, maybe some of the Smart TVs do have them...

Does that help you?

---

### Post by cariboo on 2017-09-02
> **jayj2291 said:**
> 

[Smart TV]
Can only see router 1 & Router 2 as media devices



So I guess my question is: My samba server is working in terms of file sharing and permissions as i can access (directly) and create/ edit files. But is there a way where I can have my samba share detected and displayed in my devices (other than my android) such as my tv, windows and lubuntu laptop without having to directly type in an ip address? I want this folder to be fully open and accessible (I understand the risks of exposure to those on my LAN).

Note: smbtree command does nothing on either server or lubuntu laptop.

Many thanks in advance,

- Jay

For serving media files to your smart TV you'll need a media server. Currently I use [Serviio]("http://serviio.org/"), but I have used Minidlna and [Plex]("https://www.plex.tv/"), but neither really suited my use case.

MiniDLNA is available in the repositories.

---

### Post by jayj2291 on 2017-09-02
Thanks for your replies.

Darko, I don't mind accessing the server through IP as opposed to hostname. In terms of autmount, I have already mapped the drive in windows and bookmarked the file share in lubuntu, so once set up it is no longer a problem to access. My main concern was seeing the server in my network more than anything, kind of like a windows machine shows every computer connected to the same network without mapping. They're just there y'know?

Cariboo, this makes sense. So I will need a dedicated media server if I want to see the shared folder on my devices (without explicitily searching for them by ip/ hostname), even if this were to be a simple text file/ document and not necessarily a audio/ video file?

Thanks again for your time,
Jay

---

### Post by cariboo on 2017-09-02
I have several terabytes of media files that I access via my smart Blu-ray player using Serviio, I don't have any active Windows systems on my home network, so I just have a small directory in /home/cariboo that I share using the network share utility in Nautilus. I use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") to access anything other than media files (text documents,OpenOffice documents, Owners manuals in pdf format) on my file server.

---

### Post by jayj2291 on 2017-09-03
Awesome! Ill look in to it. thanks

---

### Post by elico on 2017-09-05
add the next configurations into the end of [global] section of smb.conf
> 
domain master = no
local master = yes
preferred master = yes

and then restart the service:
> 
service smbd restart
service nmbd restart


in a matter of seconds to a minute you will see the server in the windows network.

---

