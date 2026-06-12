---
title: "Lubuntu Lifetime"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sudodus on 2012-04-08
What exactly does it mean, that Lubuntu does not have LTS status? What is the difference in support for the following cases?
 
 1. install from Lubuntu iso file 
 2. install from Xubuntu iso file and into that installing lubuntu-desktop
 3. install from Xubuntu iso file and into that installing LXDE
 
 In other words: is there a way to get 'near-lubuntu functionality' for five years?

---

### Post by Penguinnerd on 2012-04-08
Lubuntu 12.04 just has 18-month support, as far as I know. I was also very disappointed by this, as I had plans to switch over to it when 10.04 ends.

With method #1, you lose support in 18 months.

With methods #2 and #3, you still get security updates for the core OS and various apps,(stuff from Xubuntu) but you lose security updates and bug fixes for the LXDE components and anything Lubuntu-specific.

Also, keep in mind that Xubuntu is not supported for 5 years. I was also very disappointed by this, as it was my backup plan. Xubuntu 12.04 will only get 3 years of support, so it's a shorter LTS than Ubuntu.


The only way I can think of is this: Install a 5-year LTS variant, but remove the desktop stuff. (The easiest way would be to just install Ubuntu server) Next, manually install LXDE from source or from a package. Whenever an update for LXDE comes out, you'll have to manually upgrade it yourself.
You can get your desktop applications from the regular Ubuntu repositories, which might even be enabled by default.

This reminds me of a thread I started some time ago. Take a look here:
[http://ubuntuforums.org/showthread.php?t=1860567](http://ubuntuforums.org/showthread.php?t=1860567)

I sympathize with you about this. It really bothers me that I can't get a lightweight distro with 5 years of support, and it really irks me that Lubuntu 12.04 won't even be getting 3 years of support. 

I am considering other options, and that's all I'll say about that... Good luck.

---

### Post by kansasnoob on 2012-04-08
> **Penguinnerd said:**
> Lubuntu 12.04 just has 18-month support, as far as I know. I was also very disappointed by this, as I had plans to switch over to it when 10.04 ends.

With method #1, you lose support in 18 months.

With methods #2 and #3, you still get security updates for the core OS and various apps,(stuff from Xubuntu) but you lose security updates and bug fixes for the LXDE components and anything Lubuntu-specific.

Also, keep in mind that Xubuntu is not supported for 5 years. I was also very disappointed by this, as it was my backup plan. Xubuntu 12.04 will only get 3 years of support, so it's a shorter LTS than Ubuntu.


The only way I can think of is this: Install a 5-year LTS variant, but remove the desktop stuff. (The easiest way would be to just install Ubuntu server) Next, manually install LXDE from source or from a package. Whenever an update for LXDE comes out, you'll have to manually upgrade it yourself.
You can get your desktop applications from the regular Ubuntu repositories, which might even be enabled by default.

This reminds me of a thread I started some time ago. Take a look here:
[http://ubuntuforums.org/showthread.php?t=1860567](http://ubuntuforums.org/showthread.php?t=1860567)

I sympathize with you about this. It really bothers me that I can't get a lightweight distro with 5 years of support, and it really irks me that Lubuntu 12.04 won't even be getting 3 years of support. 

I am considering other options, and that's all I'll say about that... Good luck.

I didn't know that about Xubuntu ........... that's a bummer.

---

### Post by Dennis N on 2012-04-08
Seems to me that whichever method you use, you have support for those packages Lubuntu and Ubuntu have in common for the full LTS period. Almost all packages having security updates fall into this category. 

You are using the same repositories, and you access is not going to be cut off just because you use the LXDE desktop.

---

### Post by kansasnoob on 2012-04-08
> **Dennis N said:**
> Seems to me that whichever method you use, you have support for those packages Lubuntu and Ubuntu have in common for the full LTS period. Almost all packages having security updates fall into this category. 

You are using the same repositories, and you access is not going to be cut off just because you use the LXDE desktop.

I have long wondered about the security implications. I mean there are a number of rather "non-official" window managers and DE's in the repos that one can use to build a light-weight box.

---

### Post by kansasnoob on 2012-04-08
Possible useful info:

[http://www.canonical.com/content/ubuntu-1204-feature-extended-support-period-desktop-users](http://www.canonical.com/content/ubuntu-1204-feature-extended-support-period-desktop-users)

---

### Post by kansasnoob on 2012-04-08
I'd be eternally grateful if someone asked about the security implications of using the various window managers or DE's available in the repos during an LTS cycle here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

I'd do it but I already have too much on my plate, which means I'm doing a poor job at everything ATM - and getting grouchy :frown:

---

### Post by sudodus on 2012-04-08
Thank you Penguinnerd and kansasnoob and Dennis N,

This makes the situation easier to understand. So I think it might be good enough to 

- install xubuntu and lubuntu-desktop on top of that and continue using it until the next LTS release will be launched in the spring 2014.

And after that, if the hardware is still working,

- consider some other light-weight distro for non-pae computers.
- upgrade to the next *ubuntu LTS version for pae computers.

---

### Post by keithpeter on 2012-04-08
> **kansasnoob said:**
> I'd do it but I already have too much on my plate, which means I'm doing a poor job at everything ATM - and getting grouchy :frown:

[http://ubuntuforums.org/showthread.php?p=11827985#post11827985](http://ubuntuforums.org/showthread.php?p=11827985#post11827985)

Asked a question: you stay with the Classic!

---

### Post by kansasnoob on 2012-04-08
> **keithpeter said:**
> [http://ubuntuforums.org/showthread.php?p=11827985#post11827985](http://ubuntuforums.org/showthread.php?p=11827985#post11827985)

Asked a question: you stay with the Classic!

Thank you :D

I'll try to add a bit there later, right now I'd headed out for some fresh air and sunshine.

BTW classic w/o effects should be no problem, but I'm driving myself crazy with the whole non-pae thing, some recent ubiquity changes, and some non-puter issues.

---

### Post by sudodus on 2012-04-08
> **kansasnoob said:**
> I'd be eternally grateful if someone asked about the security implications of using the various window managers or DE's available in the repos during an LTS cycle here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

I'd do it but I already have too much on my plate, which means I'm doing a poor job at everything ATM - and getting grouchy :frown:
OK, I started that thread: [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1954702_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1954702")

I hope the *admin*s accept it, even if it is almost double posting. Otherwise please move this thread to the security discussion forum.

---

