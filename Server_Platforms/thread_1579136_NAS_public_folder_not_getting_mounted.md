---
title: "NAS public folder not getting mounted"
date: 2010-09-21
forum: Server Platforms
---

### Post by shreysinha on 2010-09-21
hey there, 

We have an Iomega StorCenter ix4-200d in our office. for past two days the shared public folder is not getting mounted. but it's working fine through the web interface i.e user can upload/download.that rules out the permissions problems. 

I am providing the output of mount command: 

t227@t227:/var/log$ sudo mount -t cifs --verbose //192.100.100.37/public /mnt/public/ -o username=shrey 
[sudo] password for t227: 
Password: 

mount.cifs kernel mount options: unc=//192.100.100.37\public,ver=1,rw,username=shrey,ip=192.100.100.37,pass=******** 
retrying with upper case share name 

mount.cifs kernel mount options: unc=//192.100.100.37\PUBLIC,ver=1,rw,username=shrey,ip=192.100.100.37,pass=******** 
mount error(6): No such device or address 
Refer to the mount.cifs( manual page (e.g. man mount.cifs) 

in fact i can't access any of the folder which I am having permissions to rw.but it's working fine through the web interface.

P.S:- On windows also I can't mount the folder.

---

### Post by the_original_billq on 2010-09-21
While I am not familiar with your particular NAS device, it is fairly common for NAS devices to use multiple protocols for filesystem access, which may explain why the web interface works (WebDAV?) while CIFS mounts (Samba?) don't.  The fact that the mount does not work from Linux or Windows leads me to the suspicion that the problem is with the server, and not the client.  I would look at the CIFS server configuration, and see if something has changed.

HTH,

-Bill

---

