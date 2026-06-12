---
title: "An encryption question"
date: 2007-06-12
forum: Server Platforms
---

### Post by joe.turion64x2 on 2007-06-12
Hello everybody.

I have a question regarding encryption, not exactly in Linux perhaps. It is for a thesis a friend is writing.

Do you know what kind of encryption is used in the banks? Of course I am not requesting technical details, just an idea, for academic purposes. I did not consider wise to just go to a bank and ask somebody "what kind of encryption do you use?" and preferred to rely in your vast knowledge.

Alternatively, do you know any application for the AES-128 standard to protect data?

Thank you very much.
Joe.

---

### Post by turinglabs on 2007-06-12
Banks will most likely use publicly available, peer-reviewed strong encryption where they need it. While the question might seem odd, they wouldn't be compromising their security by telling you what encryption schemes they use (hopefully they are not using proprietary encryption schemes), modern encryption algorithms (AES, Twofish, CAST, etc.) are designed to be secure with full knowledge of the encryption algorithm. This essay touches on a lot of this: [http://www.schneier.com/essay-031-ft.txt](http://www.schneier.com/essay-031-ft.txt)

The free software application you can use is GNU Privacy Guard, or gpg. 'sudo apt-get install gnupg' and 'man gpg' will get you started, Also see [http://www.gnupg.org/(en)/features.html](http://www.gnupg.org/(en)/features.html) for a list of supported algorithms. For web applications, the strength of the encryption depends on the SSL certificate issued.

---

### Post by joe.turion64x2 on 2007-06-12
Thanks for the info Doug.

---

### Post by joe.turion64x2 on 2007-06-13
And how do the banks communicate among themselves? I mean, how do they know the operations made in the 'other' banks network?

Thanks.
Joe.

---

### Post by Chayak on 2007-06-13
I’d guess they use encryption passthrough hardware where only those with the same equipment and the correct keys loaded can participate.  The old systems likely use Triple-DES and the newer ones AES as they tend to follow along with Gov standards.

This is just guessing from what I know from working with military encryption systems.

---

