---
title: "HyperV - Ubuntu 10.10 can't boot with Synthetic Network Adapter"
date: 2011-02-24
forum: Virtualisation
---

### Post by jimmydorry on 2011-02-24
FOR MODS: Sorry for new thread, but last thread had a vague thread title, and I couldn't see how to change it. Not to mention that it got hijacked.

Hi,
Just writing to see if anyone has any pointers for me regarding running  Ubuntu 10.10 under the windows server 2008 R2 Hyper Visor... or just  HyperV R2 as it is reffered to. My issue pertains to the addition of  synthetic network drivers to a virtual OS.

I do not know what information you require to help me, so please tell me and I will be more than willing to oblige.

Here is what I have done so far.

TBH, so far it has been an uphill battle all the way. Ubuntu refused to  install initially, it kept freezing during install. On the fourth  attempt, it just installed properly... like magic (exact same settings  for all 4 attempts).

Once in, there were 2 main priorities, networking & iSCSI adapter  support. Networking was taken care of automatically (In the hypervisor  settings, I removed the synthetic network adapter, and added a legacy  adapter) ... albeit that its performance was so sub-par that it could  only ever be a temporary solution.

The second priority, being iSCSI support, required the installation of  the LIC 2.1 drivers (Linux Integration Components). After a lot of  research and a bit of trial and error, I found out that the LIC  components were now distributed as part of the distribution (in a  compiled format compatible with Ubuntu). It didn't help that  documentation is scarce for this, and most guides that claimed to  install these components were only 3steps long and completely irelevant.

After making LIC drivers work on boot, I could now see any physical harddrives attached to machine.

The only major issue left, was finding a more ideal solution for the  networking, since the theoretical max through-put of the legacy network  adapter is 100mbit... but I never saw more than 900KB/s pass through.

[B]The only solution is to re-add the synthetic network driver... but  everytime I tried... it borked my installation, either causing it to not  boot, not have any network connectivity, or freeze regularly.
[/B] 

Any tips pertaining to attaching a synthetic network driver would be  appreciated. Please assume I am a complete linux nub (which isn't too  far off the truth here), and phrase your questions and solutions  accordingly. I would hate to waste both my time and yours trying to  comprehend what you are writing.

cheers

---

