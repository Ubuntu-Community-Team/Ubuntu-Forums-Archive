---
title: "Samba Permissions"
date: 2012-03-28
forum: Server Platforms
---

### Post by rwslippey on 2012-03-28
Hello,

I've been searching the net for some way to do the following.

I am currently running a samba file server that I use as a development sandbox on my local network. 

I have groups setup withing samba as well as within linux.

Here is my request.

I want to have permissions of all files to be 770 with owner being www-data (so php can run and work with the files as well as file uploads to function properly) and the group to be developers, so users of that group can edit those files.

Its easy to do from the command line but I find everytime I either upload files via samba or install something thats running on the web server the permissions are changed and then either I can't access it or the web server runs into issues.

is their as way to have all files uploaded on a particular share take the role of chgrp developers and chown www-data?

Thanks

---

### Post by Morbius1 on 2012-03-28
I'm taking your request literally. In the share definition add 2 lines:

```
force user = www-data
force group = developers

```After morbius gets through Samba authentication I will be converted to user:www-data and have a group:developers so everthing I save will have those ownership settings. Conversely, everything I attempt to access will also appear to be mine so I have full access.

---

### Post by rwslippey on 2012-03-28
I knew their was a way to do it, I was stuck in command line mode and searching the net for chmod samba.:lolflag:..


thanks  :guitar:

---

