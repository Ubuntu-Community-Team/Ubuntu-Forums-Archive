---
title: "I get an error right after Fail2ban restart in Ubuntu 14.04"
date: 2016-03-11
forum: Server Platforms
---

### Post by Grigoriy on 2016-03-11
Hello!

I've been having this little issue, after I've installed recently fail2ban on Ubuntu 14.04
Right after I restart fail2ban in the terminal I get an error message.  Though I do get [OK], meaning that generally restart went OK. Still I  wish to get rid of this probably minor issue. I get this error message:

```
WARNING  'ignoreregex' not defined in 'Definition'. Using default one: ''
```

After some googling, I found a possible solution. Which is to add this:

```
ignoreregex =
```

to fail2ban conf files in /etc/fail2ban/filter.d directory
I've checked all the conf files there and I've seen that line in all of them, EXCEPT for one, which is **postfix-sasl.conf**
I have to add that [sasl] jail is **enabled** in my jail.local file

So my question is whether the solution is correct and also I would appreciate some explanation of what it's all about.

---

### Post by Habitual on 2016-03-11
Yes!
check postfix-sasl.conf for ignoreregex = at bottom of file.
restart fail2ban.

---

### Post by Grigoriy on 2016-03-12
Thanks!

---

### Post by Habitual on 2016-03-12
Ya!

---

