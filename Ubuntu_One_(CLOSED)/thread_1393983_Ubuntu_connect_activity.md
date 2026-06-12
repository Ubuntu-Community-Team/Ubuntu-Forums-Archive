---
title: "Ubuntu connect activity"
date: 2010-01-30
forum: Ubuntu One (CLOSED)
---

### Post by su-37 on 2010-01-30
When ever i used to start up a window would open asking me for my password. No problem. One day i clicked cancel and it has never come up again, when i start up the ubuntu one logo switches to updating folders for a bit and then it switches to the default but with a little red x on it. I havent been able to get it to connect. I can place files into the folder on my computer but they dont show in my ubuntu one account folder also.

If any one could help much appreciated. Also i heard, that soon we`d be able to upload folders instead of file by file is this true?

---

### Post by joshuahoover on 2010-02-01
> **su-37 said:**
> When ever i used to start up a window would open asking me for my password. No problem. One day i clicked cancel and it has never come up again, when i start up the ubuntu one logo switches to updating folders for a bit and then it switches to the default but with a little red x on it. I havent been able to get it to connect. I can place files into the folder on my computer but they dont show in my ubuntu one account folder also.

If any one could help much appreciated. Also i heard, that soon we`d be able to upload folders instead of file by file is this true?

When you were prompted for a password, was it in your web browser or an Ubuntu dialog prompt? If it was a web browser prompt and it was happening every time, you may have been affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/437165](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/437165)  

If you were prompted for a keyring password, then you likely either have auto-login turned on and will get this prompt to unlock your keyring (which Ubuntu One and other applications use to store/unlock passwords) or your keyring password is different than your Ubuntu login password. Check out this FAQ out for some help: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/839](https://answers.edge.launchpad.net/ubuntuone-client/+faq/839)

Thanks,

Joshua

---

