---
title: "ACC format in audacity"
date: 2008-11-07
forum: Ubuntu Studio
---

### Post by wildman4god on 2008-11-07
I am using audacity to edit sound files for my church, but I want to export as ACC (itunes format) but when I do this it says It needs ffmpeg to do this so I installed ffmpeg from synaptic but audacity can't find it. when I click find library in preferences it keeps trying to find a windows library, why would a linux program do this and how can I get ffmpeg to work in it. Please help and thanks in advanced.

---

### Post by wildman4god on 2008-11-07
Anybody????
:confused:

---

### Post by Stochastic on 2008-11-07
I thankfully have never had to use an ACC file in my life (or an AAC file for that matter), but the fact that it directs you to a windows library should be filed as a bug on launchpad.net

If it is looking for ffmpeg, there are quite a few ffmpeg libraries in the repositories, though wikipedia has this to say about AAC files > a patent license is required for all manufacturers or developers of AAC codecs [9]. It is for this reason FOSS implementations such as FAAC and FAAD are distributed in source form only, in order to avoid patent infringement.  so you may find the ffmpeg in the repos lacking in AAC support.

---

### Post by wildman4god on 2008-11-08
thanks for the info, another question, I have sound converter and it has an option to convert into acc but it gives me no bitrate or any options is this normal? also is there a universal media converter, i came across one for windows once and it could convert anything from pictures, to audio and video to any other formate, it there something like this for linux?

---

