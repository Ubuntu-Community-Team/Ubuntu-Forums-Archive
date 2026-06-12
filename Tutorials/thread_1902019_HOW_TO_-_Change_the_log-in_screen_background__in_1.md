---
title: "HOW TO - Change the log-in screen background  in 11.10"
date: 2011-12-29
forum: Tutorials
---

### Post by Bryan Hill on 2011-12-29
Hello, 

I just recently returned to Ubuntu after a few years in Windows 7 due to the requirements of some of the programming classes I had to take at my university. In any case, upon returning and installing the newest version I was saddened by the log-in screen that was mandated by the Ubuntu creators (no offense Ubuntu creators). After doing some searching I found that no one where I was looking (including here) had any worthwhile suggestions. Maybe I overlooked a post but I thought it would be worthwhile to tell those who may want to make such a change how it is done. And for the sake of simplicity the code that follows is assuming that the image you wish to use for your log-in screen is stored in your /home/<username>/Pictures folder (if the image is not in this folder, change the directory to the folder that does contain the image you would like to have as your log-in screen). You also will need root privileges to make this change. One more thing before I start, the image you wish you replace the current log-in screen will need to be a PNG (Portable Network Graphics) formatted image. 
Start by opening a new terminal window [Ctrl+Alt+t]. Then enter the following commands into the terminal window (the [code] prompts are not entered, they are simply to mark the beginning and the ends of the lines of code, and the <username> section is where you enter the name you are logged into your system as).

[code]
cd /usr/share/backgrounds
sudo rm -r warty-ubuntu-final.png
cd /home/<username>/Pictures
sudo cp warty-ubuntu-final.png /usr/share/backgrounds
[code]

It is actually pretty straight-forward, once you have the image you want to change your log-in window to selected and re-named warty-final-ubuntu.png . If you do not have any images that are in the png format you can easily change them to png simply by opening them in the gimp image editing software, and then save the image as a png image. If you do not have an image you would like to use as your log-in screen, I have attached a zip file containing two images that I created and currently have as my log-in screens on my desktop and laptop. One is 1920x1080, the other is 1366x768. The penguin in the image and the gun he is holding are not of my creation, I simply found them and put them together, and made the penguin realistically look like he is holding the weapon. Someone else had done this before but it didn't appeal to me. I also put it on a larger background and made it into a suitable log-in window background. Let me know if you have any questions, or if the images I supplied are not in a format you can use (they are both widescreen formatted images). 
 - Bryan Hill

---

### Post by Joentokyo on 2012-01-01
When I entered the first line of code you provide ( cd /usr/share/backgrounds) I get the response: no such file or directory. This despite the fact that if I navigate to that file I find it. Don't know why the system says it does not exist.

---

### Post by JRV on 2012-01-01
You can change it with simple-lightdm-manager.

```
sudo apt-add-repository ppa:claudiocn/slm
sudo apt-get update
sudo apt-get install simple-lightdm-manager
```

I have this new program installed on two machines.  It works on one and not the other. 

I'll report back when I am done testing it.

Edit:
I think it is a problem with permissions on the machine where it doesn't work.
I must have changed something.  There has been other weirdness on this machine.

More Editing:
I did a reinstall on the offending machine, it works good now.

---

### Post by yugnip on 2012-01-01
Ubuntu Tweak makes this pretty easy for 11.10 and earlier versions.

---

### Post by Joentokyo on 2012-01-03
> **yugnip said:**
> Ubuntu Tweak makes this pretty easy for 11.10 and earlier versions.

Yeah, when I could not get the method recommended by the original poster to work, I installed Ubuntu Tweaks and used it.

---

### Post by Bryan Hill on 2012-01-04
I don't know what you guys are doing wrong but the suggestion I made works perfectly in 11.10 as it is installed on my machine, installed only days ago with no other modifications. You do not need to do anything else to change the log-in screen background. There probably is a more involved way to change the background, but you do not need to do that since you can easily change it using the method I listed in minutes. As for the person that cannot find the proper directory using the terminal, dunno what to tell you, but if I copy and paste the code directly from my original post ```
 cd /usr/share/backgrounds 
``` I am placed directly in the proper directory and upon then typing ```
 dir 
```  into the terminal I am shown the exact files I am looking for.

---

### Post by Joentokyo on 2012-01-11
> **Bryan Hill said:**
> I don't know what you guys are doing wrong but the suggestion I made works perfectly in 11.10 as it is installed on my machine, installed only days ago with no other modifications. You do not need to do anything else to change the log-in screen background. There probably is a more involved way to change the background, but you do not need to do that since you can easily change it using the method I listed in minutes. As for the person that cannot find the proper directory using the terminal, dunno what to tell you, but if I copy and paste the code directly from my original post ```
 cd /usr/share/backgrounds 
``` I am placed directly in the proper directory and upon then typing ```
 dir 
```  into the terminal I am shown the exact files I am looking for.

I am using the Gnome 3 desktop with 11.10 instead of Unity. That may be a factor.

---

