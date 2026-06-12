---
title: "Difference between the k/x/l/ubuntu-restricted-extras packages"
date: 2011-05-20
forum: The Cafe
---

### Post by user1397 on 2011-05-20
What is the fundamental difference between all these packages?  Is one really worse off installing the ubuntu-restricted-extras packages under kubuntu or vice-versa?  Why is this even needed, shouldn't there just be one meta-package (the ubuntu-restricted-extras and that's it)?

---

### Post by Oxwivi on 2011-05-20
Wow, I didn't even know these packages existed.

---

### Post by dniMretsaM on 2011-05-20
I'm really not sure. I might have different libraries for their respective *buntus. But personally, I don't really think it matters. If you install Ubuntu Restricted Extras on Kubuntu, it's not going to cause any problems. I just install for whatever *buntu I'm using though. That way I'm sure it's optimised for my system.

---

### Post by 3Miro on 2011-05-20
> **ubuntuman001 said:**
> What is the fundamental difference between all these packages?  Is one really worse off installing the ubuntu-restricted-extras packages under kubuntu or vice-versa?  Why is this even needed, shouldn't there just be one meta-package (the ubuntu-restricted-extras and that's it)?

Just checked Ubuntu vs Kubuntu. Ubuntu installs the "bad" and "ugly" gstreamer codecs since gstreamer is in the core of Gnome audio and video. I think Kubuntu uses xine, which comes with its own codecs and those are not part of the kubuntu-restricted extras.

There are small differences like that, I would stick to the one for the appropriate distribution.

---

### Post by jerrrys on 2011-05-20
when i installed xubuntu i installed ubuntu restricted extras, not knowing that an xubuntu package existed at the time.  seem to worked fine, but was replaced with the proper package a day later.  so i too am wondering why they both appear in synaptic.  and no, i didn't look for package differences, really not that curious

---

### Post by el_koraco on 2011-05-20
> **3Miro said:**
> Just checked Ubuntu vs Kubuntu. Ubuntu installs the "bad" and "ugly" gstreamer codecs since gstreamer is in the core of Gnome audio and video. I think Kubuntu uses xine, which comes with its own codecs and those are not part of the kubuntu-restricted extras.



it was so in the past, now it's moved to gstreamer as a plugin.

---

### Post by 3Miro on 2011-05-20
> **el_koraco said:**
> it was so in the past, now it's moved to gstreamer as a plugin.

I looked at the packages for 10.10 and Kubuntu-restricted-extra did not include the gstreamer codecs.

Is the new Kubuntu 11.04 using Phonon-gstreamer? That would be good news actually, as previous versions had some sound incompatibilities with the many Ubuntu oriented programs in the repos.

---

### Post by el_koraco on 2011-05-20
Yes, it's using gstreamer as a Phonon backend, with benefits to the experience, but the implementation of pulseaudio is still kinda sucky at times (not Kubuntu's fault, of course).

---

### Post by SeijiSensei on 2011-05-20
The kubuntu package has some other items that are designed for specific KDE applications like K3b.

---

### Post by Gremlinzzz on 2011-05-20
ubuntu-restricted-extras comes with that icetea java which i have to remove and install sun-java6-jre sun-java6-plugin
xubuntu-restricted-extras doesn't come with icetea java.other than that never looked for differences.

---

