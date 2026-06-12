---
title: "Help getting samba working"
date: 2011-04-14
forum: Server Platforms
---

### Post by AcousticDementia on 2011-04-14
I'm new to this so I'm wondering if anyone could give me a hand. Sorry if I posted this in the wrong forum.    I'm trying to set up a samba server to share files with my roommates. 

I want to share a folder I created in the admins home directory /home/meatwad/meatwadshare. I clicked on properties>"share this folder","Allow others to create and delete".  I then opened the samba application, set a workgroup name (123house), set the authentication mode as user, set encrypt passwords to yes, and no guest account.  I created machine accounts for the people whom I want to be able to access the folder, and then created samba accounts with passwords. 

After that, I checked the "writable" and "visible" boxes and the boxes of the users I want to access it.  After restarting samba no one but the admin could connect (probably because it is his folder). I followed several guides but still cant get it to work. I have a feeling that I forgot something stupid. Any suggestions on what I am forgetting or doing wrong?

---

### Post by falko on 2011-04-15
Not sure what went wrong, but maybe it is easier to set up a Samba server from the command line (e.g. like this: [http://www.howtoforge.com/ubuntu-10.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-10.10-samba-standalone-server-with-tdbsam-backend) ).

---

### Post by Morbius1 on 2011-04-15
**[1]** There are 2 methods of creating Samba shares - Usershare and Classic-share - and from your description you are using both methods on the same target folder. This is generally not a good idea. Please post the output of the following commands so we can see how Samba is set up:
```
net usershare info --long
testparm -s
```**[2] **> I created machine accounts for the people whom I want to be able to  access the folder, and then created samba accounts with passwords. For reasons that are not entirely clear to me Ubuntu recently has been installing a package: libpam-smbpass. It's function is to override the smbpasswd you have set for the remote user with the server login password for that user. If you set the samba password to match then it makes no difference. If however you set the samba password to be different from the login password ( as one should - in my opinion ) then it's best to remove the package:
```
sudo apt-get remove libpam-smbpass
```**[3]** Is the folder you are sharing an ntfs or fat32 partition by any chance. Unless you have fstab entries for these partition it will mount with access only to you so you will need to make a modification to your smb.conf to compensate.

---

### Post by kevinthecomputerguy on 2011-04-15
[http://woodel.com](http://woodel.com)

---

