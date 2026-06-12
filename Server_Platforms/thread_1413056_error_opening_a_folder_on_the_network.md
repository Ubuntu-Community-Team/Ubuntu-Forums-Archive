---
title: "error opening a folder on the network"
date: 2010-02-21
forum: Server Platforms
---

### Post by associates on 2010-02-21
Hi,

I have Ubuntu 9.10 up and running. I need help with getting the data shared to work between Microsoft client PCs and Ubuntu Server.

I was following the documentation provided by Samba online but am encountering an issue here.

So far what i have done is i have created a new smb.conf right from scratch as follows

[global]
    netbios name = toltec
    server string = Samba %v on %L
    workgroup = METRAN
    encrypt passwords = yes

[data]
    path = /Documents/data
    comment = Data Drive
    volume = Sample-Data-Drive
    writable = yes

Then, i saved it and restarted the samba server. I went to the terminal to create a directory as follows

Documents$ mkdir data
Documents$ chmod 777 data 

On windows PC running on XP Pro, i could actually see the toltec under entire network window. When I double clicked on it, data folder came up (which is good). However, when i double click on the data folder, i got an error message saying \\toltec\data is not accessible. You might not have permission to use this network resource...

Any help would be greatly appreciated.

Thank you in advance

---

