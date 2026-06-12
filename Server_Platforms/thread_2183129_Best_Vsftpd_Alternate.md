---
title: "Best Vsftpd Alternate?"
date: 2013-10-23
forum: Server Platforms
---

### Post by chetanmadaan on 2013-10-23
Hi -

we have a small ubuntu server (around 5 - 10 accounts) with PHP projects going on. The problem we are facing is Vsftp sometimes works really fast most of the time... but sometimes... it just doesn't respond and we can't even cancel the request and reupload the files or something.

May be this is because we have 2 - 4 users at anytime using one particular account to upload/download files.. or may be Vsftpd isn't just the right solution.

Would anyone recommend going for Proftpd?? or is there a solution to make Vsftpd faster... this is really out local server... so, we aren't that worried about security and all.

---

### Post by chetanmadaan on 2013-10-29
Hi - Anyone?

---

### Post by chetanmadaan on 2013-11-06
anyone in the Milkhyway?

---

### Post by coffeecat on 2013-11-06
@chetanmadaan, I've moved this into the Server Platforms section for you. It's quieter than General Help, but it's more likely that people who can help you with FTP servers will see the thread.

Good luck in finding a solution.

---

### Post by chetanmadaan on 2013-11-06
Thank you Sir.

---

### Post by chetanmadaan on 2013-11-12
Anyone... before i officially give up.

---

### Post by thufirhawat2 on 2013-11-12
Hey, I am by no means an expert, but it looks like no one has responded to your post, so I thought I would try my best to throw my 2 cents in on the off chance it could help you. 

When you say it is just a local server and you are not worried about security, do I take that to mean the users connecting to it are all on the same LAN as the server? If that is the case, the simplest solution may be to use samba (assuming you have windows/MAC clients) and set up a network share the users can access to save their project data.

---

### Post by nerdtron on 2013-11-13
Yes samba would make a good if you just want your local computers to share/upload/download PHP projects on your server.

Another good alternative (if all computers are linux) is to setup a NFS shares. You can have 10 different folder share for each account and have each client mount each folder of their computers.

---

### Post by chetanmadaan on 2013-11-14
Thanks for the reply guys.

A. this is a local server... but sometimes we work from home or any other location and then using samba will not be a appropriate solution.
B. all the other clients we have are Windows... Not sure if NFS shares would work.

Thanks

---

