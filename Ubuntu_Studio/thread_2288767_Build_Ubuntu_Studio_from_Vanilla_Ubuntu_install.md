---
title: "Build Ubuntu Studio from Vanilla Ubuntu install"
date: 2015-07-29
forum: Ubuntu Studio
---

### Post by Lesbinary on 2015-07-29
Hi. I want to ask a little question regarding Ubuntu and Ubuntu Studio. I want to convert a vanilla install of Ubuntu or Linux Mint with my development configuration into Ubuntu Studio, so I created this script: [https://rhythmtreble.wordpress.com/2014/07/24/use-linux-mint-17-as-ubuntu-studio/](https://rhythmtreble.wordpress.com/2014/07/24/use-linux-mint-17-as-ubuntu-studio/)


```
sudo apt-get update && sudo apt-get --install-recommends install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-photography ubuntustudio-publishing ubuntustudio-video ubuntustudio-font-meta linux-lowlatency && sudo adduser $USER audio
```


My question is: is there anything missing in that script from Ubuntu Studio distribution? Any package? Any configuration? I read the wiki pages [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) and [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) but they are outdated. I tried to do a diff from Ubuntu 15.04 install and Ubuntu Studio 15.04, but the configuration files (like the audio user) are not listed there, obviously. Also, installing Ubuntu Studio and configuring the development environment is not an option.


I would really appreciate the help or any given information.

---

### Post by jejeman on 2015-07-30
Looks, it is all there.

---

