---
title: "apt-get update Ign and Err"
date: 2006-10-21
forum: Server Platforms
---

### Post by nettucu on 2006-10-21
Hi,

  I seem to have a very nasty problem which I can't solve. I installed a minimal server dapper 6.06 and after that I tried to get the latest packages from the net.
   apt-get update returns:

apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

   wget any of the files above works without problems.
   I changed the sources.list to many possible sources without any luck; now I'm kinda stuck.
   What can the problem be ?

Thanks,
Catalin

---

### Post by DragonView on 2006-10-21
Hey friend, we got exactly the same problem.  :p 
Have u tried using the LIVE CD? I think when using LIVE CD  we can update while booting from the hard disk, no. Are u using a laptop of desktop?

---

### Post by DragonView on 2006-10-23
Hey my friend, I think I got the reason.
Just delete the /etc/apt/apt.conf  (maybe u should make a backup be4 doing so)
Then u can connect to the sources  ^^ ;)

---

