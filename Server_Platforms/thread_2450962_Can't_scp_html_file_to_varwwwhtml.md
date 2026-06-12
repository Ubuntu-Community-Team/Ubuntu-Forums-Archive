---
title: "Can't scp html file to /var/www/html"
date: 2020-09-23
forum: Server Platforms
---

### Post by levilone on 2020-09-23
So I have apache2 running on a machine in my house, and I'm able to connect, and scp works to upload files, but when trying this directory, the terminals says it doesn't exist. How can I fix this.

---

### Post by levilone on 2020-09-23
Here's the command I used "sudo scp [email]levi@127.0.0.1:'/home/levi/Desktop/folder/landing.html[/email]'  test@192.168.1.148 /var/www/html/" trying to copy from a folder on my desktop to 192.168.1.148 into the /var/www/html folder. it instead copied to my desktop, where did I go wrong.

---

### Post by levilone on 2020-09-23
I fixed my command to "scp index.html test@192.168.1.148:/var/www/html" but now I get permission denied. Why is that.

---

### Post by The Cog on 2020-09-23
I guess that user *test* does not have permissions to write in /var/www/html. Try just ssh-ing to the server as test and writing to that directory.

---

### Post by levilone on 2020-09-23
I just figured it out. test had permission to delete in that directory, scp couldn't copy straight into it, the permissions on html had to be changed. I also had to change the permissions on the file index.html to be able to view it in my web browser.

---

### Post by LHammonds on 2020-09-23
I usually have to copy files to /tmp, then ssh into the server and sudo move the files/folders once I sudo chown/chmod the correct permissions.

LHammonds

---

