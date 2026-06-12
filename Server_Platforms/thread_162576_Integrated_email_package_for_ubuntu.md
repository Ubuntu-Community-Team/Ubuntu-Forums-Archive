---
title: "Integrated email package for ubuntu"
date: 2006-04-19
forum: Server Platforms
---

### Post by alamba on 2006-04-19
Hi all,

I was recently looking at XAMPP and tried it on a server install of ubuntu and it worked beautifully. Lately, I&#8217;ve been fielding a number of questions on installation of POP3+SMTP+Webmail on ubuntu (on and off the forum) and it got me thinking on creating a integrated package like XAMPP for email. My coding skills are pretty limited so incase anyone would like to contribute please drop me a line. So far I&#8217;m considering a package that would incorporate the following:

exim (mta) + courier-imap (imap/pop3) + procmail(for mail routing) + Uebimiau(webmail) + spamassasin(spam control) + clamav(anti-virus)

I'll also be interesting in hearing from everyone here on component selection (such as above) and integration issues. Would such a "middleware" even make sence?

A

---

### Post by nagilum on 2006-04-19
Just a note, Exim is a MTA and no POP3 server as you wrote.

---

### Post by alamba on 2006-04-20
Oops...me bad. Corrected.

A

---

