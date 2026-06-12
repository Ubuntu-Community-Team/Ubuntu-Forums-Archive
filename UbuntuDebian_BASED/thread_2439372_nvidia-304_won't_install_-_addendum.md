---
title: "nvidia-304 won't install - addendum"
date: 2020-03-26
forum: Ubuntu/Debian BASED
---

### Post by fljarvis on 2020-03-26
(The original definitive post on this subject, originated by enigma9o7, is on
 page 23 or 24 of this forum, [https://ubuntuforums.org/showthread.php?t=2396263;](https://ubuntuforums.org/showthread.php?t=2396263;)
 it was closed Dec. 5, 2019).

With the release of Bodhi-5.1.0 earlier this week,  I proceeded with
the nvidia-304 install on the 32-bit Legacy version, as I had done
previously with Bodhi-5.0.0.

The procedure failed, even though the very same kernel version 4.9 is
used on 5.1.0 as on 5.0.0.  The failure was characterized by a peculiar
information message, "nvidia installer skips kernel preparation".
**************************************************************************************
Fortunately, the Bodhi  32-bit repository contain headers and images for the
very newest version 4.15 kernels.
With synaptic, I marked linux-headers-generic and linux-image-generic for
installation, both version 4.15.0.91.83,  which then included other headers,
another image file, and some dependencies, for a total of 11 packages.
After installation, and rebooting, the newest image becomes the default, so
I followed enigma9o7's procedure as usual, including the patch.

The nvidia installation completed successfully, with both sudo lshw -C video
and sudo inxi -Gxx indicating that the nvidia driver was in effect.

Len E.

---

### Post by Frogs Hair on 2020-03-26
Bodhi-Linux moved to *Ubuntu Debian Based*.

---

