---
title: "Packet Filter Firewall?"
date: 2010-07-13
forum: Security
---

### Post by rbb138 on 2010-07-13
I use ubuntu for many of my gameservers in an online game company i work for and have hit a large exploit problem with the game.
Players are using mass spam of actions to trigger a rollback on their character and therefor duplicate items.

What we need to stop this is a way to filter out and reject packets that are identicle to each other and occur within 0.1 seconds of each other. This way the rollback will not be triggered.

This exploit is spreading like wildfire and myself and many other game developers are working flat out to find a fix for it, all help is appricated!

---

### Post by bodhi.zazen on 2010-07-13
You can use iptables to rate limit the connection or use the strings option to filter the content.

Hard to advise you further without more information, and iptables has a steep learning curve ...

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by rbb138 on 2010-07-13
is it possible to configure iptables to compare the packet to previous ones also?
rather than blocking floods of packets simply if they are from the same address.

---

### Post by bodhi.zazen on 2010-07-13
> **rbb138 said:**
> is it possible to configure iptables to compare the packet to previous ones also?
rather than blocking floods of packets simply if they are from the same address.

yes, if you can match on a string. Is there something unique to the packet ?

iptables -A INPUT -m string --algo bm --sting "foo" -m limit --limit 1/min -j ACCEPT

You will need to know what is in the packet to identify a string (text) to match.

---

### Post by rbb138 on 2010-07-13
there would be yes, but theres about 8 different packets they can flood to cause the problem. Ill begin logging the responsible packets now and find a constant that can be used to identify it.

---

### Post by bodhi.zazen on 2010-07-13
> **rbb138 said:**
> there would be yes, but theres about 8 different packets they can flood to cause the problem. Ill begin logging the responsible packets now and find a constant that can be used to identify it.

Either that or 8 rules, not that bad a solution.

---

### Post by rbb138 on 2010-07-13
As far as i can work out all the packets are unique, there are no similarities between them.

However in order for them to have do this they would need to do the same action every 60milliseconds. So is it possible to use IPTables to reject or delay any incoming packets that go faster than this?
without blocking their ip (which most anti-dos scripts iv found do).

---

### Post by bodhi.zazen on 2010-07-13
> **rbb138 said:**
> As far as i can work out all the packets are unique, there are no similarities between them.

However in order for them to have do this they would need to do the same action every 60milliseconds. So is it possible to use IPTables to reject or delay any incoming packets that go faster than this?
without blocking their ip (which most anti-dos scripts iv found do).

That is what the -m limit option does , allows one packet every so often. I would imagine once a minute is sufficient, but you can fine tune it.

The -m string will match a specific packet content, not the ipaddress.

So if all goes well you will rate limit only a few packets and not the entire connection / ipaddress.

---

### Post by rbb138 on 2010-07-13
I have worked out the maximum amount of packets i can allow them before it also allows them to abuse the error is 10 per second.
however its limited to 1 second, and i need 60ms.

edit: worked it out now, just tweaking things to prevent a flood and override the anti-flood system in the serverscript which is broken and was causing the issue.

edit2: -A INPUT -p tcp -m tcp -m limit --limit 6/second -j ACCEPT is certainly causing some disturbance but is only delaying the packets, not rejecting them. The result of the action is still clear after a few seconds.

---

### Post by bodhi.zazen on 2010-07-13
Ouch.

Try a more restrictive limit on those packets.

Obviously this idea is a bandaid and not the real problem, so it may not be as effeective as you hope.

Of course, you could ban their IP for 10 minutes, I assume legitimate traffic would not be affected by that.

A 10 min ban can be increased if they do not take the hint ;)

---

### Post by rbb138 on 2010-07-13
We cannot fix the problem itself within the next few months and so desperate measures are being put in place.

I am currently running tests to see if it is effective at stopping the exploit.

---

### Post by CharlesA on 2010-07-13
If it was me, I'd just IP ban them for a day or two for using exploits. Perm ban if they keep it up.

But that's just me.

---

### Post by bodhi.zazen on 2010-07-13
> **CharlesA said:**
> If it was me, I'd just IP ban them for a day or two for using exploits. Perm ban if they keep it up.

But that's just me.

Until you have a better solution I think that is all you can do.

---

### Post by rbb138 on 2010-07-14
That is what i have been doing for the past week but it is beyond that point now.

The packets are still being delayed instead of dropped or rejected. I even tried putting the default action to drop and a rule only accepting when rate is below than 6 per second.
should i be putting drop if rate is below 6 a second or accept if rate is below 6 a second?

Maybe theres annother firewall that could reject too many packets from a certain address.

edit: have now tried putting a limit-burst also.
still the exact same problem with there being disturbance only.

---

### Post by rbb138 on 2010-07-15
have now put in place a hash limit to create a filter for each player.

however the same problem still occurs, instead of the packets moving down the rule chain once the limit is exceeded, they get put on hold and take effect usualy 20 seconds after.

currently using:
-A INPUT -p tcp -m hashlimit --hashlimit 2/sec --hashlimit-mode srcip,dstport --hashlimit-name hosts --hashlimit-burst 10 --hashlimit-htable-gcinterval 1000 --hashlimit-htable-expire 1000 -j ACCEPT

my iptables are 1.4.4

edit: seems to be that the packets are being put on hold if they exceeed the speed until the counter is emptied or the speed returns to normal, at that point it simply lets them all through.... pointless?

---

