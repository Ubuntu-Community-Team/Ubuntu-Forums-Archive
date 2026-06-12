---
title: "wine1.6 and wine1.7 conflict with fglrx-amdcccle"
date: 2014-12-20
forum: Ubuntu Development Version
---

### Post by darksidedude on 2014-12-20
I'm not sure if anyone is aware of this conflict at this time. if it known I apologize.

however at this current time I am being forced to choose between ati drivers or wine. naturally playing Borderlands trumps WOW at this time :lolflag:

```
sudo apt-get install wine1.7
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libp11-kit-gnome-keyring:i386 secureboot-db shim wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ocl-icd-libopencl1 ocl-icd-libopencl1:i386 wine1.7-amd64 wine1.7-i386:i386
Suggested packages:
  opencl-icd opencl-icd:i386 dosbox:any winbind
The following packages will be REMOVED:
  fglrx fglrx-amdcccle fglrx-core
The following NEW packages will be installed:
  ocl-icd-libopencl1 ocl-icd-libopencl1:i386 wine1.7 wine1.7-amd64 wine1.7-i386:i386
0 upgraded, 5 newly installed, 3 to remove and 35 not upgraded.
Need to get 0 B/36.7 MB of archives.
After this operation, 8,552 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by darksidedude on 2014-12-21
I decided to run aptitude to see if it could better give me an idea as to the conflicting packages. here is the output of aptitude. 


```
sudo aptitude install wine1.7
[sudo] password for xxxxx: 
The following NEW packages will be installed:
  ocl-icd-libopencl1{ab} ocl-icd-libopencl1:i386{ab} wine1.7 wine1.7-amd64{a} wine1.7-i386:i386{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/36.7 MB of archives. After unpacking 286 MB will be used.
The following packages have unmet dependencies:
 fglrx-core : Conflicts: libopencl1 which is a virtual package.
              Conflicts: libopencl1:i386 which is a virtual package.
 ocl-icd-libopencl1 : Conflicts: libopencl1 which is a virtual package.
 ocl-icd-libopencl1:i386 : Conflicts: libopencl1 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     fglrx                       
2)     fglrx-amdcccle              
3)     fglrx-core                  



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     ocl-icd-libopencl1 [Not Installed]                 
2)     ocl-icd-libopencl1:i386 [Not Installed]            
3)     wine1.7 [Not Installed]                            
4)     wine1.7-amd64 [Not Installed]                      
5)     wine1.7-i386:i386 [Not Installed]                  


```

---

### Post by darksidedude on 2014-12-25
well I was able to get wine installed and running. although not threw any package manager I had to compile from source. 

I followed the thread located [http://wiki.winehq.org/BuildingBiarchWineOnUbuntu]("http://wiki.winehq.org/BuildingBiarchWineOnUbuntu") 

it works and wow D3 is functional. however when in my situation I had to build without OpenCL support. 

so when you run ```
sudo apt-get build-dep wine 
``` make sure you don't install the OpenCL libs or it will remove AMDCCCLE and thus defeat the purpose of this.

---

### Post by Yellow Pasque on 2014-12-26
Is there a bug report on this? wine should not depend on one specific version of libopencl. It should depend on a virtual package that allows for different OpenCL implementations.

---

### Post by darksidedude on 2014-12-26
not sure I posted on the wine forums. and got a rather... uhh how do I put it. disrespectful response about using a dev version of ubuntu and that I should just post here and not clog their forum :mad:

although pulseaudio is giving me some grief. sound is really choppy.

---

### Post by Yellow Pasque on 2014-12-26
> **darksidedude said:**
> not sure I posted on the wine forums. and got a rather... uhh how do I put it. disrespectful response about using a dev version of ubuntu and that I should just post here and not clog their forum :mad:

Yeah, it's a Debian/Ubuntu packaging issue. The wine forum was not the place for that.

---

