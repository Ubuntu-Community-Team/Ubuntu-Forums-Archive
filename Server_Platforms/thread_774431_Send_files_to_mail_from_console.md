---
title: "Send files to mail from console"
date: 2008-04-29
forum: Server Platforms
---

### Post by adamitj on 2008-04-29
In a near time ago, I saw some linux package (do not remember exactly the name) wich could send **files** to an e-mail from console.

Is there anything similar in Ubuntu Server ?

*Note: I'm use Ubuntu Server Gutsy Gibbon 7.10.*

---

### Post by cdtech on 2008-04-29
I just use the command line:
```
cat /file.txt | mail -s 'subject' user@somewhere.com
```

I use this in scripts to monitor my server.

---

### Post by adamitj on 2008-04-30
Thanks for reply me cdtech. I have 2 additional questions:

1) Do I need to set an e-mail server on the machine to sendo e-mails? Is there a way to use a 'fake' SMTP server (like freeSMTP Server for Windows)? 

2) This tip you sent me is helpfull on administration, and is very worth for me. But I need to send other files too, like "tar.bz2" archives. How can I do it?

Thanks in advance!

---

### Post by Dr Small on 2008-04-30
I just install Postfix and mailutils and then I can send mail from the console.

---

