---
title: "SSH and Samba File Sharing"
date: 2007-02-10
forum: Server Platforms
---

### Post by DustinW on 2007-02-10
I installed Ubuntu 6.10 and SSH today. My goal is to setup a file/print server that I can access  from any computer. I would like to be able to upload files from work or share documents with  people. Will Samba work in this application? I've thought about using FreeNX for a VNC setup but I don't think that would be necessary or an efficient use of resources.

 I'm also wondering what the interface for downloading or uploading files to the server would be like if Samba is used. I'm open for suggestions and advice regarding which server type I should use. 

Thanks in advance!
Dustin

---

### Post by linuchsan on 2007-02-10
You can use openvpn (for linux, windows and mac), or if you only want to share files over ssh, try winscp if you are using windows

---

### Post by chrisfay on 2007-02-11
Samba is for internal networking with Win machines; it sounds like you're trying to share files both in and 'out' of your LAN and in that case you would need some type of externally accessable protocol. You could certainly use SMB for inside your network, then configure a web server or public ftp/scp/sftp bank for stroring files you want to share externally.

I would think creating an entire VPN solution just to share some files might be a bit overkill. But if you need constant access to your network remotely, it may be something to look into.  I had good success with OpenVPN as previously mentioned.

---

### Post by nix4me on 2007-02-11
Why not a simple ftp server?  You could enable ssl/tls on it also.

nix4me

---

### Post by DustinW on 2007-02-12
Never even thought of doing a FTP server! I'll have to look into that and the openvpn suggestion. Thanks !

---

