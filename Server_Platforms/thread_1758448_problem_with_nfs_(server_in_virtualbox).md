---
title: "problem with nfs (server in virtualbox)"
date: 2011-05-14
forum: Server Platforms
---

### Post by g_lev on 2011-05-14
Hello,
I have ubuntu and I installed ubuntu server in virtualbox.
I tried setting up nfs but for some reason I can't write to the folder inside the server (no permission).

the line that i used in etc/exports is -
var/www 192.168.0.100/255.255.255.0(rw,async,all_squash,no_subtree_check,anonuid=1001,anongid=100)

then I mounted the folder in ubuntu but it's not writable.
my var/www folder permissions are set as follow -
drwxr-xr-x   2   root   root   4096

any idea how to fix this ?
thank you.

---

### Post by drdos2006 on 2011-05-14
Try /var/www  instead of var/www

You might install Webmin on your server and control your server from a browser.


```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

