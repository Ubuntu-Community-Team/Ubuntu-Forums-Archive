---
title: "New PanP8 Won't Boot"
date: 2011-11-14
forum: System76 Support
---

### Post by jwh400 on 2011-11-14
I took delivery of it today, started it and went through the set-up of username, password, timezone, etc. When I finished that the screen went black and I waited about 15 minutes and hit Ctl Alt Delete and restarted.

I got the splash screen, the Ubuntu screen and then a black screen with the following;

*Starting bluetooth [OK]
*PulseAudio configured for per-user sessions saned disabled; edit /etc/default/saned [OK]
*Stopping cold plug devices [OK]
*Stopping log initial device creation [OK]
*Starting configure network device security [OK]

And that's where it stays. I've restarted several times with the same results.

I called the toll free number but no one was in. does anyone know the tech service hours?

---

### Post by Flyers2391 on 2011-11-15
I believe they are around 8 AM - 5 PM Denver time Monday through Friday.  

I read other folks with brand new systems have the same issue and they had to re-install.  I thought I read it was a problem with their imaging of the systems right after 11.10 but I can't find where I read that now.  

You are probably best to re-install and follow these instructions: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by jwh400 on 2011-11-15
WTF!!! They know about this and they're shipping them anyway? No wonder they won't return my call or reply to my email. Shipping it DOA is bad enough but not providing a disk to aid in our self-service tech support is a slap in the face. 

What is this System76 driver? Why is it needed? The installation of Ubuntu has been streamlined to the point of being a breeze and I actually look forward to installing it on a new user's computer. But the added steps of installing this driver is clumsy and retro. Unbelievable.

I guess since it's up to me to correct this $1000 mistake, this issue can be marked as resolved.

---

### Post by isantop on 2011-11-15
This issue does not require reinstallation. You can recover your system by pressing Ctrl+Alt+F1, logging into the text terminal, then running these commands:

```
sudo chown lightdm:lightdm -R /var/lib/lightdm
sudo reboot
```
After running the second command, your system will reboot, and will pull up the login screen.

We didn't find out about this issue until very recently, after some computers had shipped. We have since applied a fix that patches the issue, but the systems that already left manufacturing obviously couldn't have had it applied.

---

### Post by jwh400 on 2011-11-15
Command seemed to work, no error message.
Tried restart command but remained on black screen.
Waited a few minutes.
Held power button to shut down.
Restarted and made it to black screen with text.

Repeated above three times.

I'm re-installing Ubuntu. Is the System76 driver actually needed to run Ubuntu on this computer?

---

### Post by isantop on 2011-11-16
It sounds almost like you're not actually at a command line. Were you able to log in fine? What did you see after pressing Ctrl+Alt+F1?

On the PanP8, the driver is required to enable the brightness hotkeys on the laptop. Ubuntu will install and otherwise run just fine on it.

---

### Post by jwh400 on 2011-11-16
I had no problem with the command line. After entering the first line the cursor moved down waiting for the next command. The reboot command did nothing. I mentioned in an email to System76 that this was the first time I've been unable to shut down a machine from command line. 

But anyway the OS is installed and I'll grab the driver and this should be finished.

---

### Post by jwh400 on 2011-11-17
I have everything up and running. Spent yesterday evening customizing it and took it to work today and put it through it's paces which means it was under constant use. No problems, no issues.
A very nice laptop. Highly recommended.

---

