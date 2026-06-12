---
title: "Bye bye"
date: 2010-05-11
forum: Testimonials &amp; Experiences
---

### Post by leodp on 2010-05-11
I upgraded to 10.4 from Karmik Koala, I am having infinite issues, even after trying a fresh install. There seem to be a lot of people with similar problems, maybe not all of them with the whole bunch I have. I could solve some (mouse, keyboard freezing), 'till I could not boot up and I was prompted with a grub command line which was untreatable even after setting devices, kernel, directories as it should have been.
The list:

- Upgrade did not complete by itself: after installing new packages the process froze, keyboard and mouse were unresponsive.
Reboot, sudo apt-get autoremove, some reconfiguration. Then I got some more problem, that took me to a fresh install. Some more problems.

- Keyboard and mouse and touchpad freeze: as soon as I try to move the mouse the cursor changes from "vertical line" to "arrow", then all I can do is push the power button.
One in ten times I reboot they magically work.
Running the live CD somehow mouse and keyboard work and I can edit files in the installation.

- eth0 does not work. I get the correct IP address, but somehow I'm in ipv6 mode. Tried avouiding that by playing with the Networkmanager. No way. If I have a nice GUI that does the job should I go CLI? eth0 has always worked ever since I have this PC (4.5 years).

- Where is grub menu.lst? I am not able to go into recovery mode or low graphical mode (which after the upgrade/before the fresh install was accessible and helped in reviving the keyboard and touchpad, but not the mouse). I cannot stop grub at boot and enter parameters.

- Sound seems to be broken, I cannot check now that the keyb/mouse are frozen. After upgrade/before the fresh install sound was almost ok, there were a lot of "clicks" and noises in flash websites and also by playing videos with mplayer (never had that problem before).

I am using ubuntu since Dapper Drake. Have tried fresh installs or upgrades since then.
Every time I wanted to avoid problems I have burnt a live CD, checked that it was working and gone forward. 
Why am I supposed to do that? Why is the outcome of an upgrade so unreliable? 
Now I even have problems (keyboard, mouse, sound) that were not present in the live CD.

I'm using the computer at home mainly for for email, film, music, photos. Nothing that unusual.  
It's a not anymore so strange laptop (17", ECS G900) with an old ATI card (9700 M10), standard integrated audio card SIS7012 AC'97, Pentium IV, Ralink R2500 Wlan, and Gigabit-LAN 10/100/1000Mbps (DSL capable) Marvell 8001.

What should I do to have a running system? Avoid upgrades?
Maybe I'll try some other distro for a while.
I have gone through Mandrake/Mandriva, Gentoo and I have come to Ubuntu for the ease of use.
If I do not get that from Ubuntu why should I keep it.
MAybe I'll come back. There is not a perfect solution in the real world.
Thanks anyhow for all the help I got in the forums and to Ubuntu for the fun of the last few years.

Ciao,
Leodo

---

### Post by mörgæs on 2010-05-11
If 9.10 works then just stay with it. It is half a year old and finally getting stable. 

It is supported a year from now.

---

### Post by poo_22 on 2010-05-11
wow op, you had it rough! i had numerous issues too but not such major ones (your eth0 didnt work that crazy!)
my sound was broken,
grub 2 pissed me off, didnt' let me boot windows 7,
video drivers completely failed - i had no opengl of any kind which i use quite a bit...
anyway all these things led me to switch to gentoo, and like op its because ubuntu no longer was simple to use. after spending some time installing gentoo (since its done by hand) i came out knowing a lot more about linux, and on top of that felt i knwo my system so much more in depth that i was was able to fix all issues and now have a very pretty kde based system.

tl;dr; - ubuntu is not in a working state atm, and calling 10.04 a major release is wrong its still beta quality. its been hyped up, people update, and it doesn't work. bad.

ttl; ddr: fix 10.04.

---

### Post by luvr on 2010-05-11
> **leodp said:**
> Maybe I'll try some other distro for a while.

I'm thinking about this option, too.

Not that I'm running into any major showstopping bugs so far, but I'm somewhat disappointed about the power management issues in Lucid (see [Bug #563862 in gnome-power-manager (Ubuntu): "When logging on power manager fails"]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862")).

An earlier release, 8.10, had similar issues on my laptop, but I consider *"intermediate"* releases sufficiently experimental that I can live with the occasional (albeit pretty annoying) glitch. The later releases, 9.04 and 9.10, no longer had the problem, so I certainly didn't expect it to return in a **Long-Term Support** release, like Lucid&#8212;which, in my (probably naive) opinion *should* primarily be stable (or, at least *"as stable as possible"*). I'm very sorry, but I expect **Long-Term Support** releases to be a *little* higher quality&#8212;mess with the *"intermediate"* releases as you will, but do pay far more attention to **Quality Assurance** when it comes to **Long-Term Support** releases.

This reminds me of the *previous* Long-Term Support release, 8.04, which initially worked fine, but then, after some update, no longer automounted USB disks (you needed to manually run some command to force it to rescan the USB bus). This problem never got solved, to the best of my knowledge; the only work-around that I know of, was to dump 8.04 altogether.

Anyway, I will be keeping an eye on the power management bug report for now, but I'm not particularly hopeful. In the meantime, I've installed a few different Linux distributions on my laptop, and I'll see if I can find any that I like.

---

### Post by Melindrea on 2010-05-11
> **poo_22 said:**
> my sound was broken,
This shows how much people's experiences can differ depending on their systems. When I first installed Ubuntu (08.04), my soundcard broke. With this installation, it works perfectly.

---

### Post by ukripper on 2010-05-11
Thanks for sharing with us.

---

### Post by Jazzy_Jeff on 2010-05-11
I am sorry to hear about all your issues. I guess I am one of the lucky ones where everything just works and no bugs that I have found so far.

Good luck to you and I hope you find a distro that you like. I have used arch linux in the past and really liked it. It takes some learning though.

---

### Post by Ms_Angel_D on 2010-05-11
leodp, thank you for sharing your experience, if you need support please utilize the support area's of the forum.

Angel

---

