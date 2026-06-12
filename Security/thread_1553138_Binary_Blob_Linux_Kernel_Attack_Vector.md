---
title: "Binary Blob Linux Kernel Attack Vector"
date: 2010-08-14
forum: Security
---

### Post by earthpigg on 2010-08-14
Assume for a moment that there are forces who would profit immensely from compromising Linux. NYSE, Google, Amazon.com, etc, are some pretty high-value targets.

Assume employees of corporations submitting binary blobs to Linus are corruptible. Either financially, or because those forces know secrets about their personal lives.

So, an employee sending binary blob patches to Linus gets turned. Perhaps, a few of them do. The binary blob is committed to the kernel.

What assurances do we have that the 1s and 0s do not contain malicious code?

---

### Post by bodhi.zazen on 2010-08-14
If your kernel is closed source, you have no protection at all.

If the kernel is open source, we have brad :

[http://ubuntuforums.org/showthread.php?t=1550295](http://ubuntuforums.org/showthread.php?t=1550295)

In other works, many people who know more about kernels then I presume you may watching the code and submitting security flaws.

If you feel you can not trust them, you would need to examine the code yourself.

---

### Post by earthpigg on 2010-08-14
ooo, interesting reading. thank you.

---

### Post by FuturePilot on 2010-08-14
I don't think binary blobs are even allowed to go into the kernel.

---

### Post by Bachstelze on 2010-08-14
Not into the vanilla kernel, but a lot of distributions ship a blobbed kernel. And even without a blob, the Debian OpenSSL fiasco demonstrated that a huge security flaw can very well go unnoticed for years even in perfectly open source code.

---

### Post by earthpigg on 2010-08-14
the 27th post of [this thread]("http://ubuntuforums.org/showthread.php?t=1550295") addressed my question very thoroughly, for anyone coming across this.

Edit: bodhizazen - I fixed the link for you, hope you do not mind :twisted:

---

### Post by rookcifer on 2010-08-14
I wouldn't just be worried about binary blobs.  There are numerous other vectors which need to be checked out.  One of the more ingenious ones made famous by Ken Thompson is immune to code review since the backdoor cannot be seen in the code.  I covered this is post #31 of [this thread.]("http://ubuntuforums.org/showthread.php?t=1550295&page=4")

---

