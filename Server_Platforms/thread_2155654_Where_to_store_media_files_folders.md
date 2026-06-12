---
title: "Where to store media files folders"
date: 2013-06-19
forum: Server Platforms
---

### Post by johnycage on 2013-06-19
Hello, I've setup Ubuntu Server 12.04 for home network/media server. I'm planning to use it for NAS, storing media files (all my MP3, movies, archives etc.); and also a space to store backup of my regular Windows-work PCs. 
Where should I store these files? As I see all directories in ubuntu filesystem are important to run the server, so I would not touch them. /home folder is for users but is restricted to particular user and is not publicly available. 
what /opt folder is for? Can I store my data in that folder? or should I create a new folder altogether e.g. /store ?

Thank you.

---

### Post by redmk2 on 2013-06-19
> **johnycage said:**
> Hello, I've setup Ubuntu Server 12.04 for home network/media server. I'm planning to use it for NAS, storing media files (all my MP3, movies, archives etc.); and also a space to store backup of my regular Windows-work PCs. 
Where should I store these files? As I see all directories in ubuntu filesystem are important to run the server, so I would not touch them. /home folder is for users but is restricted to particular user and is not publicly available. 
what /opt folder is for? Can I store my data in that folder? or should I create a new folder altogether e.g. /store ?

Thank you.

From a performance point of view it doesn't matter where you store the data.  Convention and tradition mean a lot.  The basic file system structure is described [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")**[COLOR="#FF8C00"][/COLOR]**.

I follow the convention.  All the data that is served from the particular host is stored under the directory /srv.  

```
/srv contains site-specific data which is served by this system.

  This main purpose of specifying this is so that users may find
  the location of the data files for particular service, and so that
  services which require a single tree for readonly data, writable data
  and scripts (such as cgi scripts) can be reasonably placed. Data that
  is only of interest to a specific user should go in that users'
  home directory.
```

In the original configuration the /srv directory is owned by root:root and there is no reason to change that. All users will be able to traverse the /srv directory to the subdirectories.  The directories below can be chown'd to the ownership you want for rw access.

---

