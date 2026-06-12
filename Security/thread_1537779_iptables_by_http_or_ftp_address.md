---
title: "iptables by http or ftp address"
date: 2010-07-24
forum: Security
---

### Post by yashar on 2010-07-24
i need to open this address [ftp.nai.com]("ftp://ftp.nai.com/"), is there a way to use address not ip in iptables?

---

### Post by wacky_sung on 2010-07-24
I do not think it is possible.The only way is convert the address into IP address before you can input into the iptables including the port use.

---

### Post by CharlesA on 2010-07-24
You can tell it to allow that address, but iptables will convert the hostname to an IP address anyway.

---

### Post by wacky_sung on 2010-07-24
> **CharlesA said:**
> You can tell it to allow that address, but iptables will convert the hostname to an IP address anyway.

Probably you can tell me how which is something that is very new to me.Beside that,can you pls show me an example.Thank.

---

### Post by bodhi.zazen on 2010-07-24
> **wacky_sung said:**
> Probably you can tell me how which is something that is very new to me.Beside that,can you pls show me an example.Thank.

What traffic are you wanting to allow ? inbound ? outbound ? What ports ?

```
sudo iptables -A INPUT -s [ftp.nai.com]("ftp://ftp.nai.com/") -j ACCEPT
```

Would be the basics, you can specify a protocol and port.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by wacky_sung on 2010-07-24
Thank you bodhi.zazen.Pardon me for my ignorance.

---

### Post by bodhi.zazen on 2010-07-24
> **wacky_sung said:**
> Thank you bodhi.zazen.Pardon me for my ignorance.

We are all learning. Take a look at the link I gave you, keep reading, and keep asking questions.

---

### Post by yashar on 2010-07-28
thank you

---

