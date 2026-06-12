---
title: "Things I use Ubuntu for."
date: 2010-02-10
forum: The Cafe
---

### Post by megahurts on 2010-02-10
I've been a pretty consistent user of Ubuntu since around 6.10 and I thought I'd share what I actually use it for.

Running DHCP, DNS, NFS, Samba and TFTP/PXE on my home network via dnsmasq.  We are a family of six and between us have six laptops, eight desktops, and three Xbox360s not to mention assorted smartphones and pdas. The cheapo wifi router that replaced an ageing linksys WRT54 has a habit of dropping it's DHCP server every couple of days, I re-purposed an old IBM thinkpad with Server 9.10 and a 1TB USB drive to take over. dnsmasq provides DHCP and DNS forwarding out of the box as well as a TFTP server for PXE boots.

I've got the 9.10 LiveCD available via PXE boot as well as a custom LiveCD with various tools for recovering data etc without having to worry about finding either a DVD or USB stick for when one of the XP PCs goes south, and I can also boot into clonezilla for rebuilding.  Samba is used both for normal fileserver duties and also for serving the various images of Windows.

Out HTPC is running XBMC on top of Unbuntu pulling media files via NFS from the server.

My laptop is a standard 9.10 install that is mostly used for casual browsing and reading various e-books with fbreader.

My desktop dual boots 64bit 9.10 and XP since no matter what I try I can't seem to get Cinema4D working correctly on Ubuntu.

---

