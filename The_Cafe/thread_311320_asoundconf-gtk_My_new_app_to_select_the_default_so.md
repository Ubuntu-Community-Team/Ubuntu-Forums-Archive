---
title: "asoundconf-gtk: My new app to select the default sound card"
date: 2006-12-02
forum: The Cafe
---

### Post by .t. on 2006-12-02
Whilst using XFCE, I have missed the functionality to select the ALSA default sound card. In GNOME Ubuntu, this is easy through System->Preferences->Sound. Select the card, and it runs asoundconf set-default-card <card>. Done.

In XFCE, there is no such functionality. I felt the desire to have that, and also motivation to get that working. I took it upon myself to learn Python, and I did just about. I wrote my applet so that it would also fill a deficiency in the GNOME Sound Properties applet: when you have ejected a card, it is still active, and there is no way to remedy that. My applet runs asoundconf on quit, so that it makes sure the card selected is the correct one. (And writing that, I've just thought of where it could be buggy... but I'll need to test that...)

Now, I keep referring to asoundconf. I designed my applet to be multi-platform, so that it could run on non-Debian based distributions. This would be hard with a dependency on asoundconf. Fortunately, asoundconf is also in Python, so (thanks to the GPL), I've stolen quite a few functions from that. Now, my applet will run anywhere with PyGTK and ALSA.

To run the applet, you will need to copy and paste it into a text file, and mark that as executable. You can get it here: [http://tibsplace.co.uk/asoundconf-gtk](http://tibsplace.co.uk/asoundconf-gtk)

If you want an easy way to get it: "wget [http://tibsplace.co.uk/asoundconf-gtk](http://tibsplace.co.uk/asoundconf-gtk) && chmod +x asoundconf-gtk"

---

### Post by .t. on 2006-12-03
*bump*

There's gotta be someone like me... with XFCE and two sound cards...

---

### Post by raublekick on 2006-12-03
this sounds pretty neat. i have a PCMCIA sound card in addition to my internal sound. even with Gnome i have to blacklist my internal one if i want my sound blaster to be used, so maybe this will sidestep that issue!

---

### Post by .t. on 2006-12-03
Well, hopefully I'll have it in Feisty universe soon... so if your brave enough to be using that then it'll be easy to get. However, if not, you'll have to install the package which I've attached.

The attached deb is gzip'd. It was built for feisty, and says it's for i386. However, it should work in Edgy, and I think it may work in Dapper.

---

### Post by ssamoon on 2008-09-08
hate to resurrect something so old, but this just solved my problems! thank you for making this! installed using apt-get, take care

---

### Post by gibberz on 2008-10-18
Yea i have to thank you .t. ! i can`t remember where i found your app but it was awhile ago now in some tutorial(maybe you wrote?). Anyway i install this little  app on any debian based system that i`ve tried so far and it works great. I use it to switch between my internal sound card and my logitech clear chat pro usb headset , works a treat! so thanks again kind sir!

Just need to try get it to work on my new distro of the  week , Mandriva 2009. :)

---

### Post by wayward4now on 2009-07-19
Since we seem to no longer have /usr/bin/asoundconf in Karmic, is there an upgrade in the works to have this application back?? I used the heck out of it and it was sweet!! I hope you can figure out the new sound system so we can have your application back!! . My hat is off to you sir. One of the handiest little apps in the whole schebang. Ric

As of today August 21st 2009, Still waiting!!

---

### Post by anonymous_user on 2009-07-23
Why the [expletive] does asoundconf-gtk need so many dependencies? I mean its only a frontend for asoundconf right?

---

### Post by bodymind on 2010-06-25
it doesn't work for me.. .s

Traceback (most recent call last):
  File "/usr/bin/asoundconf-gtk", line 361, in <module>
    aconf = asoundconf()
  File "/usr/bin/asoundconf-gtk", line 337, in __init__
    cb_set_active_text(self.combo, string.strip(get("defaults.pcm.card")))
  File "/usr/lib/python2.5/string.py", line 255, in strip
    return s.strip(chars)
AttributeError: 'bool' object has no attribute 'strip'

---

### Post by cariboo on 2010-06-25
I think you may have to wait quite a while for support, the last time the op logged in was over 2 years ago.

---

