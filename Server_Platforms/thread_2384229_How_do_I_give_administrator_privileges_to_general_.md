---
title: "How do I give administrator privileges to general users? (VPS)"
date: 2018-02-04
forum: Server Platforms
---

### Post by omuru on 2018-02-04
I learned that it is important to create general users, give administrator privileges, and disable root users.
Currently I have only root user.
Specifically, what should I do?
If I enter the following, will a user named username be created and given administrator privileges?

adduser username sudo

Then,
Does the root user become invalid if I enter as follows?

sudo passwd -l root
or
usermod --expiredate 1

Can I just use the above two lines of commands?

---

### Post by coffeecat on 2018-02-04
***Edit:** the text below was written when the thread was in New to Ubuntu before the "VPS" addendum to the thread title, under the assumption that this was a desktop installation. See further posts below.*


I think you are confused between what is the root account and the administrator account, and also confused with the difference between "user" and "account". 

[quote=omuru]Currently I have only root user.[/quote]

No. In a default installation of Ubuntu the root account is locked and the first-created user account has sudo, that is administrative, privileges. The first-created user account is **not** the root account. If you wish to create additional user accounts, you can choose whether to give them administrator privileges or not. Leave the root account alone. There are many accounts in a default installation, quite apart from the root and user accounts.

You will find this useful: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by omuru on 2018-02-04
thank you for your answer.
I was short of explanation.
I use VPS, but if I select Ubuntu as the OS, root and its password will be given as user name.
And I am supposed to login as root.
Of course, it is a real root user.
Thank you for telling me the reference page.
Do I need to enter as follows?

sudo adduser <username>
sudo adduser <username> sudo
sudo passwd - dl root
sudo usermod --expiredate 1 root

(not
sudo passwd - l root)

---

### Post by coffeecat on 2018-02-04
Hmmm. Virtual Private Server. 

It's important to give full information when asking for help here, so that you get appropriate advice. The fact that you are using a server version of Ubuntu and that you are using a VPS are the most salient points, facts that you omitted from your OP. Most people posting in New to Ubuntu are running a standard desktop system.  

I've added an edit to my earlier post, so that I don't look like a complete idiot, and have moved this thread from ***New to Ubuntu*** to ***Server Platforms***, which is a more appropriate sub-forum. I've also added a "VPS" addendum to the thread title.

I'm sure someone with VPS Ubuntu experience will be along to help you with more focussed advice.

Good luck, and a belated welcome to the forum.

---

### Post by darkod on 2018-02-04
Correct, many VPS providers actually deploy your VPS with enabled root account and give you the password. Unlike when installing ubuntu yourself...

I usually create admin users like this:
```
sudo adduser <username>
sudo usermod -aG sudo <username>
```

That will create it and then add it to the sudo group. Your commands above might do the same, just that I haven't used them before.

To lock a user (if you want to lock root afterwards) I usually use:
```
sudo usermod -L root
```

Again, your commands above might do the same since there are multiple ways to reach the same result.

To check which users are locked, you can try something like:
```
sudo cat /etc/shadow
```

If you see ! after the username then the user is locked. If there are many users in the output you can grep just the one you are interested in, like:
```
sudo cat /etc/shadow | grep root
```

---

### Post by omuru on 2018-02-04
Sorry for making an uncertain question.
I set it with reference to advice.
Thank you very much.

---

### Post by Habitual on 2018-02-05
Your VPS provider likely has some FAQs or General "How-To"s...maybe even some non-general ones also!

In addition to the excellent link for RootSudo, I'd like to suggest
[https://help.ubuntu.com](https://help.ubuntu.com) in General and
[https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults) specifically.

---

