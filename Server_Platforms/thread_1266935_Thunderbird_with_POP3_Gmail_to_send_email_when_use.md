---
title: "Thunderbird with POP3 Gmail to send email when user login to SSH or FTP"
date: 2009-09-15
forum: Server Platforms
---

### Post by pi4r0n on 2009-09-15
Hello ALL

I have SSH and FTP demons running on my Ubuntu 9.04 (opne to all) and would like to have a option to send emails through **Thunderbird with Gmail POP3 setups** each time user logs in.

I found many tuts on how to do it with SMTP demon on linux but I don't want to open another port so trying to find other way around.

**Scenario:**
User Mike logs is to ssh or ftp ------->  email is send from Thunderbird with POP3 Gmail --------> to me

Is there anyone how can help me with my query ??

Cheers

pi4r0n

---

### Post by grantemsley on 2009-09-15
Running an SMTP daemon is the best way.
It doesn't necessarily have to open another port on the outside, it just needs to be able to send mail out.
It can even send through your gmail account if you want it to.

Thunderbird isn't designed to be scriptable, so you are better off using a normal SMTP daemon.

---

