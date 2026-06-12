---
title: "Reset remote Linux server ubuntu"
date: 2011-05-27
forum: Server Platforms
---

### Post by vahdani_d on 2011-05-27
Hi 
I am a Linux server with remote reset that have problems can you please help where is the problem? 
From their command system reset Systmm comfortable coming up now and 
Code: 
reboot, but the remote when the remote connection'm system (SSH) system off now and again up coming course PowerShot clear Gone should go hand Rystsh I should What can I do to reset open command I use, but the system just off now and PowerShot clear Gone and Thank you for coming up please guide 
Code: 
reboot

---

### Post by arrrghhh on 2011-05-27
> **vahdani_d said:**
> Hi 
I am a Linux server with remote reset that have problems can you please help where is the problem? 
From their command system reset Systmm comfortable coming up now and 
Code: 
reboot, but the remote when the remote connection'm system (SSH) system off now and again up coming course PowerShot clear Gone should go hand Rystsh I should What can I do to reset open command I use, but the system just off now and PowerShot clear Gone and Thank you for coming up please guide 
Code: 
reboot

This is incoherent.

Please take it slowly and simply describe what you're trying to do...

You want to reboot to server remotely - but cannot?```
sudo reboot
```or```
sudo shutdown -r now
```Should do the trick.  However, if you're not near the server physically, you may need 'remote hands' to help you if the reboot doesn't go so well...

---

### Post by vahdani_d on 2011-05-27
I want to reboot to server remotely - but cannot?
I work with the same command
sudo reboot
 But just off the system s will not restart and will not turn on

---

### Post by arrrghhh on 2011-05-27
> **vahdani_d said:**
> I want to reboot to server remotely - but cannot?
I work with the same command
sudo reboot
 But just off the system s will not restart and will not turn on

Like I said, when rebooting a server having physical access (or knowing someone with physical access) is **required**.

If there's any issues with the reboot, the server won't come back up remotely - unless you have some sort of backdoor in (HP has iLO, IBM RSA, Dell DRAC, etc) then you'll need someone to physically check the box.

---

