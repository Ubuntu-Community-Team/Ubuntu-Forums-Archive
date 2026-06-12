---
title: "iptables: What's the difference between DROP and REJECT"
date: 2018-09-06
forum: Security
---

### Post by webmiester on 2018-09-06
Hi Everyone,

In setting up iPtables, what is the difference between DROP and REJECT? Are there any compelling reasons to choose one over the other?
Also, I found a thread which had this line:

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

So what is postrouting and masquerade?  Thanks

---

### Post by #&amp;thj^% on 2018-09-06
> **webmiester said:**
> what is the difference between DROP and REJECT? Are there any compelling reasons to choose one over the other?


Have a look: [http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

> **webmiester said:**
> So what is postrouting and masquerade? 

And a short view on  masquerade. 
Edit: A good read: [https://terrywang.net/2016/02/02/new-iptables-gotchas.html](https://terrywang.net/2016/02/02/new-iptables-gotchas.html)
It is an algorithm dependant on the iptables implementation that allows one to route traffic without disrupting the original traffic. 
And others will also join in here with their findings.

---

### Post by webmiester on 2018-09-06
Oh wow, thank you.

I was thinking that DROP would be safer that REJECT but your link says that it isn't.  Thanks so much.

I still cant get the postrouting and masquerade part though.  The article was a little too technical for me, and it described the difference between SNAT and masquerade, but I dont understand both SNAT and masquerade.  The DROP and REJECT was easier...

Lets say I go to a party and there was a closed door and a guard in the door.

In ACCEPT, the door is simply open and there is no guard
In REJECT, the door is  closed and the guard will tell me "Im sorry but you cant enter", so I know at once that I cant enter.
In DROP, the door is closed and and there is no guard in sight, so I keep knocking until I get tired.

this is an oversimplification of things, Im sure.

I think the nicest way to do this is to make our server look like it isnt  there.  For instance, if my server is at 192.123.123.123 and I visit 192.123.123.1, then I should get something like "The site Cant be reached" error.  So if an unauthorized person were to visit my server and he gets the same response, he will think there is no server there and can move on.  Ive been using DROP, and what happens is like this... If I visit ...122 I get (The site Cant be reached), if I visit ....123 that the computer just stalls...  A smart guy (or even robot) who sees that the response is different in this address would know that there is something there.  Whereas if the error was "The Site Cant be reached", then we can trick him to think here was nothing there...  

I am now trying our REJECT, and I also get the same result as DROP, the computer visiting the site simply stalls.  Is there a way to make it look like "The Site Cant be Reached"?

---

### Post by SeijiSensei on 2018-09-07
There isn't any "smart guy" there most of the time.  It really doesn't matter at all.

My servers use
```
/sbin/iptables -P INPUT DROP
```

to define the default policy as DROP.  I've always thought "dropping packets on the floor," as the famed [Alan Cox]("https://en.wikipedia.org/wiki/Alan_Cox") once put it, is the best default.

---

### Post by QIII on 2018-09-07
I have read a number of people make good arguments for each suggestion.  I find the most compelling argument to be DROP.  REJECT might be taken as a challenge to be accepted.

I use DROP.

---

### Post by #&amp;thj^% on 2018-09-08
> **QIII said:**
> I have read a number of people make good arguments for each suggestion.  I find the most compelling argument to be DROP.  **_REJECT might be taken as a challenge to be accepted_**.

I use DROP.

+1 I also use DROP.
> DROP (aka DENY, BLACKHOLE)
    Prohibit a packet from passing. Send no response.

---

### Post by webmiester on 2018-09-11
Thanks, I changed my settings to drop.

---

