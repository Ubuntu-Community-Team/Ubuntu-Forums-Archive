---
title: "Installing Cisco Unified Communications (CallManager) in VirtualBox"
date: 2009-01-03
forum: Virtualisation
---

### Post by fouadatmeh on 2009-01-03
** Warning: the below is for educational purposes only, Cisco says in a file about this product: "We have to make sure this is a VMWARE which supports our Licensing Scheme" **

I have managed to start the Installation Cisco Unified Comm. in VirtualBox without giving the "Hardware you are using is no supported for this product" error message.. I haven't completed the installation and testing yet so errors may still appear later on.

Anyway,  the procedure goes as follows:
1- Create a new virtual machine with >=1Gb ram and >=40 GB hdd.
2- Replace <VM name> with your virtual machine name and <username> with your username in all the below.
3- Edit the virtual machine's xml setting file found at "/home/<username>/.VirtualBox/Machines/<VM name>/<VM name>.xml"
4- add the following lines to it in the "<ExtraData>  </ExtraData>" section:
[FONT="Courier New"]      <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" value="6 "/>
      <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" value="VMware"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" value="Phoenix Technologies LTD"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" value="VMware Virtual Platform"/>[/FONT]
5- **INSTEAD OF** steps 3 & 4, you can run the following cmd's in a terminal window:
```
VBoxManage setextradata "<VM name>" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" "6 "
VBoxManage setextradata "<VM name>" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" "VMware"
VBoxManage setextradata "<VM name>" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" "Phoenix Technologies LTD"
VBoxManage setextradata "<VM name>" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" "VMware Virtual Platform"
```
6- Run the virtual machine and all should work.
** Note: the value for the DmiBIOSVersion is equal to "6 " (there should be a space after the 6 for VitualBox to work.

Information sources which helped me can be found at:
* VirtualBox Bios cpp file:
[http://www.virtualbox.org/browser/trunk/src/VBox/Devices/PC/DevPcBios.cpp]("http://www.virtualbox.org/browser/trunk/src/VBox/Devices/PC/DevPcBios.cpp")

* Communications Manager Hardware detection script:
/media/cdrom0/Cisco/base_scripts/ihardware.sh

Hope this helps someone.. any comments are most welcome.

---

### Post by sdk1 on 2009-04-02
Any updates on the final state of installation or testing with CUCM that you reached with this setup? And what version of CUCM are you using 6/7? 

Being a newbie, I had tried using RHEL4 with VMWare Server but couldnt get VMWare to work, now hoping to try with VirtualBox on RHEL4. 
Any advice, suggestions or links would be appreciated.

---

### Post by Dark Theli on 2009-05-27
Just did what you posted and that solved my issue xD. I'm installing CUCM 6.x. I will post later on how was it xD. Thanks a lot fouadatmeh.

cheers,
Dark Theli

---

### Post by Dark Theli on 2009-05-28
Everything looked to be ok. When suddenly reboot the to complete installation. At that point every time I tried to start my virtual machine it looked like was about to start but it closes the Virtual Machine window.

Fouadatmeh, what version of CUCM you attempted to install? Do you configure it to work with SCSI HDD?

I would appreciate any advice or suggestion.

Thanks,
Dark Theli

---

### Post by fouadatmeh on 2009-05-28
Hello,
Sorry for the extremely late reply..
I remember that it finished the installation but it wasn't able to boot up correctly.. it seemed that it needed some drivers or something.. but since I am not an expert in linux nor in CUCM I stopped trying.
I used CUCM ver. 6.0.1
sorry for not being of much help :(

---

### Post by arotey on 2009-06-17
Hello,
Did anybody manage to finish an installation of Cisco Unified Communications (Callmanager) in VirtualBox ?
The installation completed, but when booting the server, it is stuck in a state "Uncompressing Linux .... OK, booting the kernel"
nothing happens afterwards ...
Anybody an idea ?
Thanks,

---

### Post by CVirus on 2009-10-02
The installation went fine but after rebooting into the system, VirtualBox panics during Uncompressing the Linux kernel.

Here's the log file attached.

I would appreciate if anyone could solve this .. Thanks !

---

### Post by z0n on 2009-10-21
I've been battling the "Hardware not supported" issue for yonks and this sorted me out straight away - BIG thanks!

---

### Post by jy92 on 2009-10-29
just activate PAE/NX support (if it still fail , disable VT support)

---

### Post by pillitiere on 2010-03-29
Hello all... I am building a training lab for some of my guys and we are running call manager 4.1(3). I have been unable to get virtual box to run the install. I am assuming that the parameters in the first post are for cucm 6 and above. Does anyone have the parameters for 4.1(3)? 
 
I have a dell 2970 server with 4gig mem, and 360gig hard drive. I have disabled the audio on the callmanager virtual box machine as well as added the extradata entries in the xml, but still get hardware not supported.
 
Any help will be appreciated!
 
Thank you
P

---

