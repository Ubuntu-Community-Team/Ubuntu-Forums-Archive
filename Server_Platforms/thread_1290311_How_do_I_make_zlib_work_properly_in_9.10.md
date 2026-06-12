---
title: "How do I make zlib work properly in 9.10 ?"
date: 2009-10-13
forum: Server Platforms
---

### Post by x94bp6ru6 on 2009-10-13
I found that pclzip.php isn't working properly after I set everything up in 9.10

(I actually found it out when trying to upgrade a plugin in wordpress 2.8.4, it gave me an error saying "Abort class-pclzip.php : Missing zlib extensions")

but I'm pretty sure that i have zlib extension installed,  (zlib1g)

can anyone help me or give me some suggestion on what to do next? thanks in advance

and below is some settings about zlib taken from phpinfo

zlib
ZLib Support     enabled
Stream Wrapper support     compress.zlib://
Stream Filter support     zlib.inflate, zlib.deflate
Compiled Version     1.2.3.3
Linked Version     1.2.3.3

Directive    Local Value    Master Value
zlib.output_compression    On    On
zlib.output_compression_level    -1    -1
zlib.output_handler    no value    no value


zip
Zip     enabled
Extension Version     $Id: php_zip.c,v 1.1.2.50 2009/03/01 17:35:25 iliaa Exp $
Zip version     1.8.11
Libzip version     0.9.0 

I apreciate your time on reading it,
Victor

---

### Post by rossigee on 2009-10-14
Keep an eye on this bug report...

[https://bugs.launchpad.net/ubuntu/+source/zlib/+bug/439407](https://bugs.launchpad.net/ubuntu/+source/zlib/+bug/439407)

---

### Post by x94bp6ru6 on 2009-10-14
so it's a bug,
all right, thank you!!
now awaiting for it to be solved

Victor

---

### Post by aim on 2009-10-30
any updates on this bug? it's the release time and the bug still exist in the php5...

---

### Post by x94bp6ru6 on 2009-10-31
Fixed!!!! ya!~

---

### Post by suniyo on 2009-10-31
Hai how you fixed that? I am having a bit trouble with it too...

---

### Post by PixelDJ on 2009-11-02
I'm having this issue as well. I saw the bug report but I didn't see anything that helped. Is there a fix around?

---

