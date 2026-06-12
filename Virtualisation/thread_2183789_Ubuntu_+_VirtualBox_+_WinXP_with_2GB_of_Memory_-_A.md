---
title: "Ubuntu + VirtualBox + WinXP with 2GB of Memory - Any tips?"
date: 2013-10-26
forum: Virtualisation
---

### Post by Jeff_Berrian on 2013-10-26
Hi Everyone,

I am seeking your insight about Ubuntu + Virtualbox and memory allocation:

I am running Windows XP Pro SP2 as guest. I only have 2Gb of memory available on my desktop (older Core 2 Duo machine w/dedicated video card) re-purposed to run Ubuntu. 

I would like to allocate as much memory as possible to XP without effecting Ubuntu host adversely. In short, I would like both host + guest OS to run as relatively smooth as possible pending a memory upgrade.

I don't plan to do anything intensive inside xp next to a few docs in ms office word and excel and maybe firefox (Chrome running in Ubuntu). I've optimized XP by disabling unnecessary start-up programs and services via msconfig and services.msc including making all the nice little "tweaks" and "hacks" that can help it fly right along with minimum memory requirements.

**Question(s): ***When memory is allocated to Windows XP (currently at 512mb) VM, does this allocation become reserved from total system memory leaving Ubuntu with 1.5gb of ram when XP VM is active?*

[I]Or, is the memory dynamically allocated on a as-needed basis similar to VirtualBox's Dynamic HDD option and not exceed the allocated amount??

I am thinking that since I am splitting time equally on both OS's that I should divide the memory in half 50/50 - sound thinking or am I off the mark on how memory is handled?[/I]

Suggestions?

I'd love to hear any cool tweaks and tips you may have that will help Ubuntu and XP fly given my rather limited memory quantity.

PS. I am running a Dell Precision 390 series with virtualization enabled on the cpu. Settings are configured accordingly on VirtualBox.

---

### Post by SeijiSensei on 2013-10-26
With 2 GB I'd give Windows 1280 MB and leave the rest for Ubuntu.  You could also switch to a lighter-weight desktop environment like LXDE or XFCE which would let you shrink the Ubuntu allocation further.  With those 512/1536 MB will work.

Make sure you have swap allocated, either as a separate partition during installation, or by the use of a swap file: [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/).  If Windows is running really slowly, try pushing up its memory footprint bit by bit.  

2 GB is just about the minimum I think for an Ubuntu host/XP guest session.  I have a machine probably rather like yours, a Dell Inspiron dual-core with 2 GB though with motherboard graphics.  The last time I did this was during tax season.  It works but it is very slow.  Eventually I gave up and booted into XP since my files were all sitting on my server.

---

