---
title: "Can hear guitar plugged in but can't run through apps eg rackarack"
date: 2012-04-24
forum: Ubuntu Studio
---

### Post by GoaTzaR on 2012-04-24
Hi People. I avoided writing in for as long as possible. I wanted to try every single conceivable possibility first, including other versions other distro's and it all points to 1 thing: I AM the problem, apparently.
So i can plug my guitar into mic/line-in input and i can hear it fine, but i can't do anything with it, like running it through rackarack, jack. I've tried different settings, connecting outputs to inputs, vice versa. I am totally stumped. It's sending me mental! I've spent more hours on this than i can remember, it's even weeks now. If someone could PLEASE put me out of my misery and help me with this? Thank you in advance.

---

### Post by jejeman on 2012-04-24
Which version of ubuntu?
give us output from
```
arecord -l
```
Is jack running?

---

### Post by birdie_in_texas on 2012-04-24
Wouldn't you need an interface such as a Tascam 144mkii in order to actually get a useable signal?

This is the only way it "works" in windows..

I am here for help myself and spied this thread.

Pardon me if I intruded.

---

### Post by sgx on 2012-04-24
> **GoaTzaR said:**
> Hi People. I avoided writing in for as long as possible.  PLEASE put me out of my misery and help me with this? Thank you in advance.

Hi, Rakarrack has a tiny fx button you must push, to engage the audio, in its upper right corner. I forget, a few times per
month.

qjackctl Setup page, Audio tab, left side,
'System' is the line-in.  A widget is there to expand
the list with all connectable items, 1 and 2 are stereo l/r
Any fx with a listing on the
right side of the Audio tab, can receive input from
the left. Click one on each side, (or a stereo pair
if the list is expanded) and press
'Connect'

Then go to the fx output on the left side, and connect it to the
'System' on the right side, your line-out.


after starting rakarrack, change its settings, to output
stereo, instead of mono, and to NOT start jackd on startup. 

Do this also in qjackctl settings panel, Misc tab
on startup. reboot

Now rakarrack won't wrestle for jackd startup control, and you can
adjust qjackctl settings as needed, without re-starting qjackctl.

(all this assumes your sound is working. If it is not. refer back 2 or three pages for other rakarrack and jackd topics, for links and details.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  links 4 and 8



Get a Fender Mustang1 usb modeling amp/interface $110 max,
best linux guitar rig out there! Great sound, plug/play
usb setup :guitar:
Cheers

---

