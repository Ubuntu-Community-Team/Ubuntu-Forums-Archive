---
title: "AVCHD Editing with Gazelle Professional?"
date: 2011-03-30
forum: System76 Support
---

### Post by pjman on 2011-03-30
I'm thinking of buying the Gazelle Professional with the default Intel Core i7-2630QM CPU. Does this laptop have enough power to edit 1080i AVCHD video with OpenShot?

Thanks!

---

### Post by isantop on 2011-03-30
Actually, I was in the process of editing AVCHD video on my PanP7 with the i7-840QM. It wasn't the absolute best experience, but I managed just fine. You shouldn't have any problem at all.

---

### Post by pjman on 2011-03-30
Thanks for the reply. That definitely helps :)

---

### Post by pjman on 2011-05-04
Just received my GazP6 and I have to say I really like the hardware. I ended up going with the i7-2720QM and 8GB of RAM. 

I finally got 11.04 installed. I had to do a complete wipe since I installed a new 500GB 7200 drive. The desktop iso would not work. I tried USB and CD created from multiple machines. I ended up using using the alternate disk burned on CD as USB did not work with it. 

I'm now playing around with some video editing. I have to say I'm a little bummed. Using OpenShot my 1080i AVCHD video is very choppy. I even tried it in Ubuntu Classic with no compiz. After some reading it looks like OpenShot and the MLT framework don't support multi-threads... As an alternative I tried PiTiVi and it doesn't even scrub the video :(

What video editor were you using on your PanP7?

---

### Post by isantop on 2011-05-05
It was Openshot. I'm not sure why you were getting poor video performance. Was the proprietary driver installed? That would slow video down to a halt on an Nvidia system.

---

### Post by pjman on 2011-05-06
The proprietary has been installed. The only video player I could get to play my AVCHD files is mplayer since it supports VDPAU. Totem and VLC are choppy and unwatchable (totem more so). Multi-thread support on standard applications sure would be nice. At least I would be able to make use of these 4 cores :P

I'll do some more digging into VDPAU support in OpenShot/MLT.

Thanks

---

