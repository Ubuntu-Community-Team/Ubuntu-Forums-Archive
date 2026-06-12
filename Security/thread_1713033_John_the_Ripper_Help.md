---
title: "John the Ripper Help"
date: 2011-03-23
forum: Security
---

### Post by hijiz on 2011-03-23
Hi, a while ago i started doubting the security of myself, so i decided to test the security i would try hacking it myself and i installed john the ripper. however whenever i try doing anything with it i get the this mesage.>  Password files required, but none specified
how do i get the password files.
sorry for being such a noob.

---

### Post by bodhi.zazen on 2011-03-23
[http://www.cyberciti.biz/faq/unix-linux-password-cracking-john-the-ripper/](http://www.cyberciti.biz/faq/unix-linux-password-cracking-john-the-ripper/)

---

### Post by hijiz on 2011-03-23
ithought this command would help me
> sudo /usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.password.db
But when i type it nothing happens. am i doing something wrong?

---

### Post by sisco311 on 2011-03-23
Does `John the Ripper' support sha512?

---

### Post by hijiz on 2011-03-23
i dont know.
How should I?

---

### Post by sisco311 on 2011-03-23
> **hijiz said:**
> i dont know.
How should I?

You read its documentation.

But I have a better question, why do you think that using `joe' will increase your system's security?

---

### Post by hijiz on 2011-03-23
I wanna see how secure my system is and how prone it is to attaks.
can we get back on topic here.

---

### Post by sisco311 on 2011-03-23
Start here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Use strong passwords & don't run commnds/executables which you don't understand and/or trust.

---

### Post by hijiz on 2011-03-23
Im not asking how to make my system more secure. i want to know how secure it is right now.

---

### Post by hijiz on 2011-03-23
After searching in google i find nothing to prove that john supports sha512. does anyone know if it is or not? and also back to the main topic how do i make it work.

---

### Post by hijiz on 2011-03-23
I searched a bit more it seems it doesnt support sha512 apparently i need a patch called Jumbo2 how can i install this patch?

---

### Post by bodhi.zazen on 2011-03-24
I thought john was patched in Ubuntu, at least there was a bug report on Launchpad, although I have not tried it recently.

Google search and you will find what you need.

[https://bugs.launchpad.net/ubuntu/+source/john/+bug/586544](https://bugs.launchpad.net/ubuntu/+source/john/+bug/586544)

---

### Post by cariboo on 2011-03-24
According to th bug report, the fix was committed, but never released, maybe the op should give the devs a nudge to get some action. :)

---

### Post by nixor01 on 2011-05-08
yes it does support sha512.

---

