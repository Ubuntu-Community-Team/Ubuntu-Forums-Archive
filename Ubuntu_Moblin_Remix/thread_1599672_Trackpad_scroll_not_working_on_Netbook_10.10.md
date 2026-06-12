---
title: "Trackpad scroll not working on Netbook 10.10"
date: 2010-10-18
forum: Ubuntu Moblin Remix
---

### Post by sriman on 2010-10-18
Greetings All,

I have installed Netbook 10.10 on my Samsung NP-N148-DP03IN. Sound, camera and most of the stuff works just fine. I am not able to use the track-pad scroll. Please provide a solution for the same. I am looking for a permanent solution which continues to work even after the system restart. TIA.

Cheers,
Sriman

---

### Post by sturg_nz on 2010-10-18
Hi Sriman,
I don't have a Samsung but found a package which got my touchpad scrolling working much more realiably. 
gpointing-device-settings

Hope this helps,

---

### Post by sriman on 2010-10-18
Thanks a lot for your input sturg_nz. I will try this out and update the results.

---

### Post by farbridges on 2010-10-18
On the Dell e6410 scrolling on the touchpad also does not work. So i gave gpointing-device-settings a try. Unfortunately it only lists a "PS/2 Generic Mouse". So probably it's a driver problem?

---

### Post by ankushgaur on 2010-12-27
Hi
This is my first post in Ubuntu forums :)

I am still a noob with ubuntu but i think i have a solution. Try this ,  when u update Ubuntu your grub is updated. so boot with the previous  entry in the grub, this fixed the problem for me.

---

### Post by logangorence on 2011-01-02
Try Mouse settings in system.

---

### Post by slw0000 on 2011-02-10
Penitence is something that enervates our spirit, causing a greater loss than loss itself and making a bigger mistake than mistake itself, so never regret.

---

### Post by drsjlazar on 2011-03-27
This is probably a little too late but I was also experiencing the same problem on another Samsung N148 netbook. I found that the root problem is that Xorg is not setting the proper values for the right edge of the touchpad. In short, it expects the touchpad to be bigger and hence the edge to be further off to the right from where it actually is. The solution is telling Xorg where the edge really is.

Edit the file /usr/share/X11/xorg.conf.d/50-synaptics.conf with admin privileges and add the option line as shown below.

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "RightEdge" "790"
EndSection

```The solution for other laptop/netbook models will be similar though the value (790) may differ. A lower value places the edge further to the left and vice versa. A similar solution can be applied for horizontal scrolling if required. Run 'man synaptics' for more info.

This may not be the ideal file to place this setting as it will affect all touchpads... but I don't plan on using another one on this machine.

Hope this helps.

P.S. Many times while using two-finger scrolling, on lifting the fingers the page would jump to either the very top or bottom. Did you experience this behavior?

---

### Post by myjr52 on 2011-04-13
>>P.S. Many times while using two-finger scrolling, on lifting the fingers the page would jump to either the very top or bottom. Did you experience this behavior?

This was driving me crazy for the last several months. The following would fix the jumping cursor problem. It works for my samsung nb30plus.

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

---

### Post by rosencrantz on 2011-04-15
I am not sure whether this applies to you, but there has been an issue with a number of Asus laptops and their Elantech touchpads. Add (temporarily) 
psmouse.force_elantech=1
to your kernel parameters in grub.
How to do that:
In the grub menu, select the standard Ubuntu, press 'e'
Append 'psmouse.force_elantech=1' to the end of the line starting with 'linux' 
Press Ctrl+X to boot.

If this works, you can make the boot parameter permanent by editing /etc/default/grub and adding psmouse.force_elantech=1 to the parameter list set by GRUB_CMDLINE_LINUX_DEFAULT.
(e.g. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.force_elantech=1")

---

