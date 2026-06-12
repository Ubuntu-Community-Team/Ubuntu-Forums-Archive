---
title: "Detecting Windows Bootloader in Ubiquity"
date: 2015-01-03
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-01-03
I can't believe I did it!!

After removing the hdd and letting it sit for a few minutes I was going to try and use my PLOP boot loader CD to Force boot xubuntu.. but then .. at the spur of the moment I chose F10 and then selected to boot xubuntu from UEFI mode and I could not believe my eyes..

---

### Post by ventrical on 2015-01-03
documentation

```

ventrical@ventrical-desktop:~$ efivar -l
605dab50-e046-4300-abb6-3dd810dd8b23-MokListRT
8be4df61-93ca-11d2-aa0d-00e098032b8c-BootCurrent
ef152fb4-7b2f-427d-bdb4-7e0a05826e64-BootFlow
8be4df61-93ca-11d2-aa0d-00e098032b8c-OriginalLang
8be4df61-93ca-11d2-aa0d-00e098032b8c-PostErrorNumber
8be4df61-93ca-11d2-aa0d-00e098032b8c-ConErrDev
8be4df61-93ca-11d2-aa0d-00e098032b8c-ConInDev
8be4df61-93ca-11d2-aa0d-00e098032b8c-ConOutDev
fa27ed46-ba47-4d7d-8913-94366016c912-AtaCtlrInfo
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-UsbMassDevNum
8be4df61-93ca-11d2-aa0d-00e098032b8c-BootOrder
8be4df61-93ca-11d2-aa0d-00e098032b8c-Boot0001
8be4df61-93ca-11d2-aa0d-00e098032b8c-Boot0009
8be4df61-93ca-11d2-aa0d-00e098032b8c-Boot0005
8be4df61-93ca-11d2-aa0d-00e098032b8c-Timeout
8be4df61-93ca-11d2-aa0d-00e098032b8c-Boot0000
8be4df61-93ca-11d2-aa0d-00e098032b8c-Boot0003
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-Setup
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-MfgDefault
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-SetupDefault
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-iFlashUpdateFlag
05a798ea-39ee-40fc-82c5-622582fa634b-main firmware
05a798ea-39ee-40fc-82c5-622582fa634b-recovery firmware
05a798ea-39ee-40fc-82c5-622582fa634b-memory initialization firmware
05a798ea-39ee-40fc-82c5-622582fa634b-backup recovery firmware
015698bc-457c-43f4-b257-f2ac5ed55f28-BadgeBackgroundColor
3812723d-7e48-4e29-bc27-f5a39ac94ef1-ItkBiosModVar
b452fd8a-c9ca-4764-977e-59d839dd861b-Events
30b98b95-dfa3-4501-a3ce-e38c186384a0-CpuS3Resume
af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e-AcpiGlobalVariable
523db52e-5474-423e-9fc1-15adbc1600bc-BiosSynDataStuct
1b838190-4625-4ead-abc9-cd5e6af18fe0-HiiDB
3812723d-7e48-4e29-bc27-f5a39ac94ef1-ItkDataVar
8be4df61-93ca-11d2-aa0d-00e098032b8c-Lang
efc071ae-41b8-4018-afa7-314b185e578b-FirmwareId
6b2dd245-03f2-414a-8c02-9ffc2352e31e-BoardId
94b9e8ae-8877-479a-9842-f5974b82ced3-BoardFeatures
a56074db-65fe-45f7-bd21-2d2bdd8e9652-LegacyDevOrder
8be4df61-93ca-11d2-aa0d-00e098032b8c-ConIn
8be4df61-93ca-11d2-aa0d-00e098032b8c-ConOut
0f7a52a8-62d9-4219-bcb0-365ed9df2dc4-PayLoadChkSum
0f7a52a8-62d9-4219-bcb0-365ed9df2dc4-LastUnLockMode
0f7a52a8-62d9-4219-bcb0-365ed9df2dc4-LastBootMode
8be4df61-93ca-11d2-aa0d-00e098032b8c-MemCeil.
41282ef2-9b5a-4eb7-95d8-d9cd7bdce367-SLP20Magic
d7bd52b0-b2dc-4f08-b467-de50d728f6bd-NBMrcInfo
ec87d643-eba4-4bb5-a1e5-3f3e36b20da9-SetupCpuFeatures
9d0da369-540b-46f8-85a0-2b5f2c301e15-EfiTime
8be4df61-93ca-11d2-aa0d-00e098032b8c-MonotonicCounter
4599d26f-1a11-49b8-b91f-858745cff824-MfgDefaults
4599d26f-1a11-49b8-b91f-858745cff824-StdDefaults
f9861214-9260-47e1-bcbb-52ac033e7ed8-Guid1394
d357c710-0ada-4717-8dba-c6adc7cd2b2a-UUID
70e56c5e-280c-44b0-a497-09681abc375e-DmiData
ventrical@ventrical-desktop:~$ 

```

---

### Post by sudodus on 2015-01-03
Congratulations :KS

---

### Post by ventrical on 2015-01-03
Thanks coach :)

---

### Post by sudodus on 2015-01-03
Yeah, this time I didn't take any part in the testing, just sat on the bench watching the game ;-)

---

### Post by ventrical on 2015-01-03
Just making a further note on this. During my last attempt to detect Windows 8 Bootloader successfully with UEFI I recall that I had enabled network shares during the installation process. Share other computers, printers .. etc... I am never one to enable this but I thought it might help .. so there are three things I did differently  and so I hope I can isolate which one of those things allowed for the succesful install.

Just for the sake of documenting this up to now:

1. Do full install of Windows 8 in UEFI mode <no manual partitions>
2. Enable networks shares when prompted by Windows 8 "Connect to other computers"?
3. Shut down PC after install is done.
4. Disconnect hdd (not sure if it is necessary - but may have something to do with it.
5. Reboot into BIOS and disable UEFI./ Then restart and re-enable UEFI.
6. Restart computer with Trsuty iso (or better yet ) xubuntu 15.04 daily.
7. Choose 'live' mode
8. Hot-plug connect your hdd to running PC. (xubuntu will not detetct hdd so it is fail.
9. Shut down PC and then restart. You will notice that PC will not boot from USB but directly from hdd!! This is a fail. It will appear that something busted with your USB stick (but this is not the case- the hot-swap locked somthing up).

10. Shutdown and remove hdd and USB stick.
11. Reconnect hdd and USB after about 5 minutes.
12 Switch PC back on and choose F10 boot options (or that which your PC offers) then choose your boot from USB option.
13. xubuntu will load up in UEFI mode. Choose 'live'. You will see now after xubuntu is loaded that the hdd is present.
14. Double click the 'install xubuntu to disk' icon.  Follow Ubiquity process . You will see hdd icon flashing off and on ?? why I do not know then you are immediately presented with prompt to install xubuntu alongside of Windows boot loader and it will auto resize for you.

*note* Although when you are in the UEFI shell just after  you pressed F10 during boot up you will notice that GRuB has detected the Windows bootloader. You will also notice (depending on machine) that the Windows Bootloader will be in the UEFI shell . If you want to switch between operating system then I suggest to use the F10 BIOS function and not choose to boot Windows bootloader from GRuB as I have no ttried that yet... but IO do recall I had a problem in the past. I may try that soon but I am just being amazed for a while with my working dual boot Win8/ubuntu UEFI system :) lol

---

### Post by ventrical on 2015-01-03
I have been building a second system- [http://downloadmirror.intel.com/17599/eng/DB43LD_ProductGuide01_English.pdf](http://downloadmirror.intel.com/17599/eng/DB43LD_ProductGuide01_English.pdf)

and I had noticed that the UEFI still had the old <ubuntu> and <Windows Boot Loader> still in there. This was from a failed install back  just less than a year ago. I had Win8 and Ubuntu but not in UEFI mode.  So I am going to try a more direct method using xubuntu 15.04.

 To get rid of those tables I assume that I would have to remove the CMOS battery , but , remember it is UEFirmwareI !!:) so perhaps it is meant to stay until  the next system install .. etc.. That would mean the new install would have to flush the olde  tables and maps out of the UEFI buffers??

Anyways .. keeping it simple I will:


1. Install Win8 to hdd <no manual partitions> in UEFI mode.
2. Enable shares during install.
3. Finish install  <do not remove hdd>
4. Reboot using F10 option and choose  USB. xubuntu 15.04.iso


Regards..

---

### Post by oldfred on 2015-01-03
You have to have removed any folder in efi partition.
Then use efibootmgr to remove extra entries in UEFI menu.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by ventrical on 2015-01-03
> **oldfred said:**
> You have to have removed any folder in efi partition.
Then use efibootmgr to remove extra entries in UEFI menu.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Thanks Oldfred.

```

xubuntu@xubuntu:~$ sudo efibootmgr -v
BootNext: 0004
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0002,0001,0004,0008,0009
Boot0001* ubuntu    HD(2,96800,32000,164d7e13-5a38-4ab7-a0c1-953381850faa)File(\EFI\ubuntu\shimx64.efi)
Boot0002* Windows Boot Manager    HD(2,96800,32000,164d7e13-5a38-4ab7-a0c1-953381850faa)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Network Card    BIOS(6,0,00)IBA GE Slot 00C8 v1327.
Boot0008* INTERNAL EFI SHELL: USB Flash Memory    ACPI(a0341d0,0)PCI(1d,7)USB(2,0)HD(1,3e,3ba6a6,0008250a)File(\EFI\BOOT\BOOTX64.EFI)
Boot0009* Hard Drive    BIOS(2,0,00)        USB Flash Memory1.00.
xubuntu@xubuntu:~$ efibootmgr -b 2 -B
efibootmgr: Boot entry 0002 not found
efibootmgr: Could not delete boot variable: Permission denied
xubuntu@xubuntu:~$ sudo -i
root@xubuntu:~# efibootmgr -b 2 -B
BootNext: 0004
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0001,0004,0008,0009
Boot0001* ubuntu
Boot0004* Network Card
Boot0008* INTERNAL EFI SHELL: USB Flash Memory
Boot0009* Hard Drive
root@xubuntu:~# efibootmgr -b 1 -B
BootNext: 0004
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0004,0008,0009
Boot0004* Network Card
Boot0008* INTERNAL EFI SHELL: USB Flash Memory
Boot0009* Hard Drive
root@xubuntu:~# 

```

Just a reminder ... have to be in root for it to work.

:)

---

### Post by ventrical on 2015-01-03
> **ventrical said:**
> I have been building a second system- [http://downloadmirror.intel.com/17599/eng/DB43LD_ProductGuide01_English.pdf](http://downloadmirror.intel.com/17599/eng/DB43LD_ProductGuide01_English.pdf)

and I had noticed that the UEFI still had the old <ubuntu> and <Windows Boot Loader> still in there. This was from a failed install back  just less than a year ago. I had Win8 and Ubuntu but not in UEFI mode.  So I am going to try a more direct method using xubuntu 15.04.

 To get rid of those tables I assume that I would have to remove the CMOS battery , but , remember it is UEFirmwareI !!:) so perhaps it is meant to stay until  the next system install .. etc.. That would mean the new install would have to flush the olde  tables and maps out of the UEFI buffers??

Anyways .. keeping it simple I will:


1. Install Win8 to hdd <no manual partitions> in UEFI mode.
2. Enable shares during install.
3. Finish install  <do not remove hdd>
4. Reboot using F10 option and choose  USB. xubuntu 15.04.iso


Regards..

Seamless  UEFI xubuntu 15.04 install alongside Windows 8 detected.

  I'll try trusty again another day.

Regards..

---

### Post by ventrical on 2015-01-04
Working trusty daily-live and I get success in UEFI mode and Windows Bootlader detected.

[CODE]
ventrical@ventrical-desktop:~$ sudo efibootmgr -v
** Warning ** : Boot000a is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : Boot000c is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
BootNext: 0004
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0004,0009,000A,000C
Boot0000* Windows Boot Manager    HD(2,96800,32000,cf6354dc-3c32-42aa-a4fe-d138e50eb312)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu    HD(2,96800,32000,cf6354dc-3c32-42aa-a4fe-d138e50eb312)File(\EFI\ubuntu\shimx64.efi)
Boot0004* Network Card    BIOS(6,0,00)IBA GE Slot 00C8 v1327.
Boot0009* Hard Drive    BIOS(2,0,00)        USB Flash Memory1.00.
Boot000a* CD/DVD Drive    BIOS(3,0,00)SATA: HL-DT-ST DVDRAM GH24NS95.
Boot000c* INTERNAL EFI SHELL: WDC WD800JD-00LSA0    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)HD(2,96800,32000,cf6354dc-3c32-42aa-a4fe-d138e50eb312)File(\EFI\BOOT\BOOTX64.EFI)
ventrical@ventrical-desktop:~$ 
[/QUOTE]

No efibootmgr edit was neccessary so a previous assumption I had made was wrong .. now to check and see if Windows 8 still boots.

---

### Post by ventrical on 2015-02-07
Bump!

:)

---

### Post by oldfred on 2015-02-07
What is issue?

---

### Post by ventrical on 2015-02-08
> **oldfred said:**
> What is issue?

kansasnoob had asked a question a while back and I gave him this link and he said he didn't need it .. but I see that you have made contact with him in the new thread he created.

Regards..

---

