---
title: "HyperV - Ubuntu 10.10 tips"
date: 2011-02-22
forum: Virtualisation
---

### Post by jimmydorry on 2011-02-22
Hi,
Just writing to see if anyone has any pointers for me regarding running Ubuntu 10.10 under the windows server 2008 R2 Hyper Visor... or just HyperV R2 as it is reffered to. My issue pertains to the addition of synthetic network drivers to a virtual OS.

I do not know what information you require to help me, so please tell me and I will be more than willing to oblige.

Here is what I have done so far.

TBH, so far it has been an uphill battle all the way. Ubuntu refused to install initially, it kept freezing during install. On the fourth attempt, it just installed properly... like magic (exact same settings for all 4 attempts).

Once in, there were 2 main priorities, networking & iSCSI adapter support. Networking was taken care of automatically (In the hypervisor settings, I removed the synthetic network adapter, and added a legacy adapter) ... albeit that its performance was so sub-par that it could only ever be a temporary solution.

The second priority, being iSCSI support, required the installation of the LIC 2.1 drivers (Linux Integration Components). After a lot of research and a bit of trial and error, I found out that the LIC components were now distributed as part of the distribution (in a compiled format compatible with Ubuntu). It didn't help that documentation is scarce for this, and most guides that claimed to install these components were only 3steps long and completely irelevant.

After making LIC drivers work on boot, I could now see any physical harddrives attached to machine.

The only major issue left, was finding a more ideal solution for the networking, since the theoretical max through-put of the legacy network adapter is 100mbit... but I never saw more than 900KB/s pass through.

The only solution is to re-add the synthetic network driver... but everytime I tried... it borked my installation, either causing it to not boot, or not have any network connectivity.


Any tips pertaining to attaching a synthetic network driver would be appreciated. Please assume I am a complete linux nub (which isn't too far off the truth here), and phrase your questions and solutions accordingly. I would hate to waste both my time and yours trying to comprehend what you are writing.

cheers

---

### Post by TivA on 2011-02-22
Hi man,
I have ubuntu 10.10.
I have just bought a music album and I have copied it to my computer but it didn't have the track names.
I was easily able to edit that.
But i can't edit the other information like album name, Year and so on.
I tried to change all the permissions so I could edit, as soon as I select "Read and write" it goes straight back to "read-only".
Please any help will be appreciated.
Thanks
TivA

---

### Post by jimmydorry on 2011-02-22
> **TivA said:**
> Hi man,
I have ubuntu 10.10.
I have just bought a music album and I have copied it to my computer but it didn't have the track names.
I was easily able to edit that.
But i can't edit the other information like album name, Year and so on.
I tried to change all the permissions so I could edit, as soon as I select "Read and write" it goes straight back to "read-only".
Please any help will be appreciated.
Thanks
TivA

I think you have the wrong thread/section.

If you want to change the permissions of files though try:

# sudo chown --help

and I think the command will look something like:

# sudo chown -r username usergroup /home/trolol/music

where username is your username, usergroup is your usergroup, and trolol is your username (assuming that you put your music there)

---

### Post by TivA on 2011-02-22
Sorry man, I couldn't find the button to start the post- I was in a hurry

---

