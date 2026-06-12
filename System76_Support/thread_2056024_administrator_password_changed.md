---
title: "administrator password changed"
date: 2012-09-10
forum: System76 Support
---

### Post by tommyatkins on 2012-09-10
I just updated my system from 10.04 to 12.04. Everything went OK except the administrator password was changed!!
I can log into other accounts but not the one for root.

I have done other upgrades with no problems

Any help would be much appreciated.

tommy atkins

---

### Post by raja.genupula on 2012-09-10
Root ? 

OK are you able to do sudo -i in your terminal to turn as root ? 

Actually you can reset your password if you facing the problem from here 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tommyatkins on 2012-09-10
No I can not use sudo -i. It says I have entered a bad password.

Tommy Atkins

---

### Post by isantop on 2012-09-10
> **tommyatkins said:**
> No I can not use sudo -i. It says I have entered a bad password.

Tommy Atkins

The password for sudo is the login password for the account you're trying to log in with.

Ubuntu diables the root account by default, for security and other reasons. To run a command as root use: ```
sudo {command}
```

The password you type is the same one you use to log in.

To "log in" as root and get a root shell:

```
sudo -i
```

Again, the password is your login password.

Note that we don't recommend using a full root shell, since it's very easy to accidentalyy cause severe system damage this way.

---

### Post by tommyatkins on 2012-09-10
It is my root account that is disabled. I try to login my administrator account and it does not take the password. When I log in to another account it goes OK. Then when I try to run sudo in the other account it will not take the administrator password or the users password. I misspoke when I said root it should have been sys administrator.

---

### Post by overdrank on 2012-09-10
Hi and please do not create multiple threads on the same issue. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2056020"). Thread closed

---

