---
title: "Apparmor questions"
date: 2009-03-20
forum: Security
---

### Post by lovinglinux on 2009-03-20
I'm starting to learn how to use apparmor, so I created a new profile for Firefox. It seems to me that when the corresponding profile is present, Firefox use a lot more CPU to start than without it. Is this normal?

I'm also trying to use the *aa-logprof* command to generate basic rules for it, but I get this error:

```
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.
Use of uninitialized value in split at /usr/share/perl5/Immunix/SubDomain.pm line 2145, <$LOG> line 368.
Use of uninitialized value in string ne at /usr/share/perl5/Immunix/SubDomain.pm line 2155, <$LOG> line 368.

Log contains unknown mode r-profile.
```

---

### Post by bodhi.zazen on 2009-03-20
Awesome, nice to see people using apparmor.

I do not know the answer to your question, but it is a problem, IMO, that apparmor writes odd things to the logs, and then refuses to process it's own log, as demonstrated by:> Log contains unknown mode r-profile

To be honest, I just open a terminal and:

```
tail -F /var/log/messages
```

You will see a lot of messages, fix the ones you can and they will lessen (as yo urefine and re-start your profiles / apparmor).

If you get stuck, take a look at other profiles.

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

Yes it is a *pain*, but it becomes much easier after you get a few profiles under your belt. IMO firefox is not the best to start with as it requires a large profile. Start with something smaller like xchat or audacious.

The downside of apparmor if you will is it takes maintenance. The upside is it is faster to learn then SELinux and it will make you much more secure.

I hope over time arrarmor will mature and the tools will be less prone to errors and easier to use.

As an aside, this is why I set up a repository, to help people learn and I am still looking for people willing to contribute apparmor profiles. So if anyone would like to contribute, please send me a PM and I will add them to my site.

---

### Post by lovinglinux on 2009-03-20
Thanks bodhi. I agree it is a *pain*, but looks like a great tool for protection once you get things working. I will try to learn with other applications first or will leave Firefox profile in complain mode while I learn.

What about the CPU usage?

BTW, I'm only using Apparmor because of your Ubuntu Classroom session. Before that class I thought apparmor was a "monster with two heads". Is not that complicated, just requires a good profile and maintenance.

---

### Post by bodhi.zazen on 2009-03-23
May I suggest you look at what is taking all your CPU with say top ?

Apparmor alone doe snot use this much CPU.

Top should show you the problem and if your cpu usage drops when you stop aa (/etc/init.d/apparmor stop) then look at /var/log/messages to see what may be happening.

---

