---
title: "Ubuntu server questions can anyone help."
date: 2011-12-19
forum: Server Platforms
---

### Post by Jennifer29 on 2011-12-19
Ok I went and bought a dlink wireless router it seems like the easiest way to set up a server.No problems there.

Problem 1 I have satellite INTERNET they have a download limit of 250 MB during the day.But from 2 to 7 am there is no download limit so my updates need to be done during this time. Is there a way to set the server up to only download updates during this time?

Problem 2 I also bought a laptop pc that will be on the server too but i am going to use that one for my family to use when they come over.What i would like to do is set the server up were i can password protect my files and the laptop user can't access them.But sometimes I download mp3's for them and want them to have access to those files.I guess i would like two folders one password protected and the other not.

Also looking to see if there is anything else i need to install.I don't know what a open ssh server email server or print server does so i don't know if i would want them?.I have samba installed.

Thank you

---

### Post by Dangertux on 2011-12-19
> **Jennifer29 said:**
> Ok I went and bought a dlink wireless router it seems like the easiest way to set up a server.No problems there.

Problem 1 I have satellite INTERNET they have a download limit of 250 MB during the day.But from 2 to 7 am there is no download limit so my updates need to be done during this time. Is there a way to set the server up to only download updates during this time?

Problem 2 I also bought a laptop pc that will be on the server too but i am going to use that one for my family to use when they come over.What i would like to do is set the server up were i can password protect my files and the laptop user can't access them.But sometimes I download mp3's for them and want them to have access to those files.I guess i would like two folders one password protected and the other not.

Also looking to see if there is anything else i need to install.I don't know what a open ssh server email server or print server does so i don't know if i would want them?.I have samba installed.

Thank you

Pretty simple on the first one. Just disable (I assume you're using Ubuntu server) automatic updating, then just update manually via 


```

sudo apt-get update && sudo apt-get upgrade

```

Alternatively there may be some way to customize what time the updates are performed, however I'm not aware of it other than just doing them yourself.  You could also create a cron job for root to do it as well, but that is really more work than is necessary if you're using LTS, updates aren't really pushed that often.

For problem 2 just create multiple shared folders. Here is the community documentation for samba : [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

some only applies to older versions some current. So just watch your versioning while going through that.

OpenSSH gives you terminal access, if this is a headless server (no monitor) you may wish to install openssh-server

```

sudo apt-get install openssh-server

```

A print server well..Serves up access to a printer. Email is equally self explantory, it is also something of a pain to secure, so unless you need it I wouldn't recommend installing it.

Hope this helps

---

### Post by Jennifer29 on 2011-12-19
Thank you

I'M sorry I should have said it's Ubuntu server 11.10 and it is a headless server  (no gui) I didn't think i installed everything i needed too.I'LL need to reinstall the OS or is there a easier way to install open ssh?Maybe a print server I may use that.I don't know why i would need a email server so I'LL leave that one out.

---

### Post by CharlesA on 2011-12-19
Well, I suppose you could set it not to do automatic updates and then use a cronjob to run updates in the early morning. Not the best thing, but it would get the job done.

You can install openssh server by running this command:

```
sudo apt-get install openssh-server
```

---

### Post by Jennifer29 on 2011-12-19
Thank you all so much.I installed openssh server but i do not know what a cron job is or how to set it up.

---

### Post by CharlesA on 2011-12-19
> **Jennifer29 said:**
> Thank you all so much.I installed openssh server but i do not know what a cron job is or how to set it up.
Check this out:
[http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

---

### Post by Jennifer29 on 2011-12-19
Thank you once again. I'LL have a go at it and see if i can get it done.

---

### Post by CharlesA on 2011-12-19
If you have any questions, be sure to post again. :)

---

