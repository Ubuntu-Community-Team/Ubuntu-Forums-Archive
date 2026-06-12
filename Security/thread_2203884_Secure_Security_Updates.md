---
title: "Secure Security Updates???"
date: 2014-02-05
forum: Security
---

### Post by BuntuSeriously on 2014-02-05
Greetings!

A simple q for the community today; but one which has been troubling me for a good bit ;)

From what I understand, a standard Ubuntu installation does all of its security updates in the open, without any encryption.  Is this correct?

That being so, I seem to recall some commentary to the effect that payload integrity in assured by hash.  Is this true?

If all of this is so, I truly shiver at the "backdoor" prospects here.  At the very least, unless we're talking about whirlpool or some comparable hash validation, there are interests which could have an absolute field day with everyone; as MD5 (and similar) leave significant "nooks" for quick automated file alteration *en route*.

So, that being said, could someone shed a bit of light on this for the record?  Indeed, what's the current thinking here???


Thanks all; and have a great day --

---

### Post by cariboo on 2014-02-05
These **Backdoors** that you mention, how would you suggest they be taken advantage of?

---

### Post by bashiergui on 2014-02-05
Funny, I just explained this in another thread. 

The way updates work in Ubuntu is software is placed in repositories with cryptographic keys. Your computer has a key for each repository. When your computer checks for updates, it first validates that the keys match. Then the download commences. So yes, they're sent in the clear over http, but the source is validated first.

An attacker would have to own a repository or the cryptographic keys for it. While that's not impossible, it's highly unlikely because the reward for the bad guy would not exceed the cost to do it.

---

### Post by bashiergui on 2014-02-05
Here's a more thorough answer
[http://askubuntu.com/questions/131397/what-is-a-repository-key-under-ubuntu-and-how-do-they-work](http://askubuntu.com/questions/131397/what-is-a-repository-key-under-ubuntu-and-how-do-they-work)

---

### Post by cariboo on 2014-02-06
The other thing to keep in mind, is that not just anyone can upload a package to the repositories. There are several dedicated teams that make sure that any package submitted for inclusion in the repositories have been audited before acceptance.

---

### Post by BuntuSeriously on 2014-02-06
Thanks, all, for the input.  I think I might now have a reasonable grasp of what's going on here.

> An attacker would have to own a repository or the cryptographic keys for  it. While that's not impossible, it's highly unlikely because the  reward for the bad guy would not exceed the cost to do it.

Perhaps what we're looking at is a difference in scope.  Conversationally speaking, there is an adversary which operatively controls entire swaths of the web at this point; and it's likely the situation is set to expand as time goes on.  Don't know what anyone else thinks, but this type of phenomena is foundationally creepy, and, as any student of history will attest, ultimately dangerous.  But I digress...

In any event, that's the context which sees my concerns about security updates being floated about via http through this network without a quick, securely-transmitted hash such as whirlpool associated with the delivered package.  It's just too simple for everyone to get "owned" in a way which is not savory in this atmosphere of eroded digital freedoms.

Am I missing a key component of the update transaction which obviates these concerns???


Thanks again --

---

### Post by bashiergui on 2014-02-06
> **BuntuSeriously said:**
> Am I missing a key component of the update transaction which obviates these concerns???Yes. 
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

So what would have to happen for an attacker to take advantage of the http clear text transmissions of update traffic is they would have to man-in-the-middle you. They would then have to intercept the legitimate traffic, inject the malware, and then forward the traffic to you. 

That's an excellent reason not to update your system over public wifi. But if you're on your own trusted LAN, then the risk is low.

---

### Post by BuntuSeriously on 2014-02-06
@bashiergui:

Well considered; and thanks again.

However, here's a quote from a recent arstechnica article which seems to underscore the overall need for encryption, particularly in a setting such as this:
> By diverting (traffic) to unauthorized routers under control of hackers, they were then free to monitor or tamper with any data that was unencrypted before sending it to its intended recipient with little sign of what had just taken place.
[http://arstechnica.com/security/2013/11/repeated-attacks-hijack-huge-chunks-of-internet-traffic-researchers-warn/](http://arstechnica.com/security/2013/11/repeated-attacks-hijack-huge-chunks-of-internet-traffic-researchers-warn/)

Terrifyingly, this report points at relevant, large-scale MitM activity _*in the wild*_...

Of course, there will always be a way for monstrous mischief to take place.  Ultimately, you can't keep a determined attacker from stealing your goods; but it surely doesn't pay not to lock the door.

In short, and weighing everything, is http/MD5 really the best we can do here?

(Beer and pretzels, please.)

Not knowing any better (and proposing what might already be in place somewhere (?), how about a scenario like this:

Simply send a separate, quick/secure transmission to the client containing the relevant whirlpool-like hash(es) for transmitted file verification.  Reason: The update file transmission itself will take a relatively huge amount of time to complete (and any ssl/tls can probably be cracked by certain adversaries given enough time); so all could be lost as far as payload tampering goes in the event of a determined attack if the hash is transmitted along with.

However, running a separate, short-and-secure transaction (which would only convey the few bytes of required file verification hashing) wouldn't afford nearly as much time for cracking to occur; ultimately allowing file integrity to be reliably verified before client updating finally commences.

If not already in place at some level, couldn't something like this go a long way toward improving things?

Old hat?  Half baked?


Thanks so much --

---

### Post by Dave_L on 2014-02-06
What about this technique: [http://navy.memorieshop.com/Signaling/Flags.html](http://navy.memorieshop.com/Signaling/Flags.html)

It's a bit slow, but you don't have to worry about someone a thousand miles away tampering with the data.

---

### Post by bashiergui on 2014-02-06
> If not already in place at some level, couldn't something like this go a long way toward improving things?Is it currently broken? Are hundreds or thousands of people getting owned through an attack exploiting Ubuntu updates? 

I'm all for improving things. But let's focus on the really stupid **** on the internet first, like sql injection, default passwords, failing to patch. When those three are no longer gigantic massive problems then we can improve processes that are pretty decent.

---

### Post by BuntuSeriously on 2014-02-07
> It's a bit slow, but you don't have to worry about someone a thousand miles away tampering with the data.
Well, that was certainly insightful.  Always nice to know who's in the room...

> Is it currently broken? Are hundreds or thousands of people getting owned through an attack exploiting Ubuntu updates?
Don't know.

*Nothing to see here, kids...*


Good day, all.

---

### Post by bashiergui on 2014-02-07
No, it's not happening. If you really want to improve the process then the beautiful thing about Linux is you can. My point was simply it's easier to fix a problem when you can conclusively demonstrate that the problem exists and can be exploited.

---

### Post by cariboo on 2014-02-07
The forum isn't the best place to get changes made to the way a distribution works, I'd suggest you subscribe to the ubuntu-devel-discuss mailing list, and bring your concerns to the developers. This mailing list is unmoderated, so anyone can participate.

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by thnewguy on 2014-02-08
I think encrypting the connection makes sense. Not because I think there is a weakness being exploited necessarily. (There probably is not.) But encrypting the connection between the repository mirror and the client would cost very little in the way of time/bandwidth and (potentially) makes the system slightly harder to attack. Some people may question the benefits to encrypting the download, but on the flip side, it is a small change which really doe not appear to have any down side.

---

