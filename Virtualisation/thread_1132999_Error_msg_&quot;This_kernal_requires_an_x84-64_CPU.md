---
title: "Error msg: &quot;This kernal requires an x84-64 CPU, but only detected an i686 CPU."
date: 2009-04-22
forum: Virtualisation
---

### Post by Quinn70 on 2009-04-22
Unable to boot - please use a kernal appropriate for your CPU."
 
Hi All,
 
I know I'm not the first to ask this question, but I haven't been able to find a solution yet despite searching this forum and google.
 
In this thread, the OP reported the same issue and indicated it was solved, though I don't know how:
 
[http://ubuntuforums.org/showthread.php?t=824813&highlight=64-bit](http://ubuntuforums.org/showthread.php?t=824813&highlight=64-bit)
 
In his screenshot, replace i1586 with i686 and otherwise the error msg is identical to mine. 
 
Here are the other details:
 
CPU: [FONT=Arial]Intel Core 2 Duo Processor [/FONT]
[FONT=Arial]Host OS: Vista Home Premium (64-bit)[/FONT]
[FONT=Arial]Guest OS: Hardy (64-bit)[/FONT]
[FONT=Arial]VM Software: VMware Player[/FONT]
 
Any ideas on a possible solution?

---

### Post by Nostalos on 2009-04-22
Not sure about VMware, but to load 64bit OS as a Vbox guest you have to enable Virtualization in the BIOS.

---

### Post by Quinn70 on 2009-04-23
Hi Nostalos,
 
Thanks for the reply. I did some more searching and according to this technical article I found on VMware's site, paravirtualization (VMI) is not compatible with 64-bit guest OS's:
 
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1008170&sliceId=1&docTypeID=DT_KB_1_1&dialogID=15588566&stateId=1%200%2015590666](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1008170&sliceId=1&docTypeID=DT_KB_1_1&dialogID=15588566&stateId=1%200%2015590666)
 
My plan now is to download the 32-bit Hardy ISO and attempt to run that instead. I'll post the results.

---

### Post by Quinn70 on 2009-04-23
Okay, installing the 32-bit version via VMware solved the problem and I'm now running Ubuntu.  

Woo-hoo! :D

---

