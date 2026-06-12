---
title: "ubuntu 22.04 nvidia GT9600 audio spdif via hdmi not working"
date: 2022-04-17
forum: Ubuntu Development Version
---

### Post by MARCO_RUGIADOSI on 2022-04-17
[FONT=arial]Hello Ubuntu community!
I upgraded to 22.04 from 20.04 and now I don't have spdif audio in HDMI. 
In focal I installed the nvidia driver and the audio worked perfectly.

htpc@htpc:~$ ubuntu-drivers devices

htpc@htpc:~$ lspci -vnn | grep VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1) (prog-if 00 [VGA controller])


I like jammy, but this is my hardware, do you have any idea how I can fix it?[/FONT]

---

### Post by MARCO_RUGIADOSI on 2022-04-20
I solved the problem by installing the nvidia driver:

```
sudo add-apt-repository ppa:kelebek333/nvidia-legacy
sudo apt-get update
sudo apt install xorg-modulepath-fix
```

now my old GT 9600 (audio spdif via hdmi) working perfectly

---

