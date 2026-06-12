---
title: "Ubuntu Server on Apple XServe with software Raid1??"
date: 2008-01-21
forum: Server Platforms
---

### Post by yellowtip on 2008-01-21
Hi guys,

I have a client with the latest and greatest Apple XServe (well...almost). He originally bought the XServe to host our commercial php app on Leopard Server. Problem is that the folks at Zend refuse to release a 64 bit version of the Zend Optimizer. Solution: remove Leopard Server OS and install Ubuntu...

The specs of the server are as follows:
- Processors: 2x Dual Core Intel Xeon @ 2Ghz (4 Cores)
- Memory: 2GB
- Hard Drives: 3x 73GB SAS ADM @ 15,000-rpm
- *No* hardware RAID Card

So I'd like to install Ubuntu LAMP Server onto this machines and configure it as a RAID 1 (mirroring) server.

Before I proceed, I have a few questions I would like to ask:

1.) Software Raid Support in Ubuntu
I've been trying to research Ubuntu's Raid support on this forum, but the articles immediately delve into complex Raid configurations and complex partitioning schemes. I just want a simple Raid1 Config. I'm no Raid expert, so I might be missing something here. Question: could someone point me to a simple set of instructions on how to get this Raid setup?

2.) What version of Ubuntu LAMP Server?
So far I've installed and have been managing 6 Ubuntu LAMP Servers at version 6.0.6LTS. Should I consider one of the later releases for better/easier Raid Support?

3.) Hardware/driver issues?
Has anybody out there tried installing Ubuntu Server onto an Apple XServe with Intel processors? I'm assuming it should be straight forward, but still, if anybody could share their experience I would be most grateful.

4.) Do I need to enable/install any special kernel to support the 4 cores? Or will Ubuntu Server recognize and use them by default? In other words, does Ubuntu Server come with the SMP kernel or should it be installed afterwards?

5.) Anything else?
Did I miss anything? Anything else I should be aware of?

Thanks in advance!

---

### Post by smileypaul on 2008-01-22
Yellowtip: im not expert, but i like to try and help wherever I can.. usually answers can be found through discussion, and not always just looking to the "pro's"... so here goes.

1. I only have experience with hardware raid cards, as i feel they are better in a server environment.. but, that being said.. you've made your choice.. a quick google search for "ubuntu raid1" turned up this link : [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html) .. hopefully it helps.

2. Im in the same sticky situation, my hardware raid card was only supported in the newer kernels, so i had to go with 7.04 or newer.. ideally, you want to go with an LTS...  Im not sure how easy the upgrade will be from 7.10 Server to 8.04 LTS server .. im sure either 6.06LTS or one of the later releases will have similar raid options.

3. I havent tried .. but, im sure its fine.. should probably ask this question over in the apple section of this site. good luck.

4. My server has the Intel Q6600.. completely overkill for what it does, but, the price was right at the time. No additional options were required for it to recognize all four.. I am using server 7.10.

5. If its not completely critical that it be up and running tomorrow, i sugges tyou dive right in and swim to the top.. you should be fine, theres many people here that can help.

Paul.

---

### Post by fjgaude on 2008-01-22
The key for me would be if 6.04 handles mdadm, the modern tool that Ubuntu uses to create and manage software raid?

If so, then the mdadm man pages shows how to create any raid array. This link is easier to read and has search than the man pages:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

raid1 should be easy to use and setup... I use raid5 with a hot spare that has worked for months without issue.

Good luck.

---

