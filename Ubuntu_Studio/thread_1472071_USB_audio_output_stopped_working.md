---
title: "USB audio output stopped working"
date: 2010-05-04
forum: Ubuntu Studio
---

### Post by spenwah on 2010-05-04
I'm running Ubuntu Studio 64-bit on a laptop with a Behringer UCA202. The setup was working fine a week ago, but now I no longer get any output out of the device through jack except a very faint pulse. I don't recall changing anything before this problem occurred except installing some automatic updates. Now I have updated to Lynx, no change in the symptoms. Sound input from the 202 is OK. Everything works fine when I run jack using the internal sound card. I still get sound out through the 202 under Windows. Any help? I'm not very familiar with the technical side of jack or Linux, and I'm stumped. Thanks

---

### Post by sgx on 2010-05-05
Hi, if you go to youtube, type  qjackctl in the search, one of the vids
involves a behringer product. Others may be helpful too. Type
ardour in the search, and lots of linux audio tutorials appear, and qjackctl is often part of them, since it is one of the first apps
started in any session.
Cheers

---

### Post by AutoStatic on 2010-05-05
Hello spenwah, how do your connections look in QjackCtl? Could you post a screenshot or the output of **jack_lsp -c** ?

Best,

Jeremy

---

### Post by spenwah on 2010-05-05
Screenshot: [http://img.photobucket.com/albums/v310/spenwah/jack.png?t=1273104330](http://img.photobucket.com/albums/v310/spenwah/jack.png?t=1273104330)

Thanks for your help Jeremy.

---

### Post by AutoStatic on 2010-05-06
Your settings look good, but I see no connections in QjackCtl. So with the screenshot you posted JACK won't produce any sound. If it worked fine a week ago the what did you connect to where?

---

### Post by spenwah on 2010-05-06
> **AutoStatic said:**
> Your settings look good, but I see no connections in QjackCtl. So with the screenshot you posted JACK won't produce any sound. If it worked fine a week ago the what did you connect to where?
Right, I didn't open up any programs for the purposes of the screen shot. For troubleshooting I just use ZynAddSubFX. Recently I've been using SooperLooper at shows with Meterbridge for input and output monitoring. And everything works fine if I use the internal sound card for I/O. So anyway, I'm sure patching up the Jack connections is not the problem.

The weirdest thing seems to be that the audio input is OK but yet there's no output.

---

### Post by spenwah on 2010-05-10
Any more tips or pointers, anybody? The next step is either another system reinstall or to ditch Linux completely for Ableton Live and Windows... both options unappealing to me.

---

### Post by cub on 2010-05-11
After the last automatic updates I got my sound stopped working. I had to reapply Alsa 1.0.23 again and it fixed it.

---

