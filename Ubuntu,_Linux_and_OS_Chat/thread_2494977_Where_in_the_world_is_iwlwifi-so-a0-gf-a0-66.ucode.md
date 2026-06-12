---
title: "Where in the world is iwlwifi-so-a0-gf-a0-66.ucode"
date: 2024-02-02
forum: Ubuntu, Linux and OS Chat
---

### Post by pilotone on 2024-02-02
Asus Z790-PLUS wifi
running Bodhi
Still rather new at Ubuntu.
The is a new build. I am having a bluetooth problem with "iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-gf-a0-66.ucode failed with error -2"
I looked for i in [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/).
None of the updates contain wlwifi-so-a0-gf-a0-66.ucode.
Anyone know where I can find it?

Thanks

---

### Post by jeremy31 on 2024-02-02
That file was likely deleted because of a bug and it has nothing to do with Bluetooth 
Post results from terminal for ```
sudo dmesg |egrep -i 'blue|firm'
```

---

### Post by pilotone on 2024-02-02
Update.
I found it in one of my files from an earlier download.
What I found is that I would install it with modprobe but it disappears on a reboot.
I don't think it solved the problem anyway. 
Now it isn't available because of a bug.
Any suggestions on how I fix " iwlwifi-so-a0-gf-a0-66.ucode failed with error -2" ?

Thanks much for your response, jeremy31
Sorry I posted it here.
I just saw the note.

---

### Post by jeremy31 on 2024-02-02
I may be able to help if I see results from the command I posted.  I would guess the wifi used iwlwifi-so-a0-gf-a0-64.ucode as that does exist.  The iwlwifi module looks for the newest firmware version and works its way down depending on what kernel is used.  Bluetooth uses firmware in /lib/firmware/intel

---

### Post by pilotone on 2024-02-07
```
sudo dmesg |egrep -i 'blue|firm'
[sudo] password for glb:
[    2.454373] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-gf-a0-66.ucode failed with error -2
[    2.454437] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-so-a0-gf-a0-65.ucode failed with error -2
[    2.455708] iwlwifi 0000:00:14.3: loaded firmware version 64.97bbee0a.0 so-a0-gf-a0-64.ucode op_mode iwlmvm
[    3.439472] Bluetooth: Core ver 2.22
[    3.439485] NET: Registered PF_BLUETOOTH protocol family
[    3.439485] Bluetooth: HCI device and connection manager initialized
[    3.439489] Bluetooth: HCI socket layer initialized
[    3.439490] Bluetooth: L2CAP socket layer initialized
[    3.439492] Bluetooth: SCO socket layer initialized
[    3.444288] Bluetooth: hci0: Device revision is 0
[    3.444289] Bluetooth: hci0: Secure boot is enabled
[    3.444289] Bluetooth: hci0: OTP lock is enabled
[    3.444290] Bluetooth: hci0: API lock is enabled
[    3.444290] Bluetooth: hci0: Debug lock is disabled
[    3.444290] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.444291] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[    3.444952] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[    3.479263] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.479264] Bluetooth: BNEP filters: protocol multicast
[    3.479266] Bluetooth: BNEP socket layer initialized
[    4.812369] Bluetooth: hci0: Waiting for firmware download to complete
[    4.813267] Bluetooth: hci0: Firmware loaded in 1336245 usecs
[    4.813293] Bluetooth: hci0: Waiting for device to boot
[    4.829268] Bluetooth: hci0: Device booted in 15617 usecs
[    4.835942] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[    4.837307] Bluetooth: hci0: Applying Intel DDC parameters completed
[    4.841332] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[   15.213616] Bluetooth: RFCOMM TTY layer initialized
[   15.213621] Bluetooth: RFCOMM socket layer initialized
[   15.213623] Bluetooth: RFCOMM ver 1.11
[ 8198.772451] Bluetooth: hci0: Device revision is 0
[ 8198.772454] Bluetooth: hci0: Secure boot is enabled
[ 8198.772455] Bluetooth: hci0: OTP lock is enabled
[ 8198.772455] Bluetooth: hci0: API lock is enabled
[ 8198.772456] Bluetooth: hci0: Debug lock is disabled
[ 8198.772456] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[ 8198.772457] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[ 8198.772461] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[ 8200.141444] Bluetooth: hci0: Waiting for firmware download to complete
[ 8200.141446] Bluetooth: hci0: Firmware loaded in 1336899 usecs
[ 8200.141513] Bluetooth: hci0: Waiting for device to boot
[ 8200.157626] Bluetooth: hci0: Device booted in 15798 usecs
[ 8200.157630] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[ 8200.159667] Bluetooth: hci0: Applying Intel DDC parameters completed
[ 8200.163510] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[ 9580.877459] Bluetooth: hci0: Device revision is 0
[ 9580.877462] Bluetooth: hci0: Secure boot is enabled
[ 9580.877463] Bluetooth: hci0: OTP lock is enabled
[ 9580.877463] Bluetooth: hci0: API lock is enabled
[ 9580.877463] Bluetooth: hci0: Debug lock is disabled
[ 9580.877464] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[ 9580.877465] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[ 9580.877715] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[ 9582.246680] Bluetooth: hci0: Waiting for firmware download to complete
[ 9582.247329] Bluetooth: hci0: Firmware loaded in 1337512 usecs
[ 9582.247356] Bluetooth: hci0: Waiting for device to boot
[ 9582.263329] Bluetooth: hci0: Device booted in 15609 usecs
[ 9582.263347] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[ 9582.265451] Bluetooth: hci0: Applying Intel DDC parameters completed
[ 9582.269383] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[34913.691939] Bluetooth: hci0: Device revision is 0
[34913.691941] Bluetooth: hci0: Secure boot is enabled
[34913.691942] Bluetooth: hci0: OTP lock is enabled
[34913.691942] Bluetooth: hci0: API lock is enabled
[34913.691943] Bluetooth: hci0: Debug lock is disabled
[34913.691943] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[34913.691944] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[34913.691948] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[34915.061410] Bluetooth: hci0: Waiting for firmware download to complete
[34915.061962] Bluetooth: hci0: Firmware loaded in 1337903 usecs
[34915.062030] Bluetooth: hci0: Waiting for device to boot
[34915.078012] Bluetooth: hci0: Device booted in 15670 usecs
[34915.078020] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[34915.079999] Bluetooth: hci0: Applying Intel DDC parameters completed
[34915.084019] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[92934.267523] Bluetooth: hci0: Device revision is 0
[92934.267524] Bluetooth: hci0: Secure boot is enabled
[92934.267525] Bluetooth: hci0: OTP lock is enabled
[92934.267525] Bluetooth: hci0: API lock is enabled
[92934.267526] Bluetooth: hci0: Debug lock is disabled
[92934.267526] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[92934.267527] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[92934.267711] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[92935.637668] Bluetooth: hci0: Waiting for firmware download to complete
[92935.638556] Bluetooth: hci0: Firmware loaded in 1338713 usecs
[92935.638595] Bluetooth: hci0: Waiting for device to boot
[92935.654746] Bluetooth: hci0: Device booted in 15787 usecs
[92935.654782] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[92935.656689] Bluetooth: hci0: Applying Intel DDC parameters completed
[92935.660669] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[109741.853424] iwlwifi 0000:00:14.3: Loaded firmware version: 64.97bbee0a.0 so-a0-gf-a0-64.ucode
[142753.815326] Bluetooth: hci0: Device revision is 0
[142753.815329] Bluetooth: hci0: Secure boot is enabled
[142753.815330] Bluetooth: hci0: OTP lock is enabled
[142753.815330] Bluetooth: hci0: API lock is enabled
[142753.815331] Bluetooth: hci0: Debug lock is disabled
[142753.815331] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[142753.815332] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[142753.815335] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[142755.185043] Bluetooth: hci0: Waiting for firmware download to complete
[142755.185339] Bluetooth: hci0: Firmware loaded in 1337893 usecs
[142755.185354] Bluetooth: hci0: Waiting for device to boot
[142755.201402] Bluetooth: hci0: Device booted in 15685 usecs
[142755.201405] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-1040-0041.ddc
[142755.203578] Bluetooth: hci0: Applying Intel DDC parameters completed
[142755.207360] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[174936.228401] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[174936.229542] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[174936.229551] Bluetooth: hci0: Boot Address: 0x100800
[174936.229552] Bluetooth: hci0: Firmware Version: 252-24.23
[174936.229553] Bluetooth: hci0: Firmware already loaded
[175129.737288] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[175129.738493] Bluetooth: hci0: Found device firmware: intel/ibt-1040-0041.sfi
[175129.738501] Bluetooth: hci0: Boot Address: 0x100800
[175129.738502] Bluetooth: hci0: Firmware Version: 252-24.23
[175129.738502] Bluetooth: hci0: Firmware already loaded
```

Sorry I didn't post this sooner.  I missed your request for the output and was getting tired of trying to fix the problem.

Thanks for your patience.

Asus Z790 Plus WIFI

---

### Post by jeremy31 on 2024-02-07
Can you post results from terminal for ```
lsusb
```

---

### Post by pilotone on 2024-02-08
sudo lsusb
[sudo] password for glb:
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 002: ID 0b05:19af ASUSTek Computer, Inc. AURA LED Controller
Bus 001 Device 004: ID 8087:0033 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks for your reply.

---

### Post by jeremy31 on 2024-02-08
You may just have to do ```
bluetoothctl
power on
scan on
exit
```

---

### Post by pilotone on 2024-02-08
I have done that multiple times.
It may or may not pick up a device.  If it does it disappears.  And the error code remains.
In the last month of working with it I got it to connect to a wifi radio once. 
It never sees my wifi speakers.
However avahi-browse does sees everything including my speakers.
 wlp0s20f3 IPv4 Living Room                                   _spotify-connect.

That brings me to the question.
Will a different kernel make a difference? Something supporting newer hardware?
If the motherboard is the problem will adding a dongle work?

Thanks for your help. Hope you aren't too frustrated. LOL

---

