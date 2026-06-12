---
title: "PAE on CPU required for Xubuntu 12.04?"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by al.adab on 2012-03-19
hello,

I need to re-install my Xubuntu and thought I'd give 12.04 a try. Can't install it, apparently: right at the beginning of the installation process - ie, very shortly after re-booting the machine on a memory stick - a message appear saying more or less that

(can't remember the exact words) cannot boot: "pae" is required on my cpu to boot and install 12.04. Apparently I have no "pae" - I'm on a IBM Thinkpad T42. 

Does this mean I won't be able to use Xubuntu 12.04 + future versions? That's not a big issue, I can probably go on forever on the 11.10 version, just wondering what's going on...

thanks.

---

### Post by uRock on 2012-03-19
12.04 is still in testing. Moved to *Ubuntu+1(Precise Pangolin)*.

---

### Post by kansasnoob on 2012-03-19
Calm down, be patient, and start by reading this:

[http://ubuntuforums.org/showpost.php?p=11772755&postcount=1](http://ubuntuforums.org/showpost.php?p=11772755&postcount=1)

So what was going on? Look here:

[http://ubuntuforums.org/showpost.php?p=11661116&postcount=1](http://ubuntuforums.org/showpost.php?p=11661116&postcount=1)

And this bug report has some useful info:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

The bottom line is that things are still shaping up. We now know that Xubuntu will be sticking with the non-pae kernel, just be patient while they get the iso rebuilt.

I suspect that Lubuntu will follow suit but we'll just have to be patient and see.

---

### Post by grahammechanical on 2012-03-19
@kansasnoob

Isn't this where you say: "I told you so?" :p

---

### Post by kansasnoob on 2012-03-19
> **grahammechanical said:**
> @kansasnoob

Isn't this where you say: "I told you so?" :p

Not at all. I just hope that my comments paid off :)

One time I know they did here was notifying the Lubuntu devs that Xubuntu pulled it off so Lubuntu will also be non-pae by default.

I don't like playing the "I told you so" game. I'm more likely to look at battles I've fought in the past and trying to figure out the best way to win the next battle.

If I helped influence this decision I think that's great. It's a good decision IMHO.

---

