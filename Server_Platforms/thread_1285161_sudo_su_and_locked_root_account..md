---
title: "sudo su and locked root account."
date: 2009-10-07
forum: Server Platforms
---

### Post by rnodal on 2009-10-07
Hello all,

I locked my root account and when I try to do:
```
sudo su
```
I get the following message:
```
Your account has expired; please contact your system administrator
su: Authentication failure
(Ignored)

```

I thought that by locking the root account it was not possible to use the root account. Did I misinterpret what "locking" means?

I understand that it is impossible to login using the root account since the password field in /etc/shadow has the ! in front of it and that will cause the password check to always fail but I also thought that it would prevent the account from be used.  

Anyway, is the error message normal or is that a sign of misconfiguration?

Thank you for your time,

-r

---

### Post by snowpine on 2009-10-07
try:

```
sudo -i
```

---

### Post by rnodal on 2009-10-07
> **snowpine said:**
> try:

```
sudo -i
```

Thank you for the reply.
I tried it and it does what "sudo su" does except that it does not give me any errors. Under my desktop setup, if I do "sudo su" I get no error but when I try it in my server(VPS) then I get the message.

By default Ubuntu does not have root enabled but the VPS provider when they install it they enable the root account. Is there anything else that I should look for to bring the system to be like the standard way?

Thank you,

-r

---

### Post by cdenley on 2009-10-07
By default, the root account is "disabled" by using "!" as the password hash. This causes the root account to be enabled, technically, but there is no password which can authenticate as root. Another method sometimes used for disabling accounts is to set the expiration date to sometime in the past. You should not do this for root. It may cause problems with some packages or scripts.
```

sudo usermod -e 99999 -p ! root

```

---

### Post by v8YKxgHe on 2009-10-07
You're going to miss the root account if running a server. Not only because it is sometimes helpful, but when things go wrong that you can't imagine yet.

Keep the root account active with a strong password, obviously don't allow SSH logins for root, and take advantages of sudo to the full (not just allowing 1 user to do everything, but really lock down an account to what is needed - read the man page for sudo, very powerful).

---

### Post by rnodal on 2009-10-07
> **cdenley said:**
> By default, the root account is "disabled" by using "!" as the password hash. This causes the root account to be enabled, technically, but there is no password which can authenticate as root. Another method sometimes used for disabling accounts is to set the expiration date to sometime in the past. You should not do this for root. It may cause problems with some packages or scripts.
```

sudo usermod -e 99999 -p ! root

```

Thank you very much for your replay. 
I looked at my shadow file in my server and my desktop machine and I notice the following.
The last field, the one that specifies when the account expires has the value:14513. Which is probably why I get the error message from "su".

How do I delete that number from there? Or should I say, how do I set nothing for that field?

Thank you!

-r

---

### Post by cdenley on 2009-10-07
You don't have to worry about that number if the fifth field is set to 99999. If you really want to, you can edit it with a text editor, but be careful.

---

### Post by rnodal on 2009-10-07
> **AlexC_ said:**
> You're going to miss the root account if running a server. Not only because it is sometimes helpful, but when things go wrong that you can't imagine yet.

Keep the root account active with a strong password, obviously don't allow SSH logins for root, and take advantages of sudo to the full (not just allowing 1 user to do everything, but really lock down an account to what is needed - read the man page for sudo, very powerful).

Haha, is funny that you say that because I was thinking the same thing! It may not be such a bad thing to have the account available. I already have setup a good password and also root is not allow to login from ssh. I was also thinking the same about not just having one account to do everything.
I'm in the process of tuning the server and when I typed "sudo su" like I normally do to get a root shell and got the message (I actually got it before but I was very busy to take the time to investigate).

Thank you for taking the time to answer and your tips are good ones to. 

-r

---

### Post by rnodal on 2009-10-07
> **cdenley said:**
> You don't have to worry about that number if the fifth field is set to 99999. If you really want to, you can edit it with a text editor, but be careful.

I figured that, that number (assuming my math is correct) is the reason why "su" says the account is expired. So I just wanted to get rid of that number so I don't get the message. I figured there may be a safe way to edit the shadow file the same way there is visudo but I guess since I'm the only user in the system editing the file that it would not be such a big deal.

Thank you,

-r

---

### Post by cdenley on 2009-10-07
> **rnodal said:**
> I figured that, that number (assuming my math is correct) is the reason why "su" says the account is expired. So I just wanted to get rid of that number so I don't get the message. I figured there may be a safe way to edit the shadow file the same way there is visudo but I guess since I'm the only user in the system editing the file that it would not be such a big deal.

Thank you,

-r

Well, that is what the "usermod" command is for, except it edits the fifth field instead of the one you are referring to, either of which will prevent the account from being locked.

---

### Post by rnodal on 2009-10-07
```
sudo usermod -e "" root
```

Will do the trick. This set when the account should expire. The 5th field sets when the password should expire. In my case, I had my root account expired so that's why when I did:
```
sudo su
```

"su" will give me the message that it was giving me.

Thank you all.

-r

---

