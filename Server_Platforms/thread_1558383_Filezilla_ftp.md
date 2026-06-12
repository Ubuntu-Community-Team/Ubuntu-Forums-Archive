---
title: "Filezilla ftp"
date: 2010-08-22
forum: Server Platforms
---

### Post by jmore9 on 2010-08-22
Hello All !

I have been trying to get a home server to do what i want but just not getting there.  I only need it to serve up the files to a home ( non internet ) network.

I saw that filezilla also comes in a Linux version also.  I am going to give it a try next.  Anyone use the linux version of filezilla ? What happened did it work not work ?

---

### Post by Ryan Dwyer on 2010-08-22
FileZilla is an FTP client, used to connect to an FTP server. You need to install FTP server software on your Linux machine (eg. sudo apt-get install pure-ftpd).

---

### Post by 0004tom on 2010-08-22
Filezilla is also a server. There's along list of FTP servers to choose from, even other protocols that you could look into. SFTP with openssh-server, vfstp/proftpd/pureftpd etc etc list goes one.

If it's just to share files over a local net, why not just use samba?

---

### Post by jmore9 on 2010-08-22
It took about 4 minutes to install and get to using the filezilla stuff and i have spent hours on earlier installs of samba trying to get it to work the way i wanted , this was so fast and simple.  And even for linux

---

