---
title: "Contribute by using Ubuntu +1"
date: 2013-06-20
forum: Ubuntu Development Version
---

### Post by noersetiawan on 2013-06-20
Can I contribute to Ubuntu developing process just by using Ubuntu +1 version as daily basis?

---

### Post by VMC on 2013-06-20
You can help by reporting any bugs, errors that happen during the testing process. Read some of the links inside this [sticky link]("http://ubuntuforums.org/showthread.php?t=2140142") .

---

### Post by noersetiawan on 2013-06-20
Is there a way to report any bug automatically?

---

### Post by dino99 on 2013-06-20
> **noersetiawan said:**
> Is there a way to report any bug automatically?

into a terminal, run:  ubuntu-bug packagename2bereported

---

### Post by noersetiawan on 2013-06-20
Um what I mean is can I just use my computer as usual to browse the internet and typing, but whenever a bug show up, it reported automatically without I have to do anything.

---

### Post by dino99 on 2013-06-20
> **noersetiawan said:**
> Um what I mean is can I just use my computer as usual to browse the internet and typing, but whenever a bug show up, it reported automatically without I have to do anything.

hm, you seems not yet understand the very basic things about an OS. As that subforum (U+1) is about the bleeding hedge stuff, you'd better to post into the noob subforum (aka beginners subforum)

---

### Post by mc4man on 2013-06-20
> **noersetiawan said:**
> Um what I mean is can I just use my computer as usual to browse the internet and typing, but whenever a bug show up, it reported automatically without I have to do anything.

If the bug causes a crash it will pretty much do it itself, you just need to click on a popup's button or 2, then you're done. Any non crash bug you'd need to actually report as previously mentioned.

I gather If you make use of the Home scope with online access enabled (by default it is),  you'll help 'smart scopes' in some small fashion

---

### Post by wojox on 2013-06-20
> **noersetiawan said:**
> Um what I mean is can I just use my computer as usual to browse the internet and typing, but whenever a bug show up, it reported automatically without I have to do anything.

Sort of, see the [Apport]("https://wiki.ubuntu.com/Apport") app.

---

### Post by grahammechanical on 2013-06-20
What you are looking for would be called snooping by many people. Ubuntu does not report to the developers without our permission. 

When we use the development version a utility called Apport (Ubuntu-bug) is activated by default. It detects system crashes and notifies us of the crash and we are given the option to report the crash. We can choose not to report the crash. If we want to report the crash we will be taken to the Launchpad bug reporting page. We need to have set up a Launchpad account to go further. Apport will collect data from our OS that is useful in understanding why the crash happened. If there is the possibility of that data containing personal information, then we will be asked to confirm the attachment of those files to the bug report.

Sometimes Apport will tell us that there is no need to report the crash because the developers are already aware of this bug. And the process will go no further. A lot of the difficulty in reporting bugs has been removed by the use of Apport but it is still not as 'behind the scenes' as you wish.

I do not think that Ubuntu uses would want the OS to be reporting back to the developers without the agreement of the user. If that sort of activity took place inside the OS, then any kind of information could be collected without our knowledge. And I do not think that many of us would like that.

Regards.

---

### Post by noersetiawan on 2013-06-20
Wow thanks I understand it by now.

---

