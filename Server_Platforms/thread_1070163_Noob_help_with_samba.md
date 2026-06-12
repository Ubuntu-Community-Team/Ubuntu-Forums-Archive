---
title: "Noob help with samba"
date: 2009-02-14
forum: Server Platforms
---

### Post by 53880 on 2009-02-14
I'm sorry to burden you all with my noobness, but a friend of mine got me into installing ubuntu server at my work (we're a non-profit, if anyone cares to help a poor, less fortunate organization :)  despite me having no prior experience with Linux.  Anywho, our setup is simple:  we just need a file server for a couple of folders.  He set up samba, and I can see 2 of the 4 folders via the workgroup, but I can't write to them.  Also, like I just wrote, a couple of them don't even show up.  I know how to access smb.conf and edit it, and I've already spent a lot of time google'ing what I need to put in there to make the directories work but it's all for naught.  Also, I DID CHMOD, by typing this in:

sudo chmod 777 /etc/samba/serverdata

Is that correct?  I have samba folders setup like this:

[serverdata]
comment = BHWP's ServerData Folder
path = /home/samba/serverdata
public = yes
writable = yes
guest ok = yes
browseable = yes

Is there anything I'm missing?  He setup serverdata folder, as well as a subfolder named "public" which are the only 2 that appear in the workgroup.  I created serverdata/users and serverdata/imagedrive, but they have yet to make an appearance in serverdata via the workgroup.  I can access them directly, by clicking on the network workgroup, but if I open up serverdata, they're not listed.  They have the same configuration as serverdata above.  If this doesn't make any sense, let me know and I will try my best to re-explain it.

I really REALLY appreciate any help.  Seriously, my work is all over me about this!  I'm not even supposed to be doing IT stuff, I'm a Grounds Manager at a wildflower preserve!  In way over my head, and my friend that got me into this is AWOL, heh.

THANK YOU IN ADVANCE!!!

---

### Post by HermanAB on 2009-02-14
Samba is great when it works and total PITA when it doesn't.  Even on Windows it is actually easier to install Services for Unix and use a NFS server instead.

You have to test a Samba connection with 'smbclient'.  That is the only way to see the error messages and without the error messages you are poking around in the dark.  See this guide, it may help: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by dann0 on 2009-02-15
You can run the chmod with the -R flag, so all files and folders get the same setting:
chmod -R 777 /home/samba/serverdata

In the share definition in smb.comf, you can set read/write/execute with create mask:

[serverdata]
comment = BHWP's ServerData Folder
path = /home/samba/serverdata
public = yes
writable = yes
guest ok = yes
browseable = yes
**create mask = 0777**

---

