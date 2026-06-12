---
title: "testing wayland in 18.04"
date: 2017-10-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-24
Hi Team,

 I ask those who are members of U+1 team and all others who volunteer here with your precious time to find the extra time to focus on the new gnome3 default. I am advised that the 17.10 cycle was a testing ground to "gauge the quality with lots of users" and that "the jury is still out" on whether wayland will be default. This is why we have to continue testing it through this cycle. We will probably not see much  happening for a few weeks but stay tuned ! :)

Regards..

---

### Post by rrnbtter on 2017-10-24
Greetings,
I have adapted to Gnome-Shell/Wayland/GDM3.  So count me in.

---

### Post by cariboo on 2017-10-24
I'm running wayland here on Artful, waiting for the Bionic toolchain to be uploaded. I have a phantom cursor on my main screen (22" run in portrait mode) when working on my second screen (32" Samsung). I'd post a screenshot, but the cursor doesn't show up in it. It even changes to the bat when mousing over the Forum logo. It also still acts like the screen is in landscape mode.

---

### Post by Chanath on 2017-10-25
The default Ubuntu got installed in Asus, Lenovo and Medion laptops with Intel graphics, but absolutely refused to boot from hard install in Acer e15 with Nvidia graphics. It boots all right in live mode, which is Xorg, but gives a blank grey screen after install in default. 

So, I installed another 17.10 derivative for the child to use and learn Linux in that laptop. Btw, Windows 10 (the child needs it at school and to play games) is quite snappy in that laptop, but the Ubuntu derivative I installed just flies. That derivative won't break, and even if it breaks in the next 9 months, I'm not worried, as it can be corrected.

I am *not* asking any help here how to install the default Wayland Ubuntu on the Acer Nvidia laptop, just reporting. I don't want to know the workaround either, any more. How to make Wayland work out of the box is the devs' problem. We'd most probably see that solved in the next 9 months, I hope.

---

### Post by cariboo on 2017-10-25
> **Chanath said:**
> The default Ubuntu got installed in Asus, Lenovo and Medion laptops with Intel graphics, but absolutely refused to boot from hard install in Acer e15 with Nvidia graphics. It boots all right in live mode, which is Xorg, but gives a blank grey screen after install in default. 

So, I installed another 17.10 derivative for the child to use and learn Linux in that laptop. Btw, Windows 10 (the child needs it at school and to play games) is quite snappy in that laptop, but the Ubuntu derivative I installed just flies. That derivative won't break, and even if it breaks in the next 9 months, I'm not worried, as it can be corrected.

I am *not* asking any help here how to install the default Wayland Ubuntu on the Acer Nvidia laptop, just reporting. I don't want to know the workaround either, any more. How to make Wayland work out of the box is the devs' problem. We'd most probably see that solved in the next 9 months, I hope.

If you don't want help, why post here? Post in one of the chat forums.

---

### Post by Chanath on 2017-10-25
> **cariboo said:**
> If you don't want help, why post here? Post in one of the chat forums.

Why should I post in "chat' forums to get help?

I am going to move all my installs to 18.04 as soon as the dev branch appears. They are all Intel graphic computers, so I won't have the Nvidia problem. That child's laptop has another Ubuntu derivative without Wayland, so no help needed.

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> 
I am *not* asking any help here how to install the default Wayland Ubuntu on the Acer Nvidia laptop, just reporting. I don't want to know the workaround either, any more. How to make Wayland work out of the box is the devs' problem. We'd most probably see that solved in the next 9 months, I hope.

The purpose of this thread is for early adopters of 18.04 to test the default ubuntu (wayland) and report bugs against wayland to the community through launchpad. It is our testing and filing of bugs that help developers develop fixes. Without these 'out in the field' test cases the quality of a release can be greatly diminished. We are working with the devs, not apart from them, otherwise they only have corner cases to test. I can't emphasize this enough.

Regards..

---

### Post by zika on 2017-10-25
> **ventrical said:**
> **The purpose of this thread is for early adopters of 18.04 to test** the default ubuntu (wayland) **and report bugs** against wayland to the community through launchpad. It is our testing and filing of bugs that help developers develop fixes. Without these 'out in the field' test cases the quality of a release can be greatly diminished. We are working with the devs, not apart from them, otherwise they only have corner cases to test. I can't emphasize this enough.Regards..For years, almost a decade in my case, we've been taught/trained to file bugs on another place and that posting here is not a bug-report. What have changed?

---

### Post by flocculant on 2017-10-25
> **zika said:**
> For years, almost a decade in my case, we've been taught/trained to file bugs on another place and that posting here is not a bug-report. What have changed?

Ventrical didn't say report bugs here ;)

> report bugs against wayland to the community through launchpad

---

### Post by ventrical on 2017-10-25
@flocculant

Thank you. And , as we have done so many cycles before, we report anomolies, see if other users can dupe them, file bugs and then link them here to see if others have same bug so they can be confirmed more readily.

Here is more detail on U+1 history which I left in the wiki: [https://wiki.ubuntu.com/U+1/about](https://wiki.ubuntu.com/U+1/about)

Regards..

---

### Post by dino99 on 2017-10-25
Sorry to post comments about Artful experience, but its about wayland after all.

Wayland is still mysteriously configured: on an zesty->artfull partition, the xhost script is needed for 'synaptic' for example. But on a fresh Artfull install (netboot), opening a 'gnome' session, so a wayland one, synaptic works without the xhost script !!!

As Bionic archive has been populated, and receiving its first bionic package updates, i'm also on board now :P

---

### Post by Chanath on 2017-10-25
> **ventrical said:**
> @flocculant

Thank you. And , as we have done so many cycles before, we report anomolies, see if other users can dupe them, file bugs and then link them here to see if others have same bug so they can be confirmed more readily. Regards..

Consider an anomaly had been reported; the default Ubuntu (Wayland) doesn't boot, after an install to an Acer E15 i5 laptop with Nvidia graphics. It boots in the live mode (Xorg) and can be installed. Grub can be enabled and all that UEFI stuff. The laptop is given back with a different Ubuntu derivative, so there is no way to test how Wayland would work with Nvidia graphics. 

I have no problem (yet) in Intel machines with normal usage, except the jerkiness when moving open windows around the screen.

---

### Post by ventrical on 2017-10-25
> **Chanath said:**
> Consider an anomaly had been reported; the default Ubuntu (Wayland) doesn't boot, after an install to an Acer E15 i5 laptop with Nvidia graphics. It boots in the live mode (Xorg) and can be installed. Grub can be enabled and all that UEFI stuff. The laptop is given back with a different Ubuntu derivative, so there is no way to test how Wayland would work with Nvidia graphics. 

I have no problem (yet) in Intel machines with normal usage, except the jerkiness when moving open windows around the screen.

But you can file a bug while you are in the xorg session:

```

ubuntu-bug xwayland

```

and just tag nvidia and attach an inxi -Fxz file to your bug report and then link it back here.

regards..

---

### Post by Frogs Hair on 2017-10-25
> [COLOR=#000000]As Bionic archive has been populated,[/COLOR] Just added Bionic sources and ready to go.

---

### Post by ventrical on 2017-10-25
> **Frogs Hair said:**
> Just added Bionic sources and ready to go.

```

The following packages will be upgraded:
  distro-info-data

```

one little tidbit so far ;)

---

### Post by Frogs Hair on 2017-10-25
> **ventrical said:**
> ```

The following packages will be upgraded:
  distro-info-data

```

one little tidbit so far ;)

Wasn't expecting much for a few weeks based on the schedule. I had no problems in Wayland other than totem play back and elevated permissions for a few applications experienced and reported by others , not expecting much excitement . :-)

---

### Post by zika on 2017-10-25
> **flocculant said:**
> Ventrical didn't say report bugs here ;)Mea culpa. I'm glad that nothing've changed... ;)

---

### Post by jbicha on 2017-10-26
> **dino99 said:**
> 
Wayland is still mysteriously configured: on an zesty->artfull partition, the xhost script is needed for 'synaptic' for example. But on a fresh Artfull install (netboot), opening a 'gnome' session, so a wayland one, synaptic works without the xhost script !!!

Note that the default session is still named Ubuntu (or GNOME if you like vanilla) when GDM detects that Wayland is not supported on the hardware. I believe that was fixed in the first gdm3 SRU for Ubuntu 17.10, [3.26.1-3ubuntu3]("https://launchpad.net/ubuntu/+source/gdm3/3.26.1-3ubuntu3").

If you want to actually tell if you're running Wayland, see [my answer]("https://askubuntu.com/a/968772/1579").

---

### Post by cecilpierce on 2017-10-26
Has anyone talked or emailed Nvidia about making a wayland driver ?

---

### Post by mc4man on 2017-10-26
> **cecilpierce said:**
> Has anyone talked or emailed Nvidia about making a wayland driver ?

In essence they have -  EGLStreams.  Gnome is one of the few to currently support it. 
So recent nvidia drivers will work in Ubuntu 17.10+ in the wayland session

What is not supported atm are hybrid devices thru nvidia-prime, not really Nvidia's problem..

---

### Post by cecilpierce on 2017-10-26
@ mc4man

Thanks for the info

---

### Post by Frogs Hair on 2017-10-28
Gnome Tweak Bug.

[https://bugs.launchpad.net/bugs/1728239](https://bugs.launchpad.net/bugs/1728239)

---

