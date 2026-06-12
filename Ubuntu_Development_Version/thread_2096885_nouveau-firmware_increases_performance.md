---
title: "nouveau-firmware increases performance?"
date: 2012-12-21
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-12-21
According to gtkperf my nVidia card  runs  the gtkperf tests 12 seconds faster with the nouveau-firmware graphics driver installed as oppossed to the nvidia-current.

See:

[http://ubuntuforums.org/showpost.php?p=12415465&postcount=41](http://ubuntuforums.org/showpost.php?p=12415465&postcount=41)

---

### Post by sgage on 2012-12-21
> **ventrical said:**
> According to gtkperf my nVidia card  runs  the gtkperf tests 12 seconds faster with the nouveau-firmware graphics driver installed as oppossed to the nvidia-current.

See:

[http://ubuntuforums.org/showpost.php?p=12415465&postcount=41](http://ubuntuforums.org/showpost.php?p=12415465&postcount=41)

Very interesting. I might just run my own test when I get a chance. My problems with nouveau aren't performance as such, though.

1) Nouveau seems to run hotter than nvidia-current on my machine.

2) I can not resume from suspend with nouveau, while nvidia-current works perfectly.

#1 has improved over the past year, but #2 is a showstopper for me, and I wish they'd fix it.

---

### Post by mc4man on 2012-12-21
> **sgage said:**
> Very interesting. I might just run my own test when I get a chance. My problems with nouveau aren't performance as such, though.

1) Nouveau seems to run hotter than nvidia-current on my machine.

It _may _run a bit hotter as nouveau doesn't support 'powermizer' so your card is always at max performance (if your card uses powermizer under nvidia drivers

---

### Post by ventrical on 2012-12-21
2 seconds to suspend, 3 seconds to unsuspend!!  Nice stuff. Only problem is the network(eth0) will not enable. Thats a showstopper.

---

### Post by sgage on 2012-12-22
I did some checking with gtkperf.

With the nouveau drivers, I averaged around 8.4 seconds. Adding in the nouveau-firmware package took about 0.3 seconds off this time.

With the nvidia-current drivers, I averaged very marginally faster, around 7.8 seconds.

Still no resume from suspend with nouveau, so back to nvidia-current.

What were your actual scores with the two drivers? Are we running different versions of gtkperf? Our numbers seem out of whack...

Oh, my card is an Nvidia GeForce 8500 GT.

---

### Post by ventrical on 2012-12-22
gtkperf = version 0.40+ds-2

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

---

### Post by ventrical on 2012-12-22
> **sgage said:**
> I did some checking with gtkperf.

With the nouveau drivers, I averaged around 8.4 seconds. Adding in the nouveau-firmware package took about 0.3 seconds off this time.

With the nvidia-current drivers, I averaged very marginally faster, around 7.8 seconds.

Still no resume from suspend with nouveau, so back to nvidia-current.

What were your actual scores with the two drivers? Are we running different versions of gtkperf? Our numbers seem out of whack...

Oh, my card is an Nvidia GeForce 8500 GT.

 I do not get network with either nouveau or current after suspend.  Examining what mac4man had contributed and if gtkperf can be considered any type of benchmarking app then mac4mans suggested method would produce faster test results.  I cannot validate the accuracy of that program (gtkperf), but , assuming it is not useless then I find the results convincing that there is an increase in Unity performance overall with the newer kernels .

However, it is one thing to notice a visual increase in speed and performance of Unity and it is another thing to authenticate those declarations. Running compares with older kernels and newer ones proves out that Unity *has* has had increase in performance according to gtkperf.

regards..

---

### Post by sgage on 2012-12-22
> **ventrical said:**
> I do not get network with either nouveau or current after suspend.  Examining what mac4man had contributed and if gtkperf can be considered any type of benchmarking app then mac4mans suggested method would produce faster test results.  I cannot validate the accuracy of that program (gtkperf), but , assuming it is not useless then I find the results convincing that there is an increase in Unity performance overall with the newer kernels .

However, it is one thing to notice a visual increase in speed and performance of Unity and it is another thing to authenticate those declarations. Running compares with older kernels and newer ones proves out that Unity *has* has had increase in performance according to gtkperf.

regards..

I'm using the same gtkperf version as you. You said that your nouveau score was 12 seconds less than your n-c score, yet both of my scores were down around 8. Were you running the 'All Tests' with a 100 test rounds?

Incidentally, I get similar results in Gnome Shell or Unity.

With nouveau, I get the symptom of no networking on resume from suspend, plus no response to the mouse clicks. The cursor moves, but nothing happens when I click.

---

### Post by ventrical on 2012-12-22
Perhaps this link  may help clarify what I was assuming.

[http://ubuntuforums.org/showpost.php?p=12379429&postcount=34](http://ubuntuforums.org/showpost.php?p=12379429&postcount=34)

Also .. allow me to clarify myself.  When I mention performance in (Unity) Ubuntu-desktop, I am referring to the 'response' times  when a Unity launcher icon is clicked or when the Dash Home>apps  icons appear on the dashboard and the opening and closing of the Unity interactive GUI all together.

Part of this process depends on the hardware-motherboard, part depends on graphical adaptor card and, of course, another fraction of this depends on the kernel version and software drivers.

  So as I am plodding along in this beta testing environ I had noticed visually that Unity response times were more 'snappy' than usual. I had simply set out to see if this may do with with the current version install of the kernel and noticed that the 3.7.rcs actually made Unity 'appear' faster. User_figaude suggested  'gtkperf'  and so I tried that across compares of older kernels and the newer RCs. In my testing on two particular machines (one with GeForce 210/218 and one Intel graphics) gtkperf had shown that there are actual faster response time with the newer kernels.

 However, when I tried  the nouveau-firware  drivers (for nvidia) it appeared yet even snappier . mac4man suggested to set Power mizer to Preferred maximum performance which resulted (according to gtkperf) that nvidia-current was even  faster than the results presented by gtkperf using the nouveau-firmware nvidia drivers.

  Adopting mac4mans test method and according to gtkperf results, nouveau-firmware does not appear to increase performance. I am not saying that this is a wrong assumption on my part because I had originally proposed this in the form of a question and until I find some other methods of testing then I would have to safely assume that the answer to my original question is no.

regards..

---

### Post by seenthelite on 2012-12-25
VGA compatible controller  GT216 [GeForce GT 230M]

Would not suspend with nouveau, so using nvidia-current.

---

### Post by ronacc on 2012-12-25
8.26 seconds here with 3.8rc1  nvidia 304.41 driver and nvidia 7600gs card .

---

### Post by seenthelite on 2012-12-25
```
GtkEntry - time:  0.02
GtkComboBox - time:  1.35
GtkComboBoxEntry - time:  0.48
GtkSpinButton - time:  0.08
GtkProgressBar - time:  0.08
GtkToggleButton - time:  0.32
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.13
GtkTextView - Add text - time:  0.66
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.69
GtkDrawingArea - Circles - time:  0.97
GtkDrawingArea - Text - time:  0.36
GtkDrawingArea - Pixbufs - time:  0.08
```
 
Total time:  5.38

---

