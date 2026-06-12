---
title: "Xen hang on shutdown"
date: 2012-12-04
forum: Virtualisation
---

### Post by dangerjunkie2002 on 2012-12-04
Hi,

I'm having an issue with Xen 4.2 running on Ubuntu 12.04.

The install is an Ubuntu 12.04-x64 host with two Ubuntu 12.04-x64 guests and one Windows server 2008 R2 guest with the signed PV drivers. I'm using the XL toolkit.
 
I'm suffering an issue where the machine gets stuck at the "Will now reboot" line when the host is rebooted while the guests are still running. If I shut all the guests down using "xl shutdown" the guests do terminate properly (after about 30 seconds). If I then do a reboot on the host, it completes cleanly.
 
If I don't shutdown the guests, I have observed some possibly strange behaviour during the host shutdown before it hangs. In the shutdown progress I see:
 
> Stopping xenconsoled
> WARNING not stopping xenstored as it cannot be restarted
> Shutting down Xen domains: Linuxguest1 (shut) Linuxguest1 (shut) Linuxguest2 (shut) Linuxguest2 (shut) Windowsguest (shut) SHUTDOWN_ALL * [done]
 
The things I think are strange are that the two Linux guests are listed twice in the shutdown line despite each only being running once and that it blows straight through the line saying "[done]" without waiting for the guests to terminate. It then appears to unmount the discs before all the guests have wrapped up so they never do terminate. If I leave it, I get repeated kernel warnings that the reboot process has been delayed for more than 120 seconds. I waited over 300 seconds (the time specified in XENDOMAINS_STOP_MAXWAIT) but it doesn't time out and recover.
 
I looked in the Xen logs and they say that all the guests are waiting to die but then nothing. I'm not sure if this is because the guests aren't terminating or if it's because the wait didn't happen and the discs are getting unmounted before the log gets written. If I do a manual "xl shutdown -w" on each of the guests, it does indeed wait and report successful shutdown, just not when it's happening automatically on a host reboot or shutdown.

My xendomains file contains:
 
XENDOMAINS_SYSRQ=""
XENDOMAINS_USLEEP=100000
XENDOMAINS_CREATE_USLEEP=5000000
XENDOMAINS_MIGRATE=""
XENDOMAINS_SAVE=
XENDOMAINS_SHUTDOWN="--halt --wait"
XENDOMAINS_SHUTDOWN_ALL="--all --halt --wait"
XENDOMAINS_RESTORE=false
XENDOMAINS_AUTO=/etc/xen/auto
XENDOMAINS_AUTO_ONLY=false
XENDOMAINS_STOP_MAXWAIT=300
 
 
I disabled the save and restore options because I am using PCI passthrough and trying to restore a saved VM caused the machine to crash at boot.
 
I'm wondering if these problems are something to do with me using xl as most of the examples and references to the settings mention xm.
 
Do you have any suggestions why this hanging or why the "--wait" in xendomains doesn't seem to be having any effect please? I found a Bitkeeper commit to fix a bug where "-w" was respected by xl but "--wait" wasn't but changing the options in xendomains to "-w" doesn't seem to make any difference. I also tried shifting the Xen shutdown to the first item in the shutdown list but saw no improvement.
 
Thanks,
Paul.

---

