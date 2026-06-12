---
title: "Problems with JACK and qjackctrl"
date: 2009-08-29
forum: Ubuntu Studio
---

### Post by preta on 2009-08-29
I am getting the following error message when I attempt to run jackd from the qjackctl panel (the following is from the qjackctl "messages" window):

cannot use real-time scheduling (FIFO at priority 10) [for thread -1211214144, from thread -1211214144] (1: Operation not permitted)
cannot create engine
17:37:40.681 JACK was stopped successfully.
17:37:40.682 Post-shutdown script...
17:37:40.684 killall jackd
jackd: no process killed
17:37:41.100 Post-shutdown script terminated with exit status=256.
17:37:42.753 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. 

What am I doing (or have done wrong)? Any help given would be greatly appreciated.

---

### Post by dawiba on 2009-08-29
You haven't necessarily done anything wrong, but it would help to know a couple of things.

Are you running UbuntuStudio?

Which version?

What soundcard are you using?

---

### Post by preta on 2009-08-29
Hi, Dawiba:
No I'm not using Ubuntu Studio; I'm using a vanilla NBR 9.04 install. My computer is an ASUS eee 1000HE. I am using the built-in audio card. I have all my audio preferences set to ALSA and am basically not using Pulse Audio at all. 

Thank you

---

### Post by dawiba on 2009-08-29
The first thing to try is to make sure that in your jack settings, the realtime option is unchecked. Then try starting jack again.

---

### Post by preta on 2009-08-29
Dawiba:
You are a godsend my friend. Worked exactly as you said it would after I deselected realtime in settings. Thank you very much for helping me. 
Preta

---

### Post by sgx on 2009-08-30
> **preta said:**
> Dawiba:
You are a godsend my friend. Worked exactly as you said it would after I deselected realtime in settings. Thank you very much for helping me. 
Preta It's good luck to start from the cold boot, with all internet hard/software off, system sounds and screensavers off, there are likely undocumented issues that may not be drastic, but you want best for your creations. Also, I use a non-RT priority figure in qjackctl of around 70 or 80, you can experiment if you need to
Cheers

---

