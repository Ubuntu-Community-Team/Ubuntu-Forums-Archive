---
title: "OpenOffice / unoconv / java problem when run from PHP script with www-data user"
date: 2010-07-08
forum: Server Platforms
---

### Post by ufliker on 2010-07-08
Hi all,

I've a big issue using unoconv to convert Office docs in PDF format from a PHP script.

**It works perfectly when I run the script or the unoconv commands as root**, but it fails the second I do the same from web (through apache and www-data user) :(

I have installed Ubuntu 10.04 Server 64bits, openoffice.org and unoconv packages have been installed via apt-get (re-installed today). I think openoffice is version 3.2. 

Here is a command line that is called by exec() PHP command :

```
/usr/bin/unoconv -f pdf /home/www/framework/files/volume_0/document/original/1278613446MWEwwT4k.ppt
```Again : it works when runned as root, fails when runned by apache's www-data.

I logged into the server as www-data (su www-data) and run the command manually. The result is the following error :

```

[Java framework] Error in function createSettingsDocument (elements.cxx).
javaldx failed! 
Error: Unable to connect or start own listener. Aborting.
```Very very frustrating bug ](*,)

Thank you so much for the help and time to anyone who can help me with this issue ;)

---

### Post by My_web on 2010-09-07
I'm having the exact same issue. I've tried everything I found online. Did you ever find a solution?

Thanks

---

### Post by adamtog on 2010-12-04
Hi,

I had the same problem with javaldx. I got it to work by executing the following lines as root. I assume www-data's home-directory is /var/www. I admit to not knowing why it helps. 

1) Remove old .openoffice.org-folders in /var/www.
root@host: rm -rf /var/www/.openoffice.org

2) Copy .openoffice.org-folders from root 
root@host: cp -a ~/.openoffice.org /var/www

3) Change owner to www-data
root@host: chown -R www-data.www-data /var/www/.openoffice.org

---

### Post by brain90 on 2011-12-28
This a bugs in unoconv. Maybe this links can help :
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501440](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501440)

First think first, start running OpenOffice.org as listener in the background on a headless X server using this command.
> 
soffice -display :0.0 -norestore -headless \     "-accept=socket,host=localhost,port=2002;urp;StarOffice.ComponentContext" 
Try to running unoconv via php exec command.

---

