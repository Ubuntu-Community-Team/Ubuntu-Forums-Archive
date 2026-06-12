---
title: "Strange problem with server"
date: 2010-01-14
forum: Server Platforms
---

### Post by argoson on 2010-01-14
I have installed lamp server on a computer i have for website development. i use the latest ubuntu server 9.10, apache, php, mySql, Webmin - all the latest versions. it has been running very smoothly for a while now, accessing both from internal network as well as from outside.

my problem is very strange - whenever i connect using ftp client to my server from outside, to do a "massive" file operation like uploading a big number of files or deleting an entire directory, my computer/server "crashes" and i lose connection to it for a few minutes. i cannot access it via ftp, not ssh, and neither of the website installed on it run (http). i just have to wait about 10 minutes for the server to come back again.

Like i said - it only happen when accessed from the outside (internet). if i do the same operation from a local computer (the same network) no problem there.

any ideas where to start looking ?

---

### Post by neoanderthal on 2010-01-14
how is your server connected to the internet? does it go through a firewall, or is it directly connected? if it's directly connected, does it use the same network interface, or a different one? If it works ok locally but drops connection when working remotely, I'd look first into your Internet setup - firewall, router, whatever.

Are you actually seeing a reboot event in your server's logs?

---

### Post by argoson on 2010-01-14
My server is connected through a router, with the appropriate ports forwarded. It doesn't boot, this i know.

---

### Post by qchapter on 2010-01-14
argoson,

First troubleshoot the transfer protocol your are using by using scp to transfer a large file or directory to your server.  This will tell you if ftp traffic is the problem.

Do you have access to the router, or is this server hosted by someone else?

Thanks,

-qchapter

---

### Post by argoson on 2010-01-15
The server mine. i have full access to it.

How do i do the test that you described ?

---

### Post by qchapter on 2010-01-15
First make sure you have openssh-server installed on your server:

```
sudo apt-get install openssh-server
```

Then:

Open a terminal on a client that can connect to the server.  To transfer something using scp the command looks like this:

```
scp <path to file on client> user@<server ip or dns name>:<path to where you like the copied file to be store on the server>
```

Type ```
man scp
``` in a terminal on your client for more information.

-qchapter

---

### Post by argoson on 2010-01-16
I will give it a try. can i use Filezilla with SFTP protocol ?
Also, what exactly do i want to check ? if the file upload completes without any problems ?

thanks for your help

---

### Post by qchapter on 2010-01-16
Hi argoson,

If you are connecting using a windows client, use WinSCP, it's a graphical scp client.  You wan't to check if the file transfer completes without errors.

Thanks,

-qchapter

---

### Post by argoson on 2010-01-18
With Winscp the file transfer completed without any errors. So it looks like i'm ditching Filezilla and regular ftp protocol for scp. 

but why will it happen in the first place ? why does file transfer using ftp will cause the sever to halt ? is it a precautionary measure to block some kind of attack ?

---

### Post by qchapter on 2010-01-19
Your first post implies that it's the connection to the server from outside that drops, not the server itself that crashes.  

My guess would be that your router is the weak link here, check your router's logs for errors.

Thanks,

-qchapter

---

