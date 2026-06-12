---
title: "encrypt email using thunderbird"
date: 2008-08-27
forum: Security
---

### Post by firsttimeuser on 2008-08-27
Hi guys,

I already installed enigmail and stored my friend's public key into the openpgp key management. Now I am trying to send my friend an encrypt email which will only be seen by himself,

The question is, when I reply his email, I see two buttons on the toolbar, one is OpenPGP, another one is Security, and both of them have this "Encrypt email" option, which really confuse me.

MY questions are:

1: In order to encrypt this email and only let my friend see the content, do I need to choose both "Encrypt email" option?

2: When I click "Security" and choose "Encrypt email", a prompt pops up, saying: "You need to set up one or more personal certificates before you can use this secuiryt feature, would you like to do so now?", and after I select "YES", I see this security setting windows, but it looks like I can not do anything over there, I get this when I try to click select "certificate manager can't locate a valid ceftificate that other people can use to send you encypted email messages" and I have no idea how can I load certificate.

3:I know I will use my friend's public key to encrypt the email, but why there is no option somewhere letting me pick his public key when I try to reply his email?

Any input will be greatly appreciated!

---

### Post by jmtdstoc on 2008-08-27
Since I also use Enigmail let's see if I can help you.

I NEVER use the second lock button. I only use the OpenPGP one. The second button would be used IF you had a Personal Certificate (as far as I know) and that is not your case because you are simply using OpenPGP.
That should reply your questions 1 and 2.

"3:I know I will use my friend's public key to encrypt the email, but why there is no option somewhere letting me pick his public key when I try to reply his email?"
In Thunderbird go to the menu "OpenPGP / Key Management". If you see your friend's email there everything is AUTOMAGICALLY setup. When you try to send him some email Thunderbird will search that database to see if his email has a public key attached... and since it has it will automatically encrypt the emails you'll sent him.

I hope this explains your doubts.

---

### Post by firsttimeuser on 2008-08-28
Hi jmtdstoc, thanks a lot for your input!

Really helped me here! :) 

A thanks to you!

> **jmtdstoc said:**
> Since I also use Enigmail let's see if I can help you.

I NEVER use the second lock button. I only use the OpenPGP one. The second button would be used IF you had a Personal Certificate (as far as I know) and that is not your case because you are simply using OpenPGP.
That should reply your questions 1 and 2.

"3:I know I will use my friend's public key to encrypt the email, but why there is no option somewhere letting me pick his public key when I try to reply his email?"
In Thunderbird go to the menu "OpenPGP / Key Management". If you see your friend's email there everything is AUTOMAGICALLY setup. When you try to send him some email Thunderbird will search that database to see if his email has a public key attached... and since it has it will automatically encrypt the emails you'll sent him.

I hope this explains your doubts.

---

