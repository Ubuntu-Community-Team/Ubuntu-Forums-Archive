---
title: "[SOLVED] Running Vista in VirtuaBox"
date: 2008-10-16
forum: Virtualisation
---

### Post by Arl on 2008-10-16
First, Obviously, I'm new to Ubuntu/Linux/not running a Windows OS. So far it's great, but I am trying to get over that learning curve. I 'm running Intrepid, and want to get away from having to reboot in to Windows.

I set up VirtualBox so that I can run Windows and have access to Office (I know about OpenOffice, but I just like MS better and it I don't have issues with formatting when I open files from other people), NavisWWorks, and a couple other programs that are Windows specific. I installed Vista on my virtual machine with out any  problems, but I am having issues being able to access to my real HDD and my USB HDDs. I read through the manual and have looked around here a little bit, but haven't found much help.

Any suggestions on how I should set up VirtualBox and Ubuntu so I can run Vista as if it were on a real computer?

---

### Post by saj0577 on 2008-10-16
In virtualbox there is a sharing option to share folders between your real machine and your VM, which will give you access to your Home folder (or whatever folder you choose) from your VM. Is this what you are after?


Saj

---

### Post by bodhi.zazen on 2008-10-16
Moved to Virtualization.

I suggest you learn Samba.

Samba is a netwrok protocol which will allow you to share directories / files :

[http://ubuntuforums.org/showpost.php?p=5400935&postcount=11](http://ubuntuforums.org/showpost.php?p=5400935&postcount=11)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

You can probably enable shared folders in your Vista VM and mount it in Ubuntu without installing any additional software on either Vista or Ubuntu.

---

### Post by Nxion on 2008-10-16
I think in this case your better off setting up Samba. IMO It is more stable then the shared folder option in VirtualBox. I have had it break before. Here are some link that would be beneficial to check out.

[Samba? What is that?]("http://en.wikipedia.org/wiki/Samba_software")

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[URL="http://ubuntuforums.org/showthread.php?t=202605"]
http://ubuntuforums.org/showthread.php?t=202605[/URL]

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Hope that helps :)

---

### Post by Nxion on 2008-10-16
> **bodhi.zazen said:**
> Moved to Virtualization.

I suggest you learn Samba.

Samba is a netwrok protocol which will allow you to share directories / files :

[http://ubuntuforums.org/showpost.php?p=5400935&postcount=11](http://ubuntuforums.org/showpost.php?p=5400935&postcount=11)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

You can probably enable shared folders in your Vista VM and mount it in Ubuntu without installing any additional software on either Vista or Ubuntu.

AWWWW, I was beat again :)

---

### Post by Arl on 2008-10-16
> **saj0577 said:**
> In virtualbox there is a sharing option to share folders between your real machine and your VM, which will give you access to your Home folder (or whatever folder you choose) from your VM. Is this what you are after?


Saj

I tried that and it wasn't working. I want to be able to access my 2 USB HDDs, but VirtualBox gives me this message every time I go to Settings

```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: NS_ERROR_FAILURE (0x00004005)
Component: Host
Interface: IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

```

Did I miss something on install?

Bodhi and Nixon, I will look into Samba.

---

### Post by howefield on 2008-10-16
Did you install virtualbox from the repository, ie the OSE (Open Source Edition) edition ?

If you did, the PUEL (Personal Use & Evaluation Licence) version on the virtualbox website has USB support which OSE doesn't.

---

### Post by Arl on 2008-10-16
I got it from the VB website

---

### Post by Arl on 2008-10-17
*bumb*

---

### Post by bodhi.zazen on 2008-10-17
> **Arl said:**
> *bumb*

Samba ?

---

### Post by Arl on 2008-10-20
> **bodhi.zazen said:**
> Samba ?

it was supposed to be *bump* because I was gone all weekend with no Internet access so I figured it would be ok to bump it. However, I was in a rush and apparently typed *bumb* instead.

I'm not sure I really understand the error with the Host USB Proxy Service message. Any suggestions?

---

### Post by Therion on 2008-10-20
There are a couple things you probably want/need to do with a new setup of a Windows guest in Virtual Box.

To fix your error you need to enable usbfs. 

Open a terminal and type:```
sudo gedit /etc/init.d/mountdevsubfs.sh
```
Find this part:

>    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

remove the # sign in front of the last 4 lines so it looks like this:


>     # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

Reboot Ubuntu.

Restart virtualbox, select your VM, then click settings. You should have no error messages now.

The other thing you'll want to do is install Guest Additions.  You should be able to find that under "Devices" in the VB menu once you've started your VM.  If nothing happens when you click on "Install Guest Addtions" navigate to your CD/DVD drive in your VM and open it.  Click on the install/setup icon to install it.

---

