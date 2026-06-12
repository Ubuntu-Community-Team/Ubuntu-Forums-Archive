---
title: "How to enable FTP on 10.04?"
date: 2010-06-05
forum: Server Platforms
---

### Post by thatryan on 2010-06-05
I bought a new ve server from Media Temple, but can not figure out how to enable/install/whatever FTP access to it? I just want to set it up so I can use transmit on my server. Do I hace to install FTP? What is the best way to do this? 

Thank you

---

### Post by richardjh on 2010-06-05
I personally use proftpd but the Ubuntu Server Guide explains how to set up vsftpd, which is probably a better choice.

You can get details in the [Ubuntu Server Guide > File Servers > FTP Server]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html"). This will explain how to install and set up vsftpd server in about 10 steps and should get you started.

---

### Post by thatryan on 2010-06-05
Sweet thanks, heading to read it shortly.
And once it is setup I will be able to use my Transmit FTP app?

---

### Post by richardjh on 2010-06-05
Transmit is an FTP client. 

You should be able to use it to connect, if everything works in the install and configuration.

Post back if you have problems connecting once you are all set up.

---

### Post by thatryan on 2010-06-05
Will do thanks. 

Weird thing I wonder of though, is once I installed Ubuntu to the server, I created my server directories and was able to get connected, with Transmit, to the server as root.  Uploaded my site files for that one, but nothing shows on the site... 

Is that strange?

---

### Post by wwwin on 2010-06-06
Hello everyone. I installed vsftpd in Lucid and it is working great. However, I only want to use FTP to transfer files between my machines, so I don't want to have it running as a service all the time.  I can stop it manually, but every time I reboot the service is running again. Is there any way to not have this ftp program as a service but to just start it when ever I need it? I tried BUM and I can stop it and start with that, but at reboot it starts as a service on again. Thanks.

---

### Post by richardjh on 2010-06-07
You can set vsftpd to not start automatically by editing the file using sudo

```
/etc/init/vsftpd.conf
```

Find the two lines that look like this:

```
start on (filesystem
        and net-device-up IFACE!=lo)
```

and comment them out so they look like this

```

#start on (filesystem
#        and net-device-up IFACE!=lo)
```

Then you can stop vsfptd by typing

```
sudo service vsftpd stop
```

Now in future if you want to be able to transfer files to the server, you will need to manually start vsftpd yourself.

```
sudo service vsftpd start
```

---

### Post by wwwin on 2010-06-07
Thank you very much for the quick response. I really appreciate it.


> **richardjh said:**
> You can set vsftpd to not start automatically by editing the file using sudo

```
/etc/init/vsftpd.conf
```Find the two lines that look like this:

```
start on (filesystem
        and net-device-up IFACE!=lo)
```and comment them out so they look like this

```

#start on (filesystem
#        and net-device-up IFACE!=lo)
```Then you can stop vsfptd by typing

```
sudo service vsftpd stop
```Now in future if you want to be able to transfer files to the server, you will need to manually start vsftpd yourself.

```
sudo service vsftpd start
```

---

