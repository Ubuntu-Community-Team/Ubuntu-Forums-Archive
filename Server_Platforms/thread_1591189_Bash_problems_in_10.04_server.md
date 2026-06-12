---
title: "Bash problems in 10.04 server"
date: 2010-10-08
forum: Server Platforms
---

### Post by prvteprts on 2010-10-08
Bash acts weird in 10.04 server. Whenever I try to run .sh scripts, every empty line in the script results in "command not found". Then on even simple scripts I get syntax errors, but the same exact scripts work on my 9.10 desktop installation.

There's also another problem, I'm not really sure if it's bash-related. After setting the proxy using ```
export http_proxy=http://my.proxy.com:80/
``` apt-get still doesn't use whatever proxy I set. The workaround is ```
sudo -i
``` and apt-getting from the root shell, but it's kind of annoying.

Does anybody have suggestions? Any help would greatly be appreciated.

---

### Post by dtfinch on 2010-10-08
If you saved the scripts from a Windows text editor, it might have added carriage returns to the end of each line, which bash doesn't like.

---

### Post by prvteprts on 2010-10-08
> **dtfinch said:**
> If you saved the scripts from a Windows text editor, it might have added carriage returns to the end of each line, which bash doesn't like.

The scripts were created, tested, and sent from a Ubuntu 9.10 desktop installation.

---

### Post by asmoore82 on 2010-10-09
The DOS text file format was my first instinct as well.

I would re-install the bash packages for sure and maybe test the scripts with the `file` command.

---

### Post by yabbadabbadont on 2010-10-09
Try adding:
```
#!/bin/bash
```
as the first line of your script if you need bash specific features.  I beleive that dash, not bash, is the default shell in newer versions of Ubuntu.

---

### Post by prvteprts on 2010-10-09
I finally figured it out. The editor was gedit, so I knew the script was okay in that respect. However, something changed when transmitting the file through FTP (of course I set the permissions). So the workaround was, send the original script via FTP, copy the contents to a new file, and run that.

Thanks for the inputs.

I still have to figure out how to properly set the proxy without getting into the root shell...

---

