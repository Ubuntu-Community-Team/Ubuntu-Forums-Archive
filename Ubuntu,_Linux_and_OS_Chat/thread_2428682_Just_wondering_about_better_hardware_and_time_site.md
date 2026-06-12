---
title: "Just wondering about better hardware and time sites load"
date: 2019-10-07
forum: Ubuntu, Linux and OS Chat
---

### Post by crip720 on 2019-10-07
Have recently gotten another laptop with much better cpu, twice as ram and nvida graphics.  With same OS and browser and router/download speed, I am finding websites seem to snap open instead of on other laptop they would take a bit longer to load.  I am using a VPN on both laptops, and both are on wired connection.  Would the better hardware help with sites loading faster?  Thank you.

---

### Post by sdsurfer on 2019-10-07
The short answer is yes, and I am looking forward to responses to this thread.

The longer answer: the following is my own issue with speeds which I haven't sorted out yet, but may give you insight as to why the other computer can't keep up.

I have an MSI mother board in a comp I built a while ago, it has a dual boot with Windows 7 one drive, Ubuntu 18.04 other. We moved into a house with 360 mbps Internet. Awesome . . . but the onboard Ethernet is only 10/100 mbps. Obviously the best I could hope for is 100 mbps, and lo and behold, that's all I got. So I bought a 1000mbps Ethernet card, disabled the onboard Ethernet, fired it up . . . and at best get 175 mbps in a browser speedtest.

I am making an assumption that hardware, and possibly software, is definitely a factor. First you look at the max speed of your Ethernet card (and wireless, if that is what you are using) then from there . . . in my searches I discovered it may be a software issue or just that your hardware on the first computer can't process the speeds.

The first thing you might want to do is install speedtest-cli (requires Python, do a search for "ubuntu install speedtest-cli," many docs out there.) The reason being, from a command line I am getting very close to the 360 mbps speeds, but in the GUI and a browser, barely over half that. What that tells me (I think) is either I have a software issue in the GUI or my hardware, when running the GUI on top of the hardware,  just can't keep up with the processing required to move the data that fast.

---

### Post by crip720 on 2019-10-07
My speed will only top out at 20Mbps from ISP, usually get high 16Mbps when using VPN on both laptops.  Have tried to twin both laptops for OS 19.04 and browser, so only difference would be hardware.  There is not a lot of difference in sites loading, but on the better hardware there does seem to be more snappiness with loading of sites.

---

### Post by sdsurfer on 2019-10-07
You still might want to get a "baseline" without the intervention of the browser itself, hence, speedtest-cli. Have you tried comparing with different browsers on the same computer as well?

A lot of stuff goes on in a browser, and they consume CPU cycles and memory. It makes perfect sense that a faster CPU with more memory will allow the browser (or any program) to run faster.

There are also configuration issues, caching, and multi-channel connections. It's like apples to oranges, especially comparing one computer against another.

---

### Post by TheFu on 2019-10-07
> **crip720 said:**
> Have recently gotten another laptop with much better cpu, twice as ram and nvida graphics.  With same OS and browser and router/download speed, I am finding websites seem to snap open instead of on other laptop they would take a bit longer to load.  I am using a VPN on both laptops, and both are on wired connection.  Would the better hardware help with sites loading faster?  Thank you.

It depends.  Just how bad is the older machine?  How little is the RAM?  How old is the GPU? Which model?  Which network chips are used in the ethernet card?  Some network card makers offload much of the processing to the CPU (cough realtek) and others have most of the networking work handed by the ASICs on the NIC (Intel).  

Different VPNs have different capabilities, some are heavy CPU users and others will be more efficient. Seeing a VPN get much over 50 Mbps isn't common on VPNs.  My home VPN is running on limited hardware with a limited 25/5 connection, but it is more than sufficient for any web browsing I do away from home.  I also have a paid VPN service with exit nodes all around the world.

It also depends on the specific websites. Those with 20 advertising boxes and dynamic ads will always be slower than a simple text-only website with little or no javascript.

If you have a good ad-blocking DNS, the performance difference will be significantly less than if you don't have a good ad-blocking solution.   Running a lighter GUI would be very helpful too. The difference between Gnome3 and XFCE or mate or LXDE is significant.

For a reasonable answer, showing the specific hardware involved would be most helpful. Output from **inxi -Fbz** is the easiest way to provide that data for both.  The -z option removes "sensitive" identifiable data.

---

### Post by crip720 on 2019-10-07
Think it kind to say the older laptop was close to being average cpu and 8 ram, while the newer one is closer to top of the line.  Think both laptops are close in age has the newer one is a refub 4th gen I7.  I am just curious if the hardware would benefit the loading of sites, with most of everything else being close to equal.

---

### Post by TheFu on 2019-10-07
There are bad CPUs made in 2019 and there are great CPUs made in 2015.  Without exact specifications, nobody can answer any better than has already be attempted.

---

