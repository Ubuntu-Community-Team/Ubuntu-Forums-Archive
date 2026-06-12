---
title: "Ubuntu CE v2.2 Released!!!"
date: 2007-03-15
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2007-03-15
We are very happy to announce the release of Ubuntu CE v2.2!

This will be the final Edgy release of Ubuntu CE. Our focus will soon shift to the development of Ubuntu CE v3.0 (Feisty).

In Ubuntu CE 2.2 we focused on further refinements to the Dansguardian GUI. The new Dansguardian GUI went through a nice beta test period. Thanks to those from the Ubuntu CE sub forum that helped with their testing and feedback. The new Dansguardian GUI now has both "Basic" and "Advanced" configuration options. This makes it much easier for those who may not be comfortable editing the config files directly. The Enable/Disable feature has also been updated to be more comprehensive in its function. The Dansguardian GUI also includes the ability to adjust the PICS (image filtering) level. 

We have added two new packages to Ubuntu CE. Both packages were developed specifically for Ubuntu CE by user request. These packages are also available for those using default Ubuntu on our new [Popular Packages]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html") page.

The first one is the one that we are most excited about. It is the [e-Sword]("http://www.e-sword.net/") Installer. Many users of Ubuntu CE are former Windows users. Many of them are also users of the very popular [e-Sword]("http://www.e-sword.net/") Bible program for Windows. The new [e-Sword]("http://www.e-sword.net/") installer makes it possible to easily install [e-Sword]("http://www.e-sword.net/") to Ubuntu CE without the need to configure Wine. All of the necessary components are automatically downloaded and installed. Rick Meyers, the developer of [e-Sword]("http://www.e-sword.net/"), has given his blessing on the program. We didn't stop there. We have also included a special [e-Sword]("http://www.e-sword.net/") Module Manager. It allows users to easily install extra modules from the [e-Sword]("http://www.e-sword.net/") site. You can even use the manual install option to install modules from the various unofficial [e-Sword]("http://www.e-sword.net/") module sites.

The second program is also an installer for a commonly requested Windows program. It is the IEs 4 Linux Installer. It uses the [IEs4Linux script]("http://www.tatanka.com.br/ies4linux/page/Main_Page") to download and install Internet Explorer 6. This is a nice feature for webmasters and those who have to visit sites that require Internet Explorer.

We have also updated the Dapper version, Ubuntu CE v1.5.3, to include the latest version of the Dansguardian GUI.

Check it out here:
[www.christianubuntu.com](www.christianubuntu.com)

God Bless, Jereme

---

### Post by kiwidipstick on 2007-03-15
Hi, can I do an upgrade to CE v2.2 from the previous version so that it preserves my home folder and settings?
Blessings, James.

---

### Post by mhancoc7 on 2007-03-15
> **kiwidipstick said:**
> Hi, can I do an upgrade to CE v2.2 from the previous version so that it preserves my home folder and settings?
Blessings, James.

Yes, you can use the upgrade_me script available on the download page. It will allow you to upgrade from a previous release. You will need to use the Edgy version to upgrade from a previous Edgy release of Ubuntu CE.

You can get it here.
[www.mirror.christianubuntu.com](www.mirror.christianubuntu.com)

God Bless, Jereme

---

### Post by kiwidipstick on 2007-03-15
Thanks for that,
Blessings to thee, James.

---

### Post by Ederico on 2007-03-17
I'm upgrading now, will soon return with feedback. :)

---

### Post by Ederico on 2007-03-17
Installed (or rather, upgraded) successfully. Well done to Jereme! This gets even better. :)

Thanks for the *Virtual Rosary* addition, I've wanted to pray the Rosary for a while and this will make it easier for me. You have aided the promotion of prayer, God bless you.

By the way, I've wanted to ask/propose this for a while. I'm not sure whether it is technically feasible but you would be the relative expert in that case, would it be possible to provide an easy installation procedure for Beryl with Ubuntu CE?

Regards,
Ederico.

---

### Post by Ederico on 2007-03-17
I seem like having problems running E-Sword, it should have installed but when I press on "E-Sword" in my Start Menu it doesn't load. I kept all the installation settings as default, changing nothing. Any idea what could be wrong?

---

### Post by mhancoc7 on 2007-03-17
> **Ederico said:**
> I seem like having problems running E-Sword, it should have installed but when I press on "E-Sword" in my Start Menu it doesn't load. I kept all the installation settings as default, changing nothing. Any idea what could be wrong?

I am not sure what is going on here. Do this for me.

Open Terminal and run the following command.
```
/usr/local/apps/esword4linux/./runesword
```

Then post the output.

God Bless, Jereme

---

### Post by Ederico on 2007-03-18
Here you go:

> chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory
wine: cannot find '/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe'
chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory

Seems like a problem with the path I gave for the installation (I didn't change it). If that is the case, where should I install it?

---

### Post by mhancoc7 on 2007-03-18
> **Ederico said:**
> Here you go:


Seems like a problem with the path I gave for the installation (I didn't change it). If that is the case, where should I install it?

I would suggest that you download the e-Sword Installer .deb package from the link below. You can re-install it and then run the e-Sword Installer again. This should fix the problem. If not then tell me exactly what happens when you run the installer.

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

I re-tested both the upgrade_me and convert_me scripts and everything worked great. I am not sure what happened with yours. I am sure we can get it going though.

God Bless, Jereme

---

### Post by Ederico on 2007-03-18
The situation hasn't changed. I can run the Module Manager, but not e-Sword itself. Is there some command I could try perhaps?

---

### Post by mhancoc7 on 2007-03-18
> **Ederico said:**
> The situation hasn't changed. I can run the Module Manager, but not e-Sword itself. Is there some command I could try perhaps?

What exactly happened when you re-installed the .deb package. Did you run the e-Sword Installer again? Does the e-Sword Module Manager actually allow you to install modules? Try this and post the output.

Open Terminal and run:

```
/usr/local/apps/esword4linux/./dg_question
```

You might also try uninstalling the e-Sword Installer in Synaptic. The delete the following directories if they exist.

```
/home/YOURUSERNAME/.esword
/home/YOURUSERNAME/.esword_temp
/usr/local/apps/esword4linux
```

Then install the e-Sword Installer using the .deb file from the Ubuntu CE site.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

This way we are absolutely sure that you are starting fresh. Also be sure to give me every possible detail that you can.

God Bless, Jereme

---

### Post by Ederico on 2007-03-20
> **mhancoc7 said:**
> What exactly happened when you re-installed the .deb package. Did you run the e-Sword Installer again? Does the e-Sword Module Manager actually allow you to install modules?

Yes, I ran the e-Sword Installer again, and yes the e-Sword Module Manager allows me to install modules.

> Open Terminal and run:

```
/usr/local/apps/esword4linux/./dg_question
```

This is the output I got:

```
LiveCD check complete...
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

> You might also try uninstalling the e-Sword Installer in Synaptic. The delete the following directories if they exist.

```
/home/YOURUSERNAME/.esword
/home/YOURUSERNAME/.esword_temp
/usr/local/apps/esword4linux
```

Ok, I tried deleting these, the first two apparently don't exist. I used the command rmdir and I got *"No such file or directory"*, I removed the third one using rm -r and given no error message I suppose it got removed successfully (with rmdir I got the notice that the directory is not empty).

> Then install the e-Sword Installer using the .deb file from the Ubuntu CE site.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

I followed the same process, with the same results. Meaning that the Module Manager supposedly installs stuff (I tried the DR Bible), but e-Sword doesn't load from the Start menu.

---

### Post by mhancoc7 on 2007-03-20
To be sure that you deleted the last folder that I listed run this.

```
 rm -r /usr/local/apps/esword4linux
```

After doing that download the latest version of the .deb and reinstall it. Be sure to go ahead and download it again even if you have the latest version. I just want to be sure we are using the same one.

Now if you get the same result go to the /usr/local/apps folder and copy the esword4linux folder and make it an archive and send it to me. You can attach it to a post or send it via email. This way I can look and see what exactly got installed and what did not.

I am really confused. I have tested and retested the .deb and installer with no problems. Other users have reported success as well. I am really sorry you are having trouble with it. Who knows sometimes it seems that there are "gremlins" in my laptop too. ;)

God Bless, Jereme

---

### Post by Ederico on 2007-03-22
Ok, problem solved. mhancoc check PMs.

---

