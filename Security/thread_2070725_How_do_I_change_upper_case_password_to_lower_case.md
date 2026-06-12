---
title: "How do I change upper case password to lower case?"
date: 2012-10-13
forum: Security
---

### Post by gertcher on 2012-10-13
When I very recently installed Ubuntu I accidently entered my password in upper case.

I tried to change it in 'User Accounts', but I get a message saying the new password is too similar to the old one.

If I change it to something very different can I then go back to my preferred password?

Or

Is there a way of changing my password without using the 'User Accounts'?

Thanks  Greg

---

### Post by PaulW2U on 2012-10-13
> **gertcher said:**
> If I change it to something very different can I then go back to my preferred password?

I believe I have made exactly the same mistake in the past.

Try it. I'm sure that you then can use the lower case version of your password.

---

### Post by gertcher on 2012-10-13
> **PaulW2U said:**
> ..... I'm sure that you then can use the lower case version of your password.That was too simple. It took less time than posting the question. Cannot think why I just did not try it.  

That means the security only stops you making something near to the previous password and does not keep a list.

Thanks  Greg

---

### Post by gertcher on 2012-10-14
I can now log in from cold or when the computer wakes with my now lower case password, but if I need to execute a function requiring my permission and therefore my password it is still in upper case.  Where do I go to alter that password?

---

### Post by Meschi on 2012-10-14
I am not sure if this helps but maybe you can try it from the terminal with
sudo passwd username
or 
sudo passwd?
(first one changes user password second one the root password)

---

### Post by sysone on 2012-10-15
do it in recovery mode:

  	 	 	 	 	 	   [FONT=Verdana, sans-serif][SIZE=4]http://www.psychocats.net/ubuntu/resetpassword 
[/SIZE][/FONT]


[FONT=Verdana, sans-serif][SIZE=4][SIZE=4]Did it help?[/SIZE][/SIZE][/FONT]
[FONT=Verdana, sans-serif][SIZE=4][SIZE=4][/SIZE]
[/SIZE][/FONT]

---

### Post by gertcher on 2012-10-15
I tried Meschi's tip. Not sure if it worked, got a feeling it is necessary to shut down before the changes take effect.  I am not sure because I had been trying other options so something else might have produced the desired effect.  Anyway, I can now log in to all parts of my Ubuntu installation with the same lower case password.

Thanks to all

Greg

---

### Post by anonymouschief on 2012-10-19
It would help if you checked your account's password requirements policy using:

```
sudo chage -l username
```

Read more about it in the Password Policy section of the following guide:
[https://help.ubuntu.com/12.04/serverguide/user-management.html](https://help.ubuntu.com/12.04/serverguide/user-management.html)

---

