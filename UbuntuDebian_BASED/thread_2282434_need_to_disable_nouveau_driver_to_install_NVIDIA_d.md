---
title: "need to disable nouveau driver to install NVIDIA drivers"
date: 2015-06-14
forum: Ubuntu/Debian BASED
---

### Post by joseph2 on 2015-06-14
hello.
i am using Lubuntu 11.04 (Ultimate Edition Gamer 3.0) and i need help to correctly disable the nouveau video driver\kernal so i can install the NVIDIA drivers for my gpu. 
i will also need to know how to re-enable the nouveau driver just in case i am unable to install the NVIDIA drivers.

(I repectfully request that no one suggest that i get the lattest version of Lubuntu or Ultimate Edition Gamer. certain personnal issues prevent me from doing so and i count myself lucky to have this version.)

---

### Post by ventrical on 2015-06-14
> **joseph2 said:**
> hello.
i am using Lubuntu 11.04 (Ultimate Edition Gamer 3.0) and i need help to correctly disable the nouveau video driver\kernal so i can install the NVIDIA drivers for my gpu. 
i will also need to know how to re-enable the nouveau driver just in case i am unable to install the NVIDIA drivers.

(I repectfully request that no one suggest that i get the lattest version of Lubuntu or Ultimate Edition Gamer. certain personnal issues prevent me from doing so and i count myself lucky to have this version.)

```


sudo apt-get remove nouveau-firmware

```


In later development cycles it will just jockey over to nvidia. You do not need to remove nouveau-firmware. However .. there might be  a problem with xorg ... but I think the above should work.

Regards..

---

### Post by joseph2 on 2015-06-14
i just tried your suggestion and apt-get returned: "E: Unable to locate package nouveau-firmware". and the nvidia driver installer is unable to disable nouveau.
here is the nvidia-installer.log document in its entirety

```


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jun 14 06:20:26 2015
installer version: 319.60

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 319.60.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
ERROR: The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.  Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.
-> For some distributions, Nouveau can be disabled by adding a file in the modprobe configuration directory.  Would you like nvidia-installer to attempt to create this modprobe file for you? (Answer: Yes)
-> One or more modprobe configuration files to disable Nouveau have been written.  For some distributions, this may be sufficient to disable Nouveau; other distributions may require modification of the initial ramdisk.  Please reboot your system and attempt NVIDIA driver installation again.  Note if you later wish to reenable Nouveau, you will need to delete these files: /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.


```
any thoughts?

---

### Post by QDR06VV9 on 2015-06-14
**Well if you are a brave sort.**
> [COLOR=#ff0000]WARNING! IF YOU YOU DO NOT KNOW HOW TO RECOVER FROM THIS "DO NOT USE"![/COLOR][B]
Removing Nouveau (advanced/expert users)[/B]

From here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

 Nouveau, an open source driver, is installed by default. It's possible to remove it completely, but it is ***not necessary*** and therefore ***not recommended***.  
If you still desire to remove it, you can do so by entering the following command in a terminal: 
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

Just my 2 cents worth _it is better to stay with PPA's to install Nvidia Drivers_.

---

### Post by ventrical on 2015-06-14
> **runrickus said:**
> **Well if you are a brave sort.**

Just my 2 cents worth _it is better to stay with PPA's to install Nvidia Drivers_.

Yeah... after all he is using all the way back to natty so nouveau was not as developed as it is today. Thanks for the helper eh :)

Regards..

---

### Post by bapoumba on 2015-06-14
@joseph2 : 11.04 is way past end of life, you better install a supported release.

---

### Post by joseph2 on 2015-06-15
@ranrickus. i tried the command and it did remove nouveau. well, at least that is what apt-get reported. but the nivdia driver installer reports that the nouveau kernal is still in use. and i did find a nouveau folder in the /sys/module directory. nouveau seems to be dug in like a tick.

@bapoumba. if i were able to get a newer release of Ultimate Edition Gamer, i would have already.

---

### Post by QDR06VV9 on 2015-06-15
@joseph2 I'm afraid we are kind of Spitting into the wind now, your Os was released in[ April 28, 2011 and support ended]("https://lists.ubuntu.com/archives/ubuntu-announce/2011-April/000147.html")[ October 28, 2012]("https://lists.ubuntu.com/archives/ubuntu-announce/2012-October/000165.html")!
And yes I know you are aware of that! **I made a bad mistake in posting the info in my earlier post,** due to fact** I** did not_** read your first post**_ showing me
you were running 11.04. So if anyone was Offended by that I offer my sincere appoligies.
This Link is the only info I can add [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Look where it starts 
> **Up to Ubuntu 12.04**

 If  you need to change drivers without the use of the X GUI, perhaps  because those drivers are not installed, you can with the jockey-text  command. For example:

---

### Post by joseph2 on 2015-06-15
your apology is accepted. as long as we're spitting into the wind we might as well give ourselves enough distance to dodge the wad before it smacks us in the face. eh?

EDIT
-----------------------------------------------------------------------------------------------------------------------
I should mention that i got my drivers directly from the Nvidia driver web site. not the ubuntu repository. and they are for the NVIDIA Quadro NVS 290.

---

### Post by monkeybrain20122 on 2015-06-15
Your OS is long passed end of life as other said. But to answer the original question (after you have updated your OS) , you don't need to remove nouveau, if you install from the repo or use a ppa (don't use the .run file from Nvidia). just install the Nvidia driver and run 
```
sudo nvidia-xconfig
```
Then reboot and nouveau will be disabled when the nvidia driver kicks in. In old tutorials and in distros like Debian you have to remove noveau, but it is a lot easier on Ubuntu now.

It is better to keep nouveau around anyway in case the nvidia driver doesn't work for some reasons you won't boot into a black screen.

Edited: If you are talking about this, there is an up to date release [http://ultimateedition.info/index.php/ultimate-edition/ultimate-edition-4-4/](http://ultimateedition.info/index.php/ultimate-edition/ultimate-edition-4-4/)

---

### Post by joseph2 on 2015-06-16
let me see if i illuminate the the shadows of ignorance so that everyone can understand why i insist on using Ultimate Edition Gamers 3.0 and don't simply get a newer version of any ubuntu distro. 

First, i have (and am currently stuck with) 56k Dial-up internet with an average download speed of 3.0kbps. anyone wanting to ask "well why don't you get something faster?", should think a bit harder and i'm sure they'll come up with at least two good reasons. and odds are one of them would apply to my situation.

Second. the person who shiped me UE: Gamers, lives in Canada. and i live in the central-mid west region of the United States. also, everyone i know that has high-speed internet and am friends with, lives at least 700+ miles (1126.54+ km) from me. 

Third. i can't order a disc (or any other media) from any distro developer because i am EXTREAMLY POOR. 
 
Fourth and last. i do have lubuntu and xubuntu 13.04 but the don't have the games that come with UE:Gamers. and because i have Dial-Up, i can't access the internet with ubuntu.

well that should cover just about any questions. aside from any personal question,which i will not answer in these forums.

---

### Post by monkeybrain20122 on 2015-06-16
What a nice attitude for someone asking for help. Good luck finding it.

---

### Post by howefield on 2015-06-16
Thread moved and closed.

Feel free to try again without the attitude that permeates through your thread.

---

