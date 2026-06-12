---
title: "Creating User Accounts"
date: 2011-01-27
forum: Server Platforms
---

### Post by elkingrey on 2011-01-27
Hello all,

I'm currently trying to create some user accounts that will have limited access, specifically like a webhost offers access to one directory and then the user gets free reign over that directory, plus database creating and such. I just have no idea how to do that. Can somebody point me to the documentation that explains that? I couldn't find anything like that in the Ubuntu Server Doc. Thanks!

---

### Post by Steve(spt) on 2011-01-27
You can give users access to a folder of documents, that only they can upload or download using an ftp client (Filezilla) or a web browser such as Firefox.

Your users will need to find your server, I use dyndns.org to create a hosting name, such as 'someserver.dyndns.org',
Most routers will now update your account with your IP address so
'someserver.dyndns.org' will point to your IP. 

You will need to open ftp ports in your router for the server,
eg my server on my router as IP 192.168.0.10, and ports 21 & 22 are open.

So when a uses types in ftp:// or http:// someserver.dyndns.org it will be dirrected to your IP, then your router will forward it to the servers local IP 192.168.x.x and talk to your server on ports 21 and 22.


Yon need to be running an ftp service lookup vsftp,  add user accounts,  read the conf information in /etc/vsftp.conf file.

Make a copy before editting anything - just in case you mess it up.

If you set it up correctly user can log in and a fixed to their home dir  '/usr/home'

I did come across a very good youtube file ... [see here](http://www.youtube.com/watch?v=tanll-JM8y8)

He shows you how to install and set up with Ubuntu desktop, but the server version is the same.

This is only one way there are others 

Hope this helps..

---

