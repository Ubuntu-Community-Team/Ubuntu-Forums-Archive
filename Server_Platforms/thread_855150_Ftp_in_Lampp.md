---
title: "Ftp in Lampp?"
date: 2008-07-10
forum: Server Platforms
---

### Post by Sn3ipen on 2008-07-10
I am using Lampp as a virtual host on my computer and is satisfied with it.

But how can i make a ftp server on it? I have to because i need to test all the features of my cms before putting it live.

---

### Post by comandrei on 2008-07-10
```

sudo apt-get install vsftpd

```

---

### Post by carcdrcdr on 2008-07-10
Do NOT use ftp as it sends your username and password PLAIN text.

Use sftp. (SecureFTP)

---

### Post by Sn3ipen on 2008-07-10
Thanks allot.

I will try it out.

But is there any good resources on how to configure it?

---

### Post by qrwe on 2008-07-10
> **Sn3ipen said:**
> Thanks allot.

I will try it out.

But is there any good resources on how to configure it?

Found this: [http://sudan.ubuntuforums.com/showthread.php?t=91887](http://sudan.ubuntuforums.com/showthread.php?t=91887)

---

### Post by Sn3ipen on 2008-07-10
Thanks. By following the howto @qrwe linked to I am having an issue with that the user will start up at the whole home directory when logging in. Not the one i have set it to.

I am trying to have a virtual host for my test cms but i need to hve it so that when i log in i have to come to the directory i have set it to or else my cms wont work properly.

---

### Post by carcdrcdr on 2008-07-10
> 
I am trying to have a virtual host for my test cms but i need to hve it so that when i log in i have to come to the directory i have set it to or else my cms wont work properly.

Sounds like you need to change your home dir for the user in question so that when you login you are just "put" in the right path.

To do this just edit your /etc/passwd (as root)

For example a line from mine for the user "monitor":
monitor:x:1000:1000:Nagios Monitoring Account,,,:/home/monitor:/usr/bin/zsh

Note the 6th field (seperated by ':') says "/home/monitor" all I have to do is change that to something else like so:
monitor:x:1000:1000:Nagios Monitoring Account,,,:/export/jail/home/monitor:/usr/bin/zsh
I am trying to have a virtual host for my test cms but i need to hve it so that when i log in i have to come to the directory i have set it to or else my cms wont work properly.

Now next time I login I will be in this DIR: /export/jail/home/monitor

Hope that helps ;)

---

