---
title: "Meizu Mx4 Ubuntu touch all application run on the background and the switcher not wor"
date: 2015-12-11
forum: Ubuntu Phone and Tablet
---

### Post by stryker.hun on 2015-12-11
Hello!
I had big problem with my phone. I take the apt-get upgrade  commend on the terminal (phone), and freeze and restart. The result: the  phone boot and load but not fully... 
Only work the left panel but ifi lunch the call ,sms etc the program lunched and go to background (black screen).

I tired:
[http://ubuntuforums.org/showthread.php?t=2287798](http://ubuntuforums.org/showthread.php?t=2287798)
At recovery mode:

      [COLOR=#000000]foldeak@it3l:~/meizu$ ubuntu-device-flash touch --channel ubuntu-touch/stable/meizu.en --bootstrap --recovery-image recovery.img [/COLOR]
[I][FONT=monospace]2015/12/11 11:46:19 Expecting the device to be in the bootloader... waiting 
2015/12/11 11:46:21 Device is |arale| 
2015/12/11 11:46:21 Flashing version 7 from ubuntu-touch/stable/meizu.en channel and server [https://system-image.ubuntu.com](https://system-image.ubuntu.com) to device arale 
Can't boot recovery image[/FONT][/I]


Ok maybe the recovery.img wrong..[COLOR=#000000]
ubuntu-device-flash query --device=arale --channel=ubuntu-touch/stable/meizu.en --show-image[/COLOR]
[FONT=monospace] 
[/FONT]
           [FONT=monospace][COLOR=#000000]Device: arale [/COLOR]
Description: ubuntu=20151118.2,device=20151016-0b38025,custom=20151111-918-8-52,tag=OTA-8,version=7 
Version: 7 
Channel: ubuntu-touch/stable/meizu.en 
Files: 
 0 [https://system-image.ubuntu.com/pool/ubuntu-dcb4f2e9d6bd32edd5c0fda04ba2f6b74d954c0f16d93abe9d1bdcf917982177.tar.xz](https://system-image.ubuntu.com/pool/ubuntu-dcb4f2e9d6bd32edd5c0fda04ba2f6b74d954c0f16d93abe9d1bdcf917982177.tar.xz) 296138328 2861ae475d86ce3f663d79299322c1ef67f7cad792123
c03ead4ced9896b4149 
 1 [https://system-image.ubuntu.com/pool/device-a8a0e27cb5670a0ccb9dacd2b12dc80b2df8fe776235cf9a0f7478ef7aa934a4.tar.xz](https://system-image.ubuntu.com/pool/device-a8a0e27cb5670a0ccb9dacd2b12dc80b2df8fe776235cf9a0f7478ef7aa934a4.tar.xz) 108331440 b838077504b4ac2bdbc9ab99ea65d2a834fcfad6514e7
d5de16f0b9ffd8c08dd 
 2 [https://system-image.ubuntu.com/pool/custom-b431073371410216cc6bab42bc8a1aa5e2e189ec5d9e0b7e8a534f098ddaa147.tar.xz](https://system-image.ubuntu.com/pool/custom-b431073371410216cc6bab42bc8a1aa5e2e189ec5d9e0b7e8a534f098ddaa147.tar.xz) 55627136 b4f14f7366cd51dae6a663043190947525e100be9e87e9
5f9e7f275597774fc2 
 3 [https://system-image.ubuntu.com/ubuntu-touch/stable/meizu.en/arale/version-7.tar.xz](https://system-image.ubuntu.com/ubuntu-touch/stable/meizu.en/arale/version-7.tar.xz) 460 4e8a754fd1f00e1acfcd9edd21971034b8380e6c7b2861b7caf818ed7aae49ec
[/FONT]
   
i downloaded the [FONT=monospace]device-a8a0e27cb5670a0ccb9dacd2b12dc80b2df8fe776235cf9a0f7478ef7aa934a4.tar.xz and extract the recovery.img 
and again but not work...
[/FONT][FONT=monospace][I][COLOR=#000000]Can't boot recovery image
[/COLOR][/I][/FONT]


(sry for my english)

---

### Post by bugthing on 2015-12-22
Hello,
I wondered if you got anywhere with this issue?.. I seen to have a simlar symtoms with same device .. my hashes are slightly different, but the same fix might work for us both.

thanks for any help,
-ben
```


sudo ubuntu-device-flash query --device=arale --channel=ubuntu-touch/stable/meizu.en --show-image
2015/12/22 19:41:41 Device is |arale|
Description: ubuntu=20151210,device=20151016-0b38025,custom=20151111-918-8-52,tag=OTA-8.5,version=8
Version: 8
Channel: ubuntu-touch/stable/meizu.en
0 https://system-image.ubuntu.com/pool/ubuntu-0612f1183b56c12bfb61e9a2dd122714567c6083dc65b7204e3e26a4deb21c18.tar.xz 295505344 4e264b5c285f1271c2dfa6eb95e58291a16ce3b3ff5357f78746301ba98a6a3a
1 https://system-image.ubuntu.com/pool/device-a8a0e27cb5670a0ccb9dacd2b12dc80b2df8fe776235cf9a0f7478ef7aa934a4.tar.xz 108331440 b838077504b4ac2bdbc9ab99ea65d2a834fcfad6514e7d5de16f0b9ffd8c08dd
2 https://system-image.ubuntu.com/pool/custom-b431073371410216cc6bab42bc8a1aa5e2e189ec5d9e0b7e8a534f098ddaa147.tar.xz 55627136 b4f14f7366cd51dae6a663043190947525e100be9e87e95f9e7f275597774fc2
3 https://system-image.ubuntu.com/ubuntu-touch/stable/meizu.en/arale/version-8.tar.xz 456 e396f7956d4cb7c5d892d4519fc9fdf203554611affd35110b7819ba42e59c06


```

---

