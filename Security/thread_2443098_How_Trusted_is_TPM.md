---
title: "How Trusted is TPM?"
date: 2020-05-11
forum: Security
---

### Post by f00dl3 on 2020-05-11
I noticed in the upgrade to Ubuntu 20.04 it includes the TPM2 Trusted Computing "Palladium controversy" enablers, and creates a "tss" user account on the system.

I have a few concerns, and I know these may be unfounded and based on old architecture, but if my memory serves me right, the "Trusted Computing" model was basically a way for the Record Industry to gain access to music pirates's computers and delete files / get subopenas. And I know that's probably a dramatic way of illustrating what it enables, but that was a concern when the whole thing initially came out - it's a hardware backdoor built into your computer from what I understand to allow law enforcement in.

This is why the "tss" user account has me a bit concerned. Is this something that, if this is what it allows - the RIAA, law enforcement, etc - to backdoor into your computer, how easy would it be for hackers to crack the keys the account uses and get into this account?

Or am I ill mis-informed on the purpose of Trusted Computing?

---

### Post by EuclideanCoffee on 2020-05-11
It's unlikely that someone can access your device remotely from TPM2. 

For Linux, this is the definitive resource on the topic, Matthew Garret.

[URL="https://mjg59.dreamwidth.org/24818.html"]https://mjg59.dreamwidth.org/24818.html


[/URL]Note

> 
[h=2]So what can I actually use a TPM for?[/h]Drive encryption is probably the best example (Bitlocker does it on Windows, and there's a LUKS-based implementation for Linux [here]("https://github.com/shpedoikal/tpm-luks"))  - while in theory you could do things like use your TPM as a factor in  two-factor authentication or tie your GPG key to it, there's not a lot  of existing infrastructure for handling all of that. For the majority of  people, the most useful feature of the TPM is probably the random  number generator. rngd has support for pulling numbers out of it and  stashing them in /dev/random, and it's probably worth doing that unless  you have an Ivy Bridge or other CPU with an RNG.

Things get more  interesting in more niche cases. Corporations can bind VPN keys to  corporate machines, making it possible to impose varying security  policies. Intel use the TPM as part of their anti-theft technology on  education-oriented devices like the Classmate. And in the cloud,  projects like [Trusted Computing Pools]("https://wiki.openstack.org/wiki/TrustedComputingPools") use remote attestation to verify that compute nodes are in a known good state before scheduling jobs on them.
[h=2]Is there a threat to freedom?[/h]At  the moment, probably not. The lack of any workable general purpose  remote attestation makes it difficult for anyone to impose TPM-based  restrictions on users, and any local code is obviously under the user's  control - got a program that wants to read the PCR state before letting  you do something? LD_PRELOAD something that gives it the desired  response, or hack it so it ignores failure. It's just far too easy to  circumvent.
[h=2]Summary?[/h]TPMs are useful for some very  domain-specific applications, drive encryption and random number  generation. The current state of technology doesn't make them useful for  practical limitations of end-user freedom.


---

