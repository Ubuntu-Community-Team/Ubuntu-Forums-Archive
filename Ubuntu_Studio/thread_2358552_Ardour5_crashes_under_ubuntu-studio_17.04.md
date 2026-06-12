---
title: "Ardour5 crashes under ubuntu-studio 17.04"
date: 2017-04-14
forum: Ubuntu Studio
---

### Post by gerdmitpferd on 2017-04-14
Hello

I can open ardour5 projects, which I created under ubuntu-studio 16.10, not with ardour5 under ubuntu-studio 17.04. Adour then falls off.

New projects are running.

what can I do?

> 
Cannot write socket fd = 21 err = Broken pipe
CheckRes error
Could not write notification
ClientNotify fails name = ardour notification = 10 val1 = 28 val2 = 0
Unknown error...
terminate called after throwing an instance of 'Jack::JackTemporaryException'
  what():  


---

### Post by marcellendi on 2017-04-14
I have the same problems .Just installed 17.04 and I can't open my Ardour 5.0.0 files with Ardour 5.5.0. Ardour crashes after starting jack. I can make new projects, but not with templates i made with Ubuntu Studio. 16.09/Ardour 5.0.0.

Update: I tried again Ubuntu Studio 17.04/Ardour 5.5.0 out of curiosity. Even with new projects it crashes: I add one audio track, add for example a Calf Compressor and it is already crashed.

---

### Post by magomed-kei on 2017-06-04
Its because of the package "calf-ladspa" and apparently many are facing the crashes on Zesty
Deleting the package will fix the problem...

Terminal command: sudo apt-get purge calf-ladspa

Also i advise you to delete calf plugins and ardour and install them from KXStudio's repository, they have updated packages (Ardour5.9 and Calf-plugins-git)
(instructions on their website on how to add their PPA)

- Magomed-Kei

---

