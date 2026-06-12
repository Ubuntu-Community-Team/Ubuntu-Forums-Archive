---
title: "Windows guest crashes when usb enabled"
date: 2009-11-05
forum: Virtualisation
---

### Post by haxwithaxe on 2009-11-05
Hey all,
I have a windows guest running in virtualbox3. I can enable usb support, and use some non thumbdrive usb devices but if I enable/"insert" a thumbdrive windows freezes and my cpu maxes out until I kill the vm.  If I boot it up with it enabled the same thing happens except it never gets to the login screen. Any ideas?
Vbox Log:
...
 00:01:34.566 /VUSB/0/cUrbsInPool                     0 count
00:01:34.566 /VUSB/1/cUrbsInPool                     0 count
00:01:34.566 ********************* End of statistics **********************
00:01:34.811 USB: Successfully reset device '9c98b7d0[proxy 0951:1607]'
00:01:34.824 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
00:01:35.023 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={fd443ec1-0006-4f5b-9282-d72760a66916} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false

Guest: 
   OS:Windows Server 2003 R2
   ACPI: none
   CPU passthrough: none
Host:
   OS:Ubuntu Karmic
   Thumbdrive: Kingston Data Traveler 8GB

I also asked for help here:
[http://forums.virtualbox.org/viewtopic.php?f=2&t=24330&p=107990](http://forums.virtualbox.org/viewtopic.php?f=2&t=24330&p=107990)
and here:
[http://www.virtualbox.org/ticket/5425](http://www.virtualbox.org/ticket/5425)

---

