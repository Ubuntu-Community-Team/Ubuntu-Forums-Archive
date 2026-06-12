---
title: "Overwriting eip/rip on Ubuntu 12.04"
date: 2014-01-09
forum: Security
---

### Post by ad17yam on 2014-01-09
Hi Guys, 

I am a computer security student and need to exploit a basic buffer overflow vulnerability. I have a program that uses an unchecked strcpy. I am getting a segmentation fault with an input of 24, my buffer size is 10, but when I analyse the registers, I see that the eip doesn't get overwritten. I am not sure how I can overwrite it. My compile command is 

```
gcc -m32 -ggdb -fno-stack-protector -z execstack -o overflow overflow.c
```
I have tried this for both 32 and 64bit, but to no avail. Are there some other flags that I need to enable/disable.  I am doing this on a 64bit Ubuntu 12.04 system.

I was able to find this link to [https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)  and the only thing that I think I am missing is the Pointer Obfuscation. Is there a way to disable that?
Any help will be greatly appreciated.

Thanks.

---

### Post by Hungry Man on 2014-01-12
Source would be nice as well as gdb/ db output. That said, make sure you've disable ASLR.

---

