---
title: "Hardware Acceleration"
date: 2020-01-04
forum: Virtualisation
---

### Post by pairsroyale on 2020-01-04
Hello Ubuntu Forums!

         Thanks in advance for any help I get on this matter. I can't for the life of me figure this out; I've been trying for a long time now to have Ubuntu used on Oracle VirtualBox, but no matter how I follow instructions online I always encounter the same problem: I can't disable hardware acceleration. The exact words in the box are -


"The hardware virtualization is enabled in the Acceleration section of the System page although it is not supported by the host system. It should be disabled in order to start the virtual system."

         
         Is my computer too bad/slow to use VirtualBox? I can't seem to fix this in either the VirtualBox settings or my computer settings. I also included a screenshot of the window with the error. Thanks again for any help!

-pairsroyale

---

### Post by deadflowr on 2020-01-04
> Is my computer too bad/slow to use VirtualBox?
We know nothing of your system to answer that.

Anyway it tells you to go the System tab to disable the settings.
I'm not sure if you've done that or not.


Oh,
and moved to the *Virtualization* sub-forum.

---

### Post by pairsroyale on 2020-01-04
You're right, it does say to go to the Systems tab to disable the settings. That was one of the many instructions that I followed to try to accomplish this. Here are the instructions pasted from auslogics.com:


[LIST=1]
[*]Right-click an empty space on your desktop and click on Display settings.
[*]Scroll down the Display settings options page to Advanced display settings and open it.
[*]In the next window, click Display adapter properties for display 1.
[*]The graphics properties window will open. Choose the Troubleshoot tab.
[*]Click Change Settings.
[*]In the Display Adapter Troubleshooter bar, move the Hardware acceleration pointer to the left to disable hardware acceleration on your PC.
[*]Click OK to save your changes and exit.
[/LIST]
    
     There is no "troubleshoot" tab within the graphics property window. I'm able to get that far; so close. I don't want to mess around with too much in the computer settings without seeing if someone knows a way around this first.
    
    My specs btw are:

AMD A4-9125 RADEON R3, 4 COMPUTE CORES, 2C+2G  2.3GHz; 4G RAM; 64-bit operating system, x64-based processor

Thanks again

---

### Post by TheFu on 2020-01-04
4GB of RAM will be tight.  Need to leave 1GB available for the hostOS to manage VMs.
The best instructions I know are here: [https://www.virtualbox.org/wiki/Documentation](https://www.virtualbox.org/wiki/Documentation)

With an AMD A4-9125, I'd say to avoid the full Ubuntu and go with Lubuntu or Xubuntu or Ubuntu-Mate flavors instead.  Don't allocate more than 3GB of RAM to the VM.

---

### Post by pairsroyale on 2020-01-04
Thanks TheFu, I'll give that a try

---

### Post by deadflowr on 2020-01-04
> **pairsroyale said:**
> You're right, it does say to go to the Systems tab to disable the settings. That was one of the many instructions that I followed to try to accomplish this. Here are the instructions pasted from auslogics.com:


[LIST=1]
[*]Right-click an empty space on your desktop and click on Display settings.
[*]Scroll down the Display settings options page to Advanced display settings and open it.
[*]In the next window, click Display adapter properties for display 1.
[*]The graphics properties window will open. Choose the Troubleshoot tab.
[*]Click Change Settings.
[*]In the Display Adapter Troubleshooter bar, move the Hardware acceleration pointer to the left to disable hardware acceleration on your PC.
[*]Click OK to save your changes and exit.
[/LIST]
    
     There is no "troubleshoot" tab within the graphics property window. I'm able to get that far; so close. I don't want to mess around with too much in the computer settings without seeing if someone knows a way around this first.
    
    My specs btw are:

AMD A4-9125 RADEON R3, 4 COMPUTE CORES, 2C+2G  2.3GHz; 4G RAM; 64-bit operating system, x64-based processor

Thanks again

Wrong System tab. I meant the System tab/section in the virtualbox window.
The setting is a virtualbox setting.

---

### Post by pairsroyale on 2020-01-09
Sorry for the delay, and thanks again for all of the help. I'll just post this final screenshot of the Virtual Box systems page and if nothing works then I'll move on and try something else. 

So there's the next screenshot. It's on the systems page but regardless of how I adjust any of the settings the notification doesn't go away and I can't continue. I haven't found anyone else with this problem before and I'm not super tech savvy yet, so this is where it ends for me for now unless one of you knows a way around this.

Much Appreciated

Edit: I'm also going to the VirtualBox community for help; I'm probably just being a doofus and not seeing a setting somewhere lol

---

### Post by deadflowr on 2020-01-10
Looking at similar vbox threads you might need to check the settings for virtualization in the BIOS menu.

---

### Post by bernard010 on 2020-02-04
Open Virtual Box Manager  --> Select System from the list (The next after General that you posted) and open it. --> 
Their is 3 tabs (motherboard, Processor, Acceleration) Select Acceleration --> 
Leave it on Default, below that is Hardware Virtualization: UN-Check Mark the Enable VT-x. 
They will go to a grey color.: (means it is inactive) --> Select OK to save setting.

Hope this helps, Here is the Hyperlink for the VM Manual.

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

---

### Post by deadflowr on 2020-02-04
> **bernard010 said:**
> Open Virtual Box Manager  --> Select System from the list and open it. --> 
Their is 3 tabs (motherboard, Processor, Acceleration) Select Acceleration --> 
Leave it on Default, below that is Hardware Virtualization: UN-Check Mark the Enable VT-x. 
They will go to a grey color.: (means it is inactive) --> Select OK to save setting.

Hope this helps, Here is the Hyperlink for the VM Manual.

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

Did it already, Issue is a BIOS setting.
Nothing to do in virtualbox, yet.

---

### Post by bernard010 on 2020-02-05
According to the VM manual. Chapter 3.5.2 
Processor Tab- Uncheck mark both: -> Enable PAE/NX and Enable Nested VT-x/ Boxes.
In Chapter 3.5.3
 Acceleration Tab on Hardware Virtualization- Uncheck mark both: Enable VT-x and Enable Nested Paging
Click OK to save setting. The warning icon should disappear.

---

### Post by deadflowr on 2020-02-05
> **bernard010 said:**
> According to the VM manual. Chapter 3.5.2 
Processor Tab- Uncheck mark both: -> Enable PAE/NX and Enable Nested VT-x/ Boxes.
In Chapter 3.5.3
 Acceleration Tab on Hardware Virtualization- Uncheck mark both: Enable VT-x and Enable Nested Paging
Click OK to save setting. The warning icon should disappear.

They cannot unmark something that does not exist.

---

### Post by bernard010 on 2020-02-11
> They cannot unmark something that does not exist. 		
[h=2]3.5. System Settings
The **System** category groups       various settings that are related to the basic hardware that is       presented to the virtual machine.[/h][h=3]Note[/h]         As the activation mechanism of Microsoft Windows is sensitive to         hardware changes, if you are changing hardware settings for a         Windows guest, some of these changes may trigger a request for         another activation with Microsoft.       

       The following tabs are available.     
[h=3]3.5.1. Motherboard Tab[/h]


         On the **Motherboard** tab, you can         configure virtual hardware that would normally be on the         motherboard of a real computer.       

[LIST]
[*]             **Base Memory:** Sets the             amount of RAM that is allocated and given to the VM when it             is running. The specified amount of memory will be requested             from the host OS, so it must be available or made available             as free memory on the host when attempting to start the VM             and will not be available to the host while the VM is             running. This is the same setting that was specified in the             **New Virtual Machine** wizard,             as described in [Section 1.7, “Creating Your First Virtual Machine”]("https://www.virtualbox.org/manual/UserManual.html#gui-createvm").           
             Generally, it is possible to change the memory size after             installing the guest OS. But you must not reduce the memory             to an amount where the OS would no longer boot.           

[*]             **Boot Order:** Determines the             order in which the guest OS will attempt to boot from the             various virtual boot devices. Analogous to a real PC's BIOS             setting, Oracle VM VirtualBox can tell a guest OS to start from             the virtual floppy, the virtual CD/DVD drive, the virtual             hard drive (each of these as defined by the other VM             settings), the network, or none of these.           
             If you select **Network**, the             VM will attempt to boot from a network using the PXE             mechanism. This needs to be configured in detail on the             command line. See [Section 8.8, “VBoxManage modifyvm”]("https://www.virtualbox.org/manual/UserManual.html#vboxmanage-modifyvm").           

[*]             **Chipset:** You can select             which chipset will be presented to the virtual machine.             PIIX3 is the default chipset for most guests. For some guest             OSes such as Mac OS X, the PIIX3 chipset is not well             supported. As a result, Oracle VM VirtualBox supports an emulation             of the ICH9 chipset, which supports PCI express, three PCI             buses, PCI-to-PCI bridges and Message Signaled Interrupts             (MSI). This enables modern OSes to address more PCI devices             and no longer requires IRQ sharing. Using the ICH9 chipset             it is also possible to configure up to 36 network cards,             compared to a maximum of eight network adapters with PIIX3.             Note that ICH9 support is experimental and not recommended             for guest OSes which do not require it.           

[*]             **Pointing Device:** The             default virtual pointing device for some guest OSes is the             traditional PS/2 mouse. If set to **USB             Tablet**, Oracle VM VirtualBox reports to the virtual             machine that a USB tablet device is present and communicates             mouse events to the virtual machine through this device.             Another setting is **USB Multi-Touch             Tablet**, which is suitable for guests running             Windows 8 or later.           
             Using the virtual USB tablet has the advantage that             movements are reported in absolute coordinates, instead of             as relative position changes. This enables Oracle VM VirtualBox to             translate mouse events over the VM window into tablet events             without having to "capture" the mouse in the guest as             described in [Section 1.8.2, “Capturing and Releasing Keyboard and Mouse”]("https://www.virtualbox.org/manual/UserManual.html#keyb_mouse_normal"). This             makes using the VM less tedious even if Guest Additions are             not installed.           

[*]             **Enable I/O APIC:** Advanced             Programmable Interrupt Controllers (APICs) are an x86             hardware feature that have replaced Programmable Interrupt             Controllers (PICs). With an I/O APIC, OSes can use more than             16 interrupt requests (IRQs) and therefore avoid IRQ sharing             for improved reliability.           
[h=3]Note[/h]               Enabling the I/O APIC is *required*,               especially for 64-bit Windows guest OSes. It is also               required if you want to use more than one virtual CPU in a               virtual machine.             

             However, software support for I/O APICs has been unreliable             with some OSes other than Windows. Also, the use of an I/O             APIC slightly increases the overhead of virtualization and             therefore slows down the guest OS a little.           
[h=3]Warning[/h]               All Windows OSes install different kernels, depending on               whether an I/O APIC is available. As with ACPI, the I/O               APIC therefore *must not be turned off after               installation* of a Windows guest OS. Turning it               on after installation will have no effect however.             


[*]             **Enable EFI:** Enables             Extensible Firmware Interface (EFI), which replaces the             legacy BIOS and may be useful for certain advanced use             cases. See [Section 3.14, “Alternative Firmware (EFI)”]("https://www.virtualbox.org/manual/UserManual.html#efi").           

[*]             **Hardware Clock in UTC Time:**             If selected, Oracle VM VirtualBox will report the system time in             UTC format to the guest instead of the local (host) time.             This affects how the virtual real-time clock (RTC) operates             and may be useful for UNIX-like guest OSes, which typically             expect the hardware clock to be set to UTC.           
[/LIST]

         In addition, you can turn off the **Advanced         Configuration and Power Interface (ACPI)** which         Oracle VM VirtualBox presents to the guest OS by default.       
         ACPI is the current industry standard to allow OSes to recognize         hardware, configure motherboards and other devices and manage         power. As most computers contain this feature and Windows and         Linux support ACPI, it is also enabled by default in         Oracle VM VirtualBox. ACPI can only be turned off using the command         line. See [Section 8.8, “VBoxManage modifyvm”]("https://www.virtualbox.org/manual/UserManual.html#vboxmanage-modifyvm").       
[h=3]Warning[/h]           All Windows OSes install different kernels, depending on           whether ACPI is available. This means that ACPI *must           not be turned off* after installation of a Windows           guest OS. However, turning it on after installation will have           no effect.         


[h=3]3.5.2. Processor Tab[/h]


         On the **Processor** tab, you can         configure settings for the CPU used by the virtual machine.       

[LIST]
[*]             **Processor(s):** Sets the             number of virtual CPU cores the guest OSes can see.             Oracle VM VirtualBox supports symmetrical multiprocessing (SMP)             and can present up to 32 virtual CPU cores to each virtual             machine.           
             You should not configure virtual machines to use more CPU             cores than are available physically. This includes real             cores, with no hyperthreads.           

[*]             **Execution Cap:** Configures             the CPU execution cap. This limits the amount of time a host             CPU spends to emulate a virtual CPU. The default setting is             100%, meaning that there is no limitation. A setting of 50%             implies a single virtual CPU can use up to 50% of a single             host CPU. Note that limiting the execution time of the             virtual CPUs may cause guest timing problems.           
             A warning is displayed at the bottom of the Processor tab if             an Execution Cap setting is made that may affect system             performance.           

[*]             **Enable PAE/NX:** Determines             whether the PAE and NX capabilities of the host CPU will be             exposed to the virtual machine.           
             PAE stands for Physical Address Extension. Normally, if             enabled and supported by the OS, then even a 32-bit x86 CPU             can access more than 4 GB of RAM. This is made possible by             adding another 4 bits to memory addresses, so that with 36             bits, up to 64 GB can be addressed. Some OSes, such as             Ubuntu Server, require PAE support from the CPU and cannot             be run in a virtual machine without it.           

[*]             **Enable Nested VT-x/AMD-V**:             Enables nested virtualization, with passthrough of hardware             virtualization functions to the guest VM.           
[/LIST]

         With virtual machines running modern server OSes, Oracle VM VirtualBox         also supports CPU hot-plugging. For details, see         [Section 9.4, “CPU Hot-Plugging”]("https://www.virtualbox.org/manual/UserManual.html#cpuhotplug").       

[h=3]3.5.3. Acceleration Tab[/h]


         On this tab, you can configure Oracle VM VirtualBox to use hardware         virtualization extensions that your host CPU supports.       

[LIST]
[*]             **Paravirtualization             Interface:** Oracle VM VirtualBox provides             paravirtualization interfaces to improve time-keeping             accuracy and performance of guest OSes. The options             available are documented under the             --paravirtprovider option in             [Section 8.8, “VBoxManage modifyvm”]("https://www.virtualbox.org/manual/UserManual.html#vboxmanage-modifyvm"). For further details             on the paravirtualization providers, see             [Section 10.5, “Paravirtualization Providers”]("https://www.virtualbox.org/manual/UserManual.html#gimproviders").           

[*]             **Hardware Virtualization:**             You can configure hardware virtualization features for each             virtual machine.           

[LIST]
[*]                 **Enable Nested Paging:**                 If the host CPU supports the nested paging (AMD-V) or                 EPT (Intel VT-x) features, then you can expect a                 significant performance increase by enabling nested                 paging in addition to hardware virtualization. For                 technical details, see [Section 10.6, “Nested Paging and VPIDs”]("https://www.virtualbox.org/manual/UserManual.html#nestedpaging").                 For Intel EPT security recommendations, see                 [Section 13.4.1, “CVE-2018-3646”]("https://www.virtualbox.org/manual/UserManual.html#sec-rec-cve-2018-3646").               
[/LIST]

             Advanced users may be interested in technical details about             hardware virtualization. See [Section 10.3, “Hardware Virtualization”]("https://www.virtualbox.org/manual/UserManual.html#hwvirt").           
[/LIST]

         In most cases, the default settings on the         **Acceleration** tab will work         well. Oracle VM VirtualBox selects sensible defaults, depending on the         OS that you selected when you created the virtual machine. In         certain situations, however, you may want to change the         preconfigured defaults.       

[https://www.virtualbox.org/manual/UserManual.html#settings-processor](https://www.virtualbox.org/manual/UserManual.html#settings-processor)



 
[h=1]Oracle® VM VirtualBox®[/h][h=2]User Manual[/h]
[h=3]Oracle Corporation[/h]
Copyright © 2004-2020 Oracle Corporation

---

