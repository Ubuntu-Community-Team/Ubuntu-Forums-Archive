---
title: "Writing on Windows partition from Ubuntu"
date: 2017-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by jorgeguerra on 2017-05-18
Hello guys, 

I'm new at Ubuntu and I just set-up my 16.4.2 version as a dual boot with Win10. As the default, the OS allows me to manage/edit all the files that I have on Windows partition, however, I have been encouraged not to do it because it could affect Windows OS booting.

Can anyone explain me what are the real risks of doing that?

Thanks in advance.

---

### Post by sp40140 on 2017-05-18
If you edit one of the system files, you could break the windows installation. It will not boot.
The files in "Downloads", "Documents", "Pictures" usually do not cause problems.
So, If you know what you are doing, you should be fine.
However, having said that... If you are doing dual boot, it is a very good practice to create one partition for data where you keep all your documents/audio/video/etc... files. And that partition can be accessed by both OS without risk.

---

### Post by LastDino on 2017-05-18
> **jorgeguerra said:**
> Hello guys, 

I'm new at Ubuntu and I just set-up my 16.4.2 version as a dual boot with Win10. As the default, the OS allows me to manage/edit all the files that I have on Windows partition, however, I have been encouraged not to do it because it could affect Windows OS booting.

Can anyone explain me what are the real risks of doing that?

Thanks in advance.

Windows like any other OS is sensitive to its system partition being "handled", and as a Linux user on dual boot you kind of get unrestricted/unsupervised access to these system files/system partition as they are viewed as normal files. 

So, it can happen that accidentally you do something on there which you shouldn't. And this is true even if you know what you're doing, it just happens that you ended up deleting something >for example a temp file of active download on windows partition while being in Linux mode in Download folder (or whichever you have set it for). And solving problems arising from this can not be as simple as fixing problems with Linux (yes, you heard right) because you don't actually have access to the core files/codes and what not on licensed Windows as compared to any Linux OS. 

What was advantage for average user turns into disadvantage as soon as you become more advanced.

---

