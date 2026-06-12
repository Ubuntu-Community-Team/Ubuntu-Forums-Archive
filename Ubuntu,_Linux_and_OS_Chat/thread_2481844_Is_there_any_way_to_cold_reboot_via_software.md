---
title: "Is there any way to cold reboot via software?"
date: 2022-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by aledosim on 2022-12-10
Hello folks!
I'm testing a hardware on Ubuntu 20.04 and one of the tests is to cold reboot the computer 30 times. So I came here to know if there's any way to do it via software, for the sake of automation (and my sanity). Any discussion on what technically means cold rebooting a machine is very welcome too. As far as I've found in the internet, this things are not so documented.
Hope to see you soon.
Thanks

---

### Post by TheFu on 2022-12-11
No.

You'll need some external hardware that fills the same purpose as IPMI, RIBLO, or DRAC cards in servers.  For about $250, you can get a pi-kvm which I think can do the same thing.  

Or you could get a IoT stand-alone power plug controller that has a separate connection.  Then do a reboot and when the BIOS screen comes up, kill the power at the plug. The BIOS will need to be set to start automatically at power.

If it were me and I wasn't paying, I'd get the pi-kvm. It can provide remote access into a system too with 1080@30 resolutions.

---

### Post by grahammechanical on 2022-12-11
I have no idea what a cold reboot is but there is the shutdown command that will let us halt; power-off or reboot the machine. Run 

```
man shutdown
```


Uses

```
sudo shutdown --poweroff now
```

```
 sudo shutdown --reboot now
```

```
sudo shutdown --halt now
```

I think that you would need to set for automatic login if you want to avoid logging in 30 times. I am not sure what is worse. Using the mouse 30 times to shutdown or typing the shutdown command 30 times. There does not seem to be a keyboard shortcut for shutdown. There is one for logout (Ctrl + Alt + Del)

Regards

---

### Post by TheFu on 2022-12-11
> **grahammechanical said:**
> 
I think that you would need to set for automatic login if you want to avoid logging in 30 times. I am not sure what is worse. Using the mouse 30 times to shutdown or typing the shutdown command 30 times. There does not seem to be a keyboard shortcut for shutdown. There is one for logout (Ctrl + Alt + Del)

'xdotool' can be used to create a single-key-chord that runs any script.  Won't work with Wayland, but I suspect there's a tool that can do that much on Wayland too.

Then just use a non-brain-dead WM and make the chord-keys run either the script or sdotool commands in the WM control. I know how to accomplish this with openbox or fvwm. I'd be surprised if other WMs can't do it as well.

The "cold" restart means that the power was removed from the system, hence the "cold".  A reset isn't the same thing.  

I have an older system that had an older GPU that only works at boot from a cold start.  
* I use 'shutdown -h now' and when that finishes, 
* toggle the little switch on the PSU (not the case) to remove all power, 
* wait 20sec or so, then 
* toggle the power on the PSU on and 
* press the front power button on the system.  

Only this will bring the GPU back enough to boot.  Since I use the system 99.9999% as a server, I really should remove the required GPU support from grub and have it throw stuff to a serial console.  I've been too lazy and have been planning to retire the system for 3+ yrs, so it was never a priority.

Without the PSU switch off/on, the GPU doesn't get reset enough to work.

---

### Post by aledosim on 2022-12-12
Here I use a script that saves the state and includes a line in .profile file that runs the same script again on login. This way I can run a loop throughout the reboots, but unfortunately I cant do it for cold reboot (as stated by TheFu). I'm considering to buy an electronic finger to press the power button repetedly, but I'll investigate the pi-kvm idea.
Thanks a lot.

---

### Post by TheFu on 2022-12-12
> **aledosim said:**
> Here I use a script that saves the state and includes a line in .profile file that runs the same script again on login. This way I can run a loop throughout the reboots, but unfortunately I cant do it for cold reboot (as stated by TheFu). I'm considering to buy an electronic finger to press the power button repetedly, but I'll investigate the pi-kvm idea.
Thanks a lot.

Look up "Useless Machine".  Got one for a gag Xmas present a few years ago for a young relative. Less than $20. Not sure it it will have sufficient force to toggle a power button. That would depend on the case.  Definitely see if the BIOS has a "return to power on state" option.

I have a video recording device that has a finicky button that must be pressed in a specific way to start/stop recording. Sometimes the button needs to be held and wiggled to get the electrical toggle to work. It doesn't really physically depress much. In short, I'd need a slight depression and wiggle action while holding both devices so they cannot move.

---

