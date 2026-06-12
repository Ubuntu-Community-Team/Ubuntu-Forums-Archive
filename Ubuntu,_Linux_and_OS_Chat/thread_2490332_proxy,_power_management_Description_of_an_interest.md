---
title: "proxy, power management: Description of an interesting experience with 22.04 desktop"
date: 2023-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by ya-bberry on 2023-08-30
[FONT=arial]Hi, 

Just wanted to share this for whatever its' worth. Feel free to ask for  details if anyone's interested. I'll give enough for context. Sorry up  front for not being savvy on specific terminology. Ubuntu is a godsend,  and I've been a refugee from the windows badlands since about 2016, but  have selfishly remained totally in the shadows only ever reading these  forums for the tech tips I need to get through whatever I had to get  through at the time.

Punchline is that my desktop was in an unusable state this morning, and I  had to spend several hours troubleshooting and recovering. First quick  fix was temporarily reverting from "performance" to "balanced" on the  power management setting. None of this required much technical skill,  and much of the difficulty is (admitting this up front) because of my  unusual configuration.

My reason for posting is essentially just self-therapy :smile: ... but I am interested if anyone is interested in this.

My rig is an ancient dell pc (2007, i think). Again if you're interested  and want me to track down technical details, just ask. I connect to the  internet via a web proxy, although I haven't yet been able to get apt  to work through the proxy with 22. So I initially installed off of a usb  and configured the box by temporarily hogging the direct connection.  Also installed chrome at that time, because firefox doesn't work on all  sites through the proxy. Also, had used [/FONT]
powerprofilesctl set performance
to change the performance setting .. even just a half-minutes use with  the balanced setting is rather intolerable given how underpowered and  how little memory this machine has. I'd been happily enjoying an lts 18  rig on a better machine that suddenly glitched a few months back now,  and can't afford a replacement at this time.

The Symptoms:

() at first it seemed the mouse buttons didn't work, circumventing them  revealed it was intermittent, and as was later proven out, was not a  hardware problem.
() the problem continued after a reboot and was exacerbated by the  disappearance of the mouse pointer except on the top and left bars  (whatever you call them thingys).
() eventually, while I was text editing (emacs) the cursor started  jumping, that's when I gave up and realized I couldn't work until this  was fixed
() opening settings failed, and running gnome-control-center from a console gave me the error below
() eventually, when trying to fix the issue, a console I was using kept rendering the string "low", in bursts

Seems like some thread of something somewhere was trying to output this  message ... "low", and was interfering with all of these other  operations in doing so

The error I got from opening settings on a console was as follows:sad:gnome-control-center:4710):  cc-power-profile-row-CRITICAL **: 20:12:10.458:  cc_power_profile_row_get_radio_button: assertion  'CC_IS_POWER_PROFILE_ROW (self)' failed
**
power-cc-panel:ERROR:../panels/power/cc-power-panel.c:1122:razz:erformance_profile_set_active: assertion failed: (button)
Bail out! power-cc-panel:ERROR:../panels/power/cc-power-panel.c:1122:razz:erformance_profile_set_active: assertion failed: (button)
Aborted (core dumped)

================================

[FONT=arial]So from that google led me here -> [/FONT][FONT=arial]
[/FONT][https://www.jeffgeerling.com/blog/20...pu-performance]("https://www.jeffgeerling.com/blog/2022/ubuntus-settings-wont-open-after-setting-cpu-performance")

[FONT=arial]And changing the power management setting to "balanced" seemed to restore normal desktop function. 

I did a long-delayed apt update and upgrade and a cycle of app updates by reverting to the direct connection from proxy
(which is what took so much time) and replaced chrome with opera in the hopes of preventing this from recurring

I suspect chrome because I had noticed that in recent days using chrome resulted in a major overall performance hit.
I speculate that although apt can't use the proxy, I'd done enough proxy configuration on the box trying to get that 
to work that some applications or sub-sets of the os WERE getting through and updating themselves.

I suspect this because I hadn't installed anything new on the machine since the initial configuration that could
explain why it suddenly destabilized like that. The installers on previous installs of 16 and 18 had correctly self
configured during install so that apt worked through my web proxy. Not the case with 22.

Anyways, thanks for your interest.[/FONT]

---

### Post by TheFu on 2023-08-30
Good therapy session. Sometimes it has to be done.

---

### Post by grahammechanical on 2023-08-31
This may or may not be related but on 20.04, 22.04 and 23.10 (development) I find that the latest kernels are running the system hotter than earlier kernels. On 22.04 and 23.10 dropping the power setting from Balanced to Power Saving reduced the temperature by 10 degrees or more. Alternatively, I run an earlier kernel. I do not update through software updater as that will remove the earlier kernels. 

On 23.10 (development) the 6.3 kernel runs hotter than the 6.2 kernel.

I am using a laptop and although the temperature is not rising to dangerous levels I do not like the fan running all the time. Brief runs to bring the temperature down are acceptable but not constant running of the fan to keep the temperature from 70 degrees to 60 degrees. It will also reduce battery charge life.

Ubuntu 20.04 does not allow the changing of the power setting. So, I use Advance Options to run Linux kernel 5.15.0-78 instead of the latest of 5.15.0-82. Updating through the terminal is important because I do not want to lose the 15.5.0-78 kernel.

I forgot to mention that kernel 5L15.0-78 run Ubuntu 20.04.6 at 41 degrees. Why are the other kernels on 22.04 and 23.10 so mush higher. 

Regards

---

### Post by coffeecat on 2023-09-01
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

