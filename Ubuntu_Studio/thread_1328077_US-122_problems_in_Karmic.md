---
title: "US-122 problems in Karmic"
date: 2009-11-16
forum: Ubuntu Studio
---

### Post by EggplantOfFire on 2009-11-16
Hey folks, your kindly idiot neighbor here. 
So I think I jumped the gun by doing a clean install of Karmic Ubuntu Studio from Hardy Ubuntu Studio the second Karmic came out. Duh. Almost everything seemed to run ok in Hardy but there were problems. So I thought getting Karmic Ubuntu Studio would fix those problems. It made more problems. In Hardy I used an older US 122 audio interface to get anything in and out for music production. Regular audio(like video and mp3 playback) went through the normal jacks on the computer. 

I found this [https://help.ubuntu.com/community/TASCAM_US-122]("https://help.ubuntu.com/community/TASCAM_US-122") which got me half of the way. Now I open up and start JACK and then Ardour (the program I grew comfortable with in Hardy) and I only get the mic input no matter what I do. I found the "Sound" controller thing under System-Preferences-sound and found that the computer saw it there and so I made the us 122 the main card. Still no luck in Ardour. Also, Hydrogen seems to be going through the computer card and not through the US-122 like it did before. 

I'm afraid that I am a bit of an idiot when it comes to these issues so go easy on me. oh and sorry for the long text, it's four am and I'm tired. Any help would be greatly appreciated.

---

### Post by EggplantOfFire on 2009-11-16
Seriously? Nothing? At all?

---

### Post by paulmerchant on 2009-11-16
I don't have my US-122 with me right now, but it worked fine when I tested it with an early alpha version of Karmic.

I'm thinking that those old tutorials are outdated for the newest kernel builds. In fact, following the steps in those tutorials will probably just cause you problems. If I remember right, I didn't have to do much at all in Karmic. I just had alsa and jack configured well, installed an alsa firmware package, and then plugged in my US-122.

---

### Post by EggplantOfFire on 2009-11-16
Hmm... Anyway I can back track? Or should I do a clean install again?

BTW, I found that in System-Preferences- Sound I could make the US 122 the default sound card for all audio, so I did that and brought up Hydrogen and it went through the computer's sound card.

---

