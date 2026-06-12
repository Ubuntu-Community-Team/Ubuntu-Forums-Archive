---
title: "Installing MSN Live Messenger .msi problems"
date: 2011-02-01
forum: Wine
---

### Post by nubnux on 2011-02-01
I'm getting an error when trying the msiexec /i command

```
user01@ubuntu01:~$ msiexec /i Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi 
err:msi:copy_package_to_temp failed to copy package L"Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi" to L"C:\\users\\user01\\Temp\\msi193.tmp" (2)
```

I also tried another .msi file and I got the same error. What could be causing this?

---

### Post by cogadh on 2011-02-01
First of all, MSN Live Messenger doesn't really work in Wine, you'd be much better off using one of the Linux native IM apps that already supports MSN, like Pidgin or aMSN.

As for the error you are getting, it seems like a basic copy failure, which is usually caused by something simple, like a lack of drive space, a lack of permissions to the destination directory, a lack of the destination directory entirely, etc.

I do wonder why your installer has such a strange name, shouldn't it just be named something like "Install MSN Live.msi"? Its possible that is somehow indirectly causing issues. You could try renaming it to get rid of all the numbers and special characters then re-run the installer to see if it makes a difference.

---

### Post by _outlawed_ on 2011-02-01
Best bet is to go with Pidgin.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127](http://appdb.winehq.org/objectManager.php?sClass=application&iId=127)

MSN Live Messenger is rittled with Garbage ratings.

---

### Post by ronnielsen1 on 2011-02-01
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127](http://appdb.winehq.org/objectManager.php?sClass=application&iId=127)

Here's the winehq pages for msn messenger, but I'm putting in the 3rd vote for pidgin. It works great

---

### Post by nubnux on 2011-02-02
Well, I guess there's no sense in trying to make it work then. I'll give Pidgin a shot. Thx guys

---

