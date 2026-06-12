---
title: "Windows 7 bootmgr with ubuntu studio"
date: 2010-08-08
forum: Ubuntu Studio
---

### Post by Bonechilla on 2010-08-08
I have windows 7 installed on a seperate partition from ubuntu studio however after the install it seems as though grub was destroyed and i cannot load ubuntu. Instead of reinstalling grub it I was wondering if it be possible to change windows 7s boot options similar to xp's boot.ini file in order to load ubuntu studio. What is the proper way to edit this file in order to start either windows or grub or say windows or my ubuntu studio partition

---

### Post by JC Cheloven on 2010-08-11
I think it doesn't make much sense. You need a bootloader, only one, to get the booting stuff done. Dunno whether a windows bootloader can boot other OSes or not (I belive not, but a question for a windows forum anyway).

What IMO makes sense in your case is restoring the grub bootloader at the MRB, and updating grub so that your windows is included as a boot option. 

- Boot from live CD/pendrive (the one you used to install ubuntu). Open a terminal. Run the following commands.
- sudo fdisk -l  # To find out which partition is Ubuntu on. Lets assume /dev/sda1 as an example
- sudo mount /dev/sda1 /mnt  	#  change 'sda1' to match what you saw in fdisk -l
- mount --bind /dev /mnt/dev  	
- chroot /mnt			
- grub-install --recheck /dev/sda	# this loads grub at the mbr
- reboot the pc			# your ubuntu (that you had in HD) should boot

Once in your ubuntu, run in a terminal 
sudo update-grub

At next boot, grub should show alll your installed OS as boot options.

Note.- it's generally adviced to install windows first. I haven't w7 (in fact no w since years), so I don't know if you will run into additional problems due to installing w in a partition which is not the first one, not being installed the first one, etc.

---

