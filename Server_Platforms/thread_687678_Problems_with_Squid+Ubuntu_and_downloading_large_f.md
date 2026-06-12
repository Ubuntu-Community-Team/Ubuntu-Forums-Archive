---
title: "Problems with Squid+Ubuntu and downloading large files."
date: 2008-02-04
forum: Server Platforms
---

### Post by mista_eng on 2008-02-04
Hi guys, I'm pretty sure this is a Squid problem but perhaps someone here can help me out. I am still a *nix newbie but am trying to learn the ropes. Since my home server machine only has 1GB of RAM, I use small distributions and have gotten used to doing things on the command line only. Here's the situation:

My original VM was a downloaded appliance with a stripped down Debian+Squid+Dansguardian+adzapper. It was actually bit sluggish especially when restarting either the VM or dansguardian (after a dansguardian.conf edit). I also had trouble downloading large files; for example, a file from microsoft.com 1GB in size would stop at around 500MB. This was a problem that was consistently reproduced, though with ~10% variability in filesize, on different Windows Vista/2003 client machines in both FireFox and IE7.0. 

After running that setup for nearly a year, I discovered Ubuntu JeOS. I created a VM based on it and installed the following at first: TinyProxy and Dansguardian. I don't think I made any other changes to the dansguardian.conf other than commenting one of the initial lines that would allow it to work. Large files, like the one I originally had a problem with, downloaded fine. (I realize that TinyProxy is different from Squid in that it does not cache.) 

I was hoping adzapper would work with tinyproxy but there was no such luck. I did "sudo apt-get remove --purge tinyproxy" and then a "sudo apt-get install squid." The Squid installation went without any error messages and I believe I made only the following change: "http_port 3128 transparent". The rest of the configuration file was left at default. Adzapper was installed with "sudo apt-get install adzapper".


It appears to be working correctly for regular web browsing, but when I try to download large files (this time I tried a 2GB file from microsoft.com), the download incompletes. This brings me back to square one and is very frustrating. I doubt that it is caused by either dansguardian or adzapper. TinyProxy was great, but caching and adzapping is very convenient; I'd hate to see them go. Any ideas on how to fix?

---

