---
title: "viruses"
date: 2007-07-05
forum: Windows
---

### Post by Sunforge on 2007-07-05
We recently got a call from a third party that we work with. They had a PC which was having "some problems connecting to the internet". 

I asked them if they had a virus scanner (no), anti-spyware (no), firewall (they did and they thought that it did virus scanning). Hmmm....interesting. I asked that they ship the machine to us.

We got the machine to base and (without connecting it to our network) loaded on AVG and performed a scan. AVG died. So we booted into safe mode and did the same thing. AVG struggled to life and after a few hours reported 1,800 or so infected documents and hundreds of viruses. We cleaned the worst out, ran up an anti-spyware scanner rinsed and repeated.

We eventually got the machine clean enough that it would boot normally but to be honest the machine wasn't *that* usable any more, so we formatted it with an industrial strength disk eraser (just in case anything really nasty was in the boot sector) and put on a clean OS.

So - apart from a frightening number of virus infested files, we cleaned the machine and it's on it's way back to the third party. What did and still does worry me is files resident on a hard drive after formatting. I've heard that it is technically possible, so to my questions:

Has anyone come across any evidence of this?
Are there any on-line guides worth looking at?
Has someone experienced a virus or malware reappearing after a format?

I guess I'm trying to check my own paranoia here to see if I was reasonable (shutting the gate after the horse has bolted).

---

### Post by lisati on 2007-07-05
And I thought I was careless the other week (opening an attachment from someone I didn't know while I had a different anti-virus thingy to what I'd normally use: result: start-up problems, and about 2 or 3 infected files)

Ouch!

---

### Post by tribaal on 2007-07-05
Sounds pretty unprobable to me... One you format the hard drive, you should be all set.

Basic question, but: you did install antivirus software *before* connecting your PC to the internet, didn't you? Unprotected windows PC have an average time to infection of around 10 minutes... but since it's an average, it could be that you're just out of luck and got infected real fast?

- trib'

---

### Post by Sunforge on 2007-07-05
It was a six pack of ouch for the third party that's for sure.

In this case it was a machine run and maintained by a third party that we have no control over. Without giving away too much this company runs a mix of Mac and PC and were convinced that Macs didn't suffer from viruses and that this "halo effect" spread to their PCs. I found that to be an odd point of view but one that I've come across before and I'm sure will come across again.

---

### Post by lisati on 2007-07-05
> **tribaal said:**
> Sounds pretty unprobable to me... One you format the hard drive, you should be all set.

Basic question, but: you did install antivirus software *before* connecting your PC to the internet, didn't you? Unprotected windows PC have an average time to infection of around 10 minutes... but since it's an average, it could be that you're just out of luck and got infected real fast?

- trib'

The problems I had was the result of a combination of carelessness and checking out a different anti-virus product (one I'd never heard of until stumbling on it) to what I'd normally use.

---

### Post by az on 2007-07-05
> **Sunforge said:**
> .... AVG struggled to life and after a few hours reported 1,800 or so infected documents and hundreds of viruses. We cleaned the worst out, ran up an anti-spyware scanner rinsed and repeated.

We eventually got the machine clean enough that it would boot normally but to be honest the machine wasn't *that* usable any more, so we formatted it with an industrial strength disk eraser (just in case anything really nasty was in the boot sector) and put on a clean OS.
....

I haven't used windows since 1999.  How do people live like that?  Why would anyone continue to use an operating system where that can happen?  What's the matter with people?

> **Sunforge said:**
> 
What did and still does worry me is files resident on a hard drive after formatting. I've heard that it is technically possible, so to my questions:

Has anyone come across any evidence of this?
Are there any on-line guides worth looking at?
Has someone experienced a virus or malware reappearing after a format?

I guess I'm trying to check my own paranoia here to see if I was reasonable (shutting the gate after the horse has bolted).

Files are still present on your disk after you format: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

However, in order to get to them, you would need to work at it.   They don't just *pop up* out of the blue.  You would theoretically need to get infected with abother vulnerability which would carve out the latent files/data from your hard drive.  Very unlikely.

---

### Post by Sunforge on 2007-07-05
How can people live like that? More easily than I thought. 

I can remember a conversation with an epidemiologist who mentioned "herd immunity" which is the concept that a population of people can become resisant to a disease because the majority are immunised against that disease therefore protecting the minority who aren't.

To a great extent viruses would be a lot less problematic if everyone (including us Linux users) took steps to prevent their presence, either on our own machines or from being passed on without our knowledge because our machines weren't vulnerable to them. 

If every machine in the world was completely secure or ran a virus scanner then perhaps we wouldn't have these problems as we'd have "herd immunity" but we don't.

Interesting point about data recovery. I'm going to give that a good read once I've posted this.

---

### Post by smoker on 2007-07-05
we often use this if a customer wants assurance that absolutely no data can be recovered from a hard drive:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

also, most hard drive manufacturers offer an app on their support site that can give a hard drive the equivalent of what used to be called a 'low level format'.

---

### Post by az on 2007-07-05
> **Sunforge said:**
> 
To a great extent viruses would be a lot less problematic if everyone (including us Linux users) took steps to prevent their presence, either on our own machines or from being passed on without our knowledge because our machines weren't vulnerable to them. 

That's a joke.  What about actually fixing the problem?  What about shutting down the vulnerability instead of scanning for things that can exploit it?

> **Sunforge said:**
> 
If every machine in the world was completely secure or ran a virus scanner then perhaps we wouldn't have these problems as we'd have "herd immunity" but we don't.


I will not waste my CPU cycles for the shortcomings of some other (proprietary) OS!  Human bodies fight microorganisms using antibodies that they make themselves.  Every single copy of windows XP is incapable of generating its own antibodies - it's the responsibility of the owner's of the software to do that (it seems they need to buy them).  

It is absolutely not my responsibility, nor my problem.

---

### Post by kamaboko on 2007-07-05
> **az said:**
> I haven't used windows since 1999.  How do people live like that?  Why would anyone continue to use an operating system where that can happen?  What's the matter with people?



This is just a stab in the dark (not really), but it's very likely that the software they need is not available on any other platform.

---

### Post by Sunforge on 2007-07-06
I'd like to be able to confirm or deny your guess Kamboko but the machine was so full of viruses that we never quite got to the bottom of what software was actually running on the machine due to the number of virus damaged files.

Taught me a lesson though - a machine can run with thousands of infected files for some considerable time before it becomes inconvenient.

---

### Post by Lolicon on 2007-07-06
I use NOD32 on my windows, and I NEVER got a virus using it. It takes little system resources too.

---

### Post by dca on 2007-07-06
I haven't had any problems running PrevX...

---

### Post by Jimmy_r on 2007-07-06
> **tribaal said:**
> Unprotected windows PC have an average time to infection of around 10 minutes

One time when I installed xp with sp1, and forgot to activate the firewall before connecting to the internet, it just took maybe 3 to 5 minutes before i got teh popups n shutdowns... not cool :(

Anyway, I must say I have used xpsp2 with the built-in firewall as only defense(no antivirus or anything) for several weeks(as long as a windows installation used to last before I grew tired of it for a few months) without catching any viruses(at least as i know about).


To the op: I think the risk of viruses coming back to life after a format is slim to nil.
What I would be concerned about, with that amount of infection, is the risk of the BIOS getting infected with something.

---

### Post by timcredible on 2007-07-06
to answer one of the original questions - no, you can't get a virus from a reformatted drive.  what you may have heard is that a format doesn't erase all the bits off the drive, which is true, but the virus files are gone because there's no pointer to them in the file table.

---

### Post by smoker on 2007-07-06
a virus cannot spring back to life unaided from a formatted drive, but there are situations when it could happen, either accidently or deliberately. there are recovery appz available that can recover a file by examining the contents which are still there, rather than looking for deleted markers, which a format should have voided. it is highly unlikely though someone would restore a virus in this way, though it could be possible.

it is also important to check any backups made for infection before restoring the backup to a newly formatted drive, you may also be restoring a virus this way.

---

### Post by lisati on 2007-07-06
> **smoker said:**
> a virus cannot spring back to life unaided from a formatted drive, but there are situations when it could happen, either accidently or deliberately. there are recovery appz available that can recover a file by examining the contents which are still there, rather than looking for deleted markers, which a format should have voided. it is highly unlikely though someone would restore a virus in this way, though it could be possible.

it is also important to check any backups made for infection before restoring the backup to a newly formatted drive, you may also be restoring a virus this way.

Another way is if the virus makes its way to a backup undetected. Nearly happened to me a few weeks back, but I extra vigilance after cleaning up the aftermath of carelessness got it in time.

---

### Post by Sunforge on 2007-07-07
Thanks for the advice. I think that a decent formatting tool is in order for the errant windows machines.

---

