---
title: "Latency !!!!!!"
date: 2014-08-18
forum: Ubuntu Studio
---

### Post by davstar on 2014-08-18
when i use Rakarack in linux it works fine but how do i change the latency settings in Jack because it still has a little delay that is too noticeable... can anyone help ???

---

### Post by CrocoDuck on 2014-08-18
Hi! Use qjackctl to launch and setup jack. You will see the math derived latency in the right bottom corner of the setup window. Test a little until you find a stable setup. Also, make sure there is not an active delay plugin in rakarack.

Here a picture of my configuration as an example:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252913&d=1399375381[/IMG]

make sure that the "Input Device" and "Output Device" fields point to your soundcard (just leave them as you find them if everything is working fine). Hit start to launch jack. Then launch your audio software.

Hope it helps.

---

