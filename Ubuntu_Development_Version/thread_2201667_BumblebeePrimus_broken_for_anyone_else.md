---
title: "Bumblebee/Primus broken for anyone else?"
date: 2014-01-25
forum: Ubuntu Development Version
---

### Post by 3vi12 on 2014-01-25
I've been using Bumblebee for quite some time with the edgers repo and nvidia-331 drivers.  Yesterday's Trusty updates seem to have broken Bumblebee for me - OpenGL apps just immediately segfault.

I notice yesterdays updates included things such as:

libglapi-mesa:amd64 (10.1.0~git20140117.1c5e2965-0ubuntu0sarvatt, 10.1.0~git20140124.43e77215-0ubuntu0ricotz2), libglapi-mesa:i386 (10.1.0~git20140117.1c5e2965-0ubuntu0sarvatt, 10.1.0~git20140124.43e77215-0ubuntu0ricotz2), libgles2-mesa:amd64 (10.1.0~git20140117.1c5e2965-0ubuntu0sarvatt, 10.1.0~git20140124.43e77215-0ubuntu0ricotz2), libgl1-mesa-glx:amd64 (10.1.0~git20140117.1c5e2965-0ubuntu0sarvatt, 10.1.0~git20140124.43e77215-0ubuntu0ricotz2), libgl1-mesa-glx:i386 (10.1.0~git20140117.1c5e2965-0ubuntu0sarvatt...

which I assume are the cause.

I've tried re-installing bumblebee, nvdia-331, bumblebee-nvidia, bbswitch-dkms, and primus, then restarting bumblebeed to no avail.

Anyone else seeing problems, or is it just me?

---

### Post by 3vi1 on 2014-01-25
Note:  I just regained access to my old account, so if anyone PMs, this is the one to send to.

---

### Post by ubudog on 2014-01-25
Could you post any errors you see when you run:
```
sudo service bumblebeed restart
```

---

### Post by jmmL on 2014-01-25
Which kernel version are you running? The nvidia drivers don't currently work with 3.13 - I've downloaded 3.12 from the mainline ppa and this works fine for me in conjunction with bumblebee.

---

### Post by muhsli on 2014-01-25
I was googled here and I'm suffering the same issues.

For me, no errors when restarting bumblebeed service.

syslog
[ATTACH]249740[/ATTACH]

Xorg.8.log
[ATTACH]249741[/ATTACH]

---

### Post by ubudog on 2014-01-25
> **muhsli said:**
> I was googled here and I'm suffering the same issues.

For me, no errors when restarting bumblebeed service.

syslog
[ATTACH]249740[/ATTACH]

Xorg.8.log
[ATTACH]249741[/ATTACH]

Does running glxgears give you any errors in the console?
```
optirun glxgears
```

---

### Post by 3vi1 on 2014-01-25
> **ubudog said:**
> Could you post any errors you see when you run:
```
sudo service bumblebeed restart
```

I don't get any errors.  It restarts the service normally.

---

### Post by 3vi1 on 2014-01-25
> **jmmL said:**
> Which kernel version are you running? The nvidia drivers don't currently work with 3.13 - I've downloaded 3.12 from the mainline ppa and this works fine for me in conjunction with bumblebee.

It's been working fine for me with 3.13.0-1 through 3.13.0-5 until yesterday.

---

### Post by ubudog on 2014-01-25
> **3vi1 said:**
> I don't get any errors.  It restarts the service normally.

Could you post the output of this?
```
ps ax | grep -i bumblebee
```

Also, does glxgears give you any errors when run with optirun?

---

### Post by 3vi1 on 2014-01-25
> **ubudog said:**
> Does running glxgears give you any errors in the console?
```
optirun glxgears
```

glxgears and glxspheres run with optirun, but not with primusrun.

When run with optirun, the performance is not what it should be; primusrun normally gives me nearly 300fps, whereas optirun gives me 150fps - which is about the same as just using the intel HD4000 graphics:

```

evil@clevo:~$ vblank_mode=0 optirun glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 670MX/PCIe/SSE2
153.675908 frames/sec - 171.502313 Mpixels/sec
154.442926 frames/sec - 172.358305 Mpixels/sec
155.194462 frames/sec - 173.197020 Mpixels/sec
152.172838 frames/sec - 169.824887 Mpixels/sec

evil@clevo:~$ vblank_mode=0 glxspheres64
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
168.912489 frames/sec - 188.506338 Mpixels/sec
141.498887 frames/sec - 157.912758 Mpixels/sec
142.448886 frames/sec - 158.972957 Mpixels/sec
142.692777 frames/sec - 159.245139 Mpixels/sec

evil@clevo:~$ vblank_mode=0 primusrun glxspheres64
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 670MX/PCIe/SSE2
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Segmentation fault (core dumped)
evil@clevo:~$ 

```

---

### Post by 3vi1 on 2014-01-25
> **ubudog said:**
> Could you post the output of this?
```
ps ax | grep -i bumblebee
```

Also, does glxgears give you any errors when run with optirun?

Here's the ps output:

```
evil@clevo:~$ sudo service bumblebeed restart
bumblebeed stop/waiting
bumblebeed start/running, process 948
evil@clevo:~$ ps ax | grep -i bumblebee
  948 ?        Ss     0:00 /usr/sbin/bumblebeed --use-syslog
  981 pts/2    S+     0:00 grep --color=auto -i bumblebee

```

---

### Post by muhsli on 2014-01-25
No, and it runs as expected.
But running with the primus bridge however just silent crashes.
The problem lies with the primus bridge.

Same result running glxspheres. optirun runs just fine, but primus silent crashes.

The console output does'nt reveal anything really.

muhsli@muhsli:~$ optirun glxgears
[VGL] ERROR: in readback--
[VGL]    247: Window has been deleted by window manager
muhsli@muhsli:~$ optirun -b primus glxgears
muhsli@muhsli:~$ optirun glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 660M/PCIe/SSE2
138.337875 frames/sec - 154.385069 Mpixels/sec
132.196858 frames/sec - 147.531694 Mpixels/sec
142.263793 frames/sec - 158.766393 Mpixels/sec
142.692183 frames/sec - 159.244476 Mpixels/sec
muhsli@muhsli:~$ optirun -b primus glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 660M/PCIe/SSE2
muhsli@muhsli:~$

---

### Post by muhsli on 2014-01-25
> **3vi1 said:**
> Here's the ps output:

```
evil@clevo:~$ sudo service bumblebeed restart
bumblebeed stop/waiting
bumblebeed start/running, process 948
evil@clevo:~$ ps ax | grep -i bumblebee
  948 ?        Ss     0:00 /usr/sbin/bumblebeed --use-syslog
  981 pts/2    S+     0:00 grep --color=auto -i bumblebee

```

Could I mind ask you what manufacturer and model you have? I guess it's a Clevo?
(you get this in the output from: )
```
for keyword in baseboard-manufacturer baseboard-product-name baseboard-version system-manufacturer system-product-name system-version bios-vendor bios-version bios-release-date; do
    printf "%-22s: " "$keyword";
    sudo dmidecode -s "$keyword";
done
```

---

### Post by 3vi1 on 2014-01-25
Yes, it's a clevo.  I've not had any problems using bumblebee with it until after yesterday's updates.

baseboard-manufacturer: CLEVO                            
baseboard-product-name: P15xEMx
baseboard-version     : Not Applicable                    
system-manufacturer   : CLEVO                            
system-product-name   : P15xEMx
system-version        : Not Applicable                    
bios-vendor           : American Megatrends Inc.
bios-version          : 4.6.5
bios-release-date     : 02/01/2013

---

### Post by MeyGee on 2014-01-26
I had the same problem. The mistake was that I installed the 3.13.0 kernel. :)

Primus seems not to be able to work with the libgl1-mesa-glx 10.1.0. So, check your version:
> 
* ~ $ apt-cache policy libgl1-mesa-glx*
libgl1-mesa-glx:
  Installiert:           **9.2.1-1**ubuntu3
  Installationskandidat:** 10.1.0**~git20140124.43e77215-0ubuntu0ricotz3~saucy
  Versionstabelle:
     10.1.0~git20140124.43e77215-0ubuntu0ricotz3~saucy 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) saucy/main i386 Packages
 *** 9.2.1-1ubuntu3 0
        500 [http://gd.tuwien.ac.at/opsys/linux/ubuntu/archive/](http://gd.tuwien.ac.at/opsys/linux/ubuntu/archive/) saucy/main i386 Packages
        100 /var/lib/dpkg/status

I put a hold on the mesa files to prevent the system updatiung it to 10.1.0. There was no other way of getting it to work, and I tried a lot of things. I downgraded then to Kernel 3.12.8 and libgl1-mesa-glx9.2.1-1ubuntu3 (inklding dependencies).

Should you choose to reinstall your ssystem, put the mesa files on hold before adding the edgers repository. Only a way around, and not a fix, but better than nothing. For now, i would also stay clear of Kernel 3.13.0. Additionally, I expect true Optimus support in the kernel, making bumblebee obsolete and things more smooth in the close future, according to the development of PRIME that is going on currently.

---

### Post by 3vi1 on 2014-01-26
I backleveled all the libgl*, libosmesa*, libgbm*, libegl*, and libopenvg* packages that were replaced in updates two days ago, restarted bumblebeed, and now primusrun does not crash.

I think I may have missed a package though, as primusrun (though faster than optirun) doesn't seem to be any faster than the intel chipset.

```
evil@clevo:~/Downloads/oldglmesa$ vblank_mode=0 glxspheres64
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
258.060240 frames/sec - 287.995228 Mpixels/sec
222.344439 frames/sec - 248.136394 Mpixels/sec
222.091855 frames/sec - 247.854510 Mpixels/sec
222.393742 frames/sec - 248.191416 Mpixels/sec
222.497507 frames/sec - 248.307218 Mpixels/sec
222.437315 frames/sec - 248.240043 Mpixels/sec

evil@clevo:~/Downloads/oldglmesa$ vblank_mode=0 primusrun glxspheres64
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 670MX/PCIe/SSE2
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
223.728468 frames/sec - 249.680970 Mpixels/sec
223.991330 frames/sec - 249.974324 Mpixels/sec
223.434477 frames/sec - 249.352876 Mpixels/sec
223.541624 frames/sec - 249.472452 Mpixels/sec
216.976178 frames/sec - 242.145414 Mpixels/sec

```

Just last week, primusrun with the nvidia was at least 50fps faster, if not more.  Perhaps I missed backleveling a package or need to completely reboot.

I see people still blaming the 3.13 kernel, but I've been using primusrun all along with the 3.13 kernels and edgers, and not had a problem until these other packages were updated.

---

### Post by 3vi1 on 2014-01-26
I did a ppa-purge on the edgers repository, where those new libgl* and other libraries had come from, restarted bumblebeed, and now everything is working properly again (with the 3.13 kernel, and no backleveled libraries).

```
evil@clevo:~/Downloads/oldglmesa/trusty$ vblank_mode=0 primusrun glxspheres64
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 670MX/PCIe/SSE2
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
257.571911 frames/sec - 287.450253 Mpixels/sec
256.138903 frames/sec - 285.851016 Mpixels/sec
263.426611 frames/sec - 293.984098 Mpixels/sec
259.446308 frames/sec - 289.542080 Mpixels/sec
257.869906 frames/sec - 287.782815 Mpixels/sec
262.178988 frames/sec - 292.591751 Mpixels/sec
261.976671 frames/sec - 292.365965 Mpixels/sec
262.169499 frames/sec - 292.581161 Mpixels/sec

```

---

### Post by muhsli on 2014-01-26
> **3vi1 said:**
> I did a ppa-purge on the edgers repository, where those new libgl* and other libraries had come from, restarted bumblebeed, and now everything is working properly again (with the 3.13 kernel, and no backleveled libraries).

```
evil@clevo:~/Downloads/oldglmesa/trusty$ vblank_mode=0 primusrun glxspheres64
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GTX 670MX/PCIe/SSE2
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
257.571911 frames/sec - 287.450253 Mpixels/sec
256.138903 frames/sec - 285.851016 Mpixels/sec
263.426611 frames/sec - 293.984098 Mpixels/sec
259.446308 frames/sec - 289.542080 Mpixels/sec
257.869906 frames/sec - 287.782815 Mpixels/sec
262.178988 frames/sec - 292.591751 Mpixels/sec
261.976671 frames/sec - 292.365965 Mpixels/sec
262.169499 frames/sec - 292.581161 Mpixels/sec

```
I did the same, for now.

Out of curiosity, since when does nvidia modules install correctly on 3.13?
Not sure if only I had those problems, but in rc-releases I could'nt get the modules installed in the kernel..

---

### Post by 3vi1 on 2014-01-26
> **muhsli said:**
> I did the same, for now.

Out of curiosity, since when does nvidia modules install correctly on 3.13?
Not sure if only I had those problems, but in rc-releases I could'nt get the modules installed in the kernel..

I think they fixed it recently in the 331 packages.  If I recall correctly, the only reason I had added edgers was that their nvidia-331 package didn't have this problem, while the original 331 (.19?) in the trusty repo did.

---

### Post by muhsli on 2014-02-05
As I mentioned I purged the X.org edgers PPA to get the GPU running again.
Although after that added it back, upgraded everything and then downgraded the following packages (and versions):
```
libegl1-mesa-drivers:amd64=9.2.1-1ubuntu3
libgl1-mesa-dri:amd64=9.2.1-1ubuntu3
libgl1-mesa-dri:i386=9.2.1-1ubuntu3
libosmesa6:i386=9.2.1-1ubuntu3
libosmesa6:amd64=9.2.1-1ubuntu3
libglapi-mesa:amd64=9.2.1-1ubuntu3
libglapi-mesa:i386=9.2.1-1ubuntu3
libgl1-mesa-glx:i386=9.2.1-1ubuntu3
libgl1-mesa-glx:amd64=9.2.1-1ubuntu3
libgles2-mesa:amd64=9.2.1-1ubuntu3
libegl1-mesa:amd64=9.2.1-1ubuntu3
```
This made it still working as expected.

Since I knew the bug lied within these packages (Mesa), I have been checkin in on [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) daily to see if they had pushed a newer version.
For every update I tried installing, I have ended up in downgrading above mentioned packages again, until tonight!

More precisely 1 hour ago I actually noticed that they pushed an update in which bug has been sorted out!
So I'm just checking in to let you know that with the latest version everything is working again, for me. :)
I hope the same applies to you.

Peace!

---

