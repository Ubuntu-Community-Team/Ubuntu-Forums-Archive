---
title: "Ubuntu 12.04 on imac 2011(12,1)"
date: 2012-07-02
forum: Tutorials
---

### Post by Lunarts on 2012-07-02
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12179635#post12179635](http://ubuntuforums.org/showthread.php?p=12179635#post12179635)


Support threads regarding the wiki and it's content should be created in a suitable forum.


I tried editing my previous topic about this, but the edit button was gone; I tried to contact staff, so they could analyse my previous tutorial version and put it here instead of community Cafe and receive no response; so here it is, improved, updated and under a new topic:

[img]http://www.lunarts-studio.com.br/file_hosting/blendavatar.jpg[/img]

  	 	 	 	 	 	    [FONT=Liberation Serif, serif]*Article by Lunarts, last updated 03/07/12*[/FONT]
 

 

 [FONT=Liberation Serif, serif]**Installing and running Ubuntu 12.04(Precise Pangolin) on a 2011 imac with radeon HD 6770m(Dual-Boot only)**[/FONT]
  
[img]http://www.lunarts-studio.com.br/file_hosting/unprecise_pangolin.jpg[/img]

  	 	 	 	 	 	   [FONT=Droid Sans, sans-serif][SIZE=1]**This Pangolin sure needs to be tamed to be more or less precise on an imac**[/SIZE][/FONT]
 

 

 [FONT=Liberation Serif, serif]**INTRODUCTION**[/FONT]
 

  [FONT=Liberation Serif, serif]	First of all, let me make clear which this guide is only to the imac model mentioned above, the farther your hardware is from the above, the more it is probably this guide will not help you, or may even cause you problems. I'm almost sure what I have experienced regarding the above model and 12.04 ubuntu applies to all computers with this specific model(21,5 inches, radeon hd 6770m, quad core i5), but you will be following this guide at your own risk even then.[/FONT]
  

  [FONT=Liberation Serif, serif]	Ubuntu 12.04 for mac is honestly lacking a lot currently, but if you can no longer tolerate OS X due to the fact you perceived fishy things happening there currently(or even in the past), you may actually want to run linux ubuntu 12.04 at your imac anyway; you may also want too to test how a software you made behaves on linux ubuntu(maybe you want linux as a primary target platform or a secondary target platform), ubuntu is one of the most popular linux desktop distributions, together with linux mint it seems.[/FONT]
 

  

  [FONT=Liberation Serif, serif]**KNOW ISSUES**[/FONT]
 

  [FONT=Liberation Serif, serif]The current know issues, which may or may not be fixed in the near(or far) future are:[/FONT]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Cannot boot ubuntu without 	rEFInd[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Noisy screen(most noticeable 	against dark backgrounds): 	[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1020374](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1020374)[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Cannot properly use the mac 	default EFI system without running Super Grub 2 Disk once to enter 	the ubuntu OS you installed.[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Overall bad apple keyboard and 	mouse recognition.[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Brigthness control not working 	by default, very bright screen by default: 	[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1020373](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1020373)[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]For Brazilian language you will 	need to do additional configuration. 	[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1012695](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1012695)[/FONT]
[/LIST]
  

 
[LIST]
[*][FONT=Liberation Serif, serif]The 	Ubuntu open source driver for radeon hd 6770m is hugely slow, mainly 	for games and other graphic intensive tasks; no ubuntu packaged AMD 	driver will work out of the box due to video memory recognition 	issues([/FONT][https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1004546](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1004546)[FONT=Liberation Serif, serif]).[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]You will need the usb keyboard 	to choose ubuntu at rEFInd, otherwise you will have to pair again 	your keyboard as described at mac manual at OS X everytime you want 	to do the above.[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Everytime you switch which OS 	you load, that OS will take over the keyboard and mouse, and you 	will have to setup them again at the other OS to get it to work 	there, which in turn will make the other OS  lose keyboard and mouse 	input again until pairing is done again there. In resume, currently 	you will never get both OS's to have simultaneous wireless keyboard 	and mouse input. [/FONT] 	
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Your headphones will not work, 	just built-in 	speaker([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1003039](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1003039)). 	Workaround already avaible.[/FONT]
[/LIST]
  

 
[LIST]
[*] 	[FONT=Liberation Serif, serif]Needs patience to setup 	keyboard and mouse at ubuntu with the default bluetooth 	manager(bluez, 	[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825)); 	maybe installing blueman speeds things a bit, thought bluez seems 	more reliable after device detection(may be just me).[/FONT]
[/LIST]
  

  

 [FONT=Liberation Serif, serif]**IF THINGS GET NASTY**[/FONT]
  

  [FONT=Liberation Serif, serif]	If you got a black screen(probable) after the AMD driver install and nopat does not work, at grub 2 boot loader [/FONT] 
  [FONT=Liberation Serif, serif]enter your current linux kernel image under recovery mode > ¨drop to root terminal¨ > type and confirm:[/FONT]
  

  [FONT=Liberation Serif, serif]	mount -rw -o remount /[/FONT]
  

  [FONT=Liberation Serif, serif]	This will allow you to make changes to your failed ubuntu install, then type and confirm:[/FONT]
  

  [FONT=Liberation Serif, serif]	 reboot [/FONT] 
  

  [FONT=Liberation Serif, serif]	This may allow you to have a working ubuntu(if not temporary) at the next ubuntu boot; sometimes you also may need to type ¨amdconfig  &#8211;initial -f¨ before the reboot command above. If that does not work. Type and confirm the following(the first line only if you installed the no distribution specific AMD site driver):[/FONT]
  

 [FONT=Liberation Serif, serif]	sudo sh /usr/share/ati/fglrx-uninstall.sh[/FONT] [FONT=Liberation Serif, serif]	sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*[/FONT] [FONT=Liberation Serif, serif][SIZE=3]	The first line above only if you installed the amd site radeon driver without generating ubuntu packages.[/SIZE][/FONT] [FONT=Liberation Serif, serif]	sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon[/FONT] [FONT=Liberation Serif, serif]	sudo apt-get install xserver-xorg-video-ati[/FONT] [FONT=Liberation Serif, serif]	sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core[/FONT] [FONT=Liberation Serif, serif]	sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[/FONT] [FONT=Liberation Serif, serif]	sudo rm -rf /etc/ati[/FONT] [FONT=Liberation Serif, serif]	[SIZE=3]This will revert ubuntu to the default open source non AMD driver, which usually works.[/SIZE][/FONT] [FONT=Liberation Serif, serif]	If the above does not work use the ubuntu live cd>test ubuntu, start terminal(ctrl+alt+T) and do(X is the number of your root / partition):[/FONT]
  

  [FONT=Liberation Serif, serif][SIZE=2]	sudo mount /dev/sdaX /mnt[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=2]	sudo chroot /mnt[/SIZE][/FONT]
  

  [FONT=Liberation Serif, serif]	The above will give you acess to the lost ubuntu install; from there do the video driver full cleanup and revert to open source said above.[/FONT]
    
  [FONT=Liberation Serif, serif]	If  everything else fails, use the live cd > install ubuntu, and format and reuse the root partition as root, also reuse but _**DO NOT FORMAT**_ the home partition. This last attempt is almost guaranteed to work.[/FONT]
  

  

  [FONT=Liberation Serif, serif]**DOING IT**[/FONT]
  

 [FONT=Liberation Serif, serif]	Before anything download this mac only 64bits ubuntu image and burn it to a media(cd, dvd): [/FONT][[FONT=Liberation Serif, serif]http://cdimage.ubuntu.com/releases/12.04/release/[/FONT]]("http://cdimage.ubuntu.com/releases/12.04/release/")[FONT=Liberation Serif, serif]	[/FONT]
  

  [FONT=Liberation Serif, serif]	Go to the OS X disk utility and ask it to split the hd single partition into two equally sized partitions, let the new partition be 'Free Space'.[/FONT]
 

  [FONT=Liberation Serif, serif]	Go grab yourself a cheap usb keyboard and mouse(the more popular the device brand is the merrier), you [/FONT][FONT=Liberation Serif, serif]_**WILL**_[/FONT][FONT=Liberation Serif, serif] need them, Ubuntu keyboard and mouse support is lacking currently. Then Download and burn to a disk Super Grub 2([http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)), so you can actually properly boot your ubuntu later using the system default EFI stuff; also at your OS X system, download rEFInd([http://sourceforge.net/projects/refind/files/0.4.0/refind-bin-0.4.0.zip/download](http://sourceforge.net/projects/refind/files/0.4.0/refind-bin-0.4.0.zip/download)) and install, which will let you choose between ubuntu and os x at mac startup.[/FONT]
  

  [FONT=Liberation Serif, serif]	With the ubuntu media mentioned before burn and ready, restart your imac. After the startup sound keep the keyboard alt key pressed until a menu appears, choose the cd wrongly labeled 'windows', if it does not show up, wait a bit until it do. Do not try to let the imac automatically detect the disc, because or it will not, or it will actually refuse it.[/FONT]
  

  [FONT=Liberation Serif, serif]	If you apple mouse do not work at first at the test/install screen, click it a bit and it will, enable the onscreen keyboard(probably the apple keyboard will not work) at the little man symbol at the right-top area(apple keyboard will not work) or use the usb keyboard(easier). Choose your language, mark the third-party stuff checkbox, and _**DO NOT**_ mark for ubuntu to update already(to avoid wasting your internet limit if any, just do só when the video driver is truly working later), _**WHEN**_ ubuntu ask if you want to overwrite your OS X, place it side by side or manual, **go manual**.[/FONT]
  

  [FONT=Liberation Serif, serif]	Use that space you previously freed with diskutility at OS X as 10gb or more as / with ext4, 2mb for grub bios partition, 4gb for the swap, and all the rest to a /home with ext4 too(_**do not forget to create this /home partition**_); **select for boot loader install the partition which you configured as root /**(check the labels which the partition manager show you above). Proceed until install is complete and click reboot, use the usb keyboard to finish the boot when requested. [/FONT] 
  

  [FONT=Liberation Serif, serif]	Ensure your wireless keyboard is working at startup(Super Grub 2 Disk cannot recognize usb keyboard), otherwise pair it at OS X like the mac manual says(system conf>keyboard>bluetooth conf, **shutdown keyboard**(press the keyboard power button until it shut down, dont just touch it) and turn it on again there), then press Alt at startup, but with the super grub 2 disk at the your cd reader instead, select somethind like **'detect even if the MBR is overwritten'**, select the only entry which will appear and boot ubuntu normaly, _**but just due to super grub disk 2**_. [/FONT] 
  

  [FONT=Liberation Serif, serif]	Under Ubuntu system configuration > keyboard layout, use English(Macintosh) for the apple keyboard keys to work properly; you can do this later too. If you are Brazilian, type this at terminal:[/FONT]
  

  [FONT=Liberation Serif, serif]	Add this as the last line at the newly open document, save and exit:[/FONT]
  

  [FONT=Liberation Serif, serif]	setxkbmap us -variant intl[/FONT]
  

  [FONT=Liberation Serif, serif]	You will now have support for Brazilian accents([http://digitalareablog.wordpress.com/2011/12/22/configuracao-acentuacao-no-linux-ubuntu-11-10-virtualizado-no-macbook/](http://digitalareablog.wordpress.com/2011/12/22/configuracao-acentuacao-no-linux-ubuntu-11-10-virtualizado-no-macbook/)). Thought you will need to do só every time the computer sleeps, restarts or is shutdown. This also outputs wrong quotes characters, useless and dangerous in programming.[/FONT]
  

  [FONT=Liberation Serif, serif]	I know I previously said which the Amd site radeon driver was the only option, but I discovered which there is a better solution(install direct to xorg seems unstable, generating .debs takes time and isn't very easy). Just go to Ubuntu system configurations > proprietary drivers and install the &#8220;ATI/AMD fglrx proprietary driver&#8221;(**do not install the post updates one**).[/FONT]
  

  [FONT=Liberation Serif, serif]	Since you are at terminal, update the system know packages with: sudo apt-get update[/FONT]
  

  [FONT=Liberation Serif, serif]	After that do the procedure mentioned here from step 19 to 28: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)[/FONT]
  

  [FONT=Liberation Serif, serif]	Reboot. The ubuntu screen will become fully bright, if you value your eyes you will need to do this at terminal(if 0.9 is still too bright, try 0.8 or lesser): [/FONT] 
  

  [FONT=Liberation Serif, serif]	xrandr --output LVDS --brightness 0.9[/FONT]
  

  [FONT=Liberation Serif, serif]	Go to OS X and edit rEFInd.conf to always select by default OS X, the path to the file is macintosh hd>EFI>rEFInd>refind.conf. You will need to command+i > change permission((be sure to remember how the permissions are now)) of the refind folder and refind.conf to be able to edit it with a text editor; You will know what line is responsible for rEFInd entry as the the file is well commented(at the comment it will mention which you can put a number between 1 and 9), change the default entry to 2 and save. Don't forget to command+i the two(refind folder and refind.conf) again and restore the permissions as they were(probably read only to everyone eles, read-write to system group).[/FONT]
  

  [FONT=Liberation Serif, serif]	It is very probable ubuntu will boot with a black/blank screen after boot, if that happens, leave your ubuntu entry at grub bootloader highlighted, and press e; at the line with &#8220;quite splash&#8221;, add to its end &#8220;nopat&#8221;(without quotes of course) and press F10; you will have to do that at every ubuntu startup, if it works more than twice you can change your grub file só it always include that parameter for you, if só:[/FONT]
  

  [FONT=Liberation Serif, serif]	sudo gedit /etc/default/grub[/FONT]
  

  [FONT=Liberation Serif, serif]	Add &#8220;nopat&#8221; to &#8220;quiet splash&#8221;, turning it in &#8220;quiet splash nopat&#8221;, save the file and exit.[/FONT]
  

  [FONT=Liberation Serif, serif]	For your headphones to work, go to terminal then:[/FONT]
  

  [FONT=Liberation Serif, serif]	sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]
  

  [FONT=Liberation Serif, serif]	Add to the last line of this document, the following, save and reboot:[/FONT]
  

  [FONT=Liberation Serif, serif]	options snd-hda-intel model=imac27_122[/FONT]
  

  [FONT=Liberation Serif, serif]	Your ubuntu should now be working in the limits currently possible for an imac 2011, now you can update your system software, language support and install your favorite programs. [/FONT] 
  

  

  [FONT=Liberation Serif, serif]**TESTING UNSUPPORTED NEWER KERNELS**[/FONT]
  

  **[FONT=Liberation Serif, serif]	[/FONT]**[FONT=Liberation Serif, serif]You may want to test newer linux kernels to see if there are any improvements into how ubuntu behaves at a mac computer; I will not teach you how to do that, but I will teach you how to get rid of such kernels if your experiments start to mess everything up, more specifically AMD video driver experiments([http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)). [/FONT] 
  

  [FONT=Liberation Serif, serif]	Check your current working kernel with:	[/FONT]
  

  [FONT=Liberation Serif, serif]		uname -r [/FONT] 
  

  [FONT=Liberation Serif, serif]	Check all the current installed kernels:[/FONT]
  

  [FONT=Liberation Serif, serif]		dpkg --info | grep linux-image [/FONT] 
  

  [FONT=Liberation Serif, serif]	Remove the desired kernels(replace target_linux_image with the kernel image name, just ctrl+shift+c then ctrl+shift+v), **_do not remove your current kernel image(remember the above uname -r)_**:[/FONT]
  

  [FONT=Liberation Serif, serif]	sudo apt-get purge **target_linux_image** [/FONT] 
  

  [FONT=Liberation Serif, serif]	Update the Grub 2 boot loader(that black screen before ubuntu with many entries, one of them marked as grey)[/FONT]
  

  [FONT=Liberation Serif, serif]	sudo update-grub2[/FONT]
  

  

  [FONT=Liberation Serif, serif]**CONSIDERATIONS**[/FONT]
  

  [FONT=Liberation Serif, serif]	Hope this guide helps you, as I discovered a lot of the things above the hard way; if you discover a better way of working around the current ubuntu 12.04 issues on an imac 2011, let me know; it is good to test yourself if the information provided is the indeed the best one(thought doing so is quite dangerous, I 'stained' for quite some time my imac screen pixels recently).[/FONT]
  

  [FONT=Liberation Serif, serif]	Sorry, but Ubuntu should by no way be só difficult to setup at a mac, thought the system do not ceases to be interesting due to things mentioned at the guide introduction; thought for it to be running on an imac is something surprising as mac are not as popular as the PC with windows computers, I guess Ubuntu team actually tries to make a working mac ubuntu.[/FONT]
  

  [FONT=Liberation Serif, serif]	Also, if you find a problem with ubuntu on an imac, even if it is tiny, let people know at launchpad, do not wait for others to submit the bug report for you; otherwise the problem will take longer to be solved, or will not be solved at all. Help at the bug links I presented at the 'Know Issues' section of the guide, just by saying there these bugs affects you or by providing additional information.[/FONT]
  

  

  [FONT=Liberation Serif, serif]**CREDITS**[/FONT]
  

  [FONT=Liberation Serif, serif]Thanks to English Ubuntu Forums, to the rEFInd maintainer, and people which shared their knowledge elsewhere on the web. [/FONT] 
  

  [FONT=Liberation Serif, serif]	You can redistribute and improve this guide, but **_ALWAYS_** credit me at your guide credits, I think I deserve by having almost badly damaged my imac screen testing ubuntu video and spenting a lot of time to know what works and what doesn't and writting this guide, also I have this guide original file(non PDF).[/FONT]
  

 [FONT=Liberation Serif, serif]	Further technical information on amd radeon on ubuntu precise pangolin: [/FONT][[FONT=Liberation Serif, serif]http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx[/FONT]]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx")
  

_**PDF VERSION:**_

[[img]http://www.lunarts-studio.com.br/file_hosting/ubuntu_imac_thumb.jpg[/img]](http://lunarts-studio.com.br/file_hosting/2011_imac_ubuntu_12.04.pdf)

_**Click at the image for a pdf version**_

---

