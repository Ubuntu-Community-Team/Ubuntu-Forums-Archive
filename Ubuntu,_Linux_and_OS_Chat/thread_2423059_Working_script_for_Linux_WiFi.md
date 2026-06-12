---
title: "Working script for Linux WiFi"
date: 2019-07-16
forum: Ubuntu, Linux and OS Chat
---

### Post by chefmike07 on 2019-07-16
I have seen on this site and Linux Mint forums that many users are not able to get their computers to use the WiFi. They have to use the eithernet and be trapped to a wire plugin. I know this is damn frustrating for the Linux community, that includes me as well. I don't know how to write code or a script that could be a workaround for the WiFi problem but their are guys and gals who can do that. Lets do that. I'm considering buying a copy of Windows XP on Ebay and dual booting Mint and Windows, I've been a Linux user 30 years.

---

### Post by wildmanne39 on 2019-07-16
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

We have a script that helps us diagnose wifi issues, there is an old one that use to help fix issues that was created in 2011 but it only helped with very small issues, I have thought about trying to do that but it still would only help with minor issues, but almost all wifi issues can be resolved without to much effort so I do not think this is a feasible endeavor, One issue is also that it would require to much access to the user computer and I do not believe that most linux users are comfortable with that, like install an app from an unknown source and giving it elevated permission to run, also many issues require installing a driver or firmware and that seems to me to be more then a script will be able to do because there are a lot of drivers from different sources and we would have to constantly be updating links to them to keep the script current, it would be almost impossible to maintain.

---

### Post by mastablasta on 2019-07-17
it is best to get a chip with linux drivers available. th eonly issue i have is that manufacturers are very good at "hiding" data on the model, so that consumers can't be sure if they will get a chip that works.

again business laptops often have an option to be linux preloaded (atleats in certain countries), so they would have a working wi-fi chip.

---

### Post by TheFu on 2019-07-18
I've found that choosing Intel network chips (wired and wireless) basically avoids all my network driver issues.  But the user needs to know that BEFORE they buy.  Someone with lots of experience probably learned this over the decades. I did.  

Before I buy **any** hardware, I seek out the specific chip used and look up how good the Linux kernel support is.  I've been burned by marketing and packaging that claimed "Supports Linux!" only to find the proprietary driver was for a 4+ yr old kernel that nobody used.  No newer drivers were provided by the vendor, so I was stuck.

Live and learn.

My last motherboard, bought in December, was a little more expensive because it came with an Intel i211 NIC.  But if that $20 more saved me 1 hr of frustration, then it was 100% worth it to me.  I've had ZERO frustration.
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: **I211 Gigabit** Network Connection
       vendor: **Intel** Corporation
```
Same for wifi on a laptop:
```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: **Intel** Corporation

```
I've been burned from time to time by SATA controllers too, but I don't have any specific wisdom to share about brands.  Sorry.

Intel for networking is an easy solution, however.

---

