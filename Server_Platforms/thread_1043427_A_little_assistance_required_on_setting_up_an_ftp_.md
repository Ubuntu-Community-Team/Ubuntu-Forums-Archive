---
title: "A little assistance required on setting up an ftp user"
date: 2009-01-18
forum: Server Platforms
---

### Post by Chris of Arabia on 2009-01-18
I'll readily admit that my knowledge of Ubuntu is a little thin, so my apologies if this has been covered elsewhere and I've not found it. Whilst I've searched on the topic a number of times, there seem to be so many variants on FTP set-up, I'm a little unsure as to whose "simple instructions" I'd be best following.

I want to set up vsftpd for my Ubuntu LAMP server on a home network. The aim is to have the server behave pretty much as I'd find out on an ISP provided site, where I am using FTP as a means to deploying files into the /var/www/ folder.

I've already got vsftpd installed and working, and can connect using an FTP client which by default takes me to /home/administrator/ using the credentials for the 'administrator' account. This account doesn't seem to have permissions to write into the /var/www/ folder though.

Could one of the more experienced members give me a steer on how to create an FTP user that can fully access /var/www/ and advise on what else I'll need to do to get this working.

The only changes I've made so far in vsftpd.conf are:
[FONT=monospace]
[/FONT]anonymous_enable=NO[FONT=monospace]
[/FONT]local_enable=YES[FONT=monospace]
[/FONT]write_enable=YES

Everything else is as provided.

Also idly curious as to where my previous posts on here went too - someone been cleaning up?

---

### Post by Chris of Arabia on 2009-01-19
Gratuitous bump - any thoughts from anyone here?

---

### Post by Eviltechie on 2009-01-19
Well /var/www is owned by root, so unless you are logged in as him, you can't change anything there.

The better method would be to chmod /var/www to 775.

---

### Post by Chris of Arabia on 2009-01-19
OK, so if I'm understanding this correctly, the chmod command will give rwx permissions to any user, following which, the 'administrator' account should be able to work within that folder without restriction?


...but, 'root' still owns the directory

---

### Post by Chris of Arabia on 2009-01-19
OK, did that and I'm now being shown that /var/www folder has the following permissions assigned to it:

```
dwrxrwx-x
```

Which, if I'm understanding that correctly, should give me the permissions needed. However, I'm still unable to FTP into that folder using the 'administrator' account, neither can I create a file from the server itself (using Vim in this instance) on that account - unsurprisingly, it works fine using the 'root' account.

---

### Post by Chris of Arabia on 2009-01-19
OK, did that and I'm now being shown that /var/www folder has the following permissions assigned to it: *dwrxrwx-x*

Which, if I'm understanding that correctly, should give me the permissions needed. However, I'm still unable to FTP into that folder using the 'administrator' account, neither can I create a file from the server itself (using Vim in this instance) on that account - unsurprisingly, it works fine using the 'root' account.

EDIT: It's perhaps worth noting that when trying to FTP a file into /var/www, I get a "553 Could not create file" error message

---

### Post by hyper_ch on 2009-01-19
why use ftp and nod sftp/scp?
It's so simple getting up and running scp and have it secured by MySecureShell

(Besides you could alias the usernames to the apache usernames so that all files created will run under apache.)

---

### Post by Chris of Arabia on 2009-01-19
> **hyper_ch said:**
> why use ftp and nod sftp/scp?

Just purely because I'm in the early stages of learning to use Ubuntu and many things that may be common knowledge to others aren't yet things I'm aware of.

I would still like to get this sorted out as per the original plan though. 

One odd thing I did spot, when I checked on the services running on the box, it shows that vsftpd is 'not running', but if I then go and try to start it, I get a message back saying it's already running. The message makes sense as I was actually connected via FireFTP from my Vista box at the time - the service status message makes considerably less sense.

---

### Post by Chris of Arabia on 2009-01-19
Would it be considered a safe option to run the following...

```
$ chown :webaccess /var/www
```

...where 'webaccess' is a group I've set up with a couple users in it?

---

### Post by Chris of Arabia on 2009-01-19
Well that last one seems to have done the trick. I can now FTP into the server successfully and upload files. I'd still be curious as to whether changing the ownership of /var/www should be considered an acceptable practice though.

---

