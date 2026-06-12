---
title: "apache question"
date: 2009-08-11
forum: Server Platforms
---

### Post by hockman5 on 2009-08-11
I am running Ubuntu Server with apache2 .
I have a subfolder (var/www/html/folder) which I can access photos
from the internet ([www.myserver.com/folder/whatever.jpg](www.myserver.com/folder/whatever.jpg))
This morning I ftp'd a new photo to my server and placed it in the
same folder. I changed permissions of the picture (chmod 777 image.jpg) but it doesn't show up on the internet. Is there something else I have to do for apache to serve the file? Restart the service? (I tried that too but it still doesn't serve the file)
There are many other photos in that directory that do show up, just not the new ones.

Thanks

---

### Post by Soley on 2009-08-11
If you're behind a router, do you have port 80 forwarded?

---

### Post by hockman5 on 2009-08-11
What does that have to do with anything. Like I said, I have many photos in that directory that I can access from the internet. The new photo's I added to that directory I can not access from the internet. It has nothing to do with my router but more of a permissions problem? or an apache problem?

---

