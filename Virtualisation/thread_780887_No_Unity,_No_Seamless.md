---
title: "No Unity, No Seamless"
date: 2008-05-03
forum: Virtualisation
---

### Post by Lukios on 2008-05-03
Ok heres my problem,

ive tried running xp (both tinyxp and xp pro) on both vmware workstation beta and virtualbox. both work great except i cant get the "unity" or "seamless" features to work in either one. in virtualbox im unable to install "guess additions" no matter how long i wait it never prompts me to install anything.
and when i try to select seamless mode from the drop down menu its always greyed out. in vmware, i managed to install "vmware tools" once, but i was never able to upgrade it, it was always out of date, and of course, i could not enable unity. i have googled this for a few days and have found nothing that has helped me. lots of tutorials, most are easy, one in particular was pretty complex (for me at least, im a newb [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)). the only thing i can think of is that maybe theres something wrong with my video driver. ive tried to install drivers with envy but it didnt help. so here is my set up.

Host: ubuntu 7.10
Guest: xp pro and tinyxp

Computer: Compaq Pesario sr217onx
Graphics Card: ATI Radeon Xpress 1100 (x1100)

just to note, the only way i can NOW (now because i was able to do this a couple of weeks ago with the restricted driver manager) use compiz is by installing drivers with envy.

is there any known problem with this graphics card that would stop me from using these features? anways, im at a loss, if you guys have any suggestions or links or anything at all that would help me out, i would greatly appreciate it. 

thanks

---

### Post by Oldsoldier2003 on 2008-05-04
the guest additions in virtualbox have to be installed from the guest os. mount the iso then open your xp VM. Then from withinn the xp VM install the guest additions just like you would any program in windows.

---

