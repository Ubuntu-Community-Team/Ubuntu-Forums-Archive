---
title: "Max down/up rate limit issues"
date: 2010-11-16
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2010-11-16
Hi,

Having trouble with my internet speed while my Ubuntu One client is uploading lots of files to the U1 server ( I'm on a thin ADSL line with only ~240KB/s up and ~34KB/s down) , I wanted to limit the data transfer rate in the U1 client.

I find two things that do not seem to go right:

1. When I limit the **upload** rate to 15 KB/s, the actual upload rate consumption remains at the max (around 30 KB) most of the time.

2. When I limit the **download** to any setting other than the predefined 2048 KB/s, that setting will not stick. Closing the preferences window and re-opening it shows me the old 2048 value again.

I've tried different variations/orders of hitting the Disconnect / Restart buttons after changing the values but it all seems to make no difference ...

What can I do to truly limit the data rates in U1 ?

Thanks :)

---

### Post by duanedesign on 2010-11-19
there is [a bug]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/509740") about upload/download not saving correctly. 

> This seems to be a problem in ubuntuone-preferences on Lucid and the latest PPA version. The problem is actually that the values only save when focus is taken off the input field. So, if you click outside of each input field after changing the value, it will save the values. Otherwise, the input field that didn't have focused removed will not save.

---

### Post by RavanH on 2010-11-21
> **duanedesign said:**
> there is [a bug]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/509740") about upload/download not saving correctly.

> This seems to be a problem in ubuntuone-preferences on Lucid and the latest PPA version. The problem is actually that the values only save when focus is taken off the input field. So, if you click outside of each input field after changing the value, it will save the values. Otherwise, the input field that didn't have focused removed will not save.

Thanks duanedesign, but it does not matter if I change the max download value and then change the focus (to the max upload value or another tab, for example) or not. After closing the preferences window and opening it again, the value is right back at 2024 KB/s ... :(

---

