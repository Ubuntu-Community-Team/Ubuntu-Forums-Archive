---
title: "Web server file permissions"
date: 2009-10-13
forum: Server Platforms
---

### Post by bcn17 on 2009-10-13
I have an apache webserver and I want to know what permissions are suggested for files and folders. For instance I wanted to share a picture with my brother and he couldn't access it so I opened up the permissions. 
```
sudo chmod 777 file.jpg
``` 
Everything was fine, however I am wondering if this now means that he can delete the picture remotley somehow. I don't know how, but I certainty don't want people accessing my website files, including index.html via the web server port and manipulating them. Currently, I just ssh my server to edit things. 

So, what types of permissions are good for files, I suppose 

rwxr__r__ would work for files, or do user and everyone need execute also? 

Additionally, what types of permissions for folders? 

EDIT: Okay, so the above works for letting people view files- 766, but still, are there any little things I should do for max security and usability? 

Thanks!

---

### Post by windependence on 2009-10-13
You don't want to give anything world write. I set most of my web files to 755 and config files to 644.

-Tim

---

