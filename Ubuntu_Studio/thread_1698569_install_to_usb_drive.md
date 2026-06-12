---
title: "install to usb drive"
date: 2011-03-02
forum: Ubuntu Studio
---

### Post by leg on 2011-03-02
Can I do this? I have downloaded the alternate install dvd and used netbootin to put that on usb stick but, as you probably would expect, I can only install from it. For some reason I thought there was a livecd version of studio. Is there a way I can get a live version of this onto a usb stick so that we can use it to teach a sound module with?

---

### Post by leg on 2011-03-02
Well so far I am booting the ubuntu liveCD from a usb stick as described on the pendrive linux site. I am currently thinking that I could upgrade this to include ubuntu studio and run that. Any ideas on how that might work I intend to give it a go when I get home.

---

### Post by Pablo_F on 2011-03-02
That is fine. 

When installing jackd package (included in ubustudio-audio metapackage) answer YES, you want rtprio and memlock privileges, and then do in the terminal:

sudo adduser your_user_name audio

You can make more improvements, but this is good enough for starters. Enjoy with the programs, you will have time to tweak things later, in case you need to.

Cheers, Pablo

---

### Post by leg on 2011-03-03
Yes I have the livecd working ok and I should have stopped at that. I ruined my boot process when I got home by trying to install it from the usb stick to another one. I think I have overriden my grub install as I can now only boot my laptop if the second stick is in a usb port. How can I put this back to this way it was.

If I do not have the usb stick in a port now I get a console with the message

```
Grub error>
```

---

### Post by leg on 2011-03-03
Fixed the laptop by following [this thread item 13]("http://ubuntuforums.org/showthread.php?t=1195275") so thanks to drs305. Back to trying to customise my usb stick.

---

### Post by leg on 2011-03-04
Ok so I will document what I want to do and see if any one has any info that may help me. 

1: Use a livecd version of linux and run it from a usb stick - Done using ubuntu live cd works great (on it now in fact)

2: Customise the live USB so that it is upgraded to include the Ubuntu-studio packages (because it is a project to assist the teaching of a sound module - Sound for Games)

3: Attempt to get it to recognise networked components on our network such as NAS (Windows share - My Documents), email etc (typical corporate environment). A lot is fine as web apps have been employed eg e-registers.

Item number two is ok but I would like to include in the customisation removing the initial boot menu and the install icon and also make sure that it the user is logged on automatically and is not the user that can access root.

Item three is where I am the most stumped at the moment as parts of the system are network aware but others aren't. I can (and in fact am) use Firefox and just need to set the network settings to auto detect proxy. Synaptic will not connect to servers and I can't seem to make that part work. It seems that the networks dhcp has worked as I have ip address and route info seems ok. What port does synaptic use and could blocking of that be the problem?

Any help greatly appreciated.

---

### Post by leg on 2011-03-07
So far I have managed to install the ubuntu-studio audio packages, which is all we need, and I have removed ubiquity so that the system just loads and automatically logs on the live session user. I completed this on my laptop over the weekend and it all worked fine and now I have brought the stick to work and there is no sound output. I have added the user to the audio group and I was wondering if this will be a driver issue.

---

### Post by leg on 2011-03-07
The sound is now working and it seemed to be the output set to headphones to be the problem. Also have to start jack control twice to get it working but it is now working.

---

