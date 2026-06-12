---
title: "amavisd not starting automatically upon bootup"
date: 2008-06-04
forum: Server Platforms
---

### Post by mattskr on 2008-06-04
I am running Ubuntu 8.04 as a mail/web server and everything is running fine except whenever I restart the box, amavisd does not start up automatically even though it is in the folder /etc/init.d.

So what happens is someone calls me a week later saying they haven't received mail lately, and I have to go in and start amavisd by running /etc/init.d/amavis start

Then I have to push out all the mails in my queue.

Does anyone have any ideas as to why it is not starting automatically?

---

### Post by quelx on 2008-06-04
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by mattskr on 2008-06-04
I've looked in the /etc/rc#.d directories and they have the symlink to amavis

---

### Post by quelx on 2008-06-04
> **mattskr said:**
> I've looked in the /etc/rc#.d directories and they have the symlink to amavis

Are they executable (eg is the **/etc/init.d/amavis** file *rwxr-xr-x*).? Did you run ```
sudo update-rc.d amavis start 51 S
```?

---

### Post by mattskr on 2008-06-05
> **quelx said:**
> Are they executable (eg is the **/etc/init.d/amavis** file *rwxr-xr-x*).? Did you run ```
sudo update-rc.d amavis start 51 S
```?

Permissions are correct and it is executable. I tried running that command but it tells me that they already exist

---

