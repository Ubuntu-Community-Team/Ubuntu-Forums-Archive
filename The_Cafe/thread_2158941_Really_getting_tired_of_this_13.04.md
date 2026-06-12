---
title: "Really getting tired of this 13.04"
date: 2013-07-01
forum: The Cafe
---

### Post by Ridgerunrbunny on 2013-07-01
Consistantly when I boot I get a garbled page. All maroon with little dashes, squares and what not's all over the screen. This is happening every time I turn on the computer. It takes at least 3 tries before Ubuntu OS , os's corrrectly. I am about ready to look for a more stable OS. 

I really enjoy Ubuntu when it works right, but it does not seem to work right for long. Ever! Going all the way back to 8. If it goes out of date it does not work properly forcing a person to upgrade.   Any alternatives here?

BunnyConsistantly when I boot I get a garbled page. All maroon with little dashes, squares and whatnots all over the screen. This is happening every time I turn on the computer. It takes at least 3 tries before Ubuntu OS , os's corrrectly. 
I am about ready to look for a more stable OS. I really enjoy Ubuntu when it works right, but it does not seem to work right for long. Ever! Going all the way back to 8. If it goes out of date it does not work properly forcing a person to upgrade.

---

### Post by dargaud on 2013-07-01
I had problems like that a long time ago with graphic modes not set properly in grub. But it's weird that it not the same every time. Have you played with options such as 'nomodeset' in grub ? Or GRUB_GFXMODE ? Or "sudo hwinfo --framebuffer" to get the vga codes of your video card to pass to the kernel as vga=xxx in GRUB_CMDLINE_LINUX ?

---

### Post by Ridgerunrbunny on 2013-07-01
sudo command didn't work. I don't fool with grub.

---

### Post by Frogs Hair on 2013-07-01
The program hwinfo is not installed by default on my 13.04 installation, so the command returns not found .

---

### Post by dannyboy79 on 2013-07-01
> **Ridgerunrbunny said:**
> Consistantly when I boot I get a garbled page. All maroon with little dashes, squares and what not's all over the screen. This is happening every time I turn on the computer. It takes at least 3 tries before Ubuntu OS , os's corrrectly. I am about ready to look for a more stable OS. 

I really enjoy Ubuntu when it works right, but it does not seem to work right for long. Ever! Going all the way back to 8. If it goes out of date it does not work properly forcing a person to upgrade.   Any alternatives here?

BunnyConsistantly when I boot I get a garbled page. All maroon with little dashes, squares and whatnots all over the screen. This is happening every time I turn on the computer. It takes at least 3 tries before Ubuntu OS , os's corrrectly. 
I am about ready to look for a more stable OS. I really enjoy Ubuntu when it works right, but it does not seem to work right for long. Ever! Going all the way back to 8. If it goes out of date it does not work properly forcing a person to upgrade.stick with 12.04 then, it's the latest LTS.

---

### Post by Ridgerunrbunny on 2013-07-02
So, , does that mean I must Re-install 12.04? That would be another pain.

---

### Post by MikeCyber on 2013-07-02
13.04 installed fine yesterday on my new pc. Only needed grub repair for my uefi board. Probably you need to install the proprietary nvidia or amd drivers? Anyway update it before anything else.

---

### Post by kurt18947 on 2013-07-02
Non-LTS versions seem to be effectively beta releases.  I suspect non-LTS releases are used to prove or debug technologies for the next LTS.  If 12.04 is stable for you, that's likely the best choice.  Ubuntu is doing 'point releases' i.e. 12.04.1, 12.04.2 etc.  You can also do ppa s to keep up-to-date on apps.  For example, I enabled LibreOffice's ppa so I always have the latest stable LO release.

---

### Post by buzzingrobot on 2013-07-02
Hold "Shift" down during the boot.  When the Grub menu appears, add "nomodeset" to the end of the line that loads the kernel. Hit F10 to boot with that parameter in effect. (It's temporary. No permanent change is made to Grub's config.) If the screen distortions are not present (even if the resolution is different) use "Software Sources" (in the Ubuntu Software Center menu) to add an appropriate proprietary video driver. Then, reboot. 

I can't guarantee this will work since we don't know what's really going on with your system or its video card. But, I use an Nvidia card that often either boots to a black screen or to various display anomalies (it's not an Ubuntu-specific issue) until I install a proprietary driver.  It's now the first thing I do after running the initial updates after an installation.

---

### Post by jwaclawsky on 2013-07-02
I have the same problem on my Dell Studio XPS 7100 AMD Phenom(tm) II X4 945 Processor × 4 with Gallium 0.4 on AMD JUNIPER with Ubuntu 32 bit 13.04 (that is what is says in "details"). Everything was fine before on vesrions from 11.xx to 12.xx. Sometimes it boots up correctly but most times I have to restart, occasionally 3 or 4 times before it comes up correctly. I often get the torn screen with all the "little dashes, squares and what not's all over the screen" but that eventually goes away. But the "final" symptom (in my case) remains which is that I have the sound settings greyed out and then I have no sound. Something is happening, IMHO, with the timing on boot up and I suspect drivers are getting loaded out of order or something to that effect. I haven't spent much time looking for the cause because if I just reboot it will eventually "go away" unually first or second restart. I am hoping an update will eventually fix this. So I am being lazy using restart because it is less painful than trying to find out what is going wrong. My 2 cents. I am thinking of backing off to 12.10 if it becomes too annoying.

One last point, I am very happy with Ubuntu but I just don't understand after "years" of happy usage I should suddenly have a problem on a machine. Expectations should always be a "better" system with a new release. Going backwards due to some kind of regression does not help Ubuntu's image. Again my 2 cents...

---

### Post by jwaclawsky on 2013-07-02
... see previous comment...    BTW, how do you delete a post once you have done it ...e.g. redundant etc

---

### Post by Ridgerunrbunny on 2013-07-02
I was so discusted I installed Fuduntu. Now I lost my triple boot.

---

### Post by Bucky Ball on 2013-07-02
*Thread moved to **The Cafe**.*

Not a support request. If you want help fixing an issue, please post a thread with a descriptive title and as much relevant info as you can in the relevant forum. Thanks.

---

### Post by Bucky Ball on 2013-07-02
***Thread closed.***

On second thoughts, this thread started as a Ubuntu whinge, has achieved nothing and is going nowhere but off topic. Again, if you have a support request, post in the appropriate section. For Fuduntu that would be in their forums or in ***Other OS*** here. Thanks.

---

