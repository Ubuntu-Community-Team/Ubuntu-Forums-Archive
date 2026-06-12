---
title: "kernel panic when trying to install in vm"
date: 2016-03-06
forum: Virtualisation
---

### Post by timi3 on 2016-03-06
Hi all,
i've been having issues installing ubuntu on my Hp G7 N54L Microserver  in a VM.
i am using it to learn how to build android and also run it as a nas and learn other types of things.
the specification is as follows, AMD Turion II Neo N54L / 2.2 GHz ( Dual-Core ), 16gb ecc crucial ram, 1x 3tb wd red, 1x2tb wd black, 1x500gb wd(old sata drive with data), 1x 320gb samsung drive, 1x 320 2.5" thoshiba and finally 1x 250gb seagate.
i have also installed a amd 7700hd gpu as the server was orignally purchased to be used as a media centre.

i installed server 2012 r2 orignally as host and used  hyper v to try install ubuntu. i couldn't get it to work as i would get a kernel panic. i also had issues with the vm i used for my nas to work. i then optained a liscence from a friend who works in IT gor VM workstation 2012. i installed that and therefore had to remove hyper v. the NAS VM worked flawlessly and a few other machines worked too, such as windows xp, 7 and 8.1

having decided that the issue was the OS, i reverted to set the unit back up to windows 10.
i have a laptop with much higher specifications than the server and ubuntu in workstation 12 ran flawsly; only issue was that it has a 250gb ssd and therefore i am limited in what i can do on it as data is filled very quickly.

i have now installed workstation 12 on the server and am trying to get ubuntu running. i keep getting the same error as i did in server 2012r2 VMs.
i get a kernel panic and never get to install it (however works fine on the laptop with the same software/i understand, different hardware)

i want to know what this error means and how i can proceed to install.
i am sure that this machine is capable of running ubuntu in vm. any help will be appreciated.

thanks
[ATTACH=CONFIG]267671[/ATTACH]

---

### Post by MAFoElffen on 2016-03-06
Do you have AMD-V enabled in the BIOS?

Is the ISO that you are trying to install 64bit OS?

---

### Post by timi3 on 2016-03-06
Hi and thanks for your quick reply.
by default it is enabled in my bios. it is known as Secure Virtual Machine (SVM) in the bios which has been re branded as amd-v now

i have downloaded the 15.10 ISO. i am using the iso image to install from. it boots to the keyboard logo at the bottom and then kernel panics with that screen before i can do anything.

Kind Regards

---

### Post by timi3 on 2016-03-08
so i managed to sort it out and provide feedback if anyone with the same machine as similar issues.
as a hunch, i thought it might be the bios update. to test it out, i flashed another bios. this bios seems slightly unstable with usb devices. sometimes it gets randomly disconnected and reconnects. i'll look into it and this isn't the place for that discussion either. however, it fixed the issue i faced with the ubuntu in VMs.
i redownloaded the iso image too but they both have the same md5. i then went though a typical install and it detected ubuntu 15.10 and did the rest manually.

things that bug me about doing it like this, i dont get to choose my custom installation,i.e. how much swap, location, time zone, keyboard mapping.  end result, the thing works so i'm happy

---

### Post by MAFoElffen on 2016-03-08
Good to hear that a BIOS Update fixed your problem. If this is now solved, please resvisti this thread > Use the "thread tools" link to the upper right of the first post > Use "Mark thread as solved" so that others with similar problems can find answers to theres.

---

