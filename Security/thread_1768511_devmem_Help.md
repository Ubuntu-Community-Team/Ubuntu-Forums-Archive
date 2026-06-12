---
title: "/dev/mem Help"
date: 2011-05-26
forum: Security
---

### Post by vishal00100 on 2011-05-26
So, I need to take a memory dump of my Ubuntu machine. I tried using dd, but it turns out that for kernel 2.6 (mine is 2.6.38-8) /dev/mem is disabled. I have literally tried everything that I could find on the internet. So if someone could give me clear instructions that would be great. I have tried changing the Kconfig.debug ad setting STRICT_DEVMEM=y. That did not work. So I added the lines config NONPROMISC_DEVMEM
      bool "Disable Promiscuous dev/mem"
      default n
  ---help---....  
        If in doubt, say Y.
That also did work. 
I also looked at some solutions which said that changes need to be made to other (arch/x86/mm/init_32.c, init_64.c, drivers/char/mem.c). But I do not see those files. 

I don't know if I'm doing anything wrong. 
Can someone please let me know if there's anything else I need to do? Also, should I rebuild the kernel once I make changes to that file?

---

