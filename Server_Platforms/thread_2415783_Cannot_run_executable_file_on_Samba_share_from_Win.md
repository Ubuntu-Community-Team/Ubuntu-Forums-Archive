---
title: "Cannot run executable file on Samba share from Windows 7 laptop"
date: 2019-03-31
forum: Server Platforms
---

### Post by Robert_Boutin on 2019-03-31
Ubuntu 18.04 guest in VirtualBox
Installed Samba 4.7.6 onto the guest

My Windows 7 laptop finds the share and I can save files to it as well  as open files.  However, I copied a program on the share that I want to  be able to run from any Windows machine on the network.  Windows does  not let me run the executable file from the share, it gives me an error,  seems to be a permission issue.

I know this is an Ubuntu forum but hoping someone can help me  troubleshoot if the issue is on my server or my laptop.  I don't know  what files to post that may help, appreciate any guidance with that.   Thanks.

---

### Post by mastablasta on 2019-04-01
does the file have execute permission? does it have everything set that it runs on the windows machine rather than on the linux server? linux OS wont' be able to execute a windows application. if you had a windows OS you would be able to execute it but by default it would run on the windows server rather than on your PC.

---

### Post by Robert_Boutin on 2019-04-01
Thank you, that unfortunately makes complete sense.

---

