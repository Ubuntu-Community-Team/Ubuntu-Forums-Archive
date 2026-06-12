---
title: "Don't see my files in Ubuntu One catalog"
date: 2009-11-03
forum: Ubuntu One (CLOSED)
---

### Post by svyatoslav on 2009-11-03
Hello Ubuntu One team and users. Tnank you for the nice service. I gave a little problem.

I've uploaded text file to ubuntu one through desktop. Then I visit web interface and don't see my files there. What is the problem?

Svyatoslav

---

### Post by manoriax on 2009-11-03
Is your client connected to Ubuntu One? If yes, maybe you should wait a few minutes, I think sometimes this sync-process isn't the fastest.

---

### Post by svyatoslav on 2009-11-03
Thank you for the answer.

I copied files yesterday and I don't see its thought web interface today.  I have two folder in my Ubuntu One folder. First and second folder contain files. Files of first folder I see through web interface  ([https://one.ubuntu.com/files/#path=/My%20Files](https://one.ubuntu.com/files/#path=/My%20Files)), but I don't see files of the second folder through web. And I see files in both folder through desktop. I have permanent Internet connection.

One more strange. I created folder "test" through web, 10 min left I don't see it in desktop. Also I created "test1" through desktop and I don't see in web after 10 min.

I think you have bugs in your web interface or synchronization time so big or something else.

Thanks!
Svyatoslav

---

### Post by svyatoslav on 2009-11-05
Few minutes ago, when I've surfed in FireFox, Ubuntu One suggested to enter web Interface. I've entered and now I see all folder and files in web, but one folder "test"  is out of place :)) (i don't see in thought desktop).

And now there are fatal error sign on Ubuntu One icon in tray. What's meter?

Thanks!
Svyatoslav

---

### Post by andyba on 2010-04-23
I have the same problem
Ubuntu 9.10 64 bit

My files in Nautilus Ubuntu One folder and only a totally different.

---

### Post by duanedesign on 2010-04-23
The following should show you content waiting to upload:

```
 u1sdtool --waiting-content 
```


What do you get when you run the following command in a terminal: 

```
u1sdtool -s
```

---

### Post by moraxu on 2011-11-01
I have a similar problem. I've selected some folders outside my ~/Ubuntu One to synchronize but I don't see any uploaded files (there are only 2 of them).

 ```
u1sdtool --waiting-content
```command says that there are no files awaiting for upload.

```
u1sdtool -s
```says:

> State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

---

