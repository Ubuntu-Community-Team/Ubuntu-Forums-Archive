---
title: "No audio from Youtube"
date: 2013-11-15
forum: Ubuntu Studio
---

### Post by War Tribe on 2013-11-15
while watching a youtube video to get all of the software up and running so i can play my guitar through my laptop, once i started loading the software, the audio from the youtube video stopped working. is it because the software demands more out of the audio and had to stop the audio from the video? once i closed all of the software, the audio came back. i'm on a gateway nv53a24u laptop, with 2 GBs of RAM, a 320 GB harddrive and it has a dual core AMD processor of which I don't know what model # it is. i'm looking to upgrade all of this hardware in the future or just get a desktop so i can expand out even more. but for now, my laptop is it. so what gives with this audio issue?

---

### Post by su:bhatta on 2013-11-15
Did, you turn on Jack using QJackCtl when you loaded the softwares? 

Maybe I am wrong but, This can cause youtube sound to get lost if the adobe flash player doesn't route audio through Jack!

---

### Post by gdesilva on 2013-11-27
Yes, it is most likely due to starting Jackd. Stopping Jackd will restore flashplayer audio.

---

### Post by su:bhatta on 2013-11-30
Jack is kind of notorious for this.. 

I have had this problem when trying to use Skype , and only solution is to stop Jack and use programs that cannot route audio through Jack.

---

