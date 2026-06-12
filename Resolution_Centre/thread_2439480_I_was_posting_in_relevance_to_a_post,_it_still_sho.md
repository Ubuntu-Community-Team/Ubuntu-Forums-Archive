---
title: "I was posting in relevance to a post, it still shows up in search engines"
date: 2020-03-28
forum: Resolution Centre
---

### Post by incognitio222 on 2020-03-28
My post was relevant to the post? No operating system loads those drivers and those who are stuck with the device need to help each other. arrogance, shame on you

---

### Post by incognitio222 on 2020-03-28
New post, here is the link to the Linux (So you may have your linux relevance) and below is for those who want to get the windows working again.
NuVision Split 11 Linux and Windows 10 touchscreen help, if they were supported and loaded on one would ask for help with it!

[https://hackaday.io/project/83212-liberating-a-50-windows-tablet/log/116445-testing-the-touchscreen](https://hackaday.io/project/83212-liberating-a-50-windows-tablet/log/116445-testing-the-touchscreen)

[https://github.com/onitake/gsl-firmware](https://github.com/onitake/gsl-firmware)

Using one device for linux and widnows is normal, you should care to help everyone, this is why nothing works

[COLOR=#000000]Hi, so I recently obtained the Nuvision Split 11 and learned Nuvision does not properly support their devices after I had already formatted and installed windows 10 version 1909. If you visit NuVision's download page now, the drivers download for the Split 11 and other device are dead. I did did download the OS restore (Six hours to download if you do not pay the hosting site for continuous fast downloading [/COLOR]:sad:[COLOR=#000000]), NuVison provided was not a bootable version of it so I had to make one. I was able to restore the Spit 11, but the restore they provided has errors. Once I had windows and the drivers installed from the restore I ran a Powershell command to backup all of the driver "Export-WindowsDriver -Online -Destination D:\Drivers" - You have to run Powershell in administrators mode. Once I had the drivers backed up I created a windows 10 installation of Version 1909 the latest release as of 3/15/2020 when I made the Windows 10 iso. I integrated the drives so they would work during the install, and would install automatically when windows 10 installed. Additionally; all updates as of 3/15/2020 were slipstreamed into the distribution using NTLite ([/COLOR][https://www.ntlite.com/](https://www.ntlite.com/)[COLOR=#000000]). I sent the links to the extracted drivers and the Windows 10 distribution to NuVision Support, but they still did not download my provided drivers and Windows 10 iso to make available to everyone.[/COLOR]

[COLOR=#000000]If you need to install your drivers for windows 10, or you would like to do a fresh install of Windows 10 Version 1909, you are welcome to visit my Google Drive and download them. I ask you please help me help others with the NuVision Split 11 by providing a link to this page or my google driver for other to download since it seams NuVision does not really care to. I have also provided instructions on how to use the iso if you have never done it before.[/COLOR]

[COLOR=#000000]With the exception of Split 11 Drivers and Windows 10 Updates integrated, the windows 10 ISO is exactly as Microsoft Provides it. You will not need a CD-Key as it is[/COLOR]
[COLOR=#000000]integrated by NuVision in the bios and windows will just load it automatically from there. other than that it is a normal Windows 10 installation.[/COLOR]

[https://drive.google.com/open?id=1I7...rHktIQQXi0Gb-o]("https://drive.google.com/open?id=1I7N4FZuO1JhxQ-jTe8rHktIQQXi0Gb-o")


[COLOR=#000000]I already did the below for the "NuVision_(Split11)_Windows10 _(Version1909)_English_x64.iso" I only provided it if you ever need it and did not l know about it.[/COLOR]


[COLOR=#000000]If you would like to ever add your drivers to the install process for a Windows 10 installation and know about DISM, you can integrate your windows drivers into the boot.wim for the Windows PE installer. To add the drivers to the final installation, you must use NTLite. to use DISM, you need to install Microsoft's ADK Setup utility first.[/COLOR]


[COLOR=#000000]To integrate your driver's for the Windows PE environment:[/COLOR]
[COLOR=#000000]1.) Install Microsoft's ADK Setup Utility first. "[/COLOR][https://docs.microsoft.com/en-us/win...ed/adk-install]("https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install")[COLOR=#000000]"[/COLOR]
[COLOR=#000000]2.) Create a folder not in you C root, but another drive if you have one.[/COLOR]
[COLOR=#000000]3.) Copy the boot.wim from the installation iso to your new folder, you can find it in \sources\boot.wim[/COLOR]
[COLOR=#000000]3a.) you can use WinRaR to extract the iso to a folder, or just copy it form the open iso in PowerISO[/COLOR]
[COLOR=#000000]4.) Make a batch file in your directory you created and copied the boot.wim to and paste below code.[/COLOR]
[COLOR=#000000]4a.) You can open notepad paste the below code into it, select the option all files, not txt and add .bat to the end. and save[/COLOR]
[COLOR=#000000]4b.) on this line "DISM /mount-wim /wimfile:%WimFile% /index:1 /mountdir:%MountDir%" index:1, you need to set this to your index, most of the time it is 1[/COLOR]
[COLOR=#000000]4c.) This command in administrator mode will list available indexes "DISM /Get-ImageInfo /imagefile[/COLOR]:grin:[COLOR=#000000]:\"your boot.wim directory"\boot.wim"[/COLOR]
[COLOR=#000000]5.) if you open your folder with your batch file and boot.wim, just right click on the batch file and select run as administrator.[/COLOR]
[COLOR=#000000]the batch will do everything for you.[/COLOR]



[COLOR=#000000]DISM Batch script needs to be run as administrator:[/COLOR]

[COLOR=#000000]@echo off[/COLOR]


[COLOR=#000000]SET WimFile="%~dp0boot.wim"[/COLOR]
[COLOR=#000000]SET MountDir="%~dp0MNT"[/COLOR]
[COLOR=#000000]SET DriverDir="%~dp0Drivers"[/COLOR]


[COLOR=#000000]ECHO Boot.wim File:[/COLOR]
[COLOR=#000000]ECHO %WimFile%[/COLOR]


[COLOR=#000000]ECHO Making Mount Directory "MNT":[/COLOR]
[COLOR=#000000]IF NOT EXIST %MountDir% mkdir %MountDir%[/COLOR]
[COLOR=#000000]ECHO %MountDir%[/COLOR]


[COLOR=#000000]ECHO Driver Directory:[/COLOR]
[COLOR=#000000]ECHO %DriverDir%[/COLOR]


[COLOR=#000000]DISM /get-wiminfo /wimfile:%WimFile%[/COLOR]


[COLOR=#000000]DISM /mount-wim /wimfile:%WimFile% /index:1 /mountdir:%MountDir%[/COLOR]


[COLOR=#000000]DISM /Image:%MountDir% /Add-Driver /Driver:%DriverDir% /recurse[/COLOR]


[COLOR=#000000]DISM /image:%MountDir% /get-drivers[/COLOR]


[COLOR=#000000]DISM /unmount-wim /mountdir:%MountDir% /commit[/COLOR]


[COLOR=#000000]ECHO Removing Mount Directory[/COLOR]
[COLOR=#000000]rmdir %MountDir%[/COLOR]


[COLOR=#000000]PAUSE[/COLOR]




[COLOR=#000000]Exit[/COLOR]


[COLOR=#000000]I am hopeful you can find this if you need it...[/COLOR]

---

### Post by QIII on 2020-03-28
Pardon my confusion, but why have you posted this in the Resolution Centre?

---

