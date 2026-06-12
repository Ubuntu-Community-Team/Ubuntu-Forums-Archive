---
title: "fan stays on even when all cores are not bisy"
date: 2020-10-27
forum: System76 Support
---

### Post by Skaperen on 2020-10-27
i have two Kudo Pro laptops from 2014 with 16GB RAM.  both do this.  it is infrequent like about one every 2 to 4 months.  normally the fan comes on every now and then for a few seconds to a couple minutes then off, like something busy happened.  when Firefox hits a page with lots of busy things on it, it can suck up all 4 cores in worst case.

this problem happened again late Monday.  the fan comes on and i pay no attention to it.  a few minutes later i realize it is still on.  i check top and the total CPU over 4 cores (up to 400% possible) is about 15%.  the fan stays on for a couple more minutes and i stay shutting lots more stuff down and get the CPU, averaged over 20 seconds, down to 6%.  the fan is still on.  luckily, i'm not running anything serious (just playing some music ...killed), so i decide to reboot.  it goes down to BIOS and the fan is still on.  it comes back up and the fan is still on.

the fan is not running fast and loud.  it's just at a normal level.  and the air coming out on the left is cool.  it would be very warm if i was using lots pg CPU, like compressing 4 huge files in parallel.

i know there is some Fn key combination that will turn the fan on fast and loud.  i somehow it it by accident once.  but i don't know anything to turn it off.  so that's what i want to find out ... how to turn the fan off.  maybe that will help for the problem like i had on Monday.  does anyone know if it can do this and what to do? i am running Xubuntu 18.04.5 LTS bionic last upgraded 2020-10-26-215830 on Monday (a little more than a couple hours ago).

---

### Post by beameup on 2021-04-18
Try taking the back off and cleaning the inside of the fan. It accumulates dust on the inside. That's what stopped mine from doing that.
But I do find the fans run for nothing sometimes. As soon as I start up Handbrake to rip a video the fans kick on, but blowing cold air.
And thanks for reminding me I have a 7 year old Laptop :)

---

### Post by Skaperen on 2021-04-18
i'm looking at getting another laptop.  i want to go solid state on storage and more RAM.  and maybe even 3840x2160 4K UHD video.  i will need to find out how well X does with 4K.  if i can make it run in 2K for all userids except one i use on youtube, and a test userid, that would work out.  i hope the fan works better on a new laptop.  i haven't had this fan problem so far in 2021.  i did have the fan on for quite a while when i converted my .mp4 videos to .webm (vp9) format.  they became typically 1/7 the size \\:D/ but it took about 9 days with 3 parallel ffmpeg processes in the work pool.

---

