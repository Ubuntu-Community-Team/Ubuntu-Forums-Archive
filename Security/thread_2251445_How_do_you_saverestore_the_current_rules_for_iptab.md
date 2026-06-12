---
title: "How do you save/restore the current rules for iptables in plain text"
date: 2014-11-04
forum: Security
---

### Post by J_Me on 2014-11-04
So I want to do something with iptables and will probably mess it up, is there a plain text file which I can save/edit.
Thanks

---

### Post by The Cog on 2014-11-04
iptables-save prints a text representation of the config. So you can save like this:
```
sudo -i
iptables-save > save.txt
exit
```
and you can restore by sending the text to iptables-restore:
```
sudo -i
iptables-restore < save.txt
exit
```

---

### Post by J_Me on 2014-11-04
Perfect.
Thank you very much

---

