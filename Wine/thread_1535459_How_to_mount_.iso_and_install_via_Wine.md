---
title: "How to mount .iso and install via Wine"
date: 2010-07-20
forum: Wine
---

### Post by psychx on 2010-07-20
How can I mount a specific ISO file, and run it via Wine?

I am running Ubuntu 10.04. I found something online, but it's not working. I was using this in Terminal, as root:

```

sudo -s
cd /home/mike/Downloads/riseofnations/
mount -o loop -t iso9660 riseofnations.iso /cdrom

```

Nothing happens after that. Any help is appreciated. Thanks!

Edit: It's telling me it's already mounted - but I can't see it anywhere. It's not loading either. Any ideas?

---

### Post by new__buntu on 2010-07-20
> **psychx said:**
> How can I mount a specific ISO file, and run it via Wine?


I'm confused, how would Wine run an ISO if Wine's a compatibility layer for windows apps and windows doesn't natively deal with ISO's? Could somebody explain this to me?

---

### Post by psychx on 2010-07-20
I need to run an ISO in order to install it via Wine. Do you understand? If there is a different way to do it, please contribute. Otherwise, don't hijack my thread. Thank you

---

### Post by marshmallow1304 on 2010-07-21
Well, is there anything at the mount point?

```
ls /cdrom
```


If so, go ahead and run with wine.

```
wine /cdrom/setup.exe
```


EDIT: **Remember to return to normal user first**.

---

### Post by new__buntu on 2010-07-21
> **psychx said:**
> I need to run an ISO in order to install it via Wine. Do you understand? If there is a different way to do it, please contribute. Otherwise, don't hijack my thread. Thank you

Gotcha, thanks, and sorry, didn't mean to step on any toes.

---

### Post by elliotn on 2010-07-21
Right click on it and open it with archiver mounter the explore the staff that is in the iso and open whatever it is that is windows compitability with wine.

---

### Post by psychx on 2010-07-21
> **new__buntu said:**
> Gotcha, thanks, and sorry, didn't mean to step on any toes.

No problem, and I didn't mean to come off as rude - I just wasn't sure of your intentions.

---

And to marshmallow1304:
It shows that it is mounted via Terminal, I was originally checking through the GUI - which showed nothing.

Now, I logged back into my normal user account - and ran the setup.exe with wine. Now, it did work at first. Although, after giving the cd key, now it is telling me that it cannot load a certain file (PidGen.dll) that is located in the primary /cdrom/ directory. Any ideas if this might just be a corrupt ISO file, or if there is something else wrong?

---

### Post by elliotn on 2010-07-21
Remember that wine isnt windows, its an emulator it wont work perfect for some.

---

### Post by psychx on 2010-07-21
This actually what Terminal is spitting out when I get the error in the GUI.

```

mike@mike-desktop:/cdrom$ wine /cdrom/setup.exe
mike@mike-desktop:/cdrom$ fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x805, disabling mixer
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\windows\\Fonts\\BookOS.ttf") stub
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\cdrom\\Pidgenx.dll") not found

```

Do I need to install that .DLL somewhere in the windows folder within wine? Looks like that file might be part of Visual C++ 6.0, according to Google.

---

### Post by ssully on 2010-07-21
I don't use Wine much, but I can probably get you most of the way to where you want to go.

Let's suppose your image file is called image.iso and located in your home directory.  You can mount it to something like /media/iso as follows:

```
sudo mkdir /media/iso
sudo mount -t iso9660 ~/image.iso /media/iso -o loop
```

You can then check that the image file was successfully mounted by going to /media/iso and seeing that it contains the expected files.

As far as using the image in Wine, I think you can probably just add /media/iso as a drive under Wine Configuration.

You might also find some additional info here: [http://ubuntuforums.org/showthread.php?t=638068](http://ubuntuforums.org/showthread.php?t=638068)

Does that help?

---

### Post by psychx on 2010-07-21
> **ssully said:**
> I don't use Wine much, but I can probably get you most of the way to where you want to go.

Let's suppose your image file is called image.iso and located in your home directory.  You can mount it to something like /media/iso as follows:

```
sudo mkdir /media/iso
sudo mount -t iso9660 ~/image.iso /media/iso -o loop
```

You can then check that the image file was successfully mounted by going to /media/iso and seeing that it contains the expected files.

As far as using the image in Wine, I think you can probably just add /media/iso as a drive under Wine Configuration.

You might also find some additional info here: [http://ubuntuforums.org/showthread.php?t=638068](http://ubuntuforums.org/showthread.php?t=638068)

Does that help?

First, I have a question about what you said. If I mkdir any directory in /media/ then I can mount to it? so mkdir /media/2j4jj43nm3 - it would create that directory and I could mount to it? Just wondering/clarifying.

Secondly, I fixed it! When I realized that MFC42.dll was missing, I googled it. It ended up being part of the Visual C++ 6.0 set of files. I found a Microsoft KB article about it, and was able to download the installer for those files. I ran the installer in wine, and got the files extracted to the correct location. This is usually in the system32 folder. I re-ran the setup.exe on the ISO via wine, and all is working! It has installed and everything. 

Thanks for all the help, and I will check back to see if you reply to this, ssully. Thanks!

---

### Post by marshmallow1304 on 2010-07-21
You can mount anywhere you like, but in the majority of cases it's best to mount in an empty directory.

---

### Post by Elfy on 2010-07-21
Moved to Wine forum.

---

### Post by ssully on 2010-07-21
> **psychx said:**
> First, I have a question about what you said. If I mkdir any directory in /media/ then I can mount to it? so mkdir /media/2j4jj43nm3 - it would create that directory and I could mount to it? Just wondering/clarifying.

That's right.  You access a filesystem by mounting it to an empty directory.  When you're done with the mounted filesystem, you can unmounted with umount, and the directory will go back to being empty.  The directory doesn't need to be in /media, but that's a logical place to put an iso.

See additional explanation here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Glad you got everything working!

---

### Post by soldier1st on 2010-07-22
if your trying to mount an iso try installing furious iso mount and right click on it and tell wine to open it and it should begin to install like a windows program.

---

### Post by Komputor on 2010-08-17
First off, great post!  But I seem to be running into a problem. I mounted my iso to /media/iso using Gmount, and reconfigured wine's "D" drive to the path /media/iso and made sure the type is set to cdrom and the program is stuck waiting for a disk. Not sure what else to do here. I have made sure the files mounted properly and also made sure that I am logged in as a normal user and still nothing. Thanks ahead of time for the help.

---

