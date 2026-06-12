---
title: "samba usershare max shares"
date: 2008-10-19
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-19
Running ubuntu 8.04 and Samba version 3.0.28a.

I'm trying to restrict the number of directories users can share with the "usershare max shares" option.  

I set it to 3 but I can still share directories with 10 files in them from my windows machine (XP).

Here is smb.conf.

```

[global]
    wins support = yes

    netbios name = MY_GATEWAY
    server string = MY_GATEWAY
    workgroup = WORKGROUP
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam

    security = user
    encrypt passwords = true
    invalid users = root

    map to guest = bad user
    guest account = nobody

    interfaces = lo, eth1
    bind interfaces only = true

    syslog = 1
    syslog only = yes

    dns proxy = no

    **usershare max shares = 3**

[Media]
    path = /home/ftp/
    read only = yes
    create mask = 0640
    directory mask = 0750
    guest only = yes
    guest ok = yes

```

I ran testparm on my smb.conf and the syntax is correct.

---

### Post by Drezard on 2008-10-19
Basically, Samba only controls what you can share from the computer its running on side of things. So from the computer samba is running on, it can only have a maximum of 3 user shares. You will need to restrict the number of shares somehow on the XP machine. 

Daniel

---

### Post by Shwick2 on 2008-10-20
Ok thanks I understand.

I have a different problem now.  I have two machines, the linux machine with samba and a windows xp machine as a client.

When I restart the windows machine and browse Workgroups I can see the linux machine and myself.  I can also see all the shared folders in My Network Places.

When I execute a smbtree on the linux machine, it shows all the linux and windows shared directories.  After a few minutes, it sometimes doesn't see the windows directories anymore.

Also when I do a findsmb it only lists the linux machine, not the windows machine.

I don't have a second client computer to test with, but wouldn't the second client not be able to see the windows machine because it's not listed on the server from a findsmb?

I also don't know why the directories randomly don't show up from a smbtree.  I know that samba times out names after 6 days, not a few minutes.

I have file and folder sharing allowed through windows firewall.

---

### Post by Drezard on 2008-10-21
Sorry. I dont quite understand the situation. Can u explain it differently?

Daniel

---

### Post by Etrruugo on 2008-10-21
Thanks! Bump!&#12288;He wiped the dust off and gently wrapped it in brown paper. Then he placed the parcel in Reuben's hands.&#12288;&#12288;Racing home, Reuben burst through the front door. His mother was scrubbing the kitchen stove. &#8220;Here, Mum! Here!&#8221;Reuben exclaimed as he ran to her side. He placed a small box in her work roughened hand.&#12288;&#12288;She unwrapped it carefully, to save the paper. A blue-velvet jewel box appeared. Dora lifted the lid, tears beginning to blur her vision.&#12288;&#12288;In gold lettering on a small, almond-shaped brooch was the word Mother.&#12288;&#12288;It was Mother's Day, 1946.&#12288;&#12288;Dora had never received such a gift; she had no finery except her wedding ring. Speechless, she smiled radiantly and gathered her son into her arms.Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here! We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281;All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling ---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

### Post by Shwick2 on 2008-10-21
Let me clarify the questions, they may have been confusing.

The windows machine can see and download all the shared folders from the linux machine, and the linux machine can download from the windows machine with smbclient.

However, when I issue "findsmb" the linux machine only reports itself, not the windows machine.  The man pages show it printing a list of machines for the entire network.  Why is findsmb not listing the windows machine?

Even though file and printer sharing is enabled in windows firewall findsmb still doesn't list the windows machine.  I also tried disabling windows firewall, still nothing.  I allow all traffic to my linux machine from lan interface (currently).

Secondly, smbtree doesn't always return consistent results.  When I restart my windows machine and do a smbtree from the linux machine, all of the shared folders for linux and windows are listed.  Then a few minutes later smbtree may only list linux shared folders.  It seems inconsistent, is this normal?

smbstatus seems to work.  When I'm connected to a linux shared folder smbstatus lists the connection.

---

### Post by Shwick2 on 2008-10-24
I made samba a domain master and added it as a netbios server in dhcpd.conf and I'm still having the same problem.

---

### Post by Shwick2 on 2008-10-27
Someone on IRC said "that depends if the windows server is advertising on netbios, and what the permissions are on the share".  Well the permissions on the windows share allow it to be downloaded, I have "share this folder on the network" checked.

I also have file and printer sharing allowed through the firewall.  Still not sure why it isn't showing up.

---

