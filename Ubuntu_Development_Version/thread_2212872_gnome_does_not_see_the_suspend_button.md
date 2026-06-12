---
title: "gnome does not see the suspend button"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-23
looking at gnome exptensions, I see hibernate. So I installe log in and out, but it is not showing up.
[https://extensions.gnome.org/extension/755/hibernate-status-button/](https://extensions.gnome.org/extension/755/hibernate-status-button/)

also mention alt-modifier to do something with sleep. Anyone know how to get this to work?

---

### Post by kurt18947 on 2014-03-24
This is an irritant to me as well.  On previous distros, Gcampax has kept an  extension , alternate-status-menu (I think) maintained which IMO provides a  power management app superior to  Gnome's.  There are apparently issues with Gnome 3.10 and suspend so right now that extension is not available.  I find that using the 'alt' modifier in conjunction with the power button does work on my two installs.  I became curios about alternative methods to suspend so did a bit of googling.  The 'pm-utils' scripts seem to work but of course only on accounts with sudo privileges.  I was able to modify the sudoers file to allow user accounts to run the "pm-suspend" command and created a desktop launcher (Oh NO!  not THAT!:)) beneath the power button in the upper right corner.  I'm hoping there is an extension update released once 14.04 is closer to the release date.

---

### Post by buzzingrobot on 2014-03-25
The usual way to suspend in Gnome Shell is to press Alt.  The shutdown icon changes to the suspend icon.  No extension necessary.

---

### Post by james114 on 2014-03-26
Try to press the ALT button while the power menu is open, 
it reveals the suspend button in place of the power-off button.

---

### Post by sdowney717 on 2014-03-26
Thanks, hold alt button does change to show  a pause icon and then it suspends.
I am happy to know that, but why hide this? I think people would be better served to click and see suspend.
Otherwise they will have no clue unless someone shows it to them as a hidden feature, makes it less user friendly.

---

### Post by buzzingrobot on 2014-03-26
It's been a bone of contention for some time, but, in the end, it's a choice by the Gnome devs and designers. The functionality is explained in the Gnome docs and in the Gnome help file.  Of course, no one ever reads anything.  In a default Gnome, at first boot, the user is shown a configuration GUI and then the help application is displayed. Ubuntu Gnome does not do that.

---

### Post by kurt18947 on 2014-03-28
> **buzzingrobot said:**
> It's been a bone of contention for some time, but, in the end, it's a choice by the Gnome devs and designers. The functionality is explained in the Gnome docs and in the Gnome help file.  Of course, no one ever reads anything.  In a default Gnome, at first boot, **the user is shown a configuration GUI and then the help application is displayed.** Ubuntu Gnome does not do that.

Ah, that would help.  Perhaps Gnome could put a "how do I" slide show documenting common operations on their home page.  I still fail to see where adding a Suspend or Sleep button to the existing Cancel, Restart and Power Off would be that onerous.  One line of reasoning I've read is that a suspend button is superfluous on a laptop, just close the lid.  Yes that works but our desktops don't have  lids.  I'm faced with moving my wife from Ubuntu 12.04 w/ gnome-shell to 14.04 Ubuntu-Gnome.  She is very structured and doesn't like changing what has worked very well.  I'll have to see what our options are and which she prefers.

---

### Post by buzzingrobot on 2014-03-28
Yes,  putting up that kind of tutorial on first boot is something every DE do. When Gnome 3 was first released, several pretty good video tutorials were done, with a live human, that focused on one aspect of the new design. If Gnome has the resources, they should consider doing an entire tutorial series and packaging it for activation after first boot on the default install.  

I spent about a week with 14.04 Gnome.  It uses Gnome 3.10, which is an improvment over the older versions.  I did not find it dramatically different in any significant way, though, so it might not take long to get used to. Take a look at extensions.gnome.org to see if anything there can simplify things. There is an "Alternative Status Menu" extension that adds buttons for suspend and logout.

---

### Post by sdowney717 on 2014-03-28
I just installed alternative status menu.
Still no suspend button.
[https://extensions.gnome.org/extension/5/alternative-status-menu/](https://extensions.gnome.org/extension/5/alternative-status-menu/)

---

### Post by buzzingrobot on 2014-03-28
Odd.  It's Github page shows it updated for 3.10 and 3.12.

Have you checked in Tweak Tool to see if it is activated?

---

### Post by sdowney717 on 2014-03-28
Well I dont see it.
Here is picture
Am I missing something?

---

### Post by buzzingrobot on 2014-03-28
Beats me.  When I've used it, suspend has clearly displayed in the dropdown.  Can't recall if it was in the shutdown dialog.

You've logged in and out, or restarted Gnome Shell?

---

### Post by sdowney717 on 2014-03-28
yes, I logged out and in.

---

### Post by buzzingrobot on 2014-03-29
It is possible for one extension to conflict with another. Maybe disabling all the others?  If this one works, enable the rest one at a time to find the culprit.

Beyond that, I'm stumped, then.  Sorry.  If the extension is enabled, "Suspend" should appear in the dropdown menu as shown in the image at the extension site.

---

### Post by kurt18947 on 2014-03-30
> **sdowney717 said:**
> I just installed alternative status menu.
Still no suspend button.
[https://extensions.gnome.org/extension/5/alternative-status-menu/](https://extensions.gnome.org/extension/5/alternative-status-menu/)

Yes, it's there but doesn't seem to do anything.  Perhaps more patience is in order.  I've hear/read there's a problem with suspend in Gnome 3.10 but I've never heard what that problem is.  Using pm-utils/pm-suspend  seems to work okay though it doesn't require a password on resume.

Edit:  The alternative-status-menu extension appeared to install but is not present on the tweak tools extensions menu.  Places didn't work for some days and one day did start working properly so I guess there's hope.

---

### Post by anshul1manarmy on 2015-03-16
thanks for issue this instruction

---

### Post by cariboo on 2015-03-16
Not a Vivid thread. Closed

---

