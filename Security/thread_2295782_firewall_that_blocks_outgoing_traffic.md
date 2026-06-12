---
title: "firewall that blocks outgoing traffic"
date: 2015-09-21
forum: Security
---

### Post by Robbyx on 2015-09-21
Has anyone seen a simple to use/ setup  firewall that uses a whitelist / blacklist to block traffic going out from a machine onto the net?
Incoming appears well blocked via my router but a lot of mischief can come from outgoing traffic.

---

### Post by maglin2 on 2015-09-21
There's a discussion in the second half of this thread - but probably not a real answer to your question. [http://ubuntuforums.org/showthread.php?t=2294261](http://ubuntuforums.org/showthread.php?t=2294261)

---

### Post by Robbyx on 2015-09-21
I agree, it is not a real answer because it seems to suggest that all bogus output to the web is done under the guise of it being from  another bonafide properly installed  program. 

A helpful approach would be traffic monitoring combined with lists of known doubtful addresses, similar to anti-spam software. Is there a semi intelligent traffic monitoring program suitable for a desktop machine?

---

### Post by QDR06VV9 on 2015-09-21
Maybe this
[http://askubuntu.com/questions/257263/how-to-display-network-traffic-in-terminal](http://askubuntu.com/questions/257263/how-to-display-network-traffic-in-terminal)
Just my opinion here but I really like [h=1][iptraf]("http://iptraf.seul.org/")[/h]

---

### Post by Robbyx on 2015-09-21
Going down the suggestions in the referred to answers I was very impressed with the concept of nethogs. It has a big advantage in that it shows the originating process.  I thought it was probably better than the other choices  because it made it  a lot easier to find the reason for the  bandwidth use. I would appreciate your views.

---

### Post by QDR06VV9 on 2015-09-21
Before I do, Give **[iptraf]("http://iptraf.seul.org/") a look. **It is in synaptic.&#8203;Nethogs is an excellent Choice though.
Maybe it is just me I really like the whole package very configurable with a few more options.
But use what you think suits your needs the best.
Kind Regards

---

### Post by maglin2 on 2015-09-21
Plus perhaps edit hosts file to block some unwanted connections - there are examples for windows out there that I guess could be copied?

---

### Post by Robbyx on 2015-09-21
I will give iptraf a look. Thank you.  I think it will work well with Nethogs. Nethogs gives the process and iptraf gives the destination, both essential. Is it true that iptraf does not show the process that is producing the traffic?  I am a bit surprised that none are showing both the process and the destination together  in one screen . 

I can also  see a place for ifstat because that gives  a simple warning that something is wrong and  that could be followed up by the other programs!

---

