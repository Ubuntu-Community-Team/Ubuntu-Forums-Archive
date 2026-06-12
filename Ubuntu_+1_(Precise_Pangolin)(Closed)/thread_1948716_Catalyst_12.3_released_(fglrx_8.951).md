---
title: "Catalyst 12.3 released (fglrx 8.951)"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-03-28
More for reference than anything seeing as we already have Catalyst 12.4 beta drivers in the repo (fglrx 8.960), but the official 12.3 drivers are available now:

[http://www2.ati.com/drivers/linux/amd-driver-installer-12-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-3-x86.x86_64.run)

---

### Post by synaptix on 2012-04-08
Just installed 12.4 beta drivers and boy what a massively huge boost of performance over 12.3, especially in Unity2D.

---

### Post by DjDiabolik on 2012-04-11
how you have found the 12.4 beta ?!!?!?!?

IT's a FAKE ? Or false notice ?

---

### Post by zika on 2012-04-11
> **DjDiabolik said:**
> how you have found the 12.4 beta ?!!?!?!?

IT's a FAKE ? Or false notice ?It is in Precise repositories... ;) 8.960...

---

### Post by sffvba[e0rt on 2012-04-11
I just wish there was a way to see if the new drivers fixes issue you may have had with previous drivers without having to re-install the distro and then the drivers for a quick check :(

Oh well, that is way off-topic... sorry.


404

---

### Post by kaldor on 2012-04-11
> **not found said:**
> I just wish there was a way to see if the new drivers fixes issue you may have had with previous drivers without having to re-install the distro and then the drivers for a quick check :(

Oh well, that is way off-topic... sorry.


404

You could make a live USB session with persistence. Extremely easy and won't mess with your real install, so you can experiment with newer Fglrx versions.

---

### Post by sffvba[e0rt on 2012-04-11
> **kaldor said:**
> You could make a live USB session with persistence. Extremely easy and won't mess with your real install, so you can experiment with newer Fglrx versions.

Hmmm... did not think about that... Thanks for the tip!!


404

---

### Post by donalgodon on 2012-04-11
> **zika said:**
> It is in Precise repositories... ;) 8.960...

Sorry, but how do you get it?

---

### Post by cariboo on 2012-04-11
> **donalgodon said:**
> Sorry, but how do you get it?

If you are running Precise, you should have got the latest driver via an update.

Anything else, you may just have to wait for the update to be released for your version.

---

### Post by samurai5205 on 2012-04-11
Any progress for this bug on 12.4 driver?

[http://ati.cchtml.com/show_bug.cgi?id=276](http://ati.cchtml.com/show_bug.cgi?id=276)

---

### Post by pqwoerituytrueiwoq on 2012-04-11
> **cariboo907 said:**
> If you are running Precise, you should have got the latest driver via an update.

Anything else, you may just have to wait for the update to be released for your version.
anywhere i can download it for use in this guide?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
that guide worked with 12.3 on 11.10 back when it had 12..2 in the guide

---

### Post by jfernyhough on 2012-04-12
You can get 8.960 from the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Be warned. This is not a PPA for general use.

I would take only the fglrx packages for oneiric and install them by hand.

If you add the PPA I will not help with the mess. :)

---

### Post by Linuxisfast on 2012-04-12
Wouldn't installing post release drivers get us the latest Catalyst, we wouldn't need PPA then.

---

### Post by donalgodon on 2012-04-12
> **Linuxisfast said:**
> Wouldn't installing post release drivers get us the latest Catalyst, we wouldn't need PPA then.


The post release drivers would not install for me on daily build of 12.04 out of the box last week.

Not sure if this has been fixed recently.

---

### Post by zika on 2012-04-12
> **jfernyhough said:**
> You can get 8.960 from the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Be warned. This is not a PPA for general use.

I would take only the fglrx packages for oneiric and install them by hand.

If you add the PPA I will not help with the mess. :)Ppa-purge works nice with xorg-edgers... Not that I'm advocating usage of aforementioned ppa. Not at all... ;)
Beware: XE has X 1.12 that is incompatible with 8.960 that is (also) in XE... Catch 22...

---

### Post by Linuxisfast on 2012-04-12
> **donalgodon said:**
> The post release drivers would not install for me on daily build of 12.04 out of the box last week.

Not sure if this has been fixed recently.

Surprisingly since Oneiric, Jockey has been buggy when it comes to installing post release AMD, nvidia post release install fine. The only way to install latest Catalyst is to go via command line or software center as I have done with my ASUS EeePC 1015B netbook which has hybrid AMD ATI chip.

---

### Post by Pilot6 on 2012-04-12
In precise amd both current and postrelease drivers are same version. It makes no sense of finding ways to install other than current.

---

### Post by Linuxisfast on 2012-04-12
> **Pilot6 said:**
> In precise amd both current and postrelease drivers are same version. It makes no sense of finding ways to install other than current.

Yes I notice that as well but the premise of putting post release was always to have an updated latest driver.

---

### Post by ayozito on 2012-04-12
Today I got a 250MB update. After that, when I restarted drivers were corrupt. I used fglrxinfo and showed many errors.

I thought ok, lets reinstall them. sh /usr/share/ati/fglrx-uninstall.sh

After uninstall rebooted and tried the drivers of Ubuntu but got an error saying that they weren't installed. Tried to install them again from the file I had downloaded from ati.amd.com and it said I have the drivers already installed. Checked with fglrxinfo and I had the Galliums.

Rebooted and fglrxinfo again and now it say I have the 4.2.11627. But if I can't install it, how I have it? And now I go to /usr/share/ati and there isn't any file of the driver, just the catalyst control center. So... where are the drivers now installed?

---

### Post by caveman7 on 2012-04-14
I downloaded this version of catalyst and created the .deb files.
When running them, I encountered several errors. One of them is 
"[B]Error! Bad return status for module build on kernel: 3.2.0-23-generic-pae (i686)
Consult /var/lib/dkms/fglrx/8.951/build/make.log for more information.[/B]"

Note that I'm using Precise Pangolin Beta 2.

Here is the installation messages:
```
sudo dpkg -i *.deb
Selecting previously unselected package fglrx.
(Reading database ... 196230 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.951-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.951-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.951-0ubuntu1_i386.deb) ...
Setting up fglrx (2:8.951-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.951 DKMS files...
Building only for 3.2.0-23-generic-pae
Building for architecture i686
Building initial module for 3.2.0-23-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-23-generic-pae (i686)
Consult /var/lib/dkms/fglrx/8.951/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.951-0ubuntu1) ...
Setting up fglrx-dev (2:8.951-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

And here is the log:
> DKMS make.log for fglrx-8.951 for kernel 3.2.0-23-generic-pae (i686)
Sat Apr 14 12:51:19 WIT 2012
AMD kernel module generator version 2.1
make.sh: 390: [: 1: unexpected operator
make.sh: 396: [: 1: unexpected operator
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-23-generic-pae/build SUBDIRS=/var/lib/dkms/fglrx/8.951/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
  CC [M]  /var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c: In function &#8216;KCL_fpu_begin&#8217;:
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: error: &#8216;TS_USEDFPU&#8217; undeclared (first use in this function)
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.951/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [kmod_build] Error 2
build failed with return value 2

Can anybody help me?

**UPDATE**
After researching in a few websites..this is apparently due to changes made in the kernel version 3.2. This issue  is fixed in the 12.4 Beta. I wonder when will the official 12.4 driver be released..

**YET ANOTHER UPDATE**
Tried the beta 12.4..still same results
> DKMS make.log for fglrx-8.960 for kernel 3.2.0-23-generic-pae (i686)
Sat Apr 14 18:10:06 WIT 2012
AMD kernel module generator version 2.1
make.sh: 390: [: 1: unexpected operator
make.sh: 396: [: 1: unexpected operator
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-23-generic-pae/build SUBDIRS=/var/lib/dkms/fglrx/8.960/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
  CC [M]  /var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c: In function &#8216;KCL_fpu_begin&#8217;:
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:5839:28: error: &#8216;TS_USEDFPU&#8217; undeclared (first use in this function)
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:5839:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.960/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [kmod_build] Error 2
build failed with return value 2


---

### Post by miatawnt2b on 2012-04-17
I am having the same issue trying to build with kernel 3.4 Any updates?
-J

---

### Post by tehowe on 2012-04-17
> **miatawnt2b said:**
> I am having the same issue trying to build with kernel 3.4 Any updates?
-J

I've just had to let it run natively and install itself to X without building the .deb files. 

What's the equivalent Catalyst version that Precise is going to end up with anyways? I'm running 12.3 but once LTS goes stable I'd like to know if I should switch over to the updates stream on jockey (assuming it works)

---

### Post by speesknijn on 2012-04-25
**I just realised that i should've read the thread better. This post below was used on Catalyst 12.3. It might work on 12.4, but i havent tested that yet. Im planning on doing this now so i will post my findings.**

=======


I just registered to post my solution that partially works, since ive been struggeling with this issue as well.

The reason why i say partially, because Catalyst doesn't seem to save its settings properly. For example, i wanted to hook my 3d tv up to the pc. When i try to change the way i want to use the screens, cloning or extended, it just sits at the default settings. It doesnt matter what i change. Neither am i able to override the resolution(?) of the screen. So now i have a black edge around the picture on both screens.

Anyway, what i did...


```
sudo apt-get remove fglrx fglrx-dev fglrx-amdcccle && sudo apt-get clean && sudo apt-get autoremove
```

Then go to where your amd-driver-installer-12-3-x86.x86_64.run is located.

```
sh amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/maverick
```

Replace maverick with your distro. Oneiric, Precise, etc.. 


The installer will fail, but no worries. Attached is a patch that i found [_Here._]("http://phoronix.com/forums/showthread.php?68922-Patch-to-compile-fgrlx-module-on-Linux-3-3-rc4-with-x86-32-bit-arch#post_252230")

Drop the .txt and copy the patch to /usr/src/fglrx-8.951/

```
cp fglrx-patch.txt /usr/src/fglrx-8.951/fglrx-patch && cd /usr/src/fglrx-8.951
```

Apply the patch

```
patch -p1 < fglrx-patch
```

Now you have to install your kernel. If you dont have the deb files on your pc anymore, you will need to get them. 


Simply install them with 

```
dpkg -i *.deb
```

It will tell you that it is installing fglrx-8.951.



Reboot.



_


The latest version of this patch was made against **kernel 3.4-rc2**. I used it on 3.4-rc4. Im not sure if this exact version of the patch will work with lower kernel versions. If not, look at the link since there are older version available.

---

### Post by speesknijn on 2012-04-25
Unfortunately it doesnt work on 8.961 (12.4)

If you are going to try any of this, its wise to have a 2.6.x kernel installed. If the driver fails to load, you'll end up with a black screen. Since it builds for the 3.4 kernel, the 2.6 kernel will still work and you can easily uninstall the non-working driver.

---

