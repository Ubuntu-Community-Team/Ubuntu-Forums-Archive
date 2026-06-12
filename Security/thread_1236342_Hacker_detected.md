---
title: "Hacker detected"
date: 2009-08-10
forum: Security
---

### Post by dragos2 on 2009-08-10
I have detected a hacker on one of our servers, I let him there and collected 1 month of
traffic including his illegal activity.

Now I decided to terminate his access and report him to his ISP(possibly legal actions will be taken). Any ideas of what to say to him before disconencting him ?

---

### Post by lisati on 2009-08-10
Maybe you don't have to say anything. Just provide the ISP with the relevant logs etc......

---

### Post by tubbygweilo on 2009-08-10
Why not see what the ISP and local law enforcement recommend? 

After all they have had the run of your kit for a month so a couple of weeks more and the hope of catching them red handed might be the way to go.

---

### Post by stinger30au on 2009-08-10
i would not say anything to him/her

hand all data to the police/isp and let them sort it out

---

### Post by jamie1985 on 2009-08-10
'All your base are belong to us' ? 

On a serious note, I'd check with the ISP/law enforcement. Forward all the info you have and ask for their recomendations on next steps etc.

---

### Post by scorp123 on 2009-08-12
> **dragos2 said:**
>  Any ideas of what to say to him before disconencting him ? I'd not terminate his access but instead play "******* Operator from Hell" (BOFH) and make sure he gets to read a nice message the next time he logs in (e.g. place it into his ~/.bashrc or ~/.profile ?), e.g. something like:

"Dear Hacker,

thanks for visiting our system for the past few weeks. Yes, we've been noticing you for quite a while now. And we've been collecting all the evidence. Your ISP has been notified too. And you will get mail from our lawyers too ... Have a nice day. ;-)  .... "

Oh well .... maybe I'm just childish ... But I'd really like to see this guy's face when he reads this :lolflag:

---

### Post by Dave_Connor on 2009-08-12
It is fun being a bit of a jerk to someone who was with you with breaking into your system (depends on level of security measures) but always fun to see there reaction of them being found out :)

---

### Post by unspawn on 2009-08-13
> **dragos2 said:**
> I have detected a hacker on one of our servers, I let him there and collected 1 month of traffic including his illegal activity.
Unless this was a contained honeypot setup, that machine is exposed to a network and has a vulnerability that is good enough for the cracker to get in. 
What every response in this thread forgot to mention is that breaches of security hold the type of risk that warrants dealing with decisively and immediately. 
Deliberately letting such a situation exist for a prolonged period of time not only puts adjacent machines but the 'net as a whole at risk because you allow the cracker the opportunity to recon and subvert other machines. With all due respect but as such it's simply irresponsible.

---

### Post by Kinstonian on 2009-08-13
Unspawn, good point.  Also, I'm not a lawyer, but as I understand it, if the OP is in the US, then he should have taken some reasonable measures to notify the attacker that his activity is subject to monitoring.  You need to take away his expectation of privacy, or else god forbid you'd be violating your attacker's rights.  Whether the OP is in the US or not, I hope a lawyer was involved in the approving the monitoring.

Furthermore, unless there was significant damage caused by the attack, it is unlikely law enforcement will spend much (if any) resources investigating it.

---

### Post by ronaldprettyman on 2009-08-13
> **dragos2 said:**
> I have detected a hacker on one of our servers, I let him there and collected 1 month of
traffic including his illegal activity.

Now I decided to terminate his access and report him to his ISP(possibly legal actions will be taken). Any ideas of what to say to him before disconencting him ?

```
sudo echo "Gotta Bitch"|wall
kill -11 `ps -A|grep $HACKERPORT|awk '{print$1}'`

```

---

