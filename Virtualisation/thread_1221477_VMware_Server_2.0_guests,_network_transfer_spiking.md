---
title: "VMware Server 2.0 guests, network transfer spiking 100% CPU"
date: 2009-07-23
forum: Virtualisation
---

### Post by samosamo on 2009-07-23
please delete this thread, need to do more testing

---

### Post by dk06 on 2009-07-24
Are you running all guests at the same time? <-that might cause a lot of network traffic within your machine

Is VMware up to date?


Sounds like if you are bottlenecking at your cpu, you may be asking too much from your machine. try running less guests at the same time

also, not sure if you installed it from a .deb but if you install from source, you will get better performance out of it

& If your network isn't configured properly it could cause your machine to work harder than it should

You may want to check out the VMware forum,
[http://www.virtuatopia.com/index.php/VMware_Server_NAT_Configuration](http://www.virtuatopia.com/index.php/VMware_Server_NAT_Configuration)

[LIST=1]
[*][[IMG]http://v.googlepreview.com/preview?s=http://www.vmware.com&ra=1[/IMG]]("http://www.vmware.com/support/reference/common/performance_tips_list.html")**[Performance Tuning Tips]("http://www.vmware.com/support/reference/common/performance_tips_list.html")**

VMware Performance Tuning Tips. The performance tuning tips in this section have been developed on the basis of both the VMware technical staff's knowledge **...**
[IMG]http://ubuntuforums.org/data:image/png,%89PNG%0D%0A%1A%0A%00%00%00%0DIHDR%00%00%002%00%00%00%07%02%03%00%00%007%E6%F6%3C%00%00%00%03sBIT%08%08%08%DB%E1O%E0%00%00%00%0CPLTE%FF%FF%FF%FF%FF%FF%CC%CC%CC%A7%D3%A7Mz%23%09%00%00%00%04tRNS%00%FF%FF%FF%B3-%40%88%00%00%00%09pHYs%00%00%0B%12%00%00%0B%12%01%D2%DD%7E%FC%00%00%00%16tEXtCreation%20Time%0005%2F01%2F08%FA%82%27%90%00%00%00%18tEXtSoftware%00Adobe%20FireworksO%B3%1FN%00%00%00%22IDAT%08%99ch%60%60%00%22%05%28Z%85%04%160%EC%FF%0F%06%A1%20%90%80%97%87%AA%0F%C5L%00%05%07.7%04%2Fj%BB%00%00%00%00IEND%AEB%60%82[/IMG]www.vmware.com/support/.../performance_tips_list.html - [Cached]("http://74.125.155.132/search?q=cache:cROnkF3_IXIJ:www.vmware.com/support/reference/common/performance_tips_list.html+&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&q=related:www.vmware.com/support/reference/common/performance_tips_list.html")
[/LIST]


[LIST=1]
[*][[IMG]http://a.googlepreview.com/preview?s=http://articles.techrepublic.com.com&ra=1[/IMG]]("http://articles.techrepublic.com.com/5100-10878_11-1061279.html")**[Don't use VMware without these tuning tips]("http://articles.techrepublic.com.com/5100-10878_11-1061279.html")**

May 8, 2001 **...** TechRepublic members have turned Ed Bott from a VMware skeptic into a believer with tips like adding RAM and using physical drives.
[IMG]http://ubuntuforums.org/data:image/png,%89PNG%0D%0A%1A%0A%00%00%00%0DIHDR%00%00%002%00%00%00%07%02%03%00%00%007%E6%F6%3C%00%00%00%03sBIT%08%08%08%DB%E1O%E0%00%00%00%09PLTE%FF%FF%FF%CC%CC%CC%A7%D3%A76%95%C8%84%00%00%00%03tRNS%00%FF%FFDP%D6%21%00%00%00%09pHYs%00%00%0B%12%00%00%0B%12%01%D2%DD%7E%FC%00%00%00%16tEXtCreation%20Time%0005%2F01%2F08%FA%82%27%90%00%00%00%18tEXtSoftware%00Adobe%20FireworksO%B3%1FN%00%00%00%1FIDAT%08%99cp%60%60%00%22%01%28%0AE%02%01%0CY%AB%10%60%02%5E%1E%AA%3E%143%01%AB%7C%22%D1%AA%A9%EFt%00%00%00%00IEND%AEB%60%82[/IMG]articles.techrepublic.com.com/5100-10878_11-1061279.html - [Cached]("http://74.125.155.132/search?q=cache:TQ-FDj3bxy4J:articles.techrepublic.com.com/5100-10878_11-1061279.html+&cd=5&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&q=related:articles.techrepublic.com.com/5100-10878_11-1061279.html")
[/LIST]

---

### Post by dk06 on 2009-07-24
Also, you may want to consider upgrading your version of VMware to 5 or 6

---

### Post by samosamo on 2009-07-24
Thank you dk06, but all your questions were answered in my first post.

VMware Server 2.0.0 built from source.  It is not available as deb, not sure where you got that info.

When I said the CPU is bottleneck'd, I meant the CPU of the virtual guest.  Not the host.  Sorry, I thought I was clear on that.

My network configuration is fine, my host can handle the load, and I can't upgrade to VMWare Server 5 or 6 because, well, only 2.0 is out so far. See first post please. :D

I spent too much time troubleshooting and documenting this.  My post is clear and well written.  Please respect it as such!  Not looking for guessing games or tweaking tips.  I'm looking to see if anyone can suggest a real fix.  Thanks!

---

### Post by dk06 on 2009-07-28
> **samosamo said:**
> Thank you dk06, but all your questions were answered in my first post.

VMware Server 2.0.0 built from source.  It is not available as deb, not sure where you got that info.

When I said the CPU is bottleneck'd, I meant the CPU of the virtual guest.  Not the host.  Sorry, I thought I was clear on that.

My network configuration is fine, my host can handle the load, and I can't upgrade to VMWare Server 5 or 6 because, well, only 2.0 is out so far. See first post please. :D

I spent too much time troubleshooting and documenting this.  My post is clear and well written.  Please respect it as such!  Not looking for guessing games or tweaking tips.  I'm looking to see if anyone can suggest a real fix.  Thanks!

lol...been a little while since used VMware Server,...thought you were talking about the Workstation version 2.0 & we're at 6 now.

For a real solution try ESXi if you're looking for performance, it installs directly to the hardware.
For what you want to do, you may want to take it to the next level...VMware Server & Workstation are cool toys for your OS but if you want performance, go with ESX or ESXi (free version)

-or-

Ask on the VMware Forums 

Good Luck & May the Force be with you ;)

---

