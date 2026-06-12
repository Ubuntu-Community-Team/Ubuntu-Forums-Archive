---
title: "Installing Windows 98 in Virtualbox"
date: 2009-05-29
forum: Virtualisation
---

### Post by b@sh_n3rd on 2009-05-29
I just want to try this out. I've installed virtualbox on my PC running on Jaunty and was able to test it with a couple of LiveCD's I have of other linux distro's. Now, I thought of installing windows 98 on virtualbox as an experiment. Are there any issues for me to consider with my Ubuntu installation and Win98 on virtualbox? As it is a virtual system I'll be installing to, I think not...am I right in this aspect? I tried digging around for info, but was unable to find the information required and much of the links I found were to do with XP.

I setup Virtualbox and my Virtual system for windows 98 and tried to insall it to a virtual drive in the usual way (this is the first time I'm trying something like this). This is how I loaded it up until I encountered a problem. Virtualbox loads with my bootable Windows 98 CD and I select, "**Start computer with CD-ROM Support**". It loads from here on and then reports that drive C: is not a fat system (I've used it before :D). How could I setup C: drive for virtualbox to run windows? I tried "FDISK" on the windows 98 cd itself as it suggests. Then when I try to run setup it returns, "**Windows setup requires 7340032 bytes**" and freezes there. Any help? Thanks very much for any replies...

---

### Post by col48 on 2009-06-01
hi b_n

As far as I know there are no issues which would stop you.  But I think VirtualBox is not officially supported for a Win98 guest, so you may find there are some basic things which are not there.  I have a Hardy host and Windows95 guest and there is no way I can find of getting more than 16 colours (which frustrates me) or better resolution than 800x600 - which I can live with.

Bear in mind I've never run Windows98 - or Jaunty - and I'm no expert at installing an OS, but I'm happy to share my ignorance.

When VirtualBox creates the VM, it creates what will look to the VM like an unformatted and unpartitioned disk.  So you must boot from an 'external' medium (in the case of W95 I had an image of a bootable floppy stored on the host).  I think I was only offered DOS mode not a W95 GUI.  The first thing to do is to run fdisk to partition the disk (even if you only want 1 partition).  After that I restarted the VM in 'Normal' mode and ran ```
format c: /v LLL /q /s
``` (where LLL was the label I decided to give to the disk) and accepted the 'unconditional' option which was offered.  The VM is now ready to have the guest OS installed, so reset the VM into Normal mode and insert the installation CD (or its iso image) into the guest CD drive.  For W95 I then have to run
```
Setup
``` (not Setup.exe even though that is the full file name) at the DOS prompt, which for some reason is R:\ rather than D:\   - maybe I missed a trick at an early stage of setting up the VM.

Did you run format as well as fdisk?

One thing about a Virtual Machine is that if one attempt to set it is abortive you can have another go from the beginning without worrying about what state the previous attempt left it in!  Mine fired up at the 6th attempt (after I started counting) as I gradually worked my way to the above.

I have a CD image of the c:\windows part of my physical Windows95 machine.  Occasionally I have found I needed to copy a dll from there when putting other software on the VM.  Most of it seems to install OK but not everything.  Office95 and VB5 were OK, though.  I can't access the physical printer as it is USB and Windows95A did not know about USB, and at times the virtual floppy and virtual CD can be temperamental.

Hope this helps - I've only just seen your post and got your message.

---

### Post by b@sh_n3rd on 2009-06-02
Hey thanks, I got the installer working :D. At first I didn't quite get the format command, then just used my head. In fact, I've just skipped a very easy and simple step. All I had to do was, run fdisk then reboot, on the windows 98 SE bootable disk you get a menu asking whether to boot with CDROM support (#1) or not (#2). So as usual, I selected the first one, it loaded as it should. The win98 disk loads some diagnostic tools onto a RAM drive, which pushes the cdrom drive designation, back a letter. Then it loads some commands to "A:/" which is not my floppy. I don't have one hooked up anyway :D. It starts on "A:/_" (the underscore is the cursor as you might guess), then I just type, "format c:" and voila! It's done :D...Then I just load setup from drive "E:" (it's D but becomes E coz of the RAM drive) just like you did and that's it :D...At first I wanted to try win95, but because of this prob I thought I'll try 98. Anyways, I might try 95 after i'm done with 98. Thank you very much man, you bumped some sense into my brain :D...

---

### Post by datacw on 2009-08-28
i have my own problem its not working for me either

i cannot install 98 it keeps taking me into dos and i cant install it

neither can i install menellium

any help would be appriciated 

thx 

data:P

---

### Post by chavezgvg on 2009-10-23
Hi everybody, download Windows 98 from:

[http://victor-inox.espacioblog.com/post/2009/03/30/microsoft-windows-98-se-2k7-final-edition-espanol](http://victor-inox.espacioblog.com/post/2009/03/30/microsoft-windows-98-se-2k7-final-edition-espanol)

Then follow this instructions (I made copy-paste, it's in spanish) it works perfectly:

Instrucciones de instalación para Windows 98 en VirtualBox

Usa el archivo: Win98Final2K7.iso

Windows 98 Final 2007 
 
Esta ISO contiene Microsoft Windows 98, el cual viene con todas las 
actualizaciones disponibles  por Microsoft para este producto hasta 
el dia 15/07/2006,  el  actualizador para  Windows 98 fue elaborado 
por Feñiz.  Esta compilacion esta elaborada por TheOs [Fenix Team],
entre cual se destaca el añadido del actualizador con todos los updates 
disponibles,   una   carpeta   con   los   drivers  genericos  para  
dispositivos USB FLASH, asi  como el serial integrado al instalador 
y la correcta optimización y booteo de la ISO. 
 
CONFIGURACIÓN DE VIRTUALBOX:

System:
    Memoria base: 128MB
    Orden de arranque: FD-CD-HD
    ACPI: habilitado
    IO APIC: inhabilitado
    Procesadores: 1
    PAE/NX: inhabilitado
    VT-x/AMD-V: inhabilitado
    Paginación anidada: inhabilitado
Display:
    Memoria de video: 10 MB
    Aceleración 3D: inhabilitado
    Remote Display Server: inhabilitado
Discos Duros:
    HD: 500 MB
    Controlador IDE: PIIX4
    Controlador adicional: inhabilitado
Audio:
    Controlador anfitrión: PulseAudio
    Controlador huesped: SoundBlaster 16
Red:
    Adaptador: PCnet-PCI II (Am79C970A)
    Liga: NAT
Puertos Seriales:
    Puerto serie: inhabilitado
USB:
    Controlador USB: habilitado
    USB 2.0 (EHCI): inhabilitado

INSTRUCCIONES DE INSTALACIÓN:

1.- Montar el CD de "Win98Final2K7.iso" y arrancar la máquina virtual; seguir las instrucciones en pantalla para la instalación de Windows.

Es posible que durante la instalacion  alguna de las actualizaciones  
te pida que reinicies el equipo.  NO lo hagas, contesta que NO en el  
cuadro de dialogo  que aparece,  y deja que continue la instalacion.  
Al finalizar el  proceso,  cuando  cierres el programa actualizador,  
este te pedira que reinicies. Hazlo entonces.

---

