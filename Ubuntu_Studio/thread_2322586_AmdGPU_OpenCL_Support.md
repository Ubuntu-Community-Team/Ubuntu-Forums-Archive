---
title: "AmdGPU OpenCL Support"
date: 2016-04-29
forum: Ubuntu Studio
---

### Post by peter206 on 2016-04-29
I have a fresh installation of Ubuntu 16.04 LTE on my PC and I was told this version would ditch old ati drivers for new amdgpu. Apparently OpenCL is not yet supported which is a must for Blender 3D to use GPU rendering. 

So my question is when new amdgpu driver is available will my LTE version get this upgrade? Any idea on time frame for OpenCL support. 


Thanks for help.

---

### Post by Tommy_Johnson_ on 2016-04-29
I had the same problem with my nvidia gpus for blender , I installed latest blender and not the one through Ubuntu and now have my cuda rendering, maybe worth a shot .

---

### Post by yoshii on 2016-04-30
From what I've read AMD is currently working on new linux drivers that won't be available for several months.  We might know more at the end of this summer from what I remember reading elsewhere.  I think the estimate of August came from somebody who said that since some AMD gpu work is now open source, work is happening faster.  But every other site I've read said to wait about a year.  So yeah, AMD users who are gamers or visual arts people are kind of upset.  

I couldn't even get my AMD video to work on Ubuntu v16 without disabling all hardware acceleration, so yeah, I don't want that.  
I recently tried upgrading instead from v14.04.3 to v14.04.4 (which has a newer linux hardware kernel and moderately newer AMD gpu support).  
It did have better support than what I had before but something else was different and some of my software wouldn't install properly.  So I am still sticking with v 14.04.3 even though it's getting old now.  I don't have internet access on that computer and offline installs of .DEB files don't always work.  

From what I've read Debian Linux might be holding onto the older AMD drivers longer, but I'm not entirely sure about that.  
I also don't know if Xubuntu is keeping the old AMD drivers or not either.

---

