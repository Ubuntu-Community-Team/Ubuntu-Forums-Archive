---
title: "Probably simple issue with images not show up on website"
date: 2010-03-04
forum: Server Platforms
---

### Post by ehigginsfreese on 2010-03-04
I am using Ubuntu 9.10, Apache 2.  It works for text (like the "It works") page apache makes but no images show up.  I am 100% sure it is permissions but I suck at Linux permissions.  

Here is what I do to get the page to the web server in case that provides a clue.  I have to ftp the file to the home directory of the user (in this case I named them administrator) because I can't seem to ftp directly into the /var/www folder (which is another permissions issue I know.)  Once the file is there I putty into the server as administrator.  When I am in there I cannot move the file to /var/www unless I sudo.  Then it goes fine.  Once the file is there I can load it from the web but no images show up.  

This is a default setup which I just installed yesterday so I didn't do anything with any users or any configuration changes to Apache 2.  Just left it all alone.  

So what do I need to do to fix this?  Any clues?  I have the nagging feeling this has happened to me before when setting up websites on Linux but it has been a few years since I have done it so I just can't remember the fix!  

Thanks for any help.

---

### Post by bartos on 2010-03-04
First ly make sure your html tags are pointing to the picture properly.
I load all my images into a "image" folder in the root of the website. So my html tag will point to "image/picture.png"
Folder permissions should be 755 or 644 so you can ftp to it and it can be read.

---

