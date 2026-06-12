---
title: "SPARCstation5 Instalation"
date: 2006-08-29
forum: Sun Sparc Users
---

### Post by Wale on 2006-08-29
As the title suggest I'm attempting to install ubuntu on an old sparcstation 5. I'm not entirely sure it is 

a: possible
b: the machine is up to date

I've been starting with a cd install. Heres what i can do:

1: boot from the cd
2: silo runs
3: Get to the first what i think to be option menu- presenting an " ENTER - Boot Install" or " type "recover" to boot recover"

Here is what I can't do:
1 Get past that menu! 
2: loose keyboard control

So, this is my first sun machine. I really do not know what I'm doing. From here out I have been trudgeing my way through this. I appreciate any help, huge thank you in advance!

---

### Post by clarsen on 2006-08-30
I'm not sure how Ubuntu works but let me start by discussing Solaris and then trying address the problem you describe.

When Solaris is installed both 32-bit and 64-bit versions of the kernel are installed.  When a 32-bit processor boots, such as the microSPARC II processor in your SPARCstation 5, it is only capable of using the 32-bit kernel.  64-bit processors (UltraSPARC) use the 64-bit kernel by default but can be configured to use the 32-bit kernel.

In my experience with Linux, which consists mostly of RHEL on Intel/AMD, AFAIK, installing 32-bit kernels is mutually exclusive with installing 64-bit kernels.  I'm guessing that Dapper Drake only has a 64-bit kernel.  From the download page:  "For Sun UltraSPARC computers ....".

I repeat this in only a guess on my part.

Chris

---

