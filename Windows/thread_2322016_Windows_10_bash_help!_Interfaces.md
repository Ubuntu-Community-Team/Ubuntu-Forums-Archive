---
title: "Windows 10 bash help! Interfaces"
date: 2016-04-25
forum: Windows
---

### Post by enikath on 2016-04-25
I recently started using win 10s bash and I'm having trouble using network interfaces like wlan0. Yet ofc the internet works fine for win 10. I imagine it's a driver thing?? But I'm a total Linux noob and sadly I thought this would be a good opportunity to break into it. (Wether I was wrong or not-) can anybody help me configure my bash so I can use my interfaces properly in it?

---

### Post by enikath on 2016-04-26
ANY guesses, guidance, or griping is appreciated! Please I cant even find where I would start troubleshooting really. :[
Thanks

---

### Post by howefield on 2016-04-26
Thread moved to the "*Windows*" sub forum.

---

### Post by May_Masters on 2016-04-26
Well my first question would b: what are you trying to do ?
Bash is a shell ... do you intend scripting something ?

I don't use Win X so I can just guess ... But, is ther ificonfig avaiable within bash or do you need to use the win ipconfig ?

---

### Post by enikath on 2016-04-29
root@NARKFORB:/mnt/c/WINDOWS/system32# ifconfig eth0
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.

for example, but anywhere I try to use one I get a problem. Its like they dont exist as far as the bash shell is concerned, even tho obviously im on the internet.
like i said my internet is working that hardware with windows drivers... so maybe theres something there?

---

### Post by bhaverkamp on 2016-04-29
From what I have read on the subject. Networking interfaces are not fully baked yet. I think this is on Microsoft's plate to resolve in the WSL subsystem.

---

