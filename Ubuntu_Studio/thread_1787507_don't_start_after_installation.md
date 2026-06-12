---
title: "don't start after installation"
date: 2011-06-21
forum: Ubuntu Studio
---

### Post by ub-user on 2011-06-21
Hello,

i installed the latest version of UBUNTUstudio 11.04 (x86) on my computer ASUS P5KC,
during the installation all went good expect the DHCP installation, after the reboot the OS couldn't start , nothing is done (black screen only).

help please !

thanks

---

### Post by sanderd17 on 2011-06-21
Can you follow this steps for us and post the output?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And how did you install it? Single boot, dual boot or inside Windows with wubi?

---

### Post by ub-user on 2011-06-21
hello,

i installed it as signle boot

about  the bootinfoscript downloading & installing procedure:

1- i can't run my computer, so how it's could be done?
2- i'm not experimented enough under linux OS to execute the command on the terminal ('m new linux user)

 thank you

---

### Post by jejeman on 2011-06-21
> 1- i can't run my computer, so how it's could be done?Start livecd.
> 2- i'm not experimented enough under linux OS to execute the command on the terminal ('m new linux user)
1. download the script
2. in Nautilus find the downloaded file, right click on it, choose properties, go to permissions tab, tick allow execute
3. Open terminal: ctrl+alt+T
4. change directory to the one where you saved the script with cd command e.g.
```
cd Downloads
```
5. then start the script with command
```
./boot_info_script055.sh
```
notice that name of the script might be different.
> all went good expect the DHCP installation,
How do you know that?
What has DHCP to do with booting OS?

---

### Post by ub-user on 2011-06-21
hello,

i don't understand the 4th step:
(changing directory to the one where you saved the script with cd command e.g.)
more explaination please!
--------------

i knew that the DHCP installation doesn't done because the system shown me that and asked me if i'd like to continue . ( during the installation screen).

thank you.

---

### Post by sanderd17 on 2011-06-21
If you dowloaded it to the Downloads directory (default for Firefox), just copy paste the command.

---

### Post by ub-user on 2011-06-21
do i need to unrar the file because it's zipped!?
 
thank you!

---

### Post by sanderd17 on 2011-06-21
yes,

just go in the live CD and try it, if you see an error message, tell it to us, we will help.

---

### Post by ub-user on 2011-06-21
thank you very much for u all

---

### Post by jejeman on 2011-06-21
Well, little update for my instructions.
The step 2. is need to be done on the sh file not to the zip file. I overlooked that download file is zip file. So, after unpacking the zip file make the boot_info_script.sh file executable.
So, new step is:
1.5 unpack the downloaded file.

---

