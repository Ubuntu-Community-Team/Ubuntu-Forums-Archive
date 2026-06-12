---
title: "FTP vs NFS vs SAMBA"
date: 2011-02-27
forum: Server Platforms
---

### Post by anifort on 2011-02-27
hello all,
I was wondering what is the pest solution to my problem. I have a server which will be mainly to store files but also as a web server for internal use(not to host public web-sites). I had problems with the software raid 1 so for that i make second thoughts on using an external raid 1 device connected to the server via usb(Any advice on that?). Now i need to access my files remotely, in the local network or when i am in a different physical location, over the internet. Now i found out the easiest way is through FTP but i am also investigating solutions like NFS and Samba. NFS is not much compatible with windows and that could be an issue, but what about Samba? and also, if i go with Samba will i need to set up a VPN server for that? What is your opinion? (also for security issues i considered sftp but i actually dont like that user can see files from root / ) 
Thanks

---

### Post by CharlesA on 2011-02-27
If you need to access files remotely, you can use sftp or sshfs.

You can chroot an ssh user to their home directory if you don't want them to be able to browse the full file system.

I wouldn't use ftp or samba over the internet, as they aren't encrypted. You could use a VPN and go that route, but I haven't messed with that.

---

### Post by slimjim1520 on 2011-02-27
In your situation I would recommend sticking with a form of FTP. Mainly because you are going to be accessing this over the internet. In any kind of internet connection anywhere you are most likely not going to face a firewall problem if you got with FTP. At a hotel for instance some have almost all ports blocked excluding HTTP HTTPS and FTP FTPS . So its safe to assume that if your going to be accessing the files over the internet its best to go with some sort of FTP connection

---

### Post by Vegan on 2011-02-27
I use vsftp as it seems to do the job well.

---

### Post by aeiah on 2011-02-28
for the LAN side of things, it depends what kind of file sharing and transfer you'll be doing. i have a read only guest FTP for music and video, and an NFS for sharing and editing documents for example. if you have windows systems on the LAN and its more about transferring files than sharing them, FTP may be the best option. its fast and reliable.

for internet, just make sure you can connect via ssh and then you can use sftp, rsync, or tunnel into your LAN and use any method you have available for the LAN to access your files.

---

### Post by anifort on 2011-03-11
Thanks all for your replies! After a bit of investigation by my self i conclude that if i want to have a network drive on linux that should be accessible from windows , samba is a good approach. sftp is the ideal solution for remote access though!

---

### Post by HermanAB on 2011-03-11
BTW, UNIX Services for Windows (NFS) is a free download from Microsoft.

---

### Post by megabuffen on 2011-03-11
SFTP is definitely better than FTP over the internet, because it's encrypted. If ports being blocked is a problem, you could change the ports so that you can use SFTP over port 21, just like FTP.

---

### Post by Lars Noodén on 2011-03-11
I would second the recommendation of SFTP.  If you want a filesystem-like interface then you can use [SSHFS](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#sshfs_-_SFTP_file_transfer_via_local_folders) to mount the remote system.  

If you want to use a regular SFTP client, there is probably one built-into your file manager, but do not want users outside their own folders, then you can use the [built-in chroot](http://howtoforge.com/node/5928) capabilities in OpenSSH server.

---

