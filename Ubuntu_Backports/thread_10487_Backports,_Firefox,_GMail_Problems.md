---
title: "Backports, Firefox, GMail Problems"
date: 2005-01-08
forum: Ubuntu Backports
---

### Post by Quest-Master on 2005-01-08
I can't send mail with attachments through GMail, and I searched through their docs, and apparently, Firefox downloaded from anywhere other than the Mozilla site will not work properly with GMail. I got my Firefox from the Ubuntu backports project..

[http://gmail.google.com/support/bin/answer.py?answer=8835&topic=133](http://gmail.google.com/support/bin/answer.py?answer=8835&topic=133)

Should I revert to 0.93 Firefox? I don't remember if it was working then however.

---

### Post by tiiim on 2005-01-08
[QUOTE=Quest-Master]I can't send mail with attachments through GMail, and I searched through their docs, and apparently, Firefox downloaded from anywhere other than the Mozilla site will not work properly with GMail. I got my Firefox from the Ubuntu backports project..

[http://gmail.google.com/support/bin/answer.py?answer=8835&topic=133](http://gmail.google.com/support/bin/answer.py?answer=8835&topic=133)

Should I revert to 0.93 Firefox? I don't remember if it was working then however.[/QUOTE]
 well u could always revert then if dont work upgrade again.

i can send email attachments via firefox on gmail fine.

---

### Post by Quest-Master on 2005-01-08
[QUOTE=tiiim]well u could always revert then if dont work upgrade again.

i can send email attachments via firefox on gmail fine.[/QUOTE]
 
Are you using the 1.0 Backport?

---

### Post by tiiim on 2005-01-08
[QUOTE=Quest-Master]Are you using the 1.0 Backport?[/QUOTE]
 no im using the one that comes with Ubuntu ....

---

### Post by jdong on 2005-01-08
I'm using backports, and I can send attachments perfectly. Can you describe your problem in more detail?

---

### Post by angrylittleman on 2005-01-08
I am also using ff 1.0 from backports without a problem, works great with my gmail account.  What error messages if any are you getting???

---

### Post by Quest-Master on 2005-01-09
As soon as I hit send on the mail with an attachment, it simply returns a "The document contains no data." alert. :\

---

### Post by elvislu on 2006-01-05
I have the same problem. It's ok to send the mail without attachment. But when I want to attach some thing, and click the send button, it show sending forever.  I use deer park and I noticed that when I sent a mail with attachment in gmail, the lock on the statusbar (certificate) will have a backslash on it. Does it have something to do with our problem? :confused:

---

### Post by haocheng on 2006-01-05
I don't have any problem with GMail.
I use FF 1.5 from mozilla website.
Maybe you can try to install it manually, 
it's also much faster than 1.07 :)

---

### Post by elvislu on 2006-01-06
I got it somehow. There is no difference between FF1.07 and FF1.5 in thsi case. Actually, I use FF1.5. It has something to do with the gnutls library. I just updated the libgnutls11 package and now everything works well. So I suggest you try this and see if it works in your case. (I updated with the official ubuntu5.10 source)

---

