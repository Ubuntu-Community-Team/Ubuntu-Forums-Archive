---
title: "how to limit apt-get download speed"
date: 2005-06-03
forum: Repositories &amp; Backports
---

### Post by bepcyc on 2005-06-03
Is there any option like --limit-rate=2K to limit download speed when I get new packages with apt-get?

[here](http://www.linux.org.pe/pipermail/linux-plug/2005-March/015059.html) I found one solution, but it doesn't work (guess file /etc/apt/apt-file.conf is not in use anymore)

Any other solutions for this problem?

---

### Post by xristos on 2005-06-03
Did you try 
```
man apt-get
``` ?

---

### Post by bepcyc on 2005-06-03
[QUOTE=xristos]Did you try 
```
man apt-get
``` ?[/QUOTE]
yeah
and what about you?

---

### Post by xristos on 2005-06-03
Hey man it was just a question . I didn't imply anything.

So it appears that apt-get doesn't support bandwidth limiting.
You could try this ---> [http://ubuntuforums.org/showthread.php?t=20342](http://ubuntuforums.org/showthread.php?t=20342) instead .

---

### Post by XDevHald on 2005-06-03
I don't think he was aiming at you xristos, but the link that xristos have you bepcyc will help. Also when you make a thread, if you could start it with a "**how do I**" instead of "**how to**", so that the users are not confused with our Tips and Tricks forums. :)

---

### Post by bepcyc on 2005-06-03
[QUOTE=xristos]Hey man it was just a question . I didn't imply anything.

So it appears that apt-get doesn't support bandwidth limiting.
You could try this ---> [http://ubuntuforums.org/showthread.php?t=20342](http://ubuntuforums.org/showthread.php?t=20342) instead .[/QUOTE]

Big thanks
That's what I looked for

2xristos: Sorry for my aggression, I just had a bad day ;)

2BB: sorry, I'll note this next time

---

### Post by michallo on 2008-10-19
I found a better sollution. 
create file /etc/apt/apt.conf.d/76download with content:

Acquire
{
Queue-mode "access";
http
{
Dl-Limit "25";
};
};

That limits apt-get to 25KB/s

---

### Post by junglism on 2008-12-09
Hey michallo thanks for that - great solution! wondershaper wasnt really working for me

---

### Post by alienbrain on 2009-04-07
Sweet, nice tip. Since I only sometimes need to apply the limit, I use the -o command line option. Here is how I use it:
```

sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

---

### Post by jsenlai on 2009-06-06
had the same question. sweet tip there alienbrain. thanks

---

### Post by Alexandre Gomes on 2009-08-15
Alienbrain, man, this tip is great! Thank you so much! Editing texts files always that I wanna limit my bandwidth is very unpleasant. Thanks!

---

### Post by Xamiga on 2009-11-05
Alienbrain, man, this tip is great!   I'm on HughesNet, and need to limit my bandwidth during the day.
Thanks

---

### Post by BobXin on 2009-12-04
this tips help a lot on my server, it will not affect the access when update. great!

---

