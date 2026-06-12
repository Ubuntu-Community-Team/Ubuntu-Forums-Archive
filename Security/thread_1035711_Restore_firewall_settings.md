---
title: "Restore firewall settings"
date: 2009-01-10
forum: Security
---

### Post by Rablador on 2009-01-10
Hi!

Is there any way to restore the settings of the firewall to default? I have been messing around with ports and stuff for so long that I do not remember what has been done anymore...

/Jon

---

### Post by hyper_ch on 2009-01-10
delete all rules - that's the default state.

---

### Post by cdtech on 2009-01-10
Use the "iptables-restore" command to flush and destroy all previously inserted rules.

See this site for more information on "iptables":
[http://www.faqs.org/docs/iptables/iptables-save.html](http://www.faqs.org/docs/iptables/iptables-save.html)

---

### Post by Rablador on 2009-01-10
I tried the iptables-restore command, but nothing seemed to happen. I am not very experienced with firewalls, so if possible, could you tell me what to do in more detail?

Thanks in advance!

---

### Post by cdtech on 2009-01-10
What version of Ubuntu are you using? You can view the rules by typing in a terminal:
```
sudo iptables -L
```

---

### Post by Rablador on 2009-01-10
I am using 8.10.

I listed the contents of iptables, but it doesn't tell me much i'm afraid... Is it safe to post the output here?

---

### Post by cdtech on 2009-01-10
Sure........

---

