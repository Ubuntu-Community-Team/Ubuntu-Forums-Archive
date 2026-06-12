---
title: "Utopic 14.10 Thunderbird 24.5 stopped receiving email"
date: 2014-06-04
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-06-04
My Thunderbird recently stopped getting any emails. It just times out after a long period of time.
It used to work which is what surprises me. I tried uninstalling it **sudo apt-get purge thunderbird*** rebooted and then reinstalled it through Synaptic.
I installed thunderbird, thunderbird-locale-en, thunderbird-locale-en-us and thunderbird-gnome-support.

Then I copied ~/.thunderbird from Trusty 14.04 which uses the same version of Thunderbird and it works good there. I then dropped that folder into my home directory on Utopic.
I've done that many times since **cariboo907** showed me how and it's always worked like a charm.

I don't understand what gives.

Is any one else experiencing this problem?

---

### Post by cariboo on 2014-06-04
Check your permissions, The first time I installed Utopic, some of the email folders couldn't be accessed, I set ~/.thunderbird to 700, and the directories inside to 755.

---

### Post by Cavsfan on 2014-06-04
> **cariboo907 said:**
> Check your permissions, The first time I installed Utopic, some of the email folders couldn't be accessed, I set ~/.thunderbird to 700, and the directories inside to 755.

I just realized that I'm about sure it was caused by me. I added a bunch of gufw firewall rules from this page [http://debianhelp.wordpress.com/2013/11/30/to-do-list-after-installing-linux-mint-16/](http://debianhelp.wordpress.com/2013/11/30/to-do-list-after-installing-linux-mint-16/)
I was going into my 5 Linux systems and retreiving email as I think the email is setup to be deleted 3 days after retrival and if I don't get in each one I won't have them all up to date.

I had put those rules on Mint 17 first and then I put them on Utopic afterwards. Neither system retrieves email.

These are what I added:
```
cavsfan@cavsfan-cavsfan:~$ sudo ufw status verbose
[sudo] password for cavsfan: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
5353/udp                   DENY IN     Anywhere
5900/tcp                   DENY IN     Anywhere
22                         DENY IN     Anywhere
25/tcp                     DENY IN     Anywhere
135,139,445/tcp            DENY IN     Anywhere
137,138/udp                DENY IN     Anywhere
110                        DENY IN     Anywhere
2049                       DENY IN     Anywhere
143                        DENY IN     Anywhere
21/tcp                     DENY IN     Anywhere
5353/udp (v6)              DENY IN     Anywhere (v6)
5900/tcp (v6)              DENY IN     Anywhere (v6)
22 (v6)                    DENY IN     Anywhere (v6)
25/tcp (v6)                DENY IN     Anywhere (v6)
135,139,445/tcp (v6)       DENY IN     Anywhere (v6)
137,138/udp (v6)           DENY IN     Anywhere (v6)
110 (v6)                   DENY IN     Anywhere (v6)
2049 (v6)                  DENY IN     Anywhere (v6)
143 (v6)                   DENY IN     Anywhere (v6)
21/tcp (v6)                DENY IN     Anywhere (v6)

1:19/tcp                   DENY OUT    Anywhere
1:19/udp                   DENY OUT    Anywhere
22:52/tcp                  DENY OUT    Anywhere
22:52/udp                  DENY OUT    Anywhere
54:79/tcp                  DENY OUT    Anywhere
54:79/udp                  DENY OUT    Anywhere
81:122/tcp                 DENY OUT    Anywhere
81:122/udp                 DENY OUT    Anywhere
124:442/tcp                DENY OUT    Anywhere
124:442/udp                DENY OUT    Anywhere
444:65535/tcp              DENY OUT    Anywhere
444:65535/udp              DENY OUT    Anywhere
1:19/tcp (v6)              DENY OUT    Anywhere (v6)
1:19/udp (v6)              DENY OUT    Anywhere (v6)
22:52/tcp (v6)             DENY OUT    Anywhere (v6)
22:52/udp (v6)             DENY OUT    Anywhere (v6)
54:79/tcp (v6)             DENY OUT    Anywhere (v6)
54:79/udp (v6)             DENY OUT    Anywhere (v6)
81:122/tcp (v6)            DENY OUT    Anywhere (v6)
81:122/udp (v6)            DENY OUT    Anywhere (v6)
124:442/tcp (v6)           DENY OUT    Anywhere (v6)
124:442/udp (v6)           DENY OUT    Anywhere (v6)
444:65535/tcp (v6)         DENY OUT    Anywhere (v6)
444:65535/udp (v6)         DENY OUT    Anywhere (v6)

```

I'd like to figure out which one to allow for Thunderbird but that seems like searching for the eye of a needle in a haystack. :p
Sometimes what appears to be genious is just stupid it seems.

I read where just having UFW on denying all incoming and allowing all outgoing is sufficient.

Would you agree with that statement? 

Thanks for the post! :)

---

### Post by Cavsfan on 2014-06-04
I turned ufw off in Linux Mint 17 and it retrieved the email. I guess I just need to remove all of those rules.

---

### Post by Cavsfan on 2014-06-04
Utopic was fixed just by turning off the firewall and rebooting. I got the email and tested an email send and receive and it's all good. Then I reset the firewall removing all of the rules and turning it off.
I then turned it back on and rebooted and all is good.
Think I may have done something to Mint 17 but that's another story.

**Cariboo907** how do I figure out what is 700 or 755? I've seen that in a chmod command but I don't think I know what the numbers equate to.

Here is about all I know:

```
cavsfan@cavsfan-MS-7529:~$ ls -l ~/.thunderbird 
total 20
drwx------ 3 cavsfan cavsfan 4096 Jun  4 11:36 [COLOR=#0000ff]28sy77ef.default[/COLOR]
drwx------ 2 cavsfan cavsfan 4096 Jun  3 16:17 [COLOR=#0000ff]cqivsvnd.default[/COLOR]
drwx------ 2 cavsfan cavsfan 4096 Aug 19  2013 [COLOR=#0000ff]Crash Reports[/COLOR]
drwx------ 4 cavsfan cavsfan 4096 Jun  4 15:42 [COLOR=#0000ff]mdi6lw6d.default[/COLOR]
-rw------- 1 cavsfan cavsfan   94 Mar  3  2013 profiles.ini
```

Thanks

---

### Post by Elfy on 2014-06-04
> **Cavsfan said:**
> ...

**Cariboo907** how do I figure out what is 700 or 755? I've seen that in a chmod command but I don't think I know what the numbers equate to. 

...

Thanks
Check this out while you get you're head around the numbers

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by cariboo on 2014-06-04
> **Cavsfan said:**
> Utopic was fixed just by turning off the firewall and rebooting. I got the email and tested an email send and receive and it's all good. Then I reset the firewall removing all of the rules and turning it off.
I then turned it back on and rebooted and all is good.
Think I may have done something to Mint 17 but that's another story.

**Cariboo907** how do I figure out what is 700 or 755? I've seen that in a chmod command but I don't think I know what the numbers equate to.

Here is about all I know:

```
cavsfan@cavsfan-MS-7529:~$ ls -l ~/.thunderbird 
total 20
drwx------ 3 cavsfan cavsfan 4096 Jun  4 11:36 [COLOR=#0000ff]28sy77ef.default[/COLOR]
drwx------ 2 cavsfan cavsfan 4096 Jun  3 16:17 [COLOR=#0000ff]cqivsvnd.default[/COLOR]
drwx------ 2 cavsfan cavsfan 4096 Aug 19  2013 [COLOR=#0000ff]Crash Reports[/COLOR]
drwx------ 4 cavsfan cavsfan 4096 Jun  4 15:42 [COLOR=#0000ff]mdi6lw6d.default[/COLOR]
-rw------- 1 cavsfan cavsfan   94 Mar  3  2013 profiles.ini
```

Thanks

I'm just a bit lazy, so I use mc:

[[IMG]http://i.imgur.com/tjrfAmWl.png[/IMG]](http://imgur.com/tjrfAmW)

---

### Post by Cavsfan on 2014-06-05
> **Elfy said:**
> Check this out while you get you're head around the numbers

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

Thanks for that link Elfy! :) Octal? It's been a long time since I've dealt with octal numbers. I bookmarked it.

> **cariboo907 said:**
> I'm just a bit lazy, so I use mc:

[[IMG]http://i.imgur.com/tjrfAmWl.png[/IMG]]("http://imgur.com/tjrfAmW")

I can certainly understand why. :lol: Midnight Commander pretty sweet except that looks like there would be a learning curve for me. It looks a lot like nano which I am also unfamiliar with. 

This problem was self inflicted with the GUFW rules I added. Now I just have ufw turned on without any rules.
And my Mint 17 problem was the same thing. I tried sending an email to myself but it would not send until I realized I had misspelled the email address. #-o

---

### Post by Cavsfan on 2014-06-16
Then to throw in another curve as to why this happened. I should not have even been messing with software firewalls. I have a router with a built in hardware firewall. 
While searching for the best firewall I seen that a hardware firewall is the ultimate because it's on before the pc boots up.

I have Intrusion Detector Level set to high and to notify me if an intrusion occurs. - 
[PHP]Use packet filter settings for intrusion detector.
Detect intrusion and notify Intrusion Detector utility.[/PHP]

---

### Post by QDR06VV9 on 2014-06-16
> **Elfy said:**
> Check this out while you get you're head around the numbers

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)
Thanks Elfy I have not been able to find that page for about a year now!:)

---

