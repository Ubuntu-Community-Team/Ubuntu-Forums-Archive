---
title: "Buffer overflow safeguards"
date: 2011-02-04
forum: Security
---

### Post by ab1sh3k on 2011-02-04
Hi all,

 I am a student studying information security and as a part of my systems security course I am supposed to write a return to libc attack code and also find its prevention mechanisms.

 I have come up with a return to libc exploit, however I am still getting "Segmentation fault" error when I try to run it. I have set the kernel.randomize_va_space to zero and I am compiling the code in C with a -fno-stack-protector.

 I am running the code on Ubuntu 10.10. I am wondering if I have to turn off some other buffer overflow or return to libc safeguards to complete this assignment.

 Please note that this is purely for study purpose and I am not doing any real time hacking or exploitation. I know its purely unethical to do it.

Thanks,
Abi

---

### Post by psusi on 2011-02-04
Probably the non executable stack.  I'm not sure how to turn it off.

---

### Post by ab1sh3k on 2011-02-04
As per some previous postings the -fno-stack-protector switches off the non-executable code..if I am not wrong...

---

