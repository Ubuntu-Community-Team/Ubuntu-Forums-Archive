---
title: "Locked out again"
date: 2018-12-13
forum: Resolution Centre
---

### Post by benjetson-temp2 on 2018-12-13
This is a continuation from: [https://ubuntuforums.org/showthread.php?t=2408096](https://ubuntuforums.org/showthread.php?t=2408096)

Well, I can't log in to my primary account through any of my Ubuntu One accounts now. 

I logged out of the forum, logged out of Ubuntu One, and even cleared cache/cookies just to be safe. Then, when logging in with my preferred Ubuntu One account, I still get the blank error message from the forum software.

---

### Post by coffeecat on 2018-12-13
I really am at a loss now to understand what the problem is.

What I did was fairly straightforward. Each forum account has a unique string linking it to a specific Ubuntu One account, created when the forum account is first linked to the Ubuntu account, either with an email match with an old forum account, or when a new forum account is created. I simply swapped the strings around, so that each Ubuntu One account is now linked to the "other" forum account. That always works - until now. The only other thing I did was to re-activate the account after you changed the email. I have double-triple checked the strings with the copy I recorded before doing the swap.

That the vbulletin software is confused by showing you a blank error message is clear, but what it's confused about is not.

I'll leave a note of what I've done in the staff area for the other admins to look at. One of them might have an idea that hasn't occurred to me. I have to log off now. Hopefully, we'll get this fixed for you.

---

### Post by coffeecat on 2018-12-13
I'll just put on record one last thought before I log off.

Over many years we have been plagued with an intermittent problem where the two backend servers don't synchronise promptly. It has caused us (and me) endless headaches over the years. Canonical IS have looked at the issue many times and, as far as I know, have never really got to the bottom of it. Maybe this is the problem, maybe not. Maybe one backend has got one version of your profile and the other, another. Hence the software confusion.

My only suggestion for now. Give it half an hour. Give it an hour. Try logging out (completely) from both the forum and Ubuntu One again, and then logging in again, and hope that by then the two backends are actually talking to each other! 

Good luck!

---

### Post by benjetson-temp2 on 2018-12-13
Hi again. Thanks for the explanation -- that helps make sense of what has happened and how the identity linkage works.

It's been a few hours now, so I'd hope the two servers have synchronized by now. Just now I tried again logging out of the forum, Ubuntu One, and clearing cache/cookies then logging in with the correct Ubuntu One account and got the same blank error message.

I have an idea about what might fix this based on the description of what you said about how accounts are linked, but it might not make sense. Here goes:


[LIST]
[*]Let me DM you with the correct email address that I want to use.
[*]Change the email address of record on my account to match.
[*]Delete the Ubuntu One token/string on my account record. *(or otherwise modify my account so the software thinks I have never logged in with SSO before)*
[*]Let me know when you have done this, and I'll try signing in again with the Ubuntu One account that has the correct email.
[*]Then, when I log in, the system should match my account based on the email string match and get a new token/string from Ubuntu One to use with future logins.
[/LIST]

Could this work?

Thanks for taking the time to help me recover my account. I really appreciate it. :D

---

### Post by QIII on 2018-12-13
Please respond here when you are ready to log out of all temp accounts you have created. 

I will add a new post in this thread when I have explored this.  Hopefully, you will be straightened out -- but you won't be able to respond to this thread with your original user name.

When I have posted back, please use the credentials you used to sign in to this account (benjetson-temp2) and not another.

And please don't create a new user.  That will just cause more confusion.  I'm going to make an exception and ask you instead to contact the Admins via our mailing list at [email]ubuntu-forums-council@lists.ubuntu.com[/email] if you need further assistance.

---

### Post by benjetson-temp2 on 2018-12-13
Hi! Thanks for exploring the idea I had. Hopefully it works. :)

I wanted to make sure you know that the account I am logging in with now (**benjetson-temp2**) is linked to one of my two **temporary** Ubuntu One accounts I created to be able to post in the Resolution Centre. My point being, that if I log in with the **benjetson-temp2** credentials as you have suggested, I still have the problem I originally posted about, which is that the **real** forum account would be linked to one of the **temporary** Ubuntu One accounts.

Since you're the one working on this, I have sent you a DM with the correct email address that is the primary email address on my permanent Ubuntu One account. My permanent Ubuntu One account is the one I use everywhere else and is the one I would like to be able to use to login to the forums.

If I get locked out again, I won't make any more temporary accounts -- I'll contact the mailing list as you have directed.

This has gotten really confusing, but hopefully we can get this sorted so that the correct forum account is paired with the correct Ubuntu One account.
I really appreciate your patience in all of this. 

Within the next couple of minutes, I will have signed out of all of my forum and Ubuntu One accounts and wait for further instructions.

---

### Post by QIII on 2018-12-13
Please attempt to log in again -- use the same Ubuntu One credentials you used to sign in as benjetson-temp2

---

### Post by QIII on 2018-12-13
Please do not do so with any sort of anonymity software running.

---

