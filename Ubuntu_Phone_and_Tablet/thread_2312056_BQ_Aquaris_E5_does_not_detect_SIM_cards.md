---
title: "BQ Aquaris E5 does not detect SIM cards"
date: 2016-02-01
forum: Ubuntu Phone and Tablet
---

### Post by multiplexd on 2016-02-01
Hello all,

Due to my own curiosity getting the better of me, I have a BQ Aquaris E5 HD Ubuntu Edition which now does not detect SIM cards at all.

Up until recently, the phone has worked absolutely fine although I admit that I have occasionally used the terminal app in order to remount the root filesystem read/write from the default of read only so I can run apt-get to update the installed packages. In retrospect this is **not a good idea** as I later discovered.

However, as of this posting, Ubuntu Touch OTA-9 was recently released. What happened was I did the update to OTA-9, then later on the same day (and without rebooting the phone) I went into the terminal app and did all the necessaries to get apt-get to work. I ran apt-get update and then apt-get upgrade. There were packages held back which could have been installed via apt-get dist-upgrade, however I did not do this due to lack of time. The phone was switched off shortly afterwards.

The following day, I tried to turn the phone on, however it got stuck at the boot screen and just hung there with the BQ logo showing. Having enabled developer mode previously, I tried to connect to the phone via adb in case it was simply that the GUI wasn't starting properly, however this did not work. After a little bit of frantic googling, I discovered factory mode (boot the phone holding the power and the volume down buttons down) and poked around a little over adb, however I couldn't see anything useful there. After that I think I managed to get to the bootloader (boot while holding power and volume up) and booted through recovery mode. After that the phone booted properly, however the current problem then manifested - the phone couldn't detect the SIM cards (and I tried several different SIM cards as well, however none of them were detected at all).

I then tried to reflash Ubuntu on to the phone using ubuntu-device-flash, however this didn't work, nor did a full reset from within Ubuntu on the phone. After that I tried flashing older versions of Ubuntu Touch to the phone, however the phone wouldn't reinstall at all, even when using the specially crafted recovery images from [http://people.canonical.com/~jhm/barajas/](http://people.canonical.com/~jhm/barajas/) and the --recovery-image flag with ubuntu-device-flash. I eventually figured that somehow the recovery image on the hardware had been corrupted, so I reflashed the recovery image to the hardware using fastboot. I then managed to reinstall the latest system image of Ubuntu Touch properly, booting through recovery mode to the first time boot sequence. However, annoyingly, the problem still persisted and the phone refused to acknowledge the presence of any SIM cards.

After this I tried to install a previous image of Ubuntu Touch, however ubuntu-device-flash hangs while pushing the necessary files by adb to the phone and no files were showing up in /cache/recovery on the phone.

In the midst of all this I have tried variously reinstalling the ofono package on the phone (the package responsible for interfacing with the modems I think), reinstalling all the installed packages at once (fails due to complaints about being unable to configure perl-base) and reinstalling all the installed packages one at a time (hangs while trying to reinstall one of the bluez packages - I can't remember which exactly), all to no avail.

I would like to find some way to make the device work properly again, however I am likely to just start going round in circles and make the current state of affairs worse if I just randomly hack away at it any further. Any help that anyone is able to offer would be greatly appreciated.

Many, many thanks in advance.

---

### Post by fakrul-fakrul on 2016-10-21
Any luck? I had the same issue. None of the slots are working. Tried with installing Android, but still the same.

---

### Post by multiplexd on 2016-10-23
(Wow, I didn't expect any replies after this long)

Unfortunately I had to send my handset to BQ in Spain for IMEI repairs - the issue was that the IMEI numbers had been erased from the hardware, which can be done with the flashing tool from their website which is what I ultimately did, I think. However, I do recall that BQ's customer support was very helpful when I asked them for support (I think they paid for shipping the handset back to me following the repairs as well!) - my only heads-up would be that the customer service person I corresponded with didn't natively speak English so I had to make sure I wasn't using any complicated language.

I hope that helps :).

---

