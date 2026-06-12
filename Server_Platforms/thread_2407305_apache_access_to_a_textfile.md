---
title: "apache access to a textfile"
date: 2018-12-02
forum: Server Platforms
---

### Post by cazz on 2018-12-02
I have upload some files to the html folder of my apache server.
When I then open a browser and access everythings looks fine.

Then I did connect a extern system to upload a text file to the folder ever 30 sec and I'm the owner of the file so now the apache server does not have permission to read the file.


not sure how to fix that. maybe I can do something with the group rights but not sure how.

---

### Post by SeijiSensei on 2018-12-02
The /var/www tree is owned by the root user.  To upload files you need to be logged as root, or have write permissions to that directory.  One kludgy solution is the change the group ownership of the directory to yourself and enable group write permissions.

```

cd /var/www
sudo chgrp yourusername html -R
sudo chmod g+w html -R

```

---

### Post by cazz on 2018-12-02
mm have Think about that but at first I do not want to give root FTP access. 
And everytime my account upload a file it going to change the Group owner back to the me.

But I was thinking in the vsftp config file it was something about umask settings so I maybe can do something about that

---

### Post by cazz on 2018-12-02
I use vsftp when I upload the textfile to the folder and I trying to set the file to 666 so it can be read but not sure what to do

I did edit the config file for vsftp



```
local_umask=111
chmod_enable=YES
file_open_mode=0666

```

Not sure if that is the right but it still give the file 620 and not 666

---

### Post by cazz on 2018-12-03
A update

umask is not so easy :)

Did try this info from here

[https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

```
local_umask=111
file_open_mode=0777
```

It give me 620 of the file

then I did try 000 of umask and it gave me 777 of the file

I did try 001 and it gave me 776

101 give me 632??


so something is strange

---

### Post by TheFu on 2018-12-06
It is mask. Appears to be working as expected.

umask of 002 ---> 775 permissions.
umask of 022 ---> 755 permissions.
umask of 007 ---> 770 permissions.

---

### Post by cazz on 2018-12-06
Well yes but why does 111 not give me 666 but 620??

---

### Post by TheFu on 2018-12-06
Please post the **ls -l** for each file you attempted with the different unmask settings.  After any change, restart the webapp.  user, group, other and the permissions bits are important.

files uploaded through a web interface will be owned by the web-server process - either apache or www-data - which depends on your installation.  Access by other userids is controlled by the file and parent directory permissions.  There isn't any magic, just things not understood, yet.  ;)

---

### Post by Morbius1 on 2018-12-07
> **cazz said:**
> 
```
local_umask=111
file_open_mode=0777
```

It give me 620 of the file

then I did try 000 of umask and it gave me 777 of the file

I did try 001 and it gave me 776

101 give me 632??


so something is strange

Hmm ....

If 111 is interpreted as decimal and not octal then 111 in decimal = 157 in octal: 777-157=620
If 101 is interpreted as decimal and not octal then 101 in decimal = 145 in octal: 777-145=632
And 001 is ... well ... 001 either way.

Been a while since I've used vsftp but me thinks you need to precede the umask value by a zero to tell it it is in octal:
```
local_umask=0111
```

---

### Post by TheFu on 2018-12-07
Morbius is correct.  The vsftp.conf manpage is clear:
```
local_umask
    The value that the umask for file creation is set to for local users. 
    NOTE! If you want to specify octal values, remember the "0" prefix 
    otherwise the value will be treated as a base 10 integer!

    Default: 077
```

However, their example, sucks.  BTW, the default of 0077 **is** an important and smart security setting to prevent abuse of an FTP server storage for illegal activities.  These activities have been abusing plain FTP servers since the mid-1990s and are well-known.

Any chance we could talk you into using sftp instead?

---

### Post by cazz on 2018-12-07
wow thanks it was so simple that I did not have a zero in the beginning so now I have 666 on the file :)

---

### Post by cazz on 2018-12-07
> **TheFu said:**
> Morbius is correct.  The vsftp.conf manpage is clear:
```
local_umask
    The value that the umask for file creation is set to for local users. 
    NOTE! If you want to specify octal values, remember the "0" prefix 
    otherwise the value will be treated as a base 10 integer!

    Default: 077
```

However, their example, sucks.  BTW, the default of 0077 **is** an important and smart security setting to prevent abuse of an FTP server storage for illegal activities.  These activities have been abusing plain FTP servers since the mid-1990s and are well-known.

Any chance we could talk you into using sftp instead?

ahh I did not see that, feel stupid now but thanks again :)
Well this FTP is only going to run on the local network. I do not like to open port outside my network and if I going to do that I use SSH/SFTP with a another port then the default

---

