---
title: "Installing Adobe Creative Suite 5 (CS5) in Windows 7 through VirtualBox"
date: 2010-10-21
forum: Virtualisation
---

### Post by fantastic on 2010-10-21
I encountered two problems while installing Adobe CS5 Web Premium: meeting the minimum requirements and the actual install.

CS5 requires at least 256MB of video ram. VirtualBox's GUI only has a max of 128MB.

I tried increasing the VRAM in the ~/.VirtualBox/Machines/[machine name].xml as below but it did not work:

```
<Display VRAMSize="256" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>
```

From the shell, I ran

```
VBoxManage modifyvm "[machine name]" --vram 256
```

This seemed work and Windows 7 recognized the increase in video ram through Control Panel > Appearance and Personalization > Display > Screen Resolution > Advanced Settings > in Adapter tab

The install was more difficult. I kept getting a 


```
Exit Code: 7


-------------------------------------- Summary --------------------------------------


 - 0 fatal error(s), 121 error(s), 90 warning(s)


WARNING: The payload: Adobe Photoshop CS5 Core  {bunch of numbers and letters} requires a UI parent with following specification:

	Family: Photoshop

	ProductName: Adobe Photoshop CS5 Core_x64

	This parent relationship is not satisfied, because this payload is not present in this session.


WARNING: The payload with AdobeCode:  {bunch of numbers and letters} has recommended dependency on:


WARNING: 	Family: Adobe Web Suite CS5


WARNING: 	ProductName: Adobe Media Encoder CS5 X64


WARNING: 	MinVersion: 0.0.0.0


WARNING: 	This dependency is not satisfied, because this payload is x64 and is not supported on this machine.


WARNING: 	Removing this payload from the dependency list.


WARNING: The payload with AdobeCode:  {bunch of numbers and letters} has recommended dependency on:


WARNING: 	Family: Adobe Web Suite CS5


WARNING: 	ProductName: Adobe Media Encoder CS5 X64


WARNING: 	MinVersion: 0.0.0.0


WARNING: 	This dependency is not satisfied, because this payload is x64 and is not supported on this machine.


WARNING: 	Removing this payload from the dependency list.


WARNING: Payload cannot be installed due to dependent operation failure
```


After my many failed attempts at trying to install from the disk, even installing as Administrator, I ended up stumbling across a page on the Adobe site called [Adobe CS5 Cleaner Tool]("http://www.adobe.com/support/contact/cs5clean.html"). 

I ran the application as Administrator and restarted, but the install still did not work. I then uninstalled all Abobe applications and ran the Adobe CS5 Cleaner Tool again; install did not work.

I eventually stumbled upon a web page that recommended just downloading the trial version of CS5 and installing it, so I did. It worked.

So use what you can of this post to help you get Adobe Creative Suite 5 (Web Premium) installed.

Cheers!

---

### Post by wilddog on 2011-10-03
Thanks so much for this post.  I had a similar problem, actually the same problem, but with Adobe Creative Suite 5.5/Windows Vista SP2-32bit and Ubuntu 11.04, VirtualBox 4.1.2

I had been through all the hoops, allowed Adobe to run the install for me etc etc, all to no avail.  The problem seems to be with the x64 versions of the MFC & ATL libraries that the installer wants to install.  I was getting Exit Error 7.

Resolved the same way, downloaded the online trial version of the same, used the serial number provided - worked a treat.

Thanks for this

---

