---
title: "Sending e-mails using PHP"
date: 2007-01-08
forum: Server Platforms
---

### Post by lugos on 2007-01-08
Hello,

I don't know if this is the right place to post this question, but I have set up an Ubuntu web server and I am trying to use the PHP mail() function but it is not working.  In my research I found that PHP uses an underlying program/process in Linux that sends the e-mail.  When I installed Ubuntu, it was the LAMP version.  Is there anything else I need to set up or install for the mail() function to work?

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by chrisfay on 2007-01-08
Do you have any mail packages installed?

Try adding:

```
sudo apt-get install mailutils
```

If I remember correctly, the LAMP option doesn't provide any mail functions by default.

---

