---
title: "Flash Player"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-08
G'Day, Done an update/upgrade yesterday, seems Firefox upgraded as well, when i opened Firefox later and went to You Tube I had to reinstall Adobe flash player (??) so I downloaded the .tar.gz and installed using the code in the readme, after extracting, 
 Code.
cd Downloads
      sudo tar -zxvf (file name)install_flash_player_11_linux.tar.gz
         libflashplayer.so
         sudo cp libflashplayer.so /usr/lib/mozilla/plugins

Now when i go to You Tube the skin tones are all blue (???) any ideas ?
Regards Miykel

---

### Post by kaldor on 2012-04-08
I believe this is related to the proprietary NVIDIA driver. There have been a lot of complaints about this recently, and some people have had luck with some tweaks.

Google around for stuff from the last few days or so. I can't remember the exact place to find the fix myself. 

Temporary solution:

If you use the NVIDIA driver, but don't really need it, try removing it from the Additional Drivers application. Nouveau should be enough for basic usage and non-gaming.

---

### Post by lovinglinux on 2012-04-08
See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Miykel on 2012-04-08
G'Day and thanks for the replies, the link lovinglinux gave worked well, disable graphics acceleration,
    Kind Regards Miykel

---

