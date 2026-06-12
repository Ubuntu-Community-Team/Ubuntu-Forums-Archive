---
title: "Ubuntu 18.10 | Installation for MSI WS72"
date: 2018-11-20
forum: Tutorials
---

### Post by guillepereira on 2018-11-20
**[SIZE=3]Ubuntu 18.10 [B][SIZE=3]installation [/SIZE]**on MSI WS72[/SIZE][/B]

 (Before the following procedure we got to Ubuntu's installation menu but keyboard, touchpad, and external USB mouse and keyboard were unavailable).
-Plug in a Ubuntu 18.10 installation USB drive and turn on the computer.
-Press F11 at the MSI splash screen to enter the boot menu and choose the USB drive.

 -Press ESC at the very first Ubuntu’s graphic screen, so you get the special installation menu (F1-F6 at the bottom).

 -Now, press F6 ("Other Options") and select options: “acpi=off” and “nolapic”.
-Choose "Install Ubuntu" at the main menu.

 -Proceed with the ordinary installation including updates.

 
 
 ***Solving Post-installation problems:***

 a)The battery indicator doesn’t appear and the laptop doesn’t turn off properly.

 -Enter the BIOS setup pressing DEL at the MSI splash screen at boot.

 -Go to the "Advanced" menu tab and change "Super Charger" option to "AC/Battery".

 -Reboot and edit the grub file $ sudo gedit /etc/default/grub

 -Modify the document adding “acpi=force” at the end of the “GRUB_CMDLINE_LINUX_DEFAULT” line.

 -Update the grub with $ sudo update-grub

 -Reboot and now we can see the battery indicator and the laptop turns off properly.

  b)When the headphones are connected, the speakers don't mute. 
-Workaround: In preferences>sound we can select (S/PDIF) digital output.

c)The second hard disk isn’t detected by the BIOS.
-We haven't got any solution for this by the moment.



 
 ***Fails:***

 -Some FN functions don’t work like fly mode or eco mode.

 -The speakers make sometimes a weird noise.
 -Small occasional slowdowns.
 
 
 ***Checks:***

 -Wi-Fi OK

 -Bluetooth OK

 -Nvidia OK
 -Sound OK

 -Keyboard OK
 -Touchpad OK
 -Webcam OK
 -Turn off with/without power supply OK

---

