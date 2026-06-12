---
title: "Call for testing: (Mobile) Sandy Bridge RC6"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MacUntu on 2012-02-19
A new mail by Leann Ogasawara to the ubuntu-devel mailing list:

> On Sat, 2012-02-18 at 13:07 -0800, Leann Ogasawara wrote:
[...]
> If you are running Ubuntu 12.04 (Precise Pangolin) and willing to test
> and provide feedback, please refer to our PowerManagementRC6 wiki for
> detailed instructions [3].  Additionally, instructions for reporting any
> issues with RC6 enabled are also noted on the wiki.  We would really
> appreciate any testing and feedback users are able to provide.
I first want to thank everyone who has already tested and provided their
feedback.  It is very much appreciated.  There has however been some
recent developments with the current RC6 patch which originated this
call for testing.  An adjustment has been made to that original patch:

[http://lists.freedesktop.org/archives/intel-gfx/2012-February/015319.html](http://lists.freedesktop.org/archives/intel-gfx/2012-February/015319.html)

We're hoping this fix resolves the remaining issues when RC6 is enabled
by default.  A test kernel has already been built and posted to the RC6
bugs noted in the PowerManagementRC6 wiki [3].

For anyone else who was interested in testing, and wants to re-test, I
ask that you please hold off until we are able to upload this additional
fix.  I hope to get a Beta Freeze exception for this and intend follow
up with the Release Team accordingly.  I will respond to this email once
we have an official kernel in the archive ready for additional testing.

Thanks again,
Leann Ogasawara

> [1] [http://phoronix.com/forums/showthread.php?68199-Intel-Wants-YOUR-Linux-Questions-Feedback&p=246785#post246785](http://phoronix.com/forums/showthread.php?68199-Intel-Wants-YOUR-Linux-Questions-Feedback&p=246785#post246785)
> [2] [http://lists.freedesktop.org/archives/intel-gfx/2012-February/015131.html](http://lists.freedesktop.org/archives/intel-gfx/2012-February/015131.html)
> [3] [https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)



**OLD:**


> Hi All,

RC6 is a technology which allows the GPU to go into a very low power
consumption state when the GPU is idle (down to 0V). It results in
considerable power savings when this stage is activated. When comparing
under idle loads with machine state where RC6 is disabled, improved
power usage of around 40-60% has been witnessed [1].

Up until recently, RC6 was disabled by default for Sandy Bridge systems
due to reports of hangs and graphics corruption issues when RC6 was
enabled.  Intel has now asserted that RC6p (deep RC6) is responsible for
the RC6 related issues on Sandy Bridge. As a result, a patch has
recently been submitted upstream to disable RC6p for Sandy Bridge [2].

In an effort to provide more exposure and testing for this proposed
patch, the Ubuntu Kernel Team has applied this patch to 3.2.0-17.26 and
newer Ubuntu 12.04 Precise Pangolin kernels.  We have additionally
enabled plain RC6 by default on Sandy Bridge systems so that users can
benefit from the improved power savings by default.

We have decided to post a widespread call for testing from Sandy Bridge
owners running Ubuntu 12.04.  We hope to capture data which supports the
the claims of power saving improvements and therefore justify keeping
these patches in the Ubuntu 12.04 kernel.  We also want to ensure we do
not trigger any issues due to plain RC6 being enabled by default for
Sandy Bridge.

If you are running Ubuntu 12.04 (Precise Pangolin) and willing to test
and provide feedback, please refer to our PowerManagementRC6 wiki for
detailed instructions [3].  Additionally, instructions for reporting any
issues with RC6 enabled are also noted on the wiki.  We would really
appreciate any testing and feedback users are able to provide.

Thanks in advance,
The Ubuntu Kernel Team

[1] [http://phoronix.com/forums/showthread.php?68199-Intel-Wants-YOUR-Linux-Questions-Feedback&p=246785#post246785](http://phoronix.com/forums/showthread.php?68199-Intel-Wants-YOUR-Linux-Questions-Feedback&p=246785#post246785)
[2] [http://lists.freedesktop.org/archives/intel-gfx/2012-February/015131.html](http://lists.freedesktop.org/archives/intel-gfx/2012-February/015131.html)
[3] [https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)


---

### Post by tista on 2012-02-19
@MacUntu

Thanks for heads up... ;)

So I've added my VAIO Z's results to Wiki. Why Z showed that terrible watts? Yeah because it has standard voltage sandy-bridge i5... But anyway RC6 tweak could do a trick !!

Regards,
Tista

---

### Post by MacUntu on 2012-02-19
Unfortunately I only have a desktop with Sandy Bridge, so:
> Machine is NOT running on battery and hence we cannot measure power usage.

---

### Post by EgoGratis on 2012-02-20
I used USB key:

-Ubuntu 11.10 
-Ubuntu 12.04 daily build

I charged laptop booted Ubuntu (Try Ubuntu) and put the laptop on battery power. Then i tested two scenarios:

-Idle: Left Ubuntu to run for three minutes in idle mode and read the data from battery indicator.
-Light Workload: Opening and moving terminal, opening and switching between opened application, switching between different workspaces and testing all sorts off Compiz operations Unity provides by default and read the data from battery indicator.

Results:

1.)

Ubuntu 11.10 and Ubuntu 12.04 with appended i915.i915_enable_rc6=0 as a kernel boot parameter.

-Slightly better (power management) performance of Ubuntu 11.10.
-Ubuntu 12.04 behaved strange and when idling and in light workload power management was slightly behind Ubuntu 11.10 and when idling i noticed drops in performance when remained time was lowered substantially and then raised back to slightly lower remained time of Ubuntu 11.10.

2.)

Ubuntu 12.04 with default settings. In both scenarios average power consumption dropped for 25%.

Problems noticed:

When using Compiz Scale and selecting one of the windows when maximizing thin (1px) flickering line appears between title bar and window. I tested this with Ubuntu 11.10 and Ubuntu 12.04 with appended i915.i915_enable_rc6=0 as a kernel boot parameter and its also happening with slight difference in Ubuntu 12.04 when this is more visible (white flickering). 
 
I didn't noticed other problems or something that i didn't noticed with  Ubuntu 11.10 and Ubuntu 12.04 with appended i915.i915_enable_rc6=0 as a kernel boot parameter too.

For my hardware this is huge step forward in improving battery life and for now i don't see any problems beside mentioned one that is not Ubuntu 12.04 specific!

---

### Post by MacUntu on 2012-02-24
Bump &#8594; There's a new kernel to test, please see update to original post.

---

