---
title: "http:// password"
date: 2008-08-20
forum: Security
---

### Post by MasGui on 2008-08-20
hey guys, I just configured my Ubuntu Server and I want to know how to restrict access to my site. Right know, it require no password to enter

what i did is a php page to naviguate trough the system. I Have a mounted external USB drive on /var/www i also have a link to myphpadmin, samba and FlowTorrent. 

samba, myphpadmin and FlowTorrent all have a login require but there'no login required for the mounted usb Drive.

Also I have 5 users registred in the Server

root,gui,alex,erik & justin.

what I want to do (that I dont know) is to have a php login or something similar to log in the site/server via http.

eg [http://54.76.37.201](http://54.76.37.201) (that's not my ip)
-->user:
-->pass: 

and Also I want to know if doing so is secure enough. (all 5 accounts have Strong passwords)

Thanks alot 

ubuntu-8.04.1-server-i386 (everything up to date)

oh and also, how is it possible to send file to the server ?

thanks
Gui

---

### Post by ggaaron on 2008-08-20
This may be an option:
[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

---

### Post by troutbum13 on 2008-08-22
It is pretty simple to use webmin to restrict web directories...I would suggest running webmin if you have a dedicated server, it simplifies so many remote admin tasks.
Anyway with webmin installed all you do is https://[yoursever]:10000--> others --> protected web directories --> add protection for new directory

---

### Post by jerome1232 on 2008-08-22
Just a thought, if this is over the internet, and it's not an encrypted connection, it's not secure.

---

