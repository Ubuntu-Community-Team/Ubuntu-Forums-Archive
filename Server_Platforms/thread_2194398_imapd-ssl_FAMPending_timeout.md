---
title: "imapd-ssl: FAMPending: timeout"
date: 2013-12-18
forum: Server Platforms
---

### Post by s0mba on 2013-12-18
Hello,
I'm a beginner with courier. Could someone please help me clarify the error logs I get. The fetching of mail
seems to work fine on the clients, though, having error messages in the log does not seem like a right thing..

Observing the following logs in the mail.err log:
```
Dec 1 05:20:02 mail imapd-ssl: FAMPending: timeout
Dec 1 05:39:02 mail imapd-ssl: FAMPending: timeout
Dec 1 07:16:33 mail imapd-ssl: FAMPending: timeout
Dec 1 07:56:52 mail imapd-ssl: FAMPending: timeout
Dec 1 08:43:19 mail imapd-ssl: FAMPending: timeout
Dec 1 08:44:33  imapd-ssl: last message repeated 4 times
```

Gamin version (as at first I thought it was related to [this]("https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756")):
```
# aptitude show gamin
Package: gamin                           
New: yes
State: installed
Automatically installed: yes
Version: 0.1.10-4ubuntu0.1
```

Courier-imap version:
```
# aptitude show courier-imap
Package: courier-imap                    
New: yes
State: installed
Automatically installed: yes
Version: 4.9.1-1ubuntu4
```

Please, let me know if there is additional information needed..
Thanks.

---

### Post by bashiergui on 2013-12-20
See this
[https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756)

---

### Post by s0mba on 2013-12-20
> **bashiergui said:**
> See this
[https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756)

Had a look at it already.. The version of gamin is the updated one (mentioned in my first post)..
> Gamin version:
```
# aptitude show gamin
Package: gamin                           
New: yes
State: installed
Automatically installed: yes
Version: 0.1.10-4ubuntu0.1

```

Thanks anyways..

---

### Post by bashiergui on 2013-12-20
Ah I missed that link in your OP. I presume you tried the workarounds in this post 
[http://ubuntuforums.org/showthread.php?t=1970712](http://ubuntuforums.org/showthread.php?t=1970712)
use fam instead gaminreduce amout of message in mailboxes

---

### Post by s0mba on 2013-12-20
Right, it seems that switching to fam is the only way to verify if the problem is related to gamin.
Just did not want do fiddle with the system before making sure there is nothing more to it...
Thanks again!

---

