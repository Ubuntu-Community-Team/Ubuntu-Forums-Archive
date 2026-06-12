---
title: "Intrusion detection/prevention system"
date: 2010-02-03
forum: Security
---

### Post by phoenixfire900 on 2010-02-03
is there any Intrusion/prevention detection program with a GUI and an easy interface and has alerts that pop up whenever there is a threat?

---

### Post by running_rabbit07 on 2010-02-03
...

---

### Post by diablo69er on 2010-02-03
Well their is arcsight..but that's well over a couple hundred thousand dollars...

As far as stuff that's free really is alls you need is SNORT.  Maybe their is another program that someone else may know about that is a GUI.  But my opinion is if your not willing to check your log files everyday..then a IDS is probably not going to benefit you much more anyways.

---

### Post by bodhi.zazen on 2010-02-03
> **phoenixfire900 said:**
> is there any Intrusion/prevention detection program with a GUI and an easy interface and has alerts that pop up whenever there is a threat?

If I had a pop up alert for every attempt to access my ssh server I would pull my teeth out.

Many of the intrusion detection systems can be configured to send you an email as an alert and many have a graphical web based interface.

At a bar minimum you need something like snort to at least filter out all the important stuff. If you use snort, use base, a web based gui.

For HIDS use OSSEC or Niagos

For desktop users you almost certainly do not need such a thing, thus most are web and email based for remote access to a server.

I highly advise against using firestarter as an intrusion detection system.

---

