---
title: "modify kernel (module) without recompiling everything"
date: 2015-05-07
forum: Server Platforms
---

### Post by bartgrefte on 2015-05-07
I was considering writing a tl;dr, but I think the title of this topic covers that :)
Now for the longer version:

With a bit of help I managed to set up a 5GHz access point in Ubuntu Server 14.10 using a QCA9880 based wifi card that is using the ath10k driver and the Candelatech firmware-file. Even though this works, there's a little problem: hostapd can't use any of the channels that involve DFS, I'm stuck with channels 36, 40, 44 and 48. 

I've been told that this problem is caused by the lack of **CONFIG_ATH10K_DFS_CERTIFIED=y** and **CONFIG_CFG80211_CERTIFICATION_ONUS=y** in the kernel config file when the kernel for Ubuntu Server was compiled and after having a look in the actual config file in /boot, those options are indeed missing.

So I could recompile the entire kernel, using the existing configuration file where I will be adding those 2 options. But, since the ath10k driver seems to be a separate module and not integrated in the kernel, I'm hoping there's a way I can add those 2 options without recompiling everything. Although I am not sure if the ath10k module will be the only module that will be modified, looking at the 2nd option I mean.

Is it possible to add these 2 specific options without recompiling everything and if yes, how?

---

