---
title: "MATLAB installation tip"
date: 2005-11-15
forum: The Cafe
---

### Post by gostal on 2005-11-15
According to the info on the wiki it is not possible to get the
installation scripts to run off the CD. This is not entirely true!

It appears that during the automounting process the exec bit is not
correctly set even if all looks well in /etc/fstab and /etc/mtab. I've
experienced the same problem with Linux Mandriva (formerly Mandrake). As
far as I can make out this is a bug in the automounting process.

There is a way to remedy the situation without having to copy the CD
contents to the hard drive or for that matter download the installation
files from the Mathworks web page.

The way is to mount manually the CD at a different mountpoint in which
case the exec bit is correctly set and the installation script runs off
the CD just fine. Mathworks has a support page somewhere making a point
of this
([http://www.mathworks.com/support/solutions/data/1-184PH.html?solution=1-184PH)](http://www.mathworks.com/support/solutions/data/1-184PH.html?solution=1-184PH)).
It is not necessary to disable the automatic mounting but som care is
needed so you don't confuse the different mounts. A catch is that you
have to skip in turn the other installation CDs i.e. first manually
mount CD1 and choose to skip the contents of subsequent CDs at the
prompt in the installation program. Then umount and mount CD2 and choose
to skip CD1 etc.

Using this procedure I successfully intalled MATLAB R14 SP3 on both the
Ubuntu and the Mandriva systems. :cool: 

Starting MATLAB, however, gives rice to an error message on the Ubuntu
system :confused: :
/usr/local/matlabR14sp3/bin/util/oscheck.sh: line 134: /lib/libc.so.6:
Åtkomst nekas (Permission denied)

I am, however, not aware of any problems running MATLAB because of this.

Best wishes and thanks for a smashing Linux distro.
Gösta Ljungdahl

PS The Ubuntu system (Breezy Badger) runs on a Dell Latitude CPTs 500
sporting a 500 MHz Celeron processor and 256 MB RAM and the Mandriva
system runs on a Dell Latitude D800 (2 GHz Pentium M, 1 GB RAM)

PPS I've posted a message to [email]ubuntu-doc@lists.ubuntu.com[/email] but since I'm not a member it still awaits moderator approval.

---

