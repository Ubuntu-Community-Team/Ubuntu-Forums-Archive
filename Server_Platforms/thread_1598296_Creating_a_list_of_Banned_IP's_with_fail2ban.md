---
title: "Creating a list of Banned IP's with fail2ban"
date: 2010-10-16
forum: Server Platforms
---

### Post by mistypotato on 2010-10-16
G'morning!

I'm trying to use a technique suggested by a fella at this website....

[http://www.pseiko.nl/blog/288/persistent-iptables-bans-from-fail2ban]("http://www.pseiko.nl/blog/288/persistent-iptables-bans-from-fail2ban")

He suggests adding an echo line to the actionban line in order to create or add to a file that will contain a list of all the IP's that fail2ban has banned.....but it doesn't seem to generate any output.   .....here is the command.....

[B]
actionban = iptables -I fail2ban- 1 -s  -j DROP
                 echo  >> /etc/shitlist[/B]

I never get any IP's in the file so the echo part does not seem to work.

Does anyone see an obvious reason for it not working?

thx

---

### Post by James78 on 2010-10-16
I took a look into my own fail2ban configuration, and in iptables-allports filter, I found this line. This is what I would do. Not guaranteed to work, but it looks good too me.

```
actionban = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
            echo <ip> >> /var/log/hacklist
```

P.S. The IP list is a good idea. :) I might try this myself, for more of a permanent blacklist.

---

### Post by mistypotato on 2010-10-16
That is very helpful :)

Thank you !!!

At least now I know someone else is using the line and it works for them.   Now if I can only find out why I'm not getting any IP's in the file on my system.




:KS

---

### Post by James78 on 2010-10-16
Well, I don't know if it actually works, I haven't tested it out. It's just a suggestion I hope works for you. Today isn't my workday though, so I really don't feel like going into the configuration, changing it, and debugging it. :/

---

### Post by mistypotato on 2010-10-16
:-)

Well,
if you get a chance to check that hacklist file and see if anything is actually in it I would be interested to know.


Cheers!

---

### Post by James78 on 2010-10-20
Just a quick thought. Your original command probably worked. I suspect that the permissions were denied.

See who owns the /etc/****list, and you could chown it to the fail2ban user, or you could chmod o+rw /etc/****list

If that doesn't work, I'll think about writing a custom filter to log it to a file for you (will still require correct permissions on the file).

(If you test out your configuration by tripping it on purpose, you might find in /var/log/fail2ban.log, that it shows the error of denied permissions on your bad ip list)

---

