---
title: "[GUIDE] Getting your Teletalk 3G Modem to work on Ubuntu 14.04"
date: 2014-08-07
forum: Tutorials
---

### Post by zuhair2 on 2014-08-07
[CENTER][SIZE=5]**[GUIDE] Getting your Teletalk 3G Modem to work on Ubuntu 14.04**[/SIZE]
[/CENTER]
This guide has been tested with the **Teletalk 3G ZTE (MF-193E)**.It *might*  work with earlier versions of the Teletalk modem. It was my wish to  create this guide so that users who own this modem might find it easier  to set up the modem for the very first time on a clean installation of **Ubuntu 14.04**. After spending days (literally) scouring the internet for a **'Teletalk on Ubuntu' guide**, I finally decide there *wasn't* any. I sincerely hope this will save you from any stress.

 

 **You will be needing the following:**

 ```
A Teletalk 3G ZTE (MF-193E) modem
An internet connection on another operating system
 
``` 


First of all, you will need to download **Sakis3G, a script**  that will allow you to substitute the default program that comes with  the Teletalk modem. You will need to do this because the software that  comes with the modem is buggy and it is really hard to get it to work.  At this time of writing, the Sakis3G website is down. So you will need  to download the script from [here]("http://raspberry-at-home.com/files/sakis3g.tar.gz").

 

 Next, you will need to 'Eject' the storage (of the modem) by right-clicking on the 'CD-ROM' icon.  

 Then open up **'Terminal',** and type the following:

 ```
sudo -i  
*type in your password*  
 sudo chmod 755 *replace this text by dragging the sakis3g file here*  
 sudo cp *replace this text by dragging the sakis3g file here* usr/bin/  
 sudo sakis3g  

``` 

 A window will pop-up.
 ```
Click the 'Connect with 3G'
 Click the 'USB device'
 Click the 'ZTE WCDMA Technologies MSM'
 
``` 


It will say “Preparing modem...”

 Then... 

```

Click 'Reported by your modem (wap)'

```

 A window will appear asking you to type in your APN username. Proceed to type in *anything you like*

 The window *might *reappear, type in *anything you like* again.
According to the Sakis3G rules, you can type anything you like in the APN box, if your modem doesn't use an apn.

 
Hopefully, it will show the **“Connected ****to the internet” **message!
> 
CREDITS TO** RASPBERRY AT HOME** FOR THE SAKIS3G SCRIPT.

---

