---
title: "Desktop resolution is right but login screen isn't."
date: 2016-01-08
forum: Virtualisation
---

### Post by yongcamu on 2016-01-08
Good day there!

I'm looking for assistance for the matter mentioned. My guest OS is Lubuntu 15.10 running on a VirtualBox 4.3.10. I can't seem to be able to adjust my login screen resolution. I have done several reinstalls trying out the multiple methods recommended to adjust the resolution.
[LIST]
[*]via apt-get as mentioned [here]("http://askubuntu.com/questions/3205/higher-screen-resolution-in-virtualbox"). 
[*]via VirtualBox's guest additions iso as mentioned [here]("http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm"). 
[*]via xrandr as mentioned [here]("http://askubuntu.com/questions/95977/set-a-specific-screen-resolution-with-xrandr"). 
[/LIST]
All of the above works perfectly in changing my desktop resolution but none of them seem to affect the login screen. Any tips on what else I could try or use to solve this?

Thank you,
Nicholas.

---

### Post by MAFoElffen on 2016-01-08
What happens if you use the grub virtual terminal screen resolution settings*** (instructions in post #1 of the sticky linked in my sig line)?

***Because that setting is what effects the virtual terminal, splash, and login manager resolutions.

---

