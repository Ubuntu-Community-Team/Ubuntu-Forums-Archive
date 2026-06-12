---
title: "Ubuntu 24.04 - nautilus no longer show image thumbnails"
date: 2023-12-22
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-12-22
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256)

---

### Post by Irihapeti on 2023-12-22
Added myself as affected.

---

### Post by Claus7 on 2024-03-17
Hello,

I issued the command:
sudo apt install apparmor -t noble-proposed

and problem solved.

Regards!

---

### Post by ajgreeny on 2024-03-17
> **Claus7 said:**
> Hello,

I issued the command:
sudo apt install apparmor -t noble-proposed

and problem solved.

Regards!
Interesting!

I wonder if that might solve some of the other 24.04 problems that users are finding and are very annoying, eg the inability to run firefox as a .deb install or using the .tar.bz archive direct from Mozilla which I think is something related to apparmor.

I have many KVM virtual installs where I can try this to see what happens; probably nothing but worth trying as I don't keep these VMs running very long but einstall with new ISO files regularly.

---

### Post by ajgreeny on 2024-03-17
I have just tried the proposed repos version of apparmor to see if it allowed firefox to run as the .deb or .tar.bz install versions but regrettably it didn't work as I'd hoped.

I saw some indication that using firefox-nightly, currently version 125, is working again so i might try that when i have some spare time.
There is already a workaround for the .tar.bz version which i also have to try shown in the bug at [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57)

---

### Post by Claus7 on 2024-03-17
Hello,

> **ajgreeny said:**
> Interesting!

I wonder if that might solve some of the other 24.04 problems that users are finding and are very annoying, eg the inability to run firefox as a .deb install or using the .tar.bz archive direct from Mozilla which I think is something related to apparmor.

I have many KVM virtual installs where I can try this to see what happens; probably nothing but worth trying as I don't keep these VMs running very long but einstall with new ISO files regularly.

no, it didn't do the work. I tried it using the tar option of 123.0.1 (64-bit) firefox version.

> **ajgreeny said:**
> I have just tried the proposed repos version of apparmor to see if it allowed firefox to run as the .deb or .tar.bz install versions but regrettably it didn't work as I'd hoped.

I saw some indication that using firefox-nightly, currently version 125, is working again so i might try that when i have some spare time.
There is already a workaround for the .tar.bz version which i also have to try shown in the bug at [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57)

I tried the command of the link you provided for the same version of firefox mentioned above and it worked!

Regards!

---

### Post by ajgreeny on 2024-03-18
Great!
Thanks for that; it will be my next test of what, for me, has been more problematic than many dev versions.

---

### Post by Claus7 on 2024-03-18
Hello,

> **ajgreeny said:**
> Great!
Thanks for that; it will be my next test of what, for me, has been more problematic than many dev versions.

I'm glad that it is working. It seems that with this addition is fully functional, so I do not think that it will be hard to be implemented somehow, so as not to need to be invoked that way.

Regards!

---

### Post by corradoventu on 2024-03-27
Problem solved by proposed but on a fresh install without proposed problem remains also if [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256) says 'Fix Released'

Today Sebastian Bacher (seb128) was forced to confess that the fix was 'Committed' and not 'Released'

---

### Post by corradoventu on 2024-03-28
Problem fixed, nautilus not changed but may be some dependent
After apply the fix you must empty (or just delete) the directory /home/$USER/.cache/thumbnails/fail
don't worry, it will be recreated empty immediately afterwards

---

### Post by currentshaft on 2024-05-15
bore

---

### Post by corradoventu on 2024-05-16
Yes, nautilus is the package name of the gnome file manager.
Did You try this?
After apply the fix you must empty (or just delete) the directory /home/$USER/.cache/thumbnails/fail
don't worry, it will be recreated empty immediately afterwards

---

### Post by currentshaft on 2024-06-06
d>d

---

### Post by corradoventu on 2024-06-07
The fix should be here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256)
if the fix does not fix please add your comments here.

---

### Post by currentshaft on 2024-06-07
ada

---

### Post by anyeos-3 on 2024-06-27
Have anyone tried just installing the libraries needed to handle that kind of images?
I installed libjpeg for example and it worked. Next, ffmpeg thumbnailer and it worked. And later I make sure that libpng is installed too.
So, after deleting ~/.cache and rebooting it started showing the thumbnails.

---

### Post by currentshaft on 2024-06-28
.

---

### Post by Claus7 on 2024-07-06
Hello,

> **currentshaft said:**
> Doesn't help me. I don't have thumbnails for any files on my Ubuntu 24 installation.

I think you have to try what is mentioned under here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256/comments/33](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2047256/comments/33)

Regards!

---

### Post by currentshaft on 2024-07-07
remo

---

### Post by Claus7 on 2024-07-07
Hello,

as far as I know ubuntu devs do not appear very often here. You could mention your issue under launchpad. If you have the same issue with ubuntu desktop icons you could add yourself as affected here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/2064849](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/2064849)

even if noble is a stable release, the point release which is expected during August, I hope that it will short out many bugs. Unfortunately, I do not have any other ideas on how to fix this issue. 

Just a remark: it wouldn't be a bad idea that updating the thread with your efforts and what it happened. Even if it wasn't successful it would have been helpful to know the result. 

Also: are you getting the same thing under vb for example? Do you have any other account at the same computer that is affected? Are you sure that the fresh installation went fine? There are cases that the installation doesn't go well due to hardware issues. The things I mention might not be part of your case, yet since image thumbnails are not an issue any more under Files (formerly named as nautilus) this might be a reason for the bug you are facing.

Regards!

---

### Post by bloozguy on 2024-09-07
I went to 24.04.1 yesterday and am sorry I did.
The thumbnails no longer show and "sudo apt install apparmor -t noble-proposed" does not work"  :

"**E: The value 'noble-proposed' is invalid for APT::Default-Release as such a release is not available in the sources**"

Do I have to go to Nemo??

I saw somewhere that a bug is "confirmed" but that was a while ago now.

I also had to futz around to get some apps working and also had to play with Tweak to get half descent text.

---

