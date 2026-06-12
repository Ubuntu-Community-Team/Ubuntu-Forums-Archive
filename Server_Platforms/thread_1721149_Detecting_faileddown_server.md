---
title: "Detecting failed/down server"
date: 2011-04-04
forum: Server Platforms
---

### Post by thepurpleblob on 2011-04-04
I have a number of Ubuntu servers all of which are running munin, which is fine.

However, what it doesn't do is send me an email when one of the machines fails. I had one fry a power supply the other day and I didn't know anything about it. 

I would like something simple where machines check each other and notify me if one fails.

Does such a thing exist? I'm struggling to find anything suitable.

TIA

---

### Post by spynappels on 2011-04-04
Have a look at Nagios, It is designed to do what you want plus more.
Failing that, a script on one or more of the servers which ping the others and mails you if there is a problem.

---

### Post by thepurpleblob on 2011-04-04
> **spynappels said:**
> Have a look at Nagios, It is designed to do what you want plus more.
Failing that, a script on one or more of the servers which ping the others and mails you if there is a problem.

Thanks... I've been trying to avoid getting to grips with Nagios for a while but I can see it's inevitable :)

---

### Post by spynappels on 2011-04-04
And very worthwhile, I was in your situation and just bit the bullet, and it really has made life easier for me.

Following the tutorials from Nagios themselves, you can have a basic monitoring system set up in no time, and then you can create different files to create different configs for different sets of servers etc.

---

