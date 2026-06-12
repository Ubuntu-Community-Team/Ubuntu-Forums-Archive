---
title: "apache2 doesn't work"
date: 2008-12-13
forum: Server Platforms
---

### Post by pdo100 on 2008-12-13
Hi,

I have a problem with apache2 server. I have recently installed apache2, but somehow when I type http//localhost/ in my browser it says 'Unable to connect'. I have looked across the net, and I couldn't find solution. I tried to configure apache2 so I have search for right files - httpd.conf. But unfortunately it doesn't exist. It only apache2.conf exist. The funny thing is in apache2.conf there is a line referring to httpd.conf. which was supposed to be in the same directory. 
Can anyone explain me what is going on? Did apache  forget to include this file? I have read that new apache wants to get rid of httpd.conf. But why? If so how can I configure my apache to work?
I have installed couple of apache servers before on ubuntu and I never had a problem, but now I really get frustrated. 

Thanks for any help.

---

### Post by bluefrog on 2008-12-13
[http://localhost](http://localhost) might function in a better way.
If it was only a typo in your post then is apache installed?
Is it running? have you checked that it is running?

---

### Post by mbeach on 2008-12-13
they didn't forget the file.

see the ubuntu/debian apache2 layout here:
Debian, Ubuntu
[http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1](http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1)

as that link suggests, you can read more in:
/usr/share/doc/apache2/README.Debian

---

### Post by pdo100 on 2008-12-13
Thank you for reply,
I have handled installing apache2. What I have done I have completely uninstalled it in synoptic and then removed remain rubbish with root privileges, and after I was sure nothing exists from last apache I installed it again. And it successfully installed with all files (i believe). 
Afterwards I have tried to install php5 and everything seemed to be fine, but when I wanted to preview php file, I have created, the browser wanted to download it.   Now I am exploring this problem :-( and I even get more frustrated now. I completely cannot find any solution. I have read few posts but everything doesn't work. Any clue why apache doesn't recognize php files?

---

### Post by pdo100 on 2008-12-13
Also I am trying to chase all the files I have installed previously. 
For this obviously there is apt-show-versions available, but when I try to install it typing:
apt-get install apt-show-versions 
I get error 404 it says that two links are broken. 
How can I get this sorted?
I hope in couple of days I will forget about php and apache problem.

---

### Post by mbeach on 2008-12-13
might want to try:```

sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```
That should take care of the download php prompt.  Some people seem to report that the browser continues to try and download which turns out to be a caching issue of some sort.

related thread which may provide some other info:
[http://ubuntuforums.org/showthread.php?t=926692](http://ubuntuforums.org/showthread.php?t=926692)

---

### Post by Mechina on 2008-12-13
If you're going through a router, make sure you port forward it

---

### Post by pdo100 on 2008-12-13
Thanks for reply,
But nothing works. I have tried this and no results.
What I think may be the issue are the leftovers after I have upgraded php and apache. I have tried to completely remove all the files, but I think it is not very possible. Ubuntu seems to be not so great in respect of its hygiene. If I could chase old files, I know, I would get this sorted, but I have no clue how as I can't install apt-show-versions ... :-(

---

### Post by mbeach on 2008-12-14
clear out the httpd.conf if you still have stuff in it.

make sure that the libapache2-mod-php5 has been installed, also make sure to enable it although I've never had to do that explicitly ```
sudo a2enmod php5
```.

be sure to restart the apache server before trying again.  

I assumed that you already installed php?  If not, here's how:
```
sudo apt-get install php5
```

---

