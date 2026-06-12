---
title: "Questions about FTP over SSL: Apache or VSFTP? Mutually exclusive implementations?"
date: 2008-12-04
forum: Server Platforms
---

### Post by jamspunk on 2008-12-04
This post contains two sections:

I. Overview

II. Specific Questions


I. Overview

I am trying to set up a secure FTP server on an Ubuntu box (Gutsy Gibbon). I'm using VSFTP and following a handful of HowTos and other online documentation.  However, I'm not quite up and running.

My end goal is to allow privileged users to login and connect to my server via their web browser. I want users to use their browsers and connect to my server via https (We have SSL certificates registered with Equifax and I have the .crt and .key files). 


II. Specific Questions

Q1: Regarding implementation does Apache Server handle the HTTPS SSL connections that have been initiated by browser clients (server will always remain passive)? If so, then do I need to create PHP5 pages and a MySQL5 database to implement this functionality?

Q2: Regarding VSFTP will clients only establish a TLS/SSL FTP connection via a third FTP client application such as Fetch or <other_examples_here>? That is to ask, can clients communicate with and login to the VSFTP server with a web browser? No. Correct?


Thanks,
tommyt
[email]jamspunk@gmail.com[/email]

---

### Post by cdenley on 2008-12-04
Anything you open in a web browser using the HTTP or HTTPS protocol will be handled by apache. You can use apache's directory indexing to list the files, or you can create a nicer-looking PHP page which prints and retrieves your files.

Most browsers will handle FTP connections, but do not support SSL encryption with FTP (FTPS or FTPES). If you want it to be universally compatible and secure, I suggest you use a web-based solution. Do you require that users be able to upload? If so, I recommend uber-uploader.

---

### Post by doogy2004 on 2008-12-04
I use SSH for SSH and SFTP, just change the port to the SSH port on your ftp client.

---

