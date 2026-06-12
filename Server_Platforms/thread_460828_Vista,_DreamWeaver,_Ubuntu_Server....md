---
title: "Vista, DreamWeaver, Ubuntu Server..."
date: 2007-06-01
forum: Server Platforms
---

### Post by LindsaySlater on 2007-06-01
Hello all
Yet another problem I'm having... This time I believe it's the fault of Microsha. Microsoft, sorry... Anyways, I got my server running Ubuntu 6.10, and I'm happy with it, I can run it perfectly from my laptop, also running 6.10 (neither are powerful enough for 7.04) But today I discovered the true problems with my set up. My regular desktop runs Vista *Shudder* I use Dreamweaver, I don't think I could handle anything else. But when I try to connect to the server, everything I have tried either says that I don't have the right username/password (Which I do) or it logs me into my home folder on the server, which I also don't want... I would like to be able to FTP right into /var/www... Does anybody have any ideas? I suspect I'll be up most of the night working on this, It's rather urgent. Thanks
Lindsay

---

### Post by MystaMax on 2007-06-05
hello lindsay

so it looks like your main question is **how to change the default path after login**. I [googled vsftp config]("http://www.google.com/search?q=vsftpd+config&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a"), and found some helpful stuff. I found that [Redhat documentation]("http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-vsftpd-conf.html") is a good reference for some server stuff that I have to do. I can't wait til ubuntu server is this well documented.

You'll have to dig into the /etc/vsftp.conf file and make some changes.

first backup your conf file

```

sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.BAK

```then I opened up my vsftpd.conf file using vim

```

sudo vi /etc/vsftpd.conf

```I scrolled all the way to the bottom and added the following

```

#local_root -- Specifies the directory vsftpd changes to after a local user logs in
local_root=/var/www

```I always add comments so I know what I did and what the directive does.

After making changes to the conf file, you will have to restart vsftpd.

to stop vsftpd:

```

sudo /etc/init.d/vsftpd stop

```to start vsftpd:

```

sudo /etc/init.d/vsftpd start

```I did this myself (I also edit files in dreamweaver, but I'm slowly moving to [aptana]("http://www.aptana.com")), and it works great. If you don't know vim very well, you can use nano.

```
sudo nano /etc/vsftpd.conf
```good luck! let me know if it works for you.

---

### Post by LindsaySlater on 2007-06-05
Hmm, I'll have to try that. I did manage to get things working using Samba, added another share linked to /var/www. It works, and that's what I was after. It would be nice to FTP from school though... I think I'll try this right away. I'll let you know if it works. Thanks muchly!

---

