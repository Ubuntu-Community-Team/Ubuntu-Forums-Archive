---
title: "Help with apache"
date: 2008-08-04
forum: Server Platforms
---

### Post by divtech on 2008-08-04
I just installed Ubuntu Server.  When I try to access it from my browser by typing in the network ip address all I get on the screen are the words:  It works!
I want to install dotProject but don't know how to get past the It Works! screen.  Any help would be appreciated.
Thanks

---

### Post by jamesrfla on 2008-08-04
I created this thread when I set up my server. [http://ubuntuforums.org/showthread.php?t=844409](http://ubuntuforums.org/showthread.php?t=844409) Also if you are very new to Linux you can use a utility called webmin. It is a web based utility that can help you configure server stuff very easily. Use this code ```
sudo apt-get install webmin
``` Any questions just ask. :)

---

### Post by cariboo on 2008-08-04
If you still have a monitor and keyboard hooked up to your server, install Openssh eg:

```
sudo apt-get install openssh
```

You can then access your server remotely using ssh. You can also transfer to and from your server using sftp. If you are accessing your server from windows you can use putty to access your server in a terminal and use Winscp to copy files to your server.

Jim

---

### Post by Darkade on 2008-08-04
The "it works" is from apache web server it's to show you that... well it works. anything that you want to see in the "http://localhost" anything that you want apache to forward in your port 80 should be stored in /var/www

---

### Post by bodhi.zazen on 2008-08-04
A more descriptive title works even better !

---

### Post by divtech on 2008-08-04
> **jamesrfla said:**
> I created this thread when I set up my server. [http://ubuntuforums.org/showthread.php?t=844409](http://ubuntuforums.org/showthread.php?t=844409) Also if you are very new to Linux you can use a utility called webmin. It is a web based utility that can help you configure server stuff very easily. Use this code ```
sudo apt-get install webmin
``` Any questions just ask. :)
Thank you for the information.  I will give it a try and let you know what happens. Thanks again.

---

### Post by perlluver on 2008-08-04
Try ```
sudo apt-get install ebox
```  webmin was removed.

---

### Post by divtech on 2008-08-04
> **cariboo907 said:**
> If you still have a monitor and keyboard hooked up to your server, install Openssh eg:

```
sudo apt-get install openssh
```

You can then access your server remotely using ssh. You can also transfer to and from your server using sftp. If you are accessing your server from windows you can use putty to access your server in a terminal and use Winscp to copy files to your server.

Jim
Thanks, I have Putty and WinSCP working great.  I copied webmin to the server but don't know where to put it so when I input sudo apt-get webmin install it can find it.  Can you tell me what directory I should save it in?
Thanks

---

### Post by divtech on 2008-08-04
> **perlluver said:**
> Try ```
sudo apt-get install ebox
```  webmin was removed.
I have installed ebox but now I don't know how to run it!
Help

---

### Post by 3rods on 2008-08-04
> **perlluver said:**
> Try ```
sudo apt-get install ebox
```  webmin was removed.

Damn, ebox looks sweet. Thanks, gonna try it out tomorrow.

---

### Post by cariboo on 2008-08-05
Just put the webmin deb in your home directory and the run:

```
dpkg -i ./webmin_1.420_all.deb
```

After installing the program you can access it via your web browser:

```
https://localhost:10000
```

Jim

---

