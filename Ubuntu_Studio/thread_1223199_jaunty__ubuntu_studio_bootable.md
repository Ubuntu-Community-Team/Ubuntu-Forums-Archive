---
title: "jaunty / ubuntu studio bootable"
date: 2009-07-25
forum: Ubuntu Studio
---

### Post by tyler.mcg on 2009-07-25
can I use ubuntu studio if i already have ubuntu jaunty or do I have to boot up into the other all the time

---

### Post by chuck_notorious on 2009-07-26
Hi there,

You can install all of the extra packages for Ubuntu Studio from a regular Jaunty installation. That way you don't have to dual boot or anything. There's a pretty in depth discussion here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Hope this helps!

--Charles.

---

### Post by Stochastic on 2009-09-02
> **chuck_notorious said:**
> Hi there,

You can install all of the extra packages for Ubuntu Studio from a regular Jaunty installation. That way you don't have to dual boot or anything. There's a pretty in depth discussion here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Hope this helps!

--Charles.

That page doesn't install Ubuntu Studio at all.  It just adjusts the regular Ubuntu install to be more like Ubuntu Studio.  But that's the long way around.

The proper way of upgrading is much simpler.  See [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation) for more info.

Here are the instructions from Hardy, but they should apply just fine to Jaunty > Instead of reinstalling Ubuntu Studio, you can upgrade to it from a current Ubuntu Hardy Heron install.

    *

      To install Ubuntu Studio, enter terminal & type in:

      ```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

    *

      Optional: Change the theme to UbuntuStudio. In the Ubuntu menu, select System -> Preferences -> Appearance -> Theme and select UbuntuStudio from the list of themes that is presented to you. Then select System -> Administration -> Login Window, enter your password, and select UbuntuStudio in the list of Login Window themes that is presented to you in the Local tab. 

Note: This installs a complete system. If you only want an audio, graphics, or video platform, remove the other respective packages. 

---

