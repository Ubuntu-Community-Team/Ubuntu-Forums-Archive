---
title: "Path problem installing VMWare tools"
date: 2012-11-01
forum: Virtualisation
---

### Post by noteleks on 2012-11-01
I found directions for installing VMWare tools but having problems with the path. I have the vmware tools extracted to my desktop and it is titled "vmware-tools-distrib" the instructions tell me to open an terminal and run this command:
 
**cd Desktop/ vmware-tools-distrib** (that worked fine)
 
Then I had to run this
 
**sudo ./vmware-install.pl -d**
 
I get this error: 
 
"**command not found**"
 
I am running Ubuntu 12.04 LTS
 
What am I doing wrong? Thank you.

---

### Post by drmrgd on 2012-11-01
Can you confirm that the file is executable?  In the terminal navigate to the folder that vmware-install.pl is and run 'ls -l' (lower-case L) so you can make sure it's executable.  If it is not, then make it executable:

```
chmod +x vmware-install.pl
```

Then try running the command again.

---

### Post by noteleks on 2012-11-01
Ok, got it working. What I did was go into the folder and then ran sudo ./vmware-install.pl _d
 
That installed it. Thank you for your help. Your answer actually gave me the idea.

---

### Post by dcstar on 2012-11-11
> **noteleks said:**
> Ok, got it working.

Then MARK the thread.

---

