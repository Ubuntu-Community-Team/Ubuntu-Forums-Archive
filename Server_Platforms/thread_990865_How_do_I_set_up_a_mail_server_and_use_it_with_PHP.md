---
title: "How do I set up a mail server and use it with PHP?"
date: 2008-11-23
forum: Server Platforms
---

### Post by squeakyneb on 2008-11-23
I have an old computer running out the back. At the moment it is running Apache (apache2 i think) with PHP. It is [here]("bennym.zapto.org"). I want to be able to send emails to/from [email]ben@bennym.zapto.org[/email]. What do i need to do? I need it in command line form, as it is running ubuntu server, so no GUI. 

I then need to be able to use PHP scripts to send email e.g. from a form.

I don't need all of this to be professional quality, I just want to do it so I know how. It's a kind of "because I can" situation.

Thank you for your help.

---

### Post by Dr Small on 2008-11-23
```
drsmall@mycroft:~$ mail
The program 'mail' can be found in the following packages:
 * mailx
 * mailutils
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled

```

Try that and see if it works.

---

### Post by Philio on 2008-11-23
> **Dr Small said:**
> ```
drsmall@mycroft:~$ mail
The program 'mail' can be found in the following packages:
 * mailx
 * mailutils
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled

```

Try that and see if it works.


If you want a proper MTA you need to install one of exim, postfix, sendmail etc.

---

### Post by squeakyneb on 2008-11-24
> **Philio said:**
> If you want a proper MTA you need to install one of exim, postfix, sendmail etc.

I have postfix, but i cant send mail (using the mail command, it already works) to my hotmail or receive t from hotmail. I can send mail to other users of the computer with 'mail [email]blink@bennym.zapto.org[/email]'. What now?

---

### Post by anil_robo on 2008-11-26
I am in the same situation as the original poster. I have followed all types of tutorials from these forums and ubuntu wiki, but gave up on sendmail and postfix. However, I followed this tutorial today: [https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4) and have been successfully sending emails to "localhost". But when I try to send an email outside localhost (e.g. [email]user@gmail.com[/email]) it fails. Any idea why? Darn, I wish Linux were simpler to use :(

---

### Post by squeakyneb on 2008-12-16
Bump!!
I'm still having problems...

---

### Post by CrucifiedEgo on 2008-12-16
> **squeakyneb said:**
> I have an old computer running out the back.

First... you should go catch it!!

Second, Hotmail is terrible.  They're fairly nazi-ish when it comes to spam protection.  If you don't have correct reverse/forward DNS, HELO/Banner issues, or simply start sending them a fair amount of email without slowly ramping up, they'll just ignore your messages.  Actually, they'll accept them, and then silently discard them.  Unfortunately, there's not much you can do about it, other than tell your users to use a real email service (gmail and fastmail both come to mind.)

---

