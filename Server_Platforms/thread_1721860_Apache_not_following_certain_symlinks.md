---
title: "Apache not following certain symlinks"
date: 2011-04-05
forum: Server Platforms
---

### Post by JohnElway on 2011-04-05
Apache noob here. I have an html file on an external hard drive that I would like to symlink to my /home/user/public_html folder. Currently the symlink doesn't even show when in the index when I go to [http://localhost/](http://localhost/). I made a symlink to another html file in my home folder and I WAS able to see and access it, so I know the issue isn't symlinks in general, but specifically when I try to view symlinks of data on my external hard drive. I'm guessing the problem has to do with permissions, but when I tried 'chmod 777' on the file in question I still was not able to see or access it.

---

### Post by Viruk on 2011-04-05
You should be able to create a symbolic link from the terminal, this has always worked for me on LAMP servers, it should work for you too: 

change to the web directory
```
cd /var/www/
```
Then create a symbolic link:

```
ln -s /path/of/desired/location name
```

Where name will be part of the address you access, e.g. [http://localhost/name](http://localhost/name)

---

### Post by JohnElway on 2011-04-05
I just figured out the source of the problem:

[http://wiki.apache.org/httpd/13PermissionDenied](http://wiki.apache.org/httpd/13PermissionDenied)

Basically, I had to change not only the permissions on the file, but also the permissions of its parent directory as well as any other parent directories in the file path all the way up to the root of the external hard drive filesystem.

---

