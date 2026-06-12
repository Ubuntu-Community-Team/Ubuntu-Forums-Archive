---
title: "how to shut down pulse audio"
date: 2009-09-05
forum: Ubuntu Studio
---

### Post by rixtr66 on 2009-09-05
i am trying to run my usb audio interface,(m-audio,fast track pro)
with renoise,wich i had working.however i keep getting messages for alsa
saying its busy.im running ubuntu studio 8.04.
on the renoise forum they told me to shut down pulse audio.how do i do that?
any help would be appreciated.
Rick :confused:

---

### Post by Illska90 on 2009-09-07
System > Administration > System Monitor

Processes tab

find pulseaudio and kill that process

---

### Post by darrenalex on 2009-09-08
Hi.... I read your post and from that i would suggest that you should go with some information which i am going to share with you...Binary package hint: pulseaudio                                               When I was shutting down, I got an error saying pulse audio has crashed. The computer shut down before I was able to send the report, so I am sending it now.
  Pulse Audio was running fine before I shutdown, and if x org didn't crash on the next time I started my computer, I have a feeling that it would have worked fine then. (As I'm in the command line right now, I know of no way to test it..So, I am just sending this because of the error message, I assume there is something wrong 'under the hood'.... Thanks for sharing the post....

---

