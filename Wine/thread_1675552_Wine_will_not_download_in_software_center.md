---
title: "Wine will not download in software center"
date: 2011-01-25
forum: Wine
---

### Post by jhargis1012 on 2011-01-25
Hello.

I have Ubuntu 10.04 and am attempting to install Wine through the Software Center. When I click install, the download seems to be begin, but when the progress bar hits 50% (exactly) it stops and gives me the error message "Failed to download package files - Check your Internet connection". When I hit details, it shows three lines that start with "Failed to fetch" and then list a URL (at the end of which, it says not found and lists an IP Address).

I tried rebooting and plugging in the ethernet cable (instead of using the wireless, just to see), no luck.

I'd appreciate any help. Thanks.

---

### Post by jhargis1012 on 2011-01-25
Although the software center refused to work, I was able to do it by checking the other two boxes in Software Sources under "Other Software" in Synaptic, then in the terminal I typed

sudo apt-get install update

sudo apt-get install wine

Now I have Wine version 1.2.2 installed. I'm a real Ubuntu noob, so I don't know if this was the most efficient way of doing it, but at least I have it! :)

Still, I'd like to know what's wrong with my Software Center. Any way to find this out?

---

