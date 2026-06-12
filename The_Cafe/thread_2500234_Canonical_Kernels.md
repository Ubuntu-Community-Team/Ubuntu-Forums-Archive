---
title: "Canonical Kernels"
date: 2024-08-26
forum: The Cafe
---

### Post by makitso on 2024-08-26
I have always been a big fan of Ubuntu since the 8.04 days.  I would looked forward to each new release,  testing new features, getting things to work.  I am older now and tend to keep to LTS releases for stability.  Imagine my surprise when 24.04 was released.          My normal process is to test beta&#8217;s in Virtualbox and then after the release date install first on my 10 year old ThinkPad.  If all is good, I update my wife's 3 year old Dell XPS and then my 1 year old Dell XPS development machine. 

 The first problem I ran into was the 24.04 installer would hang in the live CD session. IMHO, the live CS should NEVER hang.  I could do a successful  install by selecting the graphics safe mode. However, the installed systems ( Ubuntu, Ubuntu Budgie, Ubuntu Xfce would all hang  once you logged in.  There was no clue in dmesg, syslog, etc.  On a hunch, I tried installing the latest Solus OS release with the exact same problem with their installer, which suggests to me a problem with the new 6.9 kernal video or mesa driver.  Anyway, I also tried newer and kernels up through 6.10 but nothing changed. The hang problem started with 6.7 if my memory serves me.        

Now on to my two Dell XPS laptops running 22.04.  Some days ago, Canonical updated the kernel in the 22.04 release from 6.5 to 6.8.  My wife's XPS with the 6.8 kernel  started to have severe graphics problems.  My XPS would no longer run Virtualbox.  Researching the forums it looked like lots of reports of weird stuff was happening with 6.8.  I reverted both machines to the 6.5 kernel and all was well.  This past day, I have installed Solus OS on my old ThinkPad with the nomodeset kernel parameter.  I then updated Solus to their latest 6.10 kernel and the system worked fine without nomodeset.  So, I reinstalled ubuntu 24.04, and then installed the latest 6.12 kernel from the Ubuntu kernel  download.  And, the system hung just the same. So, the Solus kernel works and the Ubuntu kernel doesn't.

  I will have to say that I was surprised when Canoncial updated 22.04 to the 6.8 kernel.  IMHO, they couldn't  possibly have tested it very well. And with a LTS release stability is the norm.  Oh, yes, I have submitted Ubuntu bug reports but no action on any of them.

---

### Post by Perfect Storm on 2024-08-29
We have alot of perople with nvidia cards (restricted drivers)  and kernel 6.8.0 with a lot of trouble combination over a Zorin OS which uses Canoicals kernels. So I guess they skipped the testing this time.

---

