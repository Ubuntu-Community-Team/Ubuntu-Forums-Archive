---
title: "rkhunter installation problem"
date: 2010-05-08
forum: Security
---

### Post by yeehi on 2010-05-08
I am having trouble installing root kit hunter. I have downloaded and unpacked the package. It is in /tmp

When I try and execute the command:

```
cd /tmp/rkhunter-1.3.6
```

I get an error message:

```
Permission denied
```

I don´t know why. The instructions [here]("http://rkhunter.cvs.sourceforge.net/viewvc/*checkout*/rkhunter/rkhunter/files/README") say to check that the installer.sh script is executable if there are permission error messages, but I don´t know how to do that. Anyway, the problem is that I can´t navigate to the directory to run the script.

What should I do?

Thank you.

---

### Post by cariboo on 2010-05-09
Although you don't really need it, wouldn't be easier to install rkhunter from the repositories? Rkhunter is an after the fact tool, and finds to many false positives.

---

