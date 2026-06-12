---
title: "Creating a personal server"
date: 2013-08-05
forum: Server Platforms
---

### Post by beenny on 2013-08-05
Hello,

I work as a statistician where I analyze large data sets - not "big data" in Hadoop standards but datasets that my be >10gb. I will also run computational analyses that I will write in a parallel way - either true parallel or embarrassingly parallel. I do most of my work in R with the occasional shell scripts.

Right now I do most of my work on my desktop which has 16gb and RAM and 8 core (i7 chip). It's a Dell machine that wiped and put Ubuntu on. 90% of the time it works well but when I try accessing the larger datasets things get swamped. I recently got some grant money where I can buy whatever I need. What I'm thinking is getting a server quality computer and using it as my personal computer. I've been looking at the Zareason servers and was thinking that probably covers what I need. However I was curious to get some thoughts from others. Here are a few questions:

(1) How much memory is overkill? Money isn't a concern but I don't want to be obscene. ZaReason goes up to 256gb. Is that crazy?
(2) What kind of processor? The best processor for ZaReason, System 76 & Dell is the Intel Xeon E5-2690 2.90GHz. That is an Sandy Bridge, right? Is there a reason I would want an Ivy Bridge or even Halswell? The goal is for this to last me awhile so I don't want to be kicking myself that things are out of date
(3) How many processors? I've seen configurations with multiple processors - how does that differ from multiple cores? How does that differ from virtual cores?
(4) What kind of RAID controller? I'm assuming I want mirrored so that I have redundancy. That basically means I need to get double the hard drive space, right?

Most important:

I want this to be easy. I don't want to become a server admin or anything like that. Will this work like my regular ubuntu desktops and laptops? Also if I get a tower system can this sit comfortably under my desk or will I want this in a server room?

Thoughts on this would be great. Also any thoughts on where to buy this from appreciated. I'm partial to ZaReason b/c I'm from the Bay Area but am open to whomever will give the best product and the best service...

Thanks,

bg

---

### Post by sandyd on 2013-08-05
> **beenny said:**
> Hello,

I work as a statistician where I analyze large data sets - not "big data" in Hadoop standards but datasets that my be >10gb. I will also run computational analyses that I will write in a parallel way - either true parallel or embarrassingly parallel. I do most of my work in R with the occasional shell scripts.

Right now I do most of my work on my desktop which has 16gb and RAM and 8 core (i7 chip). It's a Dell machine that wiped and put Ubuntu on. 90% of the time it works well but when I try accessing the larger datasets things get swamped. I recently got some grant money where I can buy whatever I need. What I'm thinking is getting a server quality computer and using it as my personal computer. I've been looking at the Zareason servers and was thinking that probably covers what I need. However I was curious to get some thoughts from others. Here are a few questions:

(1) How much memory is overkill? Money isn't a concern but I don't want to be obscene. ZaReason goes up to 256gb. Is that crazy?
(2) What kind of processor? The best processor for ZaReason, System 76 & Dell is the Intel Xeon E5-2690 2.90GHz. That is an Sandy Bridge, right? Is there a reason I would want an Ivy Bridge or even Halswell? The goal is for this to last me awhile so I don't want to be kicking myself that things are out of date
(3) How many processors? I've seen configurations with multiple processors - how does that differ from multiple cores? How does that differ from virtual cores?
(4) What kind of RAID controller? I'm assuming I want mirrored so that I have redundancy. That basically means I need to get double the hard drive space, right?

Most important:

I want this to be easy. I don't want to become a server admin or anything like that. Will this work like my regular ubuntu desktops and laptops? Also if I get a tower system can this sit comfortably under my desk or will I want this in a server room?

Thoughts on this would be great. Also any thoughts on where to buy this from appreciated. I'm partial to ZaReason b/c I'm from the Bay Area but am open to whomever will give the best product and the best service...

Thanks,

bg
1. If your having some trouble at 16, I would say 32GB. Check how they are filling the slots so that you can upgrade later on without buying a new set of ram. It depends on your choice, but if the RAM uses ECC, its slower, but has error correction.
2. I have an E5 currently, and even with the most video-intensive videos ive rendered with the CPU, theyve done fine.
3. Virtual Cores = Hyper Threading - generally makes your computer perform a tad faster by making it seem like one processor is two...
4. If its heavy disk io, your better off with  HW raid controller in RAID10. Software RAID is slower.
A few caveats about HW raid controllers:
- If it fails, you have to get an identical one
- If your raid controller decides to go nuts, it can vaporize all your disks
- Needs to be supported by Linux (If you want out of box support, I reccomend LSI/Adaptec, the ones by RocketRaid need a custom DKMS setup....)

---

