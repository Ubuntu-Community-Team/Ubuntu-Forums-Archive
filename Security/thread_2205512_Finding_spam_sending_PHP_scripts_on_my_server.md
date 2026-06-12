---
title: "Finding spam sending PHP scripts on my server"
date: 2014-02-14
forum: Security
---

### Post by Othmane on 2014-02-14
Hello,

Someone hacked one of my website and he is spamming and i can't find the file who is sending this spam 

the file is named : LICENSE.php 

but there is allot of file named like that so i tried to filter with some thing like that :  find . -name "LICENSE.php" -exec grep -Hn "mail(" {} \;  but no result it seems like the file is crypted

there is some information on Mail queue   

Received: by neoglob.lpm-dz.net (Postfix, from userid 33)
	id ED89F2E287C3; Thu, 13 Feb 2014 23:38:13 +0000 (UTC)
To: <snip>
Subject: =?UTF-8?B?4pqgIFtEb2N1bWVudF0gTsKwIDogNTYwNjY0OTA0Lg==?=
X-PHP-Originating-Script: 10046:LICENSE.php
From: CICBANQUE <NO-REPLAY@b.cic.fr>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="aab6952989d747177bc4ac20372a4ba4"
Message-Id: <20140213234332.ED89F2E287C3@neoglob.lpm-dz.net>
Date: Thu, 13 Feb 2014 23:38:13 +0000 (UTC)


but im a noob user so i dont how to exploit this information so please help me 

Othmane

---

### Post by CharlesA on 2014-02-14
If your website has been compromised, it is best to usually determine how they got access and figure out how to fix it and then reinstall the server and restore your data from backups because you can't be sure that is the only file they touched.

---

### Post by fugu2 on 2014-02-14
> **CharlesA said:**
> If your website has been compromised, it is best to usually determine how they got access and figure out how to fix it and then reinstall the server and restore your data from backups because you can't be sure that is the only file they touched.
+1 on a clean wipe.
most likely the mail command has been *obfuscated*. try and look for 'eval' with
```
$ find . -type f -name '*.php' -exec grep -i -l 'eval' '{}' \;
```
Maybe that will narrow it down for you.
It will probably look like extra confusing code with no coments

---

### Post by Othmane on 2014-02-15
Thanks for answer, im going to check =)

---

### Post by thnewguy on 2014-02-16
I agree with the above posters. Your best bet is to wipe the server's copy of the website and restore it from backups.

---

### Post by sandyd on 2014-02-16
Also, make sure you firewall port 25 outgoing if you can - and log attempts to send out using that port. Then, there will be no spam, and you will know when someone is trying to send spam out.

---

### Post by CharlesA on 2014-02-16
> **sandyd said:**
> Also, make sure you firewall port 25 outgoing if you can - and log attempts to send out using that port. Then, there will be no spam, and you will know when someone is trying to send spam out.

+1.

---

