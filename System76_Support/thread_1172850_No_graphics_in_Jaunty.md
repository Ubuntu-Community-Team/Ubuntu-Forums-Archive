---
title: "No graphics in Jaunty"
date: 2009-05-29
forum: System76 Support
---

### Post by teddks on 2009-05-29
I upgraded a friend's Darter Ultra 3 to Jaunty today, and when I rebooted into the new system, everything went fine up to X starting, upon which the screen flickered a few times and then just stayed black. The backlight was working and would respond to the raise/lower brightness keys, but nothing would get displayed and if she logged in, there wouldn't be any sound.

Switching the driver to vesa results in X crashing with corruption -- along the top of the screen there is a greenish image of the usplash theme, and then white horizontal bars cover the rest of the screen.

She has an Intel card -- I tried disabling DRI, enabling UXA, downgrading to xserver-xorg-video-intel-2.4, using the "intel" driver instead of "i810", but nothing got me to a working GDM.

Has anyone else faced similar issues or know of a way to resolve this?

---

### Post by thomasaaron on 2009-05-29
Sounds like a hosed upgrade. Please try booting into recovery mode and running these commands...

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg  #CHOOSE ALL DEFAULT SETTINGS
sudo reboot -h now

Hopefully that will allow you to boot up. However, if your upgrade went that poorly, you may be in for a ton of other issues.

---

### Post by teddks on 2009-05-29
> **thomasaaron said:**
> Sounds like a hosed upgrade. Please try booting into recovery mode and running these commands...

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg  #CHOOSE ALL DEFAULT SETTINGS
sudo reboot -h now

Hopefully that will allow you to boot up. However, if your upgrade went that poorly, you may be in for a ton of other issues.

The xserver-xorg-vide-intel package was installed at the latest version in the Januty repos. I tried reconfiguring X via the "xfix" option in the recovery mode menu -- that didn't work.

The problem isn't with booting, the problem is with starting GDM/X and a subsequent problem with either a system crash or VT switching errors -- there isn't really a way to tell. The only response I get after X tries to start is a response to sysrq combos and pressing the power button (which causes the system to cleanly shut down).

---

### Post by thomasaaron on 2009-05-29
Can you boot into recover mode and extract /etc/X11/Xorg.0.log? That might yield some clues. /var/log/syslog would be good too.

---

### Post by teddks on 2009-05-29
Both log files didn't show much. I don't have the system in front of me, but as I recall, there were very few (if any) errors in Xorg.0.log, and nothing about the crashes in syslog.

---

### Post by thomasaaron on 2009-05-29
Need.... data....  :p

At this point, I wouldn't trust the upgrade very much.

---

### Post by teddks on 2009-05-29
I have no reason to believe that the upgrade failed. I had issues setting up graphics the first time around, but I eventually was able to get it working. What's odd this time around is that after I start X, I can't get to a virtual terminal. I haven't tried logging in via SSH, so I don't know if it's a crash that's doing that, or if it's the graphics, like Nvidia VT bugs.

---

### Post by thomasaaron on 2009-05-29
> I upgraded a friend's Darter Ultra 3 to Jaunty today, and when I rebooted into the new system, everything went fine up to X starting, upon which the screen flickered a few times and then just stayed black.

That sounds an awful lot like a zonked upgrade to me. From a tech support perspective, I've never seen as many hosed upgrades as I've seen going from Intrepid to Jaunty. It's been a veritable nightmare.

But you may be right. If you did a lot of graphics tweaking on this computer in intrepid, it could just be some tweak that didn't translate over.

---

### Post by teddks on 2009-05-29
I don't know what would cause a bad upgrade. Everything during the upgrade process went completely smoothly, it didn't throw any errors, etc. I could check the upgrade logs tomorrow, but I doubt I'd find anything. I think it's much more likely that some tweak didn't transfer, and the new Intel drivers might be factored in somehow.

When I can, I'll post copies of the X logs and snippets from syslog, if I find any. The only interaction I can have with the system is from the "netroot" option in the recovery menu, so my options are a bit limited.

---

### Post by teddks on 2009-05-30
For some reason, fglrx was installed. After it was removed GDM started normally.

---

### Post by weinju on 2009-05-30
Pretty much identical issue: after the first reboot there's only black screen showing after the login.  GUI does not load. 
Removing fglrx packages did not help.  Video: Intel 82915G/GV/910GL Integrated.  Hilfe bitte!

---

### Post by thomasaaron on 2009-06-01
weinju, what System76 model do you have? fglrx is for ATI graphics, not Intel graphics.

---

### Post by weinju on 2009-06-01
thomasaaron, I'm sorry, I just realized I should have posted in the general support, this is not a System76 machine (Intel 82915G). Just the issue is very similar.

---

