---
title: "USB Flash drives brought by others"
date: 2010-09-13
forum: Security
---

### Post by JuliaHenson on 2010-09-13
Dear Sirs,
I have read several posts and articles regarding Ubuntu security, none of which are simple enough for me to understand, nor do I see anything relating to my question.
Background:
I help English students and teachers with their pronunciation.  Students sometimes bring a USB flash drive and I load all my English files and urls into it, so they have lots of information to help themselves.

The last time I did this, I was using Windows (now I use only Ubuntu), and the student, unknowingly, had a worm and a Trojan on her Flash drive. 

My question is,

How safe am I from a USB flash drive that contains  viruses, worm, trojan, or?

 A student is going to bring a USB flash drive for this very purpose, this Saturday.  What should I do?

Thank you,

---

### Post by krimzonstarr on 2010-09-13
Since they would presumably be Windows virus, spyware, worms, etc on the flash drives, they would not be able to have any effect on your non-Windows system.

If you are truely concerned, there are anti-virus solutions available in the repositories, such as ClamAV, that can scan the flash drives. Word of warning though, these utilities don't usually "clean" the files so much as quarantine or delete them to remove the risk.

There are many good guides written up by people much better than I. Check the stickys under the "Security" headings. [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

Long story, short: You are at Zero risk.

---

### Post by BkkBonanza on 2010-09-13
I'd agree with above. But also add, if you do use ClamAV then be prepared for lots of false positives. It tends to flag all sorts of stuff and alarm you when either they aren't threats, or at least not to you.

Viruses and Trojans that run upon insertion of disks/usb are making use of the autorun functionality of Windows. On Linux they won't even get run upon insertion and if they were run manually they wouldn't do more then throw up an error since they aren't Linux executables.

---

### Post by JuliaHenson on 2010-09-15
Thank you both for your information.  Both of you have made me feel much more comfortable about this situation.

I have, however, printed the suggested "Ubuntu Security" sticky by Bodhi.zazen and have marked it for questions to my technician.

I think these replies have provided adequate information and/or links to provide me with whatever security considerations I have.

Thank you,
Julia

---

### Post by mr-woof on 2010-09-15
Personally, I'd probably give them a scan anyway. At least that way, if it was infected with something, you could clean it. 

I work with Windows and I Can't help doing it, old habits etc :)

---

