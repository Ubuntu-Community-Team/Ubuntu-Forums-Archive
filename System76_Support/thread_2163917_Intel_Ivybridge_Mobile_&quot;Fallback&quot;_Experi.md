---
title: "Intel Ivybridge Mobile &quot;Fallback&quot; Experience"
date: 2013-07-20
forum: System76 Support
---

### Post by omelltte on 2013-07-20
Hi all. I am wondering a bit about the intel graphics 4000HD integration on Ubuntu. Ever since I've been using the laptop, the graphics driver has been listed as "Intel Ivybridge Mobile", and the graphics experience has been "Fallback" (see attached). I've noticed as well that if I run e.g. Unity with the effects, the graphics are being processed on CPU. As I use my laptop mainly for scientific computing, this really isn't ideal, and I've been using GNOME (no effects) for some time, but I'd really like to know if this problem can be corrected.

The data from lshw -c video is here:

  *-display               
       description: VGA compatible controller
       product: Ivy Bridge Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

Thanks!

---

### Post by ajgreeny on 2013-07-20
Which version of Ubuntu are you using; 12.04, 12.10 or 13.04?

If you have ivybridge graphics on your machine they will be on the CPU as that is the way the CPU and graphic chip is made; there is nothing you can do about that apart from adding another graphic card, which will probably not be easy on a laptop.

What exactly is the problem with your current graphics; too slow, tearing?  Install gtkperf and run that, and report back the final figure you get at the bottom.

---

### Post by omelltte on 2013-07-20
Hi ajgreeny,

I'm on Ubuntu Desktop 12.04. The graphics are not slow (see results below). My main question is really whether it's normal for the graphics experience to be listed as "fallback" in the system details (as in the original post), and whether anything can be done to fix this. 

To be clear, though, by "on the cpu", I mean that applications with rendering (e.g. compiz) show a non-trivial CPU load (~50% of one core) -- but certainly, the graphics will be processed "on the cpu" in the general sense. I don't think that the loads I'm seeing should ever be the case if the graphics driver is handled correctly (the load should be showing up in the intel gpu report instead), though.

---------------------------------
GtkPerf 0.40 - Starting testing: 


GtkEntry - time:  0.02
GtkComboBox - time:  0.79
GtkComboBoxEntry - time:  0.28
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.05
GtkToggleButton - time:  0.58
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.09
GtkTextView - Add text - time:  0.43
GtkTextView - Scroll - time:  0.06
GtkDrawingArea - Lines - time:  0.55
GtkDrawingArea - Circles - time:  0.58
GtkDrawingArea - Text - time:  0.30
GtkDrawingArea - Pixbufs - time:  0.08
 --- 
Total time:  3.93

---

### Post by oldfred on 2013-07-20
I do not know correct answer. There have been several other threads.

 Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)
Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
Needs Raring & new kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029)

Some have posted these suggestions.
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by 4DXwcQG on 2013-08-06
Hello,
what desktop are you using? Did you install gnome-shell 3.0? You have written, that you are using gnome desktop without effects -are you using gnome-shell or fallback-mode, intended for use only if your graphics card doesn't support 3D? The experience filed says "fallback", because you probably manually chose to run fallback desktop (which is not a problem). Try logging in unity desktop (or gnome-shell) and see if the filed says something different.

---

