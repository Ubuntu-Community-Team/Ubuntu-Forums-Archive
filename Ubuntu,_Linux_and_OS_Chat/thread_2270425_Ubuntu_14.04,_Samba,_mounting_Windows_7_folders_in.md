---
title: "Ubuntu 14.04, Samba, mounting Windows 7 folders in File Manager"
date: 2015-03-22
forum: Ubuntu, Linux and OS Chat
---

### Post by pmi2 on 2015-03-22
Not a request for specific support, just hoping for some discussion here:

Wondering what other people are using for Windows and ubuntu filesharing these days.  I somehow managed to get my system going (I don't have a proper network setup @ my home, and when I did this in the past, it seemed easier with older Linux and Windows versions.)

When I installed 14.04 I had some issues sharing files between my new Linux box and my two older Windows 7 machines - now resolved thanks to this forum, askubuntu.com, a couple other sources, some posts and articles dating back to 2011.  

However, I am wondering if I am simply missing some easier way to get this to work properly?

To get my little server-deprived network running again, I basically first followed directions to edit the two files related to Samba.

/etc/samba/smb.conf
/etc/nsswitch.conf 
(don't think I actually had to change the 2nd one, but directions did call for it)

The other issue seems to be well described in some bug reports from about a year ago.  (It has to do with sessions opened on Windows 7 closing (timing out) while shared Windows folders are still mounted in Ubuntu.  I did not find any info about a potential fix, so I am guessing it is not a priority, probably b/c it does not affect many people.

[http://askubuntu.com/questions/450206/how-to-fix-a-software-caused-connection-abort-error-in-ubuntu-14-04](http://askubuntu.com/questions/450206/how-to-fix-a-software-caused-connection-abort-error-in-ubuntu-14-04)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1312362](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1312362)

[https://bugzilla.gnome.org/show_bug.cgi?id=729298](https://bugzilla.gnome.org/show_bug.cgi?id=729298)

Seems like a lot of work for something that I expected to just work out-of-the-box.  Is there an easier way, or can anyone point me toward a recent discussion. Thanks.

---

