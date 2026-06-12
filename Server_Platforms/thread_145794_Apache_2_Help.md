---
title: "Apache 2 Help"
date: 2006-03-17
forum: Server Platforms
---

### Post by white_tiger_daniel on 2006-03-17
I try to satrt the server using the comand line when this comes up

(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down

Any help would be great.

---

### Post by Koybe on 2006-03-17
Maybe you try to start it as it's already loaded so try :
```
sudo /etc/init.d/apache2 restart
```
If you made some change to a site you can just reload :
```
sudo /etc/init.d/apache2 reload
```
If it's tilel wrong, I guess you made something wrong in your config files. What if you type?
```
sudo apache2 -t
```

---

### Post by ThaDoctor99 on 2006-03-17
i have some troubles about apache server too, i cannot put any files into the folder (in no of the folder) cause it says i have no rights to write or edit anything be course i am not "root" on this computer, which is some kind of wierd since i am the only one using this computer..... Can anyone help ?

I am very new to linux, and ubuntu....

Greetigns - Tobias

---

### Post by claes on 2006-03-17
copy the files to the folder with:

sudo cp originnal_files dest_files

Claes

---

### Post by ThaDoctor99 on 2006-03-17
i also though about how to change the chmod value ? for the folders ?

Greetings Tobias

---

### Post by white_tiger_daniel on 2006-03-23
Umm also how can I get it to start at boot? If I go to processes under gnome system monitor it is there but I have to restart it. Thx. :-k

---

### Post by Kurt` on 2006-03-23
Instead of doing /etc/init.d/apache2 restart after making a configuration change, you can do either of the following:

The update signal:
killall -SIGHUP apache2

The "user 1" signal (also forces configuration file reload):
killall -SIGUSR1 apache2

/etc/init.d/apache2 restart and killall -SIGHUP will cause any file transfers or things being processed to be interrupted.

killall -SIGUSR1 apache will cause any newly spawned processes/incoming requests to use the updated configuration file.

Handy to know if you make a change on a production server, especially one serving large files. :)

---

