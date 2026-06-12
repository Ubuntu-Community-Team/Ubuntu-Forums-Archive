---
title: "can secure copy with changed port #"
date: 2017-10-10
forum: Server Platforms
---

### Post by micahpage on 2017-10-10
Using the default 22 port i was able to secure copy somethign without a problem via a command similar to

```
scp pic.png username@website.com:/var/www/html/image/screenshots

```
and pic.png from my local PC would copy to my server at /var/www/html/image/screenshots This is from my local terminal. 

However since removing the ability to use port 22, and changing to a new port on the server, i am able ssh in the server, but cannot do the same secure copy since changing ports

so my new command would be similar to
```
scp -P 2222 pic.png username@website.com:/var/www/html/image/screenshots

```
however the error i get is this?
```
scp: /var/www/html/image/screenshots: No such file or directory

```

---

### Post by darkod on 2017-10-10
Well, the command looks correct, the syntax should be as you put it. Is pic.png already there for the second intent? Maybe on the destination you have write permissions but not modify/replace?

The message seems to be saying the folder doesn't exist but that doesn't seem true...

---

### Post by micahpage on 2017-10-10
Its a VPS and i have root access, as well as the username i am trying to secure copy with has sudo powers. The file does not exist on the server.

---

### Post by darkod on 2017-10-10
But note that sudo powers are not sent over scp or similar remote command. Can you try copying to user home folder just to make sure you can copy first on different port? Just delete the path after the : that should copy into user home.

---

### Post by micahpage on 2017-10-10
i got the same error when copying to the users home

UPDATE:
i got it to work. I changed the port again suggested by a user. Apparently the port number was too low at a 3 digit port?

---

