---
title: "How do I turn my firewall on?"
date: 2009-02-04
forum: Security
---

### Post by semitone36 on 2009-02-04
I know that the linux kernel comes with iptables as a basic firewall and I had always assumed that it was running in the background of my system.  

But I turned on my machine today and I happend to notice in the output while it was booting up that there was an entry that said something along the lines of:

**Skipping firewall, ufw not configured.**

This piqued my interest so I ran a search on my file system for any files that contained *ufw*.  I found two .conf files for ufw (one in /etc and another in /usr/share) that both had only two lines:

> #set to yes to enable
ENABLE = no

So I set both .conf files to "yes" and rebooted to see what would happen.  I dont think the skipping firewall message came up but other than that I have no idea if my tinkering did anything.

Is there anyone here who could explain any of the above?

---

### Post by semitone36 on 2009-02-04
lol nevermind

I answered my own question about 3 or 4 times just by reading the other threads in this section.  It would have been a ton easier for me to have just used **sudo ufw enable**

---

### Post by jerome1232 on 2009-02-04
Try looking at "man ufw"

```
man ufw
```

ufw is a program that manipulates iptables rules, iptables is the actual firewall, it's on by default but is set to not block anything by default.

I think giving the sticky at the top of this section would be a good read for ways to secure you installation. Most users will not benefit much in the security area from a firewall.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by cdenley on 2009-02-04
Iptables is loaded by default, but it allows everything. UFW, a front-end for iptables, is disabled by default, and won't create iptables rules until enabled. There is no need to edit any files.

to enable UFW:
```

sudo ufw enable

```

to block incoming connections by default:
```

sudo ufw default deny

```

to check the status of UFW:
```

sudo ufw status

```

---

### Post by semitone36 on 2009-02-04
Thanks guys.  I was actually just going over the man pages before this post.

---

