---
title: "Strange wireshark results?"
date: 2018-06-06
forum: Security
---

### Post by yapidumoac on 2018-06-06
[https://image.ibb.co/mROJiT/wireshark.jpg](https://image.ibb.co/mROJiT/wireshark.jpg)

---

### Post by QIII on 2018-06-06
Hello!

Rather than just posting an image, please explain in detail what your question is.

Further, please do not insert large images in your posts.  You may either use the attachment facility (the paper clip button in the toolbars) to create an expandable thumbnail (the preferred method) or add a url.  Some of our users have slow connections and data limits.  Let them decide whether they want to transfer the data.

Also, please don't ask our users to click to retrieve or open a random zip file.  Please either contain terminal output in code tags or post the plain text at a site like [Ubuntu's paste bin]("https://paste.ubuntu.com/").  While we don't believe you have ill intent, it is dangerous for our users to open such files.

Thanks

---

### Post by yapidumoac on 2018-06-06
> **QIII said:**
> Hello! Rather than just posting an image, please explain in detail what your question is.

I noticed the modem light was flashing with no apparent online activity. I then re-booted the desktop and fired up wireshark and that is the results with the desktop laying idle. What are those strange IP addresses showing up in the listing and am I compromised? The zip file is a wireshark log file. Would anyone here care to offer any advice?

---

### Post by mohicann on 2018-06-06
Honestly, I'm not sure it's possible to check if you've been compromised only with this list of connections. When your computer is idle but connected, you'll have some connections anyway. Moreover, I tend to think that a modern Linux malware won't connect when a NIDS is running, unless it is a kernel rootkit and in this case, you don't have to worry: either you will never know or you will have to reinstall without even knowing. Actually, to be more accurate, in this latter case you may try to install another -safe- kernel and see if some stuff break. But it's presumably not your case as I assume this kind of kernel rootkits are very rare, very expensive to develop and therefore used only on very high value targets.

Sorry if I've drifted a little bit from your initial question.

PS: I was talking about kernel-built-in rootkits or rootkit-build-in kernels, not about LKM.

---

### Post by yapidumoac on 2018-06-07
Thanks for the reply, over the past half-year, I have installed 'stuff', most of which I've forgotten why, maybe it's time for a fresh install.

---

