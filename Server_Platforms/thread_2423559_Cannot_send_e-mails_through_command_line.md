---
title: "Cannot send e-mails through command line"
date: 2019-07-25
forum: Server Platforms
---

### Post by alfirdaous on 2019-07-25
Hi all,

I would like to send e-mails through command line:

```

echo "File encoding finished on $Now_dmY, with some errors ffmpeg: $ffmpeg MP4Box: $mp4box Thumb: $thumb Rsync: $rsync" | mutt -s "[Failed] Encoding File" -- foo@bar.com

```[FONT=Verdana]

The result is:
[/FONT]```

/root/sent is not a mailbox.
Could not send the message.
You have mail in /var/mail/root

```[FONT=Verdana]
[/FONT]

[COLOR=#242729][FONT=Arial]When I opened the root file:
[/FONT][/COLOR]```
Diagnostic-Code: smtp; 530 5.7.1 Client was not authenticated
--A1DA321EB7.1563969927/ns366860.ip-94-23-8.eu
Content-Description: Undelivered Message
Content-Type: message/rfc822

```[COLOR=#242729][FONT=Arial]

Thanks for your help[/FONT][/COLOR]

---

### Post by aromo2 on 2019-07-25
Have you tried removing the double-dash?
```
echo "blah blah blah" | mutt -s "[Failed] Encoding File" foo@bar.com
```

---

### Post by alfirdaous on 2019-07-26
I've got the same result, may be something wrong with mail configuration, I have a doubt about the sent file under root directory:

```

# ls -l /root/sent 
-rw-r--r-- 1 root root 1 Jun 20 16:16 /root/sent

```

---

### Post by LHammonds on 2019-07-26
> **alfirdaous said:**
> I would like to send e-mails through command line[COLOR=#242729][FONT=Arial][/FONT][/COLOR]
What mail server are you trying to use?  Is it gmail?  Locally hosted mail server on another machine....or local machine?

---

### Post by alfirdaous on 2019-07-26
> **LHammonds said:**
> What mail server are you trying to use?  Is it gmail?  Locally hosted mail server on another machine....or local machine?

It is Gmail, hosted on a distant web server, not local

---

### Post by LHammonds on 2019-07-29
Gmail has been known to change how people can connect to them and thus break server configurations / scripts.  I have not used gmail as my backend mail server in a long time so I don't have any setup tutorials specific to that which are relevant today.

I would do a Google search and look for the most-recent article on how to use gmail for command-line and test each one until I found a working solution.  But be aware that Google can make changes that will break your automation at any time.

Maybe someone else here has current experience with setting up automation with gmail.  Might also want to modify your title to include "using gmail" at the end to catch the eye of those using gmail.

LHammonds

---

