---
title: "I want to upload to my server."
date: 2006-08-29
forum: Server Platforms
---

### Post by geminias on 2006-08-29
Hello, I'm trying to get a phpbb forum going on my server but I don't know how to set up something to allow me to upload it then install it.  

Can anyone help me?  I set up an ftp server on the machine but i dont know how to upload with it.

---

### Post by gertmul on 2006-08-29
Why don't you set up ssh on the server and connect to it to install software.

With ftp, you can upload some files to it, but you won't be able to start or run it.

```
sudo apt-get install openssh-server
```

---

### Post by Sam on 2006-08-29
You should use SSH instead of ftp (more secure). Search in the forums for a thread for installing SSH then read [this](https://help.ubuntu.com/community/SSHHowto).

But with ftp all you need is a ftp client, like **gftp**.

---

### Post by geminias on 2006-08-30
Okay I've got ssh server running on my server and I'm trying to use putty but I don't see how you can upload to the server.  I see that putty is good for administering the server remotely though.  Can someone tell me how it is possible to upload files from the computer using a putty client to the server?

---

### Post by chrisfay on 2006-08-30
If you're using putty then I assume you're trying to access your server via a Windows machine. There are different ssh 'secure file transfer' programs around that allow you to upload/download files. Just use them like you would an ftp client. 

I use WinSCP:
[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

It works great. Also works with putty's 'pageant' (putty authentication agent) if you want to setup keys and disable passwords altogether; which I definately recommned.

---

