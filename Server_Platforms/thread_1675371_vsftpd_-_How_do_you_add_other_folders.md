---
title: "vsftpd - How do you add other folders"
date: 2011-01-25
forum: Server Platforms
---

### Post by Steve(spt) on 2011-01-25
Ubuntu server 10.10

I have vsftp installed and working fine, I can login local and download, I can also login over the net ftp:// some servername.dyndns.org   IP updated with dyndns.org

User(s) are locked into their home folders.

How do I add a "public" folder, thats browsable to all user(s), and files can be downloaded, not changed, and still keep the read/write to uses homes?   

I would like to add /srv/public  so /public is listed in uses home folders. 

many thanks for any advice,

---

### Post by alienprdkt on 2011-01-25
Well vsftp as you probably found, doesn't support system links (ln-s) so what you will have to do is mount - bind it.

link so mount --bind /srv/public /home/someuser

hope this helps...

---

### Post by amra.sonntag on 2011-01-25
vsftpd comes with an anonymous folder and account. It is named ftp - not sure about that. You can change this folder by changing the home folder of ftp.

I suggest you look at the /etc/vsftpd.conf (hope it is right) file. The comments explain the options really good. For more information you can look at the vsftpd.conf man page. That should more or less cover it all.

If you decide to use SSL encryption. Don't forget to create your own certificate. Since using the at default isn't the best idea. After all - when i install vsftpd, i do get the same certificate.

---

### Post by madman100 on 2012-01-22
Hello Steve(spt),

Did you have any success with sharing one folder with all users i too have came to this point where a want to keep users jailed but let them all share the public folder the user have not been setup as virtual user but account user within ubuntu so can any one help please this is doing my head in for the last week.


Thanks 
Madman100
](*,)](*,)

---

