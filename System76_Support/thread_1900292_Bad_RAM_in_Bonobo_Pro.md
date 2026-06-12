---
title: "Bad RAM in Bonobo Pro"
date: 2011-12-26
forum: System76 Support
---

### Post by cookiecaper on 2011-12-26
I have had a pretty bad experience with my laptop. I have been able to wait to figure this out since my job has shifted to require less laptop use, but I believe I have bad memory in this laptop. I get frequent segmentation faults in everything and md5sums often come back invalid. Things are sometimes usable, but it goes through fits where I can barely keep anything open for more than a couple of minutes.

memtester fails profusely and immediately. I have had some serious lockups on here that have totally damaged everything. Files transferred from NFS are often corrupted and break things. Any suggestions here? I have logs from dmesg and memtester I can attach if that will be helpful.

---

### Post by 2F4U on 2011-12-26
When you say memtest do you mean the memtest from the liveCD? If that application says your RAM is bad, then this is usually true. I am not sure what recommendation you expect since bad RAM cannot be repaired and you cannot work around it, you have to replace the defect chips.

---

### Post by cookiecaper on 2011-12-26
I said "memtester", which is a Linux userspace memory test program.

I don't really expect a recommendation other than a fast tracked RMA, I guess. This will be the second time I've had to RMA my laptop. Really disappointed in System76.

---

### Post by jbelmonte on 2011-12-27
How long have you owned your Bonobo? 

Have you tried running Ubuntu from a Live-CD? If so, do you see the same problems?

Can you try running the memory test from the Live-CD? Do you still see memory errors?

Could you be having a thermal problem? Have you tried blowing out the vents with compressed air?

Have you tried re-seating your memory chips?

I do not work for System76, but these are the steps I would take to make sure of the source of the problem.

Good luck. I hope this gets rectified quickly for you.

---

### Post by cookiecaper on 2011-12-27
>How long have you owned your Bonobo?

Received in July

>Have you tried running Ubuntu from a Live-CD? If so, do you see the same problems?

I didn't have these problems when I used a Live CD, but I haven't used one for very long.

>Can you try running the memory test from the Live-CD? Do you still see memory errors?

Yes, profuse and immediate, just as I get with memtester.

>Could you be having a thermal problem? Have you tried blowing out the vents with compressed air?

Highly doubtful, machine remains cool and there is no visible dust accumulation. sensors reports normal temp ranges. (35c-40c)

>Have you tried re-seating your memory chips?
No

>Good luck. I hope this gets rectified quickly for you. 
Thanks.

---

