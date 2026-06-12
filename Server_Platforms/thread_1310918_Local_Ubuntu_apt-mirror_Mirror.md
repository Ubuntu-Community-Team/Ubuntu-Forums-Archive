---
title: "Local Ubuntu apt-mirror Mirror"
date: 2009-11-02
forum: Server Platforms
---

### Post by farooq.mis on 2009-11-02
Hello Everyone,

I have just configure my local apt-mirror on Ubuntu server 9.04 for my local network. It works when I update my another Ubuntu server on my network. But when I am going to update my Ubuntu client machine receiving following error while 'apt-get update' command. 

root@solat-desktop:~# apt-get update
Get:1 [http://192.168.1.32](http://192.168.1.32) jaunty Release.gpg [189B]
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/main Translation-en_US
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/restricted Translation-en_US
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/universe Translation-en_US
Get:2 [http://192.168.1.32](http://192.168.1.32) jaunty Release [74.6kB]
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/main Packages
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/restricted Packages
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/universe Packages
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/main Packages
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/restricted Packages
Ign [http://192.168.1.32](http://192.168.1.32) jaunty/universe Packages
Err [http://192.168.1.32](http://192.168.1.32) jaunty/main Packages
  404 Not Found
Err [http://192.168.1.32](http://192.168.1.32) jaunty/restricted Packages
  404 Not Found
Err [http://192.168.1.32](http://192.168.1.32) jaunty/universe Packages
  404 Not Found
Fetched 74.8kB in 0s (470kB/s)
W: Failed to fetch [http://192.168.1.32/ubuntu/dists/jaunty/main/binary-i386/Packages](http://192.168.1.32/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://192.168.1.32/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://192.168.1.32/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://192.168.1.32/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://192.168.1.32/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Please help in this regard. I have use the following to configure local apt-mirror

[http://www.howtoforge.com/local_debian_ubuntu_mirror_p2](http://www.howtoforge.com/local_debian_ubuntu_mirror_p2)

---

