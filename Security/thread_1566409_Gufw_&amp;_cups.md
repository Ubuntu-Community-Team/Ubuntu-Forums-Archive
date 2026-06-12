---
title: "Gufw &amp; cups"
date: 2010-09-02
forum: Security
---

### Post by uRock on 2010-09-02
In GUFW I do not see any way to allow CUPS. How do I manually add this into GUFW?

Thanks,
uRock

---

### Post by uRock on 2010-09-02
The main reason I am asking is because the GUFW only offers options for Allowing/Denying TCP and UDP.

Thanks,
uRock

---

### Post by marquinos on 2010-09-03
Hi! CUPS listen in port 631
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

Then, in Gufw you have 2 options for add a rule:
  - Open only the port: Simple Tab > 631
  - If you need set the IP too: Advance > To IP: your IP; port 631.

Best regards :)

---

### Post by uRock on 2010-09-03
Cool, I will test out trying to print from another machine to see how it does.

Thanks,
uRock

---

### Post by uRock on 2010-09-05
> **marquinos said:**
> Hi! CUPS listen in port 631
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

Then, in Gufw you have 2 options for add a rule:
  - Open only the port: Simple Tab > 631
  - If you need set the IP too: Advance > To IP: your IP; port 631.

Best regards :)
Thanks again. This allows CUPS to do its thing.

---

### Post by marquinos on 2010-09-05
Great! :)

---

