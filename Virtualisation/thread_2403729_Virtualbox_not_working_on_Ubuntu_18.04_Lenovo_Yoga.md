---
title: "Virtualbox not working on Ubuntu 18.04 Lenovo Yoga 720"
date: 2018-10-15
forum: Virtualisation
---

### Post by OiPenguin on 2018-10-15
I'm trying to run Ubuntu 18.10 in virtualbox on a Lenovo yoga 720 with running Ubuntu 10.04, however I get an error saying 
"VT-x is disabled in the BIOS for all CPU modes (VERR_VMX_MSR_ALL_VMX_DISABLED)."

Some threads recommend enabling VT-x in bios, however I've not got this option. Is there another solution? 

Yours sincerely,

Lars

---

### Post by #&amp;thj^% on 2018-10-15
I'm not sure this will work on your machine but>>> in Oracle VM VirtualBox Manager:

    1.Select the Virtual device and choose Settings
    2.Navigate to System and click the Processor tab
    3.Tick the check-box, Enable PAE/NX
    4.Click OK and Restart the VB 
Also make sure that the number of CPU is set to one.

---

### Post by OiPenguin on 2018-10-15
Thanks, however I'd already tried that solution and it doesn't work.

---

### Post by SeijiSensei on 2018-10-15
I believe you can install an i386 virtual machine even without vt-x.  

Current Ubuntu releases are no longer compiled for the i386 platform.  However 16.04 LTS does have one and will be supported through 2021.

[http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-i386.iso](http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-i386.iso)

---

### Post by OiPenguin on 2018-10-15
Thanks, however the purpose of installation was to test 18.10 before upgrading because I'm a bit uncertain about upgrading and would like to test 18.10 on my hardware. Hence, installing 16.04 will not do it unless I can upgrade from 16.04 --> 18.04 --> 18.10. That'll be an extensive process though. Testing 18.10 running from an USB is of course also an option, however, Virtualbox was excellent with my former laptop for trying out new distros and I'd like to be able to continue trying out distros in Virtualbox.

---

### Post by ajgreeny on 2018-10-15
Just in case that laptop uses an AMD processor, which seems unlikely from what I know of Lenovo, you may need to enable AMD-V not VT-x in the BIOS

---

### Post by OiPenguin on 2018-10-15
Yeah, it's Intel® Core&#8482; i7-7500U CPU @ 2.70GHz × 4.

---

### Post by #&amp;thj^% on 2018-10-15
> Yeah, it's Intel® Core&#8482; i7-7500U CPU @ 2.70GHz × 4. 
Are you sure that option isn't available??
have a look: [https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series/Y50-70-How-to-enable-VT-x-technology/m-p/2091671#M124217](https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series/Y50-70-How-to-enable-VT-x-technology/m-p/2091671#M124217)

---

### Post by OiPenguin on 2018-10-15
Cheers!

It wasn't the exact recipe, but it led me to the solution. Here it is for further reference for Lenovo Yoga 720:
[https://www.dropbox.com/s/wqdvq0f5e38s47u/2018-10-15%2021.06.52.jpg?dl=0](https://www.dropbox.com/s/wqdvq0f5e38s47u/2018-10-15%2021.06.52.jpg?dl=0)

---

### Post by #&amp;thj^% on 2018-10-15
fantastic. :)

---

### Post by jellyfishing on 2019-09-15
Hey, I also have an issues with my lenovo yoga 720 not being able to run Ubuntu in Virtualbox. I tried to access the link you provided but it is no longer valid. Can you please assist me in getting this to work?

---

### Post by wildmanne39 on 2019-09-15
Hello and welcome to the forum, please start your own thread instead of posting in someone else's especially an old thread, you can post a link in your own thread to this one if you think it will help.

Old thread closed!

Thanks

---

