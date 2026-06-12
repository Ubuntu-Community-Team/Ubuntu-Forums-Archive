---
title: "Live DVD boot &amp; WIFI: Medicine against hardware viruses?"
date: 2016-02-16
forum: Security
---

### Post by xenon3 on 2016-02-16
A security expert told me that in principle there can be hardware  viruses (like key loggers), build in, straight from the factory, in any  hardware part like CPU, motherboard, hard drive etc etc, sending his key  log data over the internet, back to the factory or any other kind of  (malicious) party.   

But what If you boot from a Live DVD and use "WPA2-PSK encryption enabled and WPS disabled" WIFI?

Hardware  key loggers running outside the Linux OS shell cannot send  their data  then over the Internet anymore (because of the encryption),  not even if the logger is build in network card,  because how  intelligent must the logger program be to get track of the  (strong)  WIFI key? Out of the hundred passwords you use? And the logger  program  cannot know all the thousands modem settings management programs  from  all Internet Service Providers? A human could fish out the key  perhaps.

Hardware key logger is either an embedded program in one  of the chips  or in or on a specially designed chip somewhere in the  hardware, so  reflashing all the chips does not help.

Is this procedure safe? To protect your privacy and security from cyber criminals and too much big brother?

---

### Post by Patrick_Van_Esch on 2016-02-17
> **xenon3 said:**
> 
Hardware  key loggers running outside the Linux OS shell cannot send  their data  then over the Internet anymore (because of the encryption),  not even if the logger is build in network card,  because how  intelligent must the logger program be to get track of the  (strong)  WIFI key? Out of the hundred passwords you use? And the logger  program  cannot know all the thousands modem settings management programs  from  all Internet Service Providers? A human could fish out the key  perhaps.


If I'm wrong, I'll learn something, but I don't think that's the way it works.  The WEP (haha) / WPA / WPA2 encryption actually happens, as far as I know, in the wireless hardware, NOT in the OS.  The OS just sends the pass phrase to the wireless hardware.  The connection between the CPU and the wireless hardware in your PC is "still in the clear" as far as I know (if not, please correct me !).  So your key logger can still send its packets in the clear to the wireless hardware, which will faithfully encrypt it with the key it got from the OS and send it out.

---

### Post by xenon3 on 2016-02-17
Maybe someone knows if Ubuntu runs in its own Sandbox, and other processes, malicious or not, cannot interfere with the LINUX Shell? I think Ubuntu does not have handles for **"Fremdkörper" **processes?

If there is such kind of Sandbox, maybe only 'by-design' (means: is accidentally so and was not intended), how can WPA2-PSK key be retrieved by malicious hardware viruses from this Sandbox, any way?

---

### Post by Patrick_Van_Esch on 2016-02-17
> **xenon3 said:**
> Maybe someone knows if Ubuntu runs in its own Sandbox, and other processes, malicious or not, cannot interfere with the LINUX Shell? I think Ubuntu does not have handles for **"Fremdkörper" **processes?

I cannot understand what you are saying.   What is "ubuntu" in this context ?  The linux kernel ?

---

### Post by xenon3 on 2016-02-17
The OS. Indeed the kernel handles the software / hardware interface

---

### Post by deadflowr on 2016-02-17
> **Patrick_Van_Esch said:**
> If I'm wrong, I'll learn something, but I don't think that's the way it works.  The WEP (haha) / WPA / WPA2 encryption actually happens, as far as I know, in the wireless hardware, NOT in the OS.  The OS just sends the pass phrase to the wireless hardware.  The connection between the CPU and the wireless hardware in your PC is "still in the clear" as far as I know (if not, please correct me !).  So your key logger can still send its packets in the clear to the wireless hardware, which will faithfully encrypt it with the key it got from the OS and send it out.

WPA/WEP/whatever/wifi encryption is encrypted from the machine to the router/access point.
But once it hits that access point, the encryption ends.

Basically your machine encrypts the data, sends out.
Then the router captures that data, decrypts it.
And sends it on it's merry way.

---

### Post by xenon3 on 2016-02-17
Yes, one problem at the time please: man-on-client, not yet man-in-the-middle

---

### Post by Patrick_Van_Esch on 2016-02-17
> **deadflowr said:**
> WPA/WEP/whatever/wifi encryption is encrypted from the machine to the router/access point.
But once it hits that access point, the encryption ends.

Basically your machine encrypts the data, sends out.
Then the router captures that data, decrypts it.
And sends it on it's merry way.

Yes.  But I suppose that the OP was pointing that if some malware is on the hardware/firmware pre-boot level, say, a key logger, that wants to send the grabbed keystrokes over the internet to someone interested in your keystrokes, that this software has no access to the networking function if one uses WPA/whatever wifi encryption, because it would be too hard for that piece of malware to send anything directly to the network, as it cannot encrypt its data stream (which is done by the OS in the mind of the OP).  If the OS is calculating the encrypted stream to the AP, then one might think that the firmware/hardware malware can only see that stream, and cannot add anything to it (well, it can, but then the cryptography would get corrupted, and the AP would refuse it).

However, as far as I understand (although I'm not 100% sure about that myself) it, the actual encryption is not done in the OS by the CPU, but is rather done in the hardware/firmware of the wireless hardware (the *client* hardware in the computer, the network card, or the USB wifi stick, say).  In that case, the data stream to the network hardware (from the OS/CPU) is still in the clear, and it only gets encrypted in the wireless hardware, before being emitted as radio waves.   But then the hardware/firmware malware can without problem send its key logger packets to the network card, just as it would to an ethernet card.  So the encryption itself is not protecting against pre-boot malware "that wouldn't know how to encrypt network packets with the WPA key", because I think that that encryption is only applied later in the data-stream, namely in the networking hardware itself.

All of the above still in the computer (which contains the CPU and the wireless network hardware of course).

> **xenon3 said:**
> The OS. Indeed the kernel handles the software / hardware interface

I'm not sure what you're pointing at with "the kernel is running in a sandbox" but the way I guess you mean it (I can guess wrong), the answer is: of course not !  If the kernel was running in a sandbox, cut off from the hardware, you, the network card, the keyboard, the mouse etc... wouldn't be able to interact with it !  

So no.  If you have a hardware/pre boot firmware infection, then of course the OS (the kernel) is not protected from it.

For instance, if the firmware contains malware that makes the kernel believe that there is an extra keyboard, then that malware keyboard can send keystrokes to the kernel, that will be indistinguishable from the OS viewpoint from you connecting another keyboard and typing instructions.   This is BTW the BADUSB attack in a nutshell.  That keyboard (fake keyboard that can send anything the malware is designed to send) can send all kinds of keyboard commands.  For instance, it can send a Ctrl-Alt-T followed by a lot of shell commands.  The kernel will not know that it got these key strokes from malware, and not from a genuine keyboard that you connected to the computer.

(that would, btw, be the simplest way to send out the grabbed keystrokes over the internet, encryption or not: in exactly the same way as you would send a file to someone over the internet using the command line).

---

### Post by xenon3 on 2016-02-17
You can exclude second keyboard possibility (hard coded). I can't imagine why one would need a second keyboard anyway, perhaps in a cyber war :D

---

### Post by Patrick_Van_Esch on 2016-02-18
> **xenon3 said:**
> You can exclude second keyboard possibility (hard coded). I can't imagine why one would need a second keyboard anyway, perhaps in a cyber war :D

That *would* be a start to a solution to the wide-open security hole that is gaping at us on the USB/firmware level.

But there are several workarounds and it does mean some loss of functionality: for instance, you cannot connect a wireless mouse/keyboard any more to your system.  I could think of a work-around for the firmware/hardware malware: disable the real keyboard, install the malware keyboard, do the deed, then disconnect the malware keyboard, and install the real keyboard again.  At no point there is more than 1 keyboard visible (maybe the OS even sees it as *the same* keyboard).  This can even happen during the init phase, before the full system has booted.

No, reasonably, if your hardware/firmware is compromised, you are in a bad position to protect the OS from that.

In my opinion, the only real step forward will come when there are hardware switches on all firmware that need to be actuated physically in order to update the firmware, and that it is physically not possible to modify firmware without actually pushing physically that button.  That doesn't protect against pre-installed malware, of course, but it would close at least the wide-open hole gaping at us from firmware contamination through "normal" software malware.

---

### Post by xenon3 on 2016-02-18
very clever

---

