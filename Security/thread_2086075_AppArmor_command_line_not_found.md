---
title: "AppArmor command line not found"
date: 2012-11-19
forum: Security
---

### Post by Kestreln8144 on 2012-11-19
I am following [this]("http://ubuntuforums.org/showthread.php?t=1008906") guide, and I'm at the step where I generate a profile for Firefox. But when I run the command "sudo genprof firefox" I get this:

```
sudo: genprof: command not found
```I've run the following commands previously, which completed successfully:

```
sudo apt-get install apparmor-utils
sudo apt-get install apparmor-profiles
```What am I doing wrong?

---

### Post by Hungry Man on 2012-11-19
The command is aa-genprof.

---

### Post by Kestreln8144 on 2012-11-19
> **Hungry Man said:**
> The command is aa-genprof.
Previously, that command also gave me the same error. But after restarting, it seems to work now.

Thank you.

---

