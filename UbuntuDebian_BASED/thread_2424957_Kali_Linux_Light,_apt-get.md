---
title: "Kali Linux Light, apt-get"
date: 2019-08-18
forum: Ubuntu/Debian BASED
---

### Post by parzi2 on 2019-08-18
hello
I am using Kali Linux Light on VM. I have a few issues with the Terminal.
I am not able to use the tool 'theharvester'.I have used the 'sudo apt install'.And then used 'apt-get update' and 'apt-get install theharvester'.
The output is attached. I am still not able to use the tool,please give me a solution.The 'ifconfig' tool is also not working,what might be the reason?

---

### Post by TheFu on 2019-08-18
a) please don't use images for text. Copy/paste the text here and wrap it in "code tags" using the advanced editor. See my example below. It should look like that.

b) command not found.  That means the command isn't in the path. It can also mean it isn't installed. After any new install on an APT system, run
```
sudo apt update
sudo apt upgrade

```before anything else.  Run those weekly, after you perform backups.

c) Kali is a hacking distro. I don't know if we are allowed to discuss it here. It certainly isn't part of the Ubuntu releases.

---

### Post by coffeecat on 2019-08-18
Support, not chat. And... Kali is not Ubuntu.

*Thread moved to an appropriate support forum*.

**Edit:** "theharvester" is not the sort of activity we support here. Thread closed.

@OP, if you want help, try the Kali forum. This is the Ubuntu forum.

---

