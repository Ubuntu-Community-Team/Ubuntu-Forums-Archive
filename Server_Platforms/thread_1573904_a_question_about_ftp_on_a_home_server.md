---
title: "a question about ftp on a home server"
date: 2010-09-13
forum: Server Platforms
---

### Post by crazyjust on 2010-09-13
I have set up a home server with ubuntu desktop since im new to this and need the gui. I have no problems with the lamp package or setting that up. My question is, can  you setup a ftp server and then connect to it from a windows pc on the same network with a client like core ftp? I want to do this to add files and make chmod a little easier if possible. Any help with this would be great. Thanks

---

### Post by junke1990 on 2010-09-13
What is your goal? making a file server? or do you need ftp for some purpose???

If you don't need ftp I would advise to use a samba server if you want to just share files over your home LAN.

I myself dont really use ftp, I use sftp, a service provided by SSH which can be connected to by WinSCP, a program which looks like most of the FTP clients out there.

---

### Post by crazyjust on 2010-09-13
I would like to set it up like my paid hosting was so i could use an ftp client and log in  with a username and pass.

---

### Post by Bachstelze on 2010-09-13
FTP generally doesn't play well with NAT. I'd also recommend SFTP, be it only because it is more NAT-friendly. Most FTP clients support it.

---

### Post by crazyjust on 2010-09-14
I would like any easy way. I just need something i could make 1 user account, restrict annonymous users, and log in from ftp client.

---

