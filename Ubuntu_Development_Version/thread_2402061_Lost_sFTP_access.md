---
title: "Lost sFTP access"
date: 2018-09-25
forum: Ubuntu Development Version
---

### Post by Nezmin2 on 2018-09-25
Hey guy's, I have a VM of Ubuntu Server 18.10 running on my win10 pc. Yesterday I was able to sFTP into my server using BitVise ssh. I was able to transfer files onto my server without any issues. Today. I keep getting a failed message. The message say's that my server is denying permission. I didn't change anything and I am very confused.

---

### Post by TheFu on 2018-09-25
Considering that 18.10 hasn't been released, this needs to in the "development release" forum.
I'd normally try to help with ssh/sftp, but can't with this version. Sorry.

---

### Post by Nezmin2 on 2018-09-25
What advice would you give for 18.04?

---

### Post by wildmanne39 on 2018-09-25
*Thread moved to **Ubuntu Development Version for a more appropriate fit**.*

---

### Post by zika on 2018-09-26
OpenSSL 1.1.1-1ubuntu1/2?

---

### Post by Nezmin2 on 2018-09-26
No treatment of the disease is unknown? I'm confused.

---

### Post by QIII on 2018-09-26
The exact text of the error might be helpful here.  So would logs from the server.

It is difficult to "treat the disease" without first diagnosing it.  There could be dozens of reasons why this is happening.  We could take stabs in the dark, but that is confusing and inefficient.

---

### Post by Nezmin2 on 2018-09-26
OK, so the exact error msg is: 

```
12:22:31.602 Current date: 2018-09-2612:22:31.602 SFTP session on '192.168.1.24:22' started successfully. Using SFTP protocol version 3.
12:22:31.610 Listing local folder 'C:\Users\Max\Downloads' succeeded.
12:22:31.610 Changing current local folder to 'C:\Users\Max\Downloads' succeeded.
12:22:31.636 Listing remote folder '/' succeeded.
12:22:31.636 Changing current remote folder to '/' succeeded.
12:22:31.639 Stating symbolic link '/initrd.img.old' succeeded.
12:22:31.643 Stating symbolic link '/vmlinuz' succeeded.
12:22:31.647 Stating symbolic link '/vmlinuz.old' succeeded.
12:22:31.651 Stating symbolic link '/initrd.img' succeeded.
12:22:35.297 Listing remote folder '/opt' succeeded.
12:22:35.297 Changing current remote folder to '/opt' succeeded.
12:22:37.013 Listing remote folder '/opt/ftbrevelation' succeeded.
12:22:37.013 Changing current remote folder to '/opt/ftbrevelation' succeeded.
12:22:46.351 Passing upload list to upload manager succeeded.
12:22:46.352 Uploading local file 'C:\Users\Max\Downloads\FTBRevelationServer_2.4.0.zip' started. Using 'binary' transfer mode.
12:22:46.369 Uploading local file 'C:\Users\Max\Downloads\FTBRevelationServer_2.4.0.zip' failed. Opening remote file '/opt/ftbrevelation/FTBRevelationServer_2.4.0.zip' failed. Open failed with SFTP error PermissionDenied: Permission denied.
12:28:00.074 Passing upload list to upload manager succeeded.
12:28:00.075 Uploading local file 'C:\Users\Max\Downloads\FTBRevelationServer_2.4.0.zip' started. Using 'binary' transfer mode.
12:28:00.104 Uploading local file 'C:\Users\Max\Downloads\FTBRevelationServer_2.4.0.zip' failed. Opening remote file '/opt/ftbrevelation/FTBRevelationServer_2.4.0.zip' failed. Open failed with SFTP error PermissionDenied: Permission denied.
```

I am unsure as to how to access the logs and add them here. Any direction would be great.

---

