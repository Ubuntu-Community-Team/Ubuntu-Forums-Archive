---
title: "install android sdk/lib32stdc++6 on raspberry pi/raspbian"
date: 2016-06-16
forum: Ubuntu, Linux and OS Chat
---

### Post by RicardoGomes on 2016-06-16
Hi,

I'm trying to install android sdk on raspberry pi 3. I've already download the sdk, however now i want to install the android studio.
The following error appears:
"Unable to run mkscard SDK Tool". 

One of the causes/solution i've search in other foruns is due to missing some libraries and compatibilities between version 64 and 32 bts... A solution to solve this was to execute the following comand "$ sudo apt-get install lib32stdc++6" the following error appears:

"Unable to locate package lib32stdc++6
Couldn't find any package by regex lib32stdc++6"

In orther to solve this situation i tried to install lib32stdc++6 manually, using the [https://packages.debian.org/jessie/lib32stdc++6](https://packages.debian.org/jessie/lib32stdc++6), however there is no permission to install and execute it from /var/cache/apt/archives as i've seen in one forum. My question is: is there any way i could install lib32stdc++6 on raspbian? Is this needed in order to later install the android studio?

Any help would be very thankful =)

---

