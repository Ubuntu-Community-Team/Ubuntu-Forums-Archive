---
title: "Samba permissions"
date: 2013-01-07
forum: Server Platforms
---

### Post by achtyl on 2013-01-07
I'm currently finishing up my senior project and am on the last step. I am attempting to create a samba share that can be seen and accessed on a windows network. Currently I have a GUI installed on 12.04 server edition running samba 3.6.3. I created the share by making a folder and sharing it out. I'm not sure if I did this properly because I can only access what is inside of this folder on the Ubuntu server itself. When I attempt to access the share on any other machine I am ported with a log in credential request. Neither the domain admin or root credentials grand access to the file. Where have I gone wrong?

---

### Post by dannyboy79 on 2013-01-07
who is intended to have permission to acess/write to this share? what does your smb.conf file look like? What kind of security are you using? Can't help without knowing those answers.

---

### Post by CaseyC on 2013-01-07
Follow this guide step by step and you will have your share up in no time :) 


I was able to create a share using Samba following this method, and I could \\MyLinuxMachineName\NameOfSharedFolder perfectly on Windows PC's.

---

