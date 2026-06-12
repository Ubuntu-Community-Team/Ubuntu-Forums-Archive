---
title: "Finally! But only after a short scare!"
date: 2010-12-22
forum: Testimonials &amp; Experiences
---

### Post by photodan on 2010-12-22
I came over from Windows XP a couple years ago, merely because I was annoyed, forst because I was tired of an OS that limited me and, second, with having to buy three (!) copies for three computers in my home. I vowed I'd never give them another dollar - NOT EVER! 

I first tried PCLinuxOS with KDE and liked it, althought I felt it could do more and I never could get accustomed to the interface. I moved to Ubuntu 9.04 and loved it and the Gnome desktop. Then, when I updated to the next iteration I began having problems with getting connected to my mail server. It would take oiver 15 seconds to connect before sending or receiving and that time grew to be intolerable. I was irked every time I opened Thunderbird and so, finally, I began sampling distros, none of which pleased me like Ubuntu.

Last week I tried PCLinuxOS's latest Gnome version and like it a lot - that is - until I tried to connect to my two printers, both connected to my wife's XP box. After four hours of irritation I decided to come back to Maverick. After wrestling with the decision for several hours, having heard several stories about problems with software and hardware, I decided to try the 64 bit version and, Man, I'm glad I did. Wow! Everything works smoothly and fast and Thunderbird is now instantaneous. 

I had reinstalled everything, including Virtualbox, and was sailing along until, at a friends request, I went to You-tube to watch a jazz band I like. Dang! The message that I had to install Adobe Flash (I'd heard stories about this plugin, none good) and I hated the idea. Nonetheless, I opened the Software Center and found that I had to get it from Adobe. After going there and finding that there was (is?) a problem with their 64 bit version I thought, "Oh Boy! Here we go! Nothing but hassles!"  [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

Then I stumbled on a thread that talked about Flash-Aid, an extension that inspects you browser, tells you which Flash plugins you need (and don't need) and installs them for you! I was a bit nervous but I installed Flash-Aid and ran it. It handled everything for me and, when I went back to You-tube, I could listen to, and watch, the old Artie Shaw Band without problems.

Now! The point of all that was that the only problem I encountered with 64 bit Maverick was solved. I'm sitting here typing and marvelling at this operating system. I also have two larger memory chips on the way since this 64 bit system will "see" them.

The bottom line: I think I've found the perfect operating system in Maverick Meerkat and can say with some authority I'll never buy anything from Microsoft again. Never!  :D:D

---

### Post by 1roxtar on 2010-12-22
I have 64 bit Maverick running flawlessly on my Alienware Area 51 desktop.  Like you, I have more RAM sticks on the way.

:guitar:

---

### Post by johntaylor1887 on 2010-12-22
Good to hear. If you want *all* the codecs, open a terminal and copy and paste:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Then:
```
sudo apt-get install non-free-codecs libdvdcss2
```
Enjoy!

And before anyone says: "all you need is ubuntu-restricted-extras", *non-free-codecs* includes ubuntu-restricted-extras, and even more. ;)

---

