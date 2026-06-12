---
title: "Vmware Edgy Madwifi Ath0 Networking Virtual Machine"
date: 2006-10-27
forum: Virtualisation
---

### Post by overmetal61 on 2006-10-27
I am not able to get my vmware working in Edgy with Madwifi Ath0 Wireless card..  Bridged networking on /dev/vmnet0 keeps failing.  When go to run vmware it says re-run vmware-config.pl

1. I have the kernel headers installed

Here is the Log from DMESG
[17217586.196000] bridge-ath0: enabling the bridge
[17217586.196000] bridge-ath0: can't bridge with ath0, bad header length 88
[17217586.196000] bridge-ath0: interface ath0 is not a valid Ethernet interface
[17217586.196000] bridge-ath0: can't bridge with ath0, bad header length 88


Here is Log of Terminal:

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                 failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

---

### Post by krnlpanik on 2006-10-28
This behavior is due to the fact that the madwifi drivers are not 100% compatible with the ethernet standard, and the vmware code checks the interface characteristics before allowing itself to bring up the bridge.

It usually shows up in the system logs with:
Bridged wireless: can't bridge with ath0, bad header length 88 ...

The following procedure fixes the issue:

Start a root shell:

sudo bash

Install your kernel headers (if you dont already have them)

apt-get install linux-headers-`uname -r`

and install some needed packages to compile the modules:

apt-get install build-essential bin86 sharutils

Get a recent copy of the source code from [http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)

cd /usr/src
wget [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r1784-20061027.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r1784-20061027.tar.gz)
tar -zxvf madwifi-ng-r1784-20061027.tar.gz
cd madwifi-ng-r1784-20061027

Then, you'll need to edit the file in ath/if_ath.c, I use vi, but gedit seems popular too.
vi ath/if_ath.c

Remove (or comment out) the following code from the file:
---
#ifdef USE_HEADERLEN_RESV
        dev->hard_header_len += sizeof(struct ieee80211_qosframe) +
                                sizeof(struct llc) +
                                IEEE80211_ADDR_LEN +
                                IEEE80211_WEP_IVLEN +
                                IEEE80211_WEP_KIDLEN;
#ifdef ATH_SUPERG_FF
        dev->hard_header_len += ATH_FF_MAX_HDR;
#endif
#endif
---
Now, make the modules:

make clean
make
make install

It will build (hopefully:)) and then ask if you want to do with the old modules.  Remove them.

Then, you have to tell the system to use the new modules at boot time.

vi /etc/modules

and add "ath_pci" (w/o the quotes) to the bottom of the file.

Reboot the machine, login again, and start a new shell.

If all went well, the new version will now be running, and will show up at boot time with the version of the code you downloaded earlier.

root@box:/# dmesg | grep ath_pci
[17179585.564000] ath_pci: 0.9.4.5 (svn r1784)
root@box:/#

Now, rerun vmware-config.pl, bridge vmnet0 to ath0, and now everything works the way it should.

---

### Post by overmetal61 on 2006-10-29
Wonderful! Thanks!!

---

### Post by stigger on 2006-11-06
hi all,

i got a problem compiling the module.
When i compile it, i got the following error:
           
             
In file included from   /usr/src/madwifi-ng-r1784-20061027/ath/if_ath_pci.c:326:
/usr/src/madwifi-ng-r1784-20061027/ath/../release.h:38:24: error: svnversion.h: No such file or directory
make[2]: *** [/usr/src/madwifi-ng-r1784-20061027/ath/if_ath_pci.o] Error 1
make[1]: *** [_module_/usr/src/madwifi-ng-r1784-20061027/ath] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Fehler 2

Any idea to solve it

thanks

stig

---

### Post by vinboy on 2007-01-24
wow.
thanks.
I spent weeks trying to look for an anwer, now I got it right here.
fast and easy.

thank you so much :guitar:

---

### Post by davekenny on 2007-01-26
thanks!!!
it works if I use the verion for madwifi listed above.
at first I tried to use the lastest list on the site but if doesn't work.

Thanks again :KS 

now if I can get the OpenOffice base form wizard to finish...

dkenny

---

### Post by in_flu_ence on 2007-02-11
It works perfect for me too. Thanks for the tips. I think it might be good to put some summarized sticky since many are facing similar problem with vmware. This will give user more options: vmware. virtual box, xen, etc.

Thanks again

---

### Post by cn4385 on 2007-04-10
Hi There,

I've used the solution detailed above and it fixed my vmware issues. However it seems that after applying this fix to the madwifi driver my machine freezes when accessing the wireless connection.

For example, if I use email or firefox or access the internet through a vmware installation it works for a minute or two then freezes completely. I can work on the machine for hours without a problem but as soon as I start accessing the internet I get a freeze...

any ideas?

---

### Post by in_flu_ence on 2007-04-11
care to tell what model of ur wireless card?

I have used a netgear wireless card and it seems to work perfectly fine using vmware. I even use it to watch streaming video with no interruption.

---

### Post by in_flu_ence on 2007-04-20
The patch doesn't seem to work on feisty. Did i miss something?
I can make vmware to run very smoothly with eth0 (wired) and I have to run the vmware-any-any patch (otherwise it won't compile properly).

I use the later madwifi file (20070417). Not sure if there is any issue in that for those who try?

---

### Post by desktophero on 2007-05-05
The "how to" on this post fixed my issue with ath0 and VMWARE Workstation  Beta

Acer 5610Z
2 Gigs RAM


I can now use eth0 or ath0 for internet connectivity in VMWare. Thanks for the great step by step!

---

### Post by buckmaster60 on 2007-05-18
Great job!  I just adjusted your doc to use the newest version of madwifi.  Thanks for the post!

---

### Post by Atomic Dog on 2007-06-29
This worked perfectly on my toshiba satellite with atheros adapter.  Thanks!

...well for some reason upon reboot I lost my wireless device.  Re installed  the driver(s) and it is working again  ...very strange.

---

### Post by pangloss on 2007-09-26
Thanks for this thread! Although I followed a slightly different process to get things working, this thread was the key!

I have an Atheros AR5006EXS (5424 chipset) and installing VMWare Workstation 6 with bridged networking for ath0 was failing. I used the madwifi-0.9.3.2 release with the one-line patch described at [http://madwifi.org/ticket/407](http://madwifi.org/ticket/407) and successfully installed VMWare 6.0.1 build-55017.

---

### Post by Malibyte on 2008-01-31
I know that his is an old thread, but I'm still having this issue on Kubuntu Feisty (fully updated).  I have a Proxim atheros card that works fine in Linux, but when I try to use the wireless as a bridged interface under VMware Workstation 6, it comes up saying /dev/vmnet0 (bridged to ath0) isn't available.

Here's the relevant dmesg info:

[ 1433.792000] bridge-ath0: enabling the bridge
[ 1433.792000] bridge-ath0: can't bridge with ath0, bad header length 88
[ 1433.792000] bridge-ath0: interface ath0 is not a valid Ethernet interface
[ 1433.792000] bridge-ath0: can't bridge with ath0, bad header length 88


I tried the above using the latest madwifi-ng source code (20080201).  The lines of code mentioned in the HOWTO above no longer exist (replaced by an #include).  Figuring that this issue had been addressed, I compiled and installed the new module, and it's being used:

[   21.908000] ath_pci: svn r3318
[   22.632000] ath_pci: wifi0: Atheros 5212: mem=0x3c000000, irq=10

However, this did not fix the problem...I still see the same info in dmesg, and VMware still doesn't work with ath0.  

Anyone got this working??

**EDIT** - I changed the settings in the VM to set the first Ethernet interface from "bridged" to "Custom" (/dev/vmnet0).  I no longer get the error message on bootup, but in the VM (in this case WinBloze XP), the interface doesn't work with either a static IP or with DHCP. (it shows that it's trying to send packets, but none are received; it comes up saying that there is "limited or no connectivity").


Thanks
Bob

---

### Post by Malibyte on 2008-02-04
OK, I seem to have found the fix - at least on the Linux side:

[http://madwifi.org/attachment/ticket/407/madwifi-ng-r1866-no-headerlen-resv.patch](http://madwifi.org/attachment/ticket/407/madwifi-ng-r1866-no-headerlen-resv.patch)

After making these changes and recompiling, the bridge seems to work - partway.  I can now assign an IP address to the interface in the WinXP guest, and ping it from the Ubuntu host, and ping the "real" Ubuntu interface from the WinXP guest.  However, I can't ping the gateway machine from the guest interface (obviously, I can ping the gateway from the Linux host).   Also, trying to get an IP address on the WinXP interface via the DHCP server on the gateway machine does not work.

I also tried this when setting the Ethernet interface as "Custom" - /dev/vmnet0 instead of "Bridged" in the VM settings.

If I enable the hard-wired interface, I can get out to the Internet from the guest.  So I still have a problem with the VMware bridge to the wireless interface, but I'm closer.  Any ideas?

Thanks in advance - Bob

---

### Post by danweston on 2008-02-25
I modified the directions a bit for the latest version of the madwifi drivers.

 madwifi-ng-r3362-20080224.tar.gz

The code section that needs to be commented out has moved to to

ath/if_ath.c

Otherwise, the directions worked just fine for me.

thanks

Dan Weston

---

### Post by Malibyte on 2008-03-02
I got the new drivers and modified the code as above, recompiled.  Still no joy.

DHCP on the XP guest doesn't work.
If I manually assign an IP address, I can ping the native Ubuntu ath0 IP and vice-versa.

However, I still can't ping the gateway from the XP guest.

Any insight would be appreciated....thanks.

---

### Post by tom17 on 2008-06-03
I'm at exactly the same point as you Malibyte. Did you ever find a solution?

Tom...

---

### Post by Malibyte on 2008-06-04
> **tom17 said:**
> I'm at exactly the same point as you Malibyte. Did you ever find a solution?

Tom...

Tom: unfortunately not.  I can get the guest and host network wifi interfaces to ping each other but can't get to my gateway from the guest OS.  :confused:

---

### Post by Efekt on 2008-06-10
Here is a solution that worked for me, and it combined two steps which I believe are necessary. This is using Ubuntu 64-bit Hardy with Workstation 64-bit 6.0.4.
 The first step is the madwifi modification above, while the second I found in the link below. This should solve the problem and you should have a working bridged ethernet to the ath0 device. Hope this helps!

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/why-is-wifi-internet-not-working-with-vmware-6.x-and-linux-kernel-2.6.22-587021/#post2905568](http://www.linuxquestions.org/questions/linux-wireless-networking-41/why-is-wifi-internet-not-working-with-vmware-6.x-and-linux-kernel-2.6.22-587021/#post2905568)

---

### Post by angus.hendrick on 2008-12-06
krnlpanic you are an eternal nuclear powered bad a$$ in my book. That solution worked beautifully.  Thanks so much.

---

