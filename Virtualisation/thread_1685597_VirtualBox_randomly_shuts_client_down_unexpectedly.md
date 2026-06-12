---
title: "VirtualBox randomly shuts client down unexpectedly after upgraded to 4.0.2"
date: 2011-02-10
forum: Virtualisation
---

### Post by excetara2 on 2011-02-10
Posted this in the general help but never realized there was a virtualization thread so I'll put a link here and recap:

I run Ubuntu Lucid and upgraded to 4.0.2 virtual box recently. Now, the machine is running guest Windows 7 64 bit and randomly shuts the entire virtual box down with no warning. I tried re-installing with the same issue occurring and prefer this version as Intel HD Audio works so would rather not revert back. Using different kernels doesn't have any effect.

Another user that also did the same that had been using virtualbox for years and recently upgraded to 4.0.2 has the same issue. He is running Windows 7 32 bit guest. He thinks it was a feature added in 4.0 from looking at the log files on VirtualBox. I can't imagine this is a desired option.

Any help would be appreciated. Also, I can file a bug report if necessary but not sure where if it's thought to be a bug.

---

### Post by Hedgehog1 on 2011-02-10
> **excetara2 said:**
> 
I run Ubuntu Lucid and upgraded to 4.0.2 virtual box recently. Now, the machine is running guest Windows 7 64 bit and randomly shuts the entire virtual box down with no warning. I tried re-installing with the same issue occurring and prefer this version as Intel HD Audio works so would rather not revert back. Using different kernels doesn't have any effect.


A few questions first - Is your Lucid install 64 bit (I assume so, but I have only just jumped from VMware to Vbox; VMware is funny about x64 guest in x32 host OS).

Also, have you installed the guest additions in your Win7 Guest Vbox?

:KS

---

### Post by whyarewehere69 on 2011-02-13
I've been having what I think is the same issue. Running VirtualBox with a windows 7 32-bit client. I have been noticing, consistently, that maybe after a 1/2 hour of the client window being minimized and not being used it just shuts down with no apparent warning. 
I believe the problem may be as simple as this; I noticed in the power settings in the windows client were set to sleep after 30 minutes idle time, plugged in. I have since set this to "never" sleep and now after 1 hour of the guest being minimized, it still has not unexpectedly shut down...Soooo, I will respond to this if it turns out to not work.

---

### Post by whyarewehere69 on 2011-02-13
So just a follow up to my last post. After 3 1/2 hours, Windows still has not shut down unexpectedly. This was NEVER the case it always **** down after a 1/2 hour. I'm concluding it has something to do with how the virtualbox handles a sleep process from the windows client, or the other way around. To me it is a bug, just not sure who's. I can guess though :P
Anyway, for me this work around works fine. Hope this helps!

---

