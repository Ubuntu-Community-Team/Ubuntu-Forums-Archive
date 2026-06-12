---
title: "exporting mp3 with audacity"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by johnnysnotdead on 2009-06-05
I am trying to export a file as mp3 with audacity. When I try to do this it tells me that I have to locate a file named libmp3lame.so.0, but I can't seem to find this file. I have looked around the forums and people have said to use the command sudo apt-get install lame. I have done that and should have the lame mp3 encoder. Can anyone help me find it?

Thanks

Keith

---

### Post by qamelian on 2009-06-05
The specific package you need to install is libmp3lame0. Confirm if it is installed by typing ```
apt-cache policy libmp3lame0
``` in a terminal.
If it is installed this command will tell you so and give you  the version number installed, as well.

---

### Post by vambo on 2009-06-05
I think what you need is libmp3lame0 ie

```
sudo apt-get libmp3lame0
```

---

### Post by johnnysnotdead on 2009-06-05
thank you both very much!

---

