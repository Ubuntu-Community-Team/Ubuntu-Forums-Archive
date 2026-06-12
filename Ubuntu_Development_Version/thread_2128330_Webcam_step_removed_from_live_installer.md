---
title: "Webcam step removed from live installer"
date: 2013-03-22
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-03-22
I thought at first that this may have been a bug, but it's intentional:

> ubiquity (2.13.17) raring; urgency=low

  [B]* Remove webcam step (LP: #1118589):
    - User testing showed people are not expecting to be photographed and
      raise privacy concerns as to where the picture will be uploaded to.
    - Provides limited benefit, as avatar only ever shown on multi-login
      systems in the switch user indicator / pkexec.
    - Crashes the installer or doesn't work with certain webcams.
    - Miss detects camera presence, when it's just a sensor.
    - The recommendation is to move webcam test to checkbox / hw testing,
      as video conferencing is very popular these days and should work
      reliably out of the box.
    - LP: #924419 , LP: #981644 , LP: #987392, LP: #1152254, LP: #843354,
      LP: #1008204, LP: #1021449, LP: #1082458, LP: #1103780, LP: #1142751[/B]
  * Do not count optional pages, when updating the progress dots. This
    fixes "Porgress dots, well don't progress after partman step"
    LP: #1152746
  * Do not mark explanatory text on "Installation Type" screen
    insensitive, as otherwise it's ineligible (LP: #1074386)

 -- Dmitrijs Ledkovs <dmitrij.ledkov@ubuntu.com>  Tue, 19 Mar 2013 15:17:51 +0000

---

### Post by pqwoerituytrueiwoq on 2013-03-22
do we sill get to pick a user icon?

---

### Post by cariboo on 2013-03-22
I don't know about that, I did an Ubuntu Gnome install last night, and the picture was pretty scary looking, it may make someone think twice about stealing the system. :-D

---

### Post by kansasnoob on 2013-03-22
> **pqwoerituytrueiwoq said:**
> do we sill get to pick a user icon?

I don't know :redface:

I was just testing some images using 'testdrive' and i noticed the change in behavior.

---

### Post by kansasnoob on 2013-03-22
> **cariboo907 said:**
> I don't know about that, I did an Ubuntu Gnome install last night, and the picture was pretty scary looking, it may make someone think twice about stealing the system. :-D

Too, too funny :lolflag:

---

