---
title: "wine and windows live messenger"
date: 2009-02-24
forum: Wine
---

### Post by Rushy on 2009-02-24
I am quite new to linux.

I have just install Easy Peasy which runs on Ubuntu 8.10 which is debian based.

I am trying to install windows live messenger through wine, but cannot work out how to get it to work.

I can install it, and when i try to open it i get a system error report.

I have tried with windows live messenger 8.5 and the latest version of wine.

I have tried other alternatives to msn, like amsn, but i need webcam to work, and amsn is crap with webcam.

any suggestions would be greatly appreciated

---

### Post by Vince4Amy on 2009-02-24
> I have tried other alternatives to msn, like amsn, but i need webcam to work, and amsn is crap with webcam.

aMSN is not crap with webcam, there is a bug in Ubuntu 8.10 which prevents webcam from working properly with aMSN and it's not aMSN's fault.

I have got the following versions of MSN/WLM Messenger to install under WINE.

MSN Messenger 6.2
**MSN Messenger 7.0 (Windows 9x Version, Best Choice)**
MSN Messenger 7.5

I think that WLM 8.1 would work at least too.

7.5 has almost the same featureset which is still in use today, however you'll have to install it in XP Mode and run it in 2000 compatibility mode as Microsoft have a forced upgrade for users running 7.5 on XP+.

---

### Post by amritmatharu on 2009-02-24
My webcam seems to work fine with aMsn, but that might be because it's built in to my laptop.

---

### Post by Rushy on 2009-02-24
mine is built in as well.

i have been trying aMsn and it seems to be getting better.

I think my problem may have been lack of available ram on my pc.

I have an eee pc that i formatted the hard drive on and installed ubuntu 8.10


if anyone has any other ideas about better msns please let me know

---

### Post by Rushy on 2009-02-24
i just tried installing messenger 7.5 and it installs and runs. however it only brings the logo up in the system tray for about 5 secs then disappears.

any ideas, i tried installing on windows xp and then running as 2000, but that didnt work

---

### Post by hikaricore on 2009-02-24
Have you looked at and or followed any advice on the appdb?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127](http://appdb.winehq.org/objectManager.php?sClass=application&iId=127)

---

### Post by Rushy on 2009-02-24
thanks that got msn running. but when i try to sign in it brings up a message saying the email address is not availabe or not complete.

the error code i am recieveing is 80070057

should i try a newer version of msn

---

### Post by CodyGuitarist on 2009-02-25
I installed msn on my computer (Intrepid 8.10) and it runs fine. HOWEVER, I can't see the  main screen it's all blue. I've tried reinstalling it and running it in different compatibilities.

Intel 32bit
Wine 1.0.1

---

### Post by Rushy on 2009-02-25
yes i got that as well when i installed msn 8.1 and 8.5 on mine and it was just a blue screen.

when i install msn 7.0 and 7.5 it intalls and runs, but will not sign in.

Thanks

---

### Post by HuaiDan on 2009-02-25
Does aMSN allow webcam feeds over conversations? In II 8.10 I have aMSN working and it recognizes my webcam (a Logitech Mac UVC cam), and I can play with the settings and see the video preview,but I haven't figured out a way to sent video. It seems like a useless feature, but I could be overlooking something. Comments?

---

### Post by Vince4Amy on 2009-02-27
> **HuaiDan said:**
> Does aMSN allow webcam feeds over conversations? In II 8.10 I have aMSN working and it recognizes my webcam (a Logitech Mac UVC cam), and I can play with the settings and see the video preview,but I haven't figured out a way to sent video. It seems like a useless feature, but I could be overlooking something. Comments?

I think SVN Does.

For those trying to run MSN/WLM on WINE did you read this:

> - Set wine to Win2K

- Do sh winetricks riched20 msxml3 flash

Then just install and enjoy it. - AppDb.

---

### Post by Rushy on 2009-02-28
> **Vince4Amy said:**
> I think SVN Does.

For those trying to run MSN/WLM on WINE did you read this:

 - AppDb.

how do i do that,

what are the codes i should enter or the steps.

thanks, im quite new to linux so any help is appreciated

---

### Post by alfplayer on 2009-03-10
I'm trying the latest 8.5 version (8.5.1302.1018). I can't install it emulating win2k, the installer says XP or greater is necessary, so I set wine to XP. I'm stuck with error 80070057 when i try to log in.
I have also tried the latest 2009 version and I get the error MSVCR80.dll not found but it is installed.
I use wine 1.1.16 and Slackware 12.2.

---

