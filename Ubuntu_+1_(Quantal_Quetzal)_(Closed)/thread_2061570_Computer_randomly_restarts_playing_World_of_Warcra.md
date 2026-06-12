---
title: "Computer randomly restarts playing World of Warcraft"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Enhein on 2012-09-22
Evening,

Unfortunately I am new to linux, so I do not have a lot of the information you may require. But I will do the best I can.

AMD Phenom X4 955 with liquid Cooler.
Geforce 560Ti Superclocked Ed. 2Gig Mem. (Running 295.33. Downgraded from the 304.43 to try and solve it.)
8Gig DDR3
Wine 1.04 (Heard 1.05 is beta and has some issues yet)

After playing World Of Warcraft 5.0something My system randomly resets. Nothing seems to trigger it, No amount of time, no going into areas, it just happens. I can play for a little while, however there is no set time to trigger this, maybe 20min. I have tried all different settings ingame. I even searched Google, spending maybe 3 days looking. Time for the pro's.

I have tried running in Opengl and D3d
I have reseated nvidia, and Ram.
I have monitored my Temps, Processor stays at about 30c and video card does not exceed 68c.
This is a fairly new system with new mobo, Ram, Vid card.

I have Dual Boot with Windows 7 and have absolutely NO issues with World of Warcraft. According to WINEhq I should not be having this issue. And believe me, I am aware that linux is not a gaming platform, and errors will occur, but I am begining to think it is something more than just WINE.


```
Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
        Error Detecting Method: 64-bit ECC
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 4096 MB
        Supported Speeds:
                70 ns
                60 ns
        Supported Memory Types:
                Standard
                EDO
        Memory Module Voltage: 3.3 V
        Associated Memory Slots: 4
                0x0006
                0x0007
                0x0008
                0x0009
        Enabled Error Correcting Capabilities:
                None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 1
        Current Speed: 53 ns
        Type: Other Unknown EDO
        Installed Size: 4096 MB (Double-bank Connection)
        Enabled Size: 4096 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2
        Current Speed: 144 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: 3
        Current Speed: 53 ns
        Type: Other Unknown EDO
        Installed Size: 4096 MB (Double-bank Connection)
        Enabled Size: 4096 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: 4
        Current Speed: 144 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 16 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: 1333 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: Unknown
        Type Detail: None
        Speed: 400 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: Unknown
        Type Detail: None
        Speed: 1333 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: None
        Speed: 400 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:
```

---

### Post by funicorn on 2012-09-24
I believe warcraft is a computer game running in Microsoft Windows. You really should find the right operation system to do what you want to.

---

### Post by Enhein on 2012-09-24
> **funicorn said:**
> I believe warcraft is a computer game running in Microsoft Windows. You really should find the right operation system to do what you want to.

Yes, World of Warcraft is a Windows/Mac application. However, I have been seeing all over that it will run flawlessly on Ubuntu. It runs great for me for awhile before it crashes out, and restarts my computer.

WineHQ directed me here in hopes that someone will be able to help me troubleshoot it. I understand with the game being "Unsupported" I may not get the help I need, and I am OK with that, I figured it can't hurt to try.

I do have dual boot, but I have warmed up to Ubuntu so much that it seems to blow Windows out of the water, and I would like to Migrate over to this permanently. I mean even 95% of Steam games will run on Linux based distro's.  I think that Linux may be the new operating system choice to the new generations that are willing to learn.

But, I am going off course here. I am hoping someone is able to jump in and be able to help me find the issue.

Also, may be related, or not at all, after a restart about an hour ago, I could not get kubuntu to load the Gui. It was giving me a USB 3 3 device descriptor read64, error. It also disabled my USB mouse and keyboard. I found that unplugging my external hard drive got me past the error, however now it goes right to terminal asking for Login. When I CTRL ALT F7, it stays on the screen showing whats stopped and started, not bringing me to the Gui. I had to reboot and boot into "Previous Ubuntu Versions" Currently in 12.04. Which I could have sworn I have been running all along. This may or may not be related. If it's not, disreguard. I am quite happy with my current version anyways, I don't know how it updated anyways :*(

Thanks

---

### Post by mcellius on 2012-09-24
Hmmm ... yeah, the version of Ubuntu could well be the problem here.  I *think* I've seen many comments that Word of Warcraft runs well on Ubuntu, but that would be on stable versions of Ubuntu, not Quantal Quetzal which is the current beta version of what will be released next month as Ubuntu 12.10.  

There is, in fact, a stable upgrade to Ubuntu 12.04, which is 12.04.1, but the beta of 12.10 is certainly not recommended for those who require a stable platform.  

If you are, indeed, running Quantal Quetzal and need to go back to 12.04, you might try asking your question in a new posting with a new title to more accurately state what you're trying to do (so that you'll catch the eye of those who know how to do it).

---

### Post by funicorn on 2012-09-24
To make sure it's not a wine problem, you can try starting WC in terminal and see what wine outputs when the game crashes. Meanwhile don't forget to check errors in ~/.xsession-errors and in /var/log/Xorg.0.log, and in any other logs you can find.

---

### Post by synaptix on 2012-09-24
> **Enhein said:**
> Wine 1.04 (Heard 1.05 is beta and has some issues yet)

The latest development version of Wine is 1.5.13, latest stable version is 1.4.1.

---

