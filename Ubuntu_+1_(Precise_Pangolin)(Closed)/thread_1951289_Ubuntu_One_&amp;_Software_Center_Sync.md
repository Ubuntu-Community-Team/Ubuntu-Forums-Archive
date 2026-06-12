---
title: "Ubuntu One &amp; Software Center Sync"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lovinglinux on 2012-04-02
I decided to give Ubuntu One another try, but is broken. 

[https://bugs.launchpad.net/ubuntuone-client/+bug/966731](https://bugs.launchpad.net/ubuntuone-client/+bug/966731)


Another thing that isn't working for me is the Software Center Sync feature. It prompts me for an account, but when I try to create it, nothing happens.

Any idea how to fix these problems?

---

### Post by lovinglinux on 2012-04-02
First issue solved. First I went to [https://login.ubuntu.com/](https://login.ubuntu.com/), clicked the Applications tab and removed the devices. Then deleted ~/.config/ubuntuone 

When I started Ubuntu One again, it went through.

---

### Post by mc4man on 2012-04-02
For the Sc sync deal have you tried logging in with your ubuntu SSO? (LP account

---

### Post by lovinglinux on 2012-04-02
> **mc4man said:**
> For the Sc sync deal have you tried logging in with your ubuntu SSO? (LP account

Yes, that was my first idea, but it didn't work. 

Now that you mentioned, I tried again and it did work. Go figure.

Perhaps, because I changed my password today and deleted the software-center config folder.

Thanks.

Awesome.

---

### Post by mc4man on 2012-04-02
Slightly OT
The first time I saw the S-C sync login page was a bit thrown, it makes it seem one needs to create a new Software Center account.
They probably could do that better

---

### Post by lovinglinux on 2012-04-02
> **mc4man said:**
> Slightly OT
The first time I saw the S-C sync login page was a bit thrown, it makes it seem one needs to create a new Software Center account.
They probably could do that better

Indeed, specially considering I am already logged with Ubuntu One account. I hope they do, because both services have a lot of potential. I usually use dpkg --get-selections, but this service gives me more control. I enjoy the graphical interface.

Now I will test on a VM to see if it also detect removed programs.

---

### Post by lovinglinux on 2012-04-02
Sync is not working for me. I get this bug:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/947774](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/947774)

Additionally, not all applications I have installed are listed.

---

