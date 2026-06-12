---
title: "Moodle + Server problems"
date: 2007-05-15
forum: Server Platforms
---

### Post by warlorddagaz on 2007-05-15
I have spent today trying to install ubuntu server 7.04 and moodle.

I installed the server normally, and the used
```
sudo apt-get install moodle
```
to install moodle.

However, I cannot find where the moodle files are installed to.

When I try to access moodle from annother computer on my network  I get a 403 (forbidden) error, although I do not when accessing the root of the server. This does not occur when accessing it from the server itself.

I'm assuming that this is due to file permissions, or something similar, but as I am new to servers, I'm not sure.

Any help will be appreciated, and feel free to call me stupid because I managed to lose moodle

---

### Post by warlorddagaz on 2007-05-15
I've tried accesing it through localhost on the server, and it works, but when I try using it's (local) IP address, I get a 403

---

### Post by quinreis on 2007-05-18
The moodle files are in /usr/share/moodle. Generally, if you have a GUI, you can always find out where package files are installed by running synaptic and searching for the package. I think you'll find that dpkg has some options to do the same on a command line if you check through the man page.

I am in much the same state as you are- moodle works fine from localhost, but I can't acess it from other hosts on the intranet. However with me the browser just times out. My guess is that it is a setting in apache, but I can't find it yet.

---

### Post by warlorddagaz on 2007-05-18
If you find anything, let me know - I'm new to LAMP, so any help if useful!

---

