---
title: "New user totally unable to log in"
date: 2013-10-27
forum: Resolution Centre
---

### Post by bunkie.lover on 2013-10-27
Hi.

I was trying to get some help in the Unity Forums today, and so I tried to "Log in with SSO". My registered e-mail is just clayton@<myvanitydomain>.

After authorizing ubuntuforums.org for that site, I was redirected to a page with the following message:


[LIST=1]
[*=left]The following errors occurred during your registration:
[*=left]That username is already in use or does not meet the administrator's standards. If you are clayton2 and [h=2]Register[/h][h=3][/h]Email Address
Confirm Email Address:

[RIGHT] [/RIGHT]have forgotten your password, click [here]("http://ubuntuforums.org/login.php?do=lostpw").
[/LIST]
[LEFT]

If it isn't obvious, I'm not clayton2, and there's no way for me to proceed. I had to create a new account with a throw-away e-mail in order to log in. Is there any way I can get my real account to work, or is everyone who shares a username with someone already registered just doomed?

Thanks,[/LEFT]

---

### Post by bunkie.lover on 2013-10-27
Not sure how to edit post, but the HTML of the page didn't paste correctly. Anyway: it says "If you are clayton2 and you have forgotten your password, click here."

---

### Post by cariboo on 2013-10-27
First off, there is already clayton and clayton2 accounts, you can choose a user name when creating an Ubuntu One account, that is other than your email address. Login to Ubuntu One, then click My Account, on on your account page, click the edit you account detail link. On the Personal Details Page type in your preferred user name in the My Name box.

Secondly the posts in this sub-form can't be edited, so that we have a paper trail if any disputes come up.

---

### Post by cariboo on 2013-10-27
I forgot to add, that when entering a name in the My Name box, it doesn't have to be your real name, it can be anything you want.

---

### Post by bunkie.lover on 2013-10-27
> **cariboo907 said:**
> First off, there is already clayton and clayton2 accounts, you can choose a user name when creating an Ubuntu One account, that is other than your email address. Login to Ubuntu One, then click My Account, on on your account page, click the edit you account detail link. On the Personal Details Page type in your preferred user name in the My Name box.

The name on my account is currently "Please Work", and yet I am still told that "clayton2" is already taken, and to please choose another name. However, I did nothing to choose this name, so...

---

### Post by coffeecat on 2013-10-27
There has been considerable fine-tuning of the algorithm used to generate the forum username from Ubuntu One details since SSO was introduced. If there are still problems with the algorithm, we need to gather some evidence for the Canonical sysadmins to work on. So - two issues:

1 - You refer to your "real account" in your first post. Do you mean a previous forum account? If so, post with the username of this account and then we can see what needs to be done to restore you to that account.

2 - The error message you quote in your first post is mystifying. The "not meeting administrator's standard" usually means a name containing a word/string in a censor list. I can assure you that neither please not work are in the list. Is there a non-printing character or null character in your "Please Work" Ubuntu one name? The other thing that is mystifying is why the forum software should quote the clayton2 username at you. So that I can look at this more closely, and for confidentiality, please pm me with the full email and the Ubuntu One username that triggered the "not meeting administrator's standard" meesage,

By the way:

[quote=bunkie.lover]or is everyone who shares a username with someone already registered just doomed?[/quote]

Not at all. It's explained in [the SSO login sticky]("http://ubuntuforums.org/showthread.php?t=2164051"):

> Please note, that the system may append a number to your forum account username. For example, if you chose “johdoe” as your Ubuntu One account name, and there is already a “johdoe” account in the forum database, your forum account will be named “johdoe2”, or "johdoe3" if there is already a johdoe2, and so on.

Which is why we need the information requested above to see what has been going on in your case.

---

