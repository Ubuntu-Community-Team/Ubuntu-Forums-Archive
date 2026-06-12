---
title: "Ardour GTK2 Problems"
date: 2008-09-05
forum: Ubuntu Studio
---

### Post by bodysnatcher on 2008-09-05
alright.

when i had windows, i used to record and mix music often using Cubase SX. now i've got ubuntu on my laptop, i've been trying to figure out a way to record music on it since installation.  

i found an open source recording program (Ardour of course), and installed that. 

it opens, and all the buttons work, but when i go to record, it doesn't run smoothly at all. i think it's a buffer problem, but i'm not too experienced.

i record using a mixer through the line in if that helps...
thanks for owt.

---

### Post by paulmerchant on 2008-09-05
Are you using the Jack Audio Server for your audio interface? Do you have the realtime kernel installed?

If you answered no to either of those questions, apt-get linux-rt, Jack, and qJackCtl. Get Jack configured and running for your card (start it with qJackCtl). Ardour will the then use Jack and you will have amazingly low latencies and wonderful stability.

---

### Post by atomkarinca on 2008-09-06
To record with Ardour you should configure the input channels. Hit shift+e to view editor mixer, select the channel you want, from the editor mixer press "Input > Edit" and select the input channel from available connections.

---

### Post by bodysnatcher on 2008-09-09
thanks so much guys,

---

### Post by TonyMaryana on 2009-05-10
I installing Ardour GTK2 in ubuntu 8.10 but I cant import audio file in menu because tihis import panel is lock, I dont know why ?
thanks

---

