---
title: "Ubuntu Gutsy PXE install server"
date: 2007-12-18
forum: Server Platforms
---

### Post by Centaur5 on 2007-12-18
I followed this howto [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer) along with many others that gave the same instructions but for some reason I get this error when trying to boot a client off the network:

PXE-E32: TFTP open timeout

I also have the following errors in /var/log/syslog on the server which constantly spams the log file:

Dec 18 16:08:49 wally inetd[4131]: /usr/sbin/in.tftpd: exit status 0x4c00
Dec 18 16:08:59 wally in.tftpd[14220]: received address was not AF_INET, please check your inetd config

I once had this operational a year ago using Edgy using that same howto and it was a piece of cake.  I don't know what I did wrong this time or if it's a bug.  I googled for hours and came across some information that the error in syslog could be a result of ipv6 support but I don't know if that applies in this situation.

---

### Post by loyeyoung on 2007-12-20
I had a similar problem. Ubuntu has been changing the way it configures networking, as well as its use of inetd. Consequently, a different procedure is indicated. 

Use the instructions written by Christer Edwards at [ Ubuntu-Tutorials]("http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/") for a more current procedure. 

BTW -- Christer writes an enormous number of technically solid tutorials. It is not possible for any one person to document everything about a system that is moving as fast as Linux / [U, Ku,Xu, Edu, Go, *] buntu, but he is making a concerted effort. His approach is almost always best practice or damn close to it. Plus, he has a healthy dose of paranoia, which gives him a sensitivity to security issues. 

Loye Young
IYCC
Laredo, Texas
[http://www.iycc.biz](http://www.iycc.biz)

---

### Post by kaapstorm on 2008-02-12
loyeyoung is right about things changing. inetd is emphasising use of IPv6. If you change the tftpd entry in /etc/inetd.conf you'll be sorted. 

I commented out this line:

#tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

And copied it to this:

tftp           dgram   udp4     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

(Note: all that changed is "udp" became "udp4" )

After that my PXE boot worked fine.

---

### Post by Centaur5 on 2008-02-13
Thanks for your replies.  I first tried the other howto that loyeyoung posted and that just made the error message say something slightly different although I didn't log it.  I was now anxious to try putting udp4 because I've noticed in a lot of forums that I was googling through that a lot of people were mentioning that the AF_INET error was a result of ipv6 and they were trying to disable ipv6 support without recompiling the kernel.  Unfortunately putting udp4 still didn't make my PXE boot work and instead it never even starts loading the pxelinux.0 file when I have that set.  I think this is real bizarre that I can't get something to work that I had up and running in no time 8 months ago.

---

### Post by paul86uk on 2008-03-03
i cant even get that far, looks like my ubuntu distro doesnt have any of the apps it needs, so if any of you could point me in the direction of downloadable versions of tftpd syslinux and dhcp3??

---

### Post by bbarrons on 2008-03-03
PAul, which tftp did you install? I had alot of problems getting it to work as well. I can get it working now just fine , I have trouble getting the install files to serve..... I end up using the us mirror instead but pxe connects fine.

---

### Post by paul86uk on 2008-03-04
none at all, as i stated earlier it appears to be absent from my install, cannot find tftpd, inetd, or syslinux...... also the network the ubuntu system is connected to is quite heavily protected so getting it onto the internet with that machine isnt possible, which is why ive asked for a downloadable version....

---

### Post by Centaur5 on 2008-03-10
Thanks to faulkes I was able to get my PXE install up and running a few weeks ago.  He informed me that with Gutsy's changes for IPV6 support I needed to use xinetd instead of inetd-utils.  I followed this howto except for I used DHCP and tftpd-hpa because that package is required for LTSP.

[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

Thanks for the help everyone and I hope this helps somebody else out.

---

