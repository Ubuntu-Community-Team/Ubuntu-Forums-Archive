---
title: "Very strange apt error here... I'm kind of worried"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-23
Weird stuff going on here. I just ran sudo apt-get update && sudo apt-get upgrade and it suddenly stopped in the middle of the upgrade. No questions asked. It just exited. No error message. Nothing in logs. Nothing.

Then I tried sudo aptitude update && sudo aptitude safe-upgrade
> Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver

It sounds a little newbie'ish, I know. And fixing it is likely easy. I'll clear the cache, probably accept one of aptitude's proposed solutions, etc. 

I'm just a little scared because it has never happened to me. And we have Beta 2 tomorrow! If it's a new problem, I really wish it had happened previously, not now...

Anyone saw anything similar? I can't find any clue / way to understand what failed, method for reproducing this behavior.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-23
> **effenberg0x0 said:**
> Weird stuff going on here. I just ran sudo apt-get update && sudo apt-get upgrade and it suddenly stopped in the middle of the upgrade. No questions asked. It just exited. No error message. Nothing in logs. Nothing.

Then I tried sudo aptitude update && sudo aptitude safe-upgrade


It sounds a little newbie'ish, I know. And fixing it is likely easy. I'll clear the cache, probably accept one of aptitude's proposed solutions, etc. 

I'm just a little scared because it has never happened to me. And we have Beta 2 tomorrow! If it's a new problem, I really wish it had happened previously, not now...

Anyone saw anything similar? I can't find any clue / way to understand what failed, method for reproducing this behavior.

Regards,
Effenberg

**Solution: **
- Removed **libtelepathy-farstream1{u} **
- Cleared the cache
- Re-ran apt update/upgrade - it went through this time
- 0 Kept Back, All Updated.[B]

What caused apt error:[/B]
- No idea.

Regards,
Effenberg

---

### Post by cariboo on 2012-03-24
I've seen that message a couple of times during this release, I usually just wait an hour or so, and the missing dependencies show up.

---

### Post by xebian on 2012-03-24
> **effenberg0x0 said:**
> And we have Beta 2 tomorrow! ....[/COLOR]

Regards,
Effenberg


Beta 2 tomorrow???  IIRIC it's on the 29th?

---

### Post by effenberg0x0 on 2012-03-24
> **xebian said:**
> Beta 2 tomorrow???  IIRIC it's on the 29th?

Yeah, you're right, sorry. I'm confusing the internal schedule/activities with the public schedule. Yesterday was Beta Freeze. Tomorrow to the 27th is a testing sprint. 29th is B2 release.

**EDIT:** I'll post a thread here tomorrow about it. It's a Step-by-Step for people that never tested a Development Release, so they can help in this last sprint. Working on it right now - which is why my mind is confused.

Regards,
EFfenberg0x0

---

### Post by ventrical on 2012-03-24
> **effenberg0x0 said:**
> Yeah, you're right, sorry. I'm confusing the internal schedule/activities with the public schedule. Yesterday was Beta Freeze. Tomorrow to the 27th is a testing sprint. 29th is B2 release.

**EDIT:** I'll post a thread here tomorrow about it. It's a Step-by-Step for people that never tested a Development Release, so they can help in this last sprint. Working on it right now - which is why my mind is confused.

Regards,
EFfenberg0x0

Nice work btw :)

[https://wiki.ubuntu.com/U+1/iso-testing](https://wiki.ubuntu.com/U+1/iso-testing)

---

### Post by effenberg0x0 on 2012-03-24
> **ventrical said:**
> Nice work btw :)

[https://wiki.ubuntu.com/U+1/iso-testing](https://wiki.ubuntu.com/U+1/iso-testing)

Thanks :) It's totally under development thou. Also, it's just a temporary resource while we invite people to test. After the sprint, I'll leave it to you to decide if/where/how to use it in the Wiki :)

Regards,
Effenberg

---

### Post by dino99 on 2012-03-24
> **effenberg0x0 said:**
> **Solution: **
- Removed **libtelepathy-farstream1{u} **
- Cleared the cache
- Re-ran apt update/upgrade - it went through this time
- 0 Kept Back, All Updated.[B]

What caused apt error:[/B]
- No idea.

Regards,
Effenberg

my 2 cents:
- mixing apt-get & aptitude on the same system  is not recommended: they both built their index differently, not sure they are able to fully communicate all the time.
- possible xapian borked index

---

