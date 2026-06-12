---
title: "Installing 10.04 LTS on fakeRAID 1"
date: 2012-10-15
forum: Server Platforms
---

### Post by dprocker on 2012-10-15
All,
 
I'm installing 10.04 LTS on an HP Proliant DL382 G2. Using HP's Smart Array Configuraton tool, I set up two HDDs to be Raid 1 and the other three to be Raid 5.
 
Using a flat panel monitor, as the server boots to the CD, it displays the POST messages and the Ubuntu splash screen with the flashing dots as if to show it's going to display the Ubuntu install screen. Then my screen goes blank (monitor light stays green as if it had a signal). I can go to other sessions to display the $ prompt, but no GUI install screen. It repeats the same display issues if I used a rack mounted KVM.
 
I did notice however, if I use the KVM tool in the iLO tool provided by HP, I can see the install screen. In addition, if I use a CRT, I have no display issues...I see everything fine.
 
I'm thinking Ubuntu video drivers don't recognize LCDs. The GUI won't display on the LCD after installing Ubunutu either. Updating security updates has no bearing on display. I still have to use the iLO tool or install xrdp.
 
I can see if they have updated drivers through updates.
 
"nomodeset" in /etc/default/grub does not work.  I tried changing the GRUB_GFXMODE=640x480 to 800x600 doesn't work either. I did a sudo update-grub after both.
 
Thoughts?
 
Thanks,
Dan

---

