---
title: "Samba BDC Users sync not working"
date: 2009-01-24
forum: Server Platforms
---

### Post by OfMacandMen on 2009-01-24
I have followed the instructions set forth in [https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html) , but I still can not get my BDC to copy the users & password from the PDC. 

The coping process shows it copies OK and the permissions are correct but when I take down the PDC users fail to log in.

PDC smb.conf
[global]
	workgroup = workgroup
	os level = 20
	server string = %h server
	security = user
	domain logons = yes
	domain master = yes


BDC smb.conf
[global]
	workgroup = workgroup
	os level = 20
	server string = %h server
	security = user
	domain logons = yes
	domain master = no

---

