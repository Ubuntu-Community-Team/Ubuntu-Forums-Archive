---
title: "Tiger security warning concerns."
date: 2006-12-06
forum: Server Platforms
---

### Post by chris_andrew on 2006-12-06
Hi, all.

Two of my favourite GNU/ Linux security tools are Bastille and Tiger.

I have just installed and run 

tiger -e

and some secures issues were raised.  Fair enough.  I am addressing them, but came across the following that worried me, so I'd appreciate your thoughts..  The reason is that I am using the "stick" /etc/apt/sources.list, and haven't installed any rogue software.  I am therefore alarmed that the following messages appear:

# Checking installed files against packages...
--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/nvidia_legacy.ko'
does not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/nvidia.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/ltserial.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/ltmodem.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fxusb.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fglrx.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcusb.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcpci.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdslusba.ko'
does not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdslusb2.ko'
does not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdslusb.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdslslusb.ko'
does not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdslsl.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdsl2.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/fcdsl.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/ath_hal.ko' does
not belong to any package.

A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

--WARN-- [lin001w] File `/lib/modules/2.6.17-10-386/volatile/.mounted' does
not belong to any package.


A program installed in your system has probably been not installed by a
package of your Linux packaging system. If this binary has been installed
by the administrator note that /usr/local/ is the place for this files.

Your comments are welcomed.

Thanks,

Chris.

---

