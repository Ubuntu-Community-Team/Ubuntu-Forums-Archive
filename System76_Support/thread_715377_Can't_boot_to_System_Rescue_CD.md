---
title: "Can't boot to System Rescue CD"
date: 2008-03-04
forum: System76 Support
---

### Post by UbuAgon on 2008-03-04
I have a System76 serp3. When I try to boot to System Rescue CD x86-0.4.3 I cannot get keyboard input. The first opportunity is when it asks for the keyboard. For the default "US" it says to press Enter but does not respond. After 20 seconds it takes the default and proceeds but at the next opportunity for keyboard input it still doesn't see the keyboard. I also tried System Rescue CD version 0.2.19 which hung right after the INITRD1 line.

---

### Post by thomasaaron on 2008-03-05
I had a look at their wiki and did't see anything helpful. Why do you need the SystemRescueCD?

If you're having a problem, there may be some other way for us to handle it.

---

### Post by UbuAgon on 2008-03-09
> **thomasaaron said:**
> I had a look at their wiki and did't see anything helpful. Why do you need the SystemRescueCD?

If you're having a problem, there may be some other way for us to handle it.

I want to run Part Image.

I also had a problem installing 64 bit Ubuntu 7.10.  I got the system installed by doing the install in safe graphics mode but now the system hangs when I boot to Ubuntu 7.10-64.

---

### Post by thomasaaron on 2008-03-10
You can create an image of a partition by just going into a terminal and entering this command:

dd if=(partition location) of=(location to put image)

where "if" is something like: /dev/sda1
and where of is something like: /home/<userName>/Desktop/sda1_image

If it is a lagre partition, you might want to put it on an external hard drive so it doesn't hog up a lot of disk space.

---

