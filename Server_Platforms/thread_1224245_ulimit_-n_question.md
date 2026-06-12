---
title: "ulimit -n question"
date: 2009-07-27
forum: Server Platforms
---

### Post by dragos2 on 2009-07-27
I am modifying ulimit on Ubuntu Server 8.04 64 bits like this
# sudo -i
# ulimit -n 65535
# exit
then as normal user
$ ulimit -a

it sees the maximum open files 1024 ..

Is this normal ?

---

### Post by wojox on 2009-07-27
What does 

```
ulimit -n
```

give you?

---

### Post by jhannah on 2009-07-27
Since ulimit is really just a feature of bash, the changes you make to the settings only apply to the bash process that the ulimit command was run in. Once you close that process or start a new shell, the settings go back to their defaults. That being said, it sounds like you wish to change the defaults. To do that, I would recommend checking out /etc/security/limits.conf. There is a decent man page on the configuration file (man limits.conf) and I expect that will do what you need.

Hope that helps.

---

### Post by dragos2 on 2009-07-27
> **jhannah said:**
> Since ulimit is really just a feature of bash, the changes you make to the settings only apply to the bash process that the ulimit command was run in. Once you close that process or start a new shell, the settings go back to their defaults. That being said, it sounds like you wish to change the defaults. To do that, I would recommend checking out /etc/security/limits.conf. There is a decent man page on the configuration file (man limits.conf) and I expect that will do what you need.

Hope that helps.

I think you are right. Can this be done without PAM ?

---

### Post by dragos2 on 2009-07-27
> **wojox said:**
> What does 

```
ulimit -n
```give you?

It is 1024 by default.

---

### Post by wojox on 2009-07-27
So  open /etc/security/limits.conf and add


* soft nofiles 65535
* hard nofiles 65535

then 

```
ulimit -n 65535
```

```
ulimit -n
```

---

### Post by jhannah on 2009-07-27
> **dragos2 said:**
> I think you are right. Can this be done without PAM ?

It can, but I'm not sure I would really recommend it. :) You could use /etc/profile, /etc/bash.bashrc or ~/.bashrc to run the ulimit command which would effectively apply the limits every time bash started. Short of that, I can't think of another way that doesn't involve pam_limits. Any particular reason you are trying to stay away from PAM?

---

### Post by dragos2 on 2009-07-27
> **jhannah said:**
> It can, but I'm not sure I would really recommend it. :) You could use /etc/profile, /etc/bash.bashrc or ~/.bashrc to run the ulimit command which would effectively apply the limits every time bash started. Short of that, I can't think of another way that doesn't involve pam_limits. Any particular reason you are trying to stay away from PAM?

No particular reason, just asking if this is pam or shell related :) .

---

### Post by dragos2 on 2009-07-27
> **wojox said:**
> So  open /etc/security/limits.conf and add


* soft nofiles 65535
* hard nofiles 65535

then 

```
ulimit -n 65535
``````
ulimit -n
```

Thanks :)

One last question. What is the highest number I can set here ?
int on 32 bits ?

---

### Post by wojox on 2009-07-27
[http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/](http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/)

---

