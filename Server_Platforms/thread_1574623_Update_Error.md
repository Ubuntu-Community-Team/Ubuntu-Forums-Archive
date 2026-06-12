---
title: "Update Error"
date: 2010-09-14
forum: Server Platforms
---

### Post by wdtice on 2010-09-14
New to Ubuntu not to Unix. I am having issues with aptitude updates. Gives error unable to locate. When I look for the file manually I cannot find it either. It is looking for [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US. Is there a site that list all mirrors that carry the updates? I would like to find manually and adjust source.list file.

---

### Post by drs305 on 2010-09-14
The site is working for me. You can try eliminating the language translation part by running this command first. I don't think root privileges are required. The command is not persistent.
```

unset LANG LANGUAGE
sudo apt-get update

```

Does your sources.list show "lucid/main" or "lucid main"?
Here's mine:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main

---

### Post by wdtice on 2010-09-14
Is the same as yours. Is there a way to turn on db or debug in ubuntu?

---

### Post by endotherm on 2010-09-14
you can get the last 10 lines of the debug log with this command
```
dmesg | tail
```

I will have a repo server or two disappear every once in a while. I just tell it to check 2-3 times, and if it fails, I put it down and come back a few hours later. that process hasn't failed me yet.

---

### Post by wdtice on 2010-09-14
I will double check the log file but still haven't found a site/page listing for all mirrors. Thanks for your help.

---

### Post by drs305 on 2010-09-14
> **wdtice said:**
> I will double check the log file but still haven't found a site/page listing for all mirrors. Thanks for your help.


This what you want?
[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

---

### Post by wdtice on 2010-09-14
Thank you for mirror list. I have reviewed multiple mirrors and not one has the file that was built by the server dist file. Specifically "Translation-en_US" This should be corrected in the down file. Thank you for your help in this matter. I will adjust and correct the issue in my project server.

---

