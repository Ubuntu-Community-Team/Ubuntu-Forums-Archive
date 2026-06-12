---
title: "Unable to download updates"
date: 2011-07-29
forum: Security
---

### Post by TXbirder on 2011-07-29
Twice this week I've tried to download " **Important security updates".**  Each time the response is:

                       
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.5_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.5_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/logrotate/logrotate_3.7.8-4ubuntu2.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/logrotate/logrotate_3.7.8-4ubuntu2.1_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.2.16-2ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.2.16-2ubuntu4.2_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
  
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2.1_amd64.deb) 
   404  Not Found [IP: 91.189.92.167 80] 
  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.5_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.94.2ubuntu6.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.94.2ubuntu6.2_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.2.16-2ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.2.16-2ubuntu4.2_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.2.16-2ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.2.16-2ubuntu4.2_amd64.deb) 
   404  Not Found [IP: 91.189.88.30 80] 
  
What am I doing wrong?  I have successfully downloaded other updates.

John

---

### Post by bodhi.zazen on 2011-07-29
try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by akoskm on 2011-07-29
Have you tried to switch your download source to the Main server?
Update Manager > Settings > Ubuntu Software > Download from: Main server.

---

### Post by bodhi.zazen on 2011-07-29
> **akoskm said:**
> Have you tried to switch your download source to the Main server?
Update Manager > Settings > Ubuntu Software > Download from: Main server.

If you look at the links in question, you will see the package version is outdated, and thus the user has to update the database, as indicated in my post :twisted:

---

### Post by akoskm on 2011-07-29
> **bodhi.zazen said:**
> If you look at the links in question, you will see the package version is outdated, and thus the user has to update the database, as indicated in my post :twisted:

I'm sorry for my response, sir!:lolflag:

---

### Post by bodhi.zazen on 2011-07-29
> **akoskm said:**
> I'm sorry for my response, sir!:lolflag:

NP, was just trying to show you how to debug the OP question.

Is it a problem with the server / url or is a problem of updating the database ?

The solution is dependent on answering that question first ^^

---

### Post by TXbirder on 2011-07-29
The terminal entry did the job.  Thanks.
John

---

