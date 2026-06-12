---
title: "4 Different Intrusion Detection Systems - which is your favoirte and why?"
date: 2016-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by patrikmellq on 2016-01-31
Vote for you favorite and add a line about why - many thanks.

1. Tripwire
2. Aide
3. Samhain
4. Afick

I will not vote, but i will add a comment about Tripwire.
After posting my Tripwire howto at Linuxquestions org forum some one pointed out that Tripwire has not been devoloping or updates during several years.
But still i got the impression pepole still use Tripwire!
At this topic some members mention Samhain and Afick.
I browse the web and got a very impressive read about both IDS.
Personally i start to install and learn more about Afick that comes with GUI and are not to difficult to learn how to configurate, my opinion.

Cheers

---

### Post by Habitual on 2016-01-31
> **patrikmellq said:**
> Personally i start to install and learn more about Afick that comes with GUI and are not to difficult to learn how to configurate, my opinion.
The difficulty doesn't arise until the GUI doesn't work. ;)

---

### Post by oldos2er on 2016-01-31
Not a support question; moved to Ubuntu, Linux & OS Chat.

---

### Post by patrikmellq on 2016-01-31
> **Habitual said:**
> The difficulty doesn't arise until the GUI doesn't work. ;)

:-) I did use nano text editor with no GUI when learning to install and configuration Tripwire, is not so scary and the Afick GUI is not so much better then a black screen with text, as the GUI only have drop meny for certain functions, the output is still plain text ...
If i get Afick working i will post a complete howto for beginners :-) that is how i contribute to the Ubuntu community ....

Cheers

---

### Post by Habitual on 2016-01-31
You missed one very popular tool, fail2ban

---

### Post by mastablasta on 2016-02-01
i don't understand why by default fail2ban doesn't save the jail.

---

### Post by Habitual on 2016-02-01
> **mastablasta said:**
> i don't understand why by default fail2ban doesn't save the jail.
Which jail are you referring to?

---

### Post by mastablasta on 2016-02-01
> **Habitual said:**
> Which jail are you referring to?

blocked IP addresses. by default they are cleared on reboot I believe. I have it setup to save all banned ip's (blacklist). though whitelisting is a better solution, it is not always possible.

---

### Post by Habitual on 2016-02-01
> **mastablasta said:**
> blocked IP addresses. by default they are cleared on reboot I believe. I have it setup to save all banned ip's (blacklist). though whitelisting is a better solution, it is not always possible.
Ah, yes. Well I have ```
/sbin/iptables-save > /etc/iptables/rules.v4 && /sbin/iptables-save > /root/jj/safe.rules.last
``` and it runs every 15 minutes.

Worse case is I lose the last 15 minutes of bans.
I avoid recidive as I ban for a whole year.

---

