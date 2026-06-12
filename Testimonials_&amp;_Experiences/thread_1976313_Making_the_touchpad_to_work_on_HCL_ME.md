---
title: "Making the touchpad to work on HCL ME"
date: 2012-05-08
forum: Testimonials &amp; Experiences
---

### Post by evnix on 2012-05-08
I couldn't get my touchpad to work from the past 2 years.
I started to dual boot ubuntu and windows since the release of ubuntu 10.04

The only thing I couldn't get to work was my touchpad.  
But I love ubuntu so much that I have been carrying an extra USB mouse(along with the laptop) in my college bag from the past 2 years.

I would patiently wait for new releases and see if the issue was fixed. ubuntu 12.04 was released and my touchpad still didn't work.

I tried every possible solution that were posted in linux support websites and forums but nothing seemed to work.

But today everything changed, I found the solution and I am literally dancing on my bed right now \\:D/

Procedure that made my touchpad work:
```

open the terminal:
gksudo gedit /etc/default/grub

and change the line from: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1 i8042.noloop=1"

save the file.

and then in the terminal:
sudo update-grub

don't forget to reboot!!

```

after searching the for the word "i8042.noloop" I found a related topic which has some more technical details.
[http://ubuntuforums.org/showpost.php?p=5290024&postcount=1](http://ubuntuforums.org/showpost.php?p=5290024&postcount=1)

My patience did payout, but there is one more issue, the touchpad has multi gesture support for operations like zoom, rotate etc. these seem to work well in windows but doesn't work in ubuntu(not a big deal though).

What I hope to see is the above issue fixed by default in the next release.

---

