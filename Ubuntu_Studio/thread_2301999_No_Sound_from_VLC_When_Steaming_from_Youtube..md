---
title: "No Sound from VLC When Steaming from Youtube."
date: 2015-11-06
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-11-06
Hi,

I only get to hear the sound when steaming youtube video through VLC for the first 3 seconds.
I am using Ubuntu Studio 14.04 installed on Asus A8N32 SLI Deluxe with two cheap USB speakers from Logitech.

I always boot this PC with kernel 3.19.0-25-lowlatency.

Can someone help?

Thanks.

---

### Post by CrocoDuck on 2015-11-07
Oh man, it really doesn't want to go smoothly :shock:. First thing first, I would try without JACK running. Have a look at both VLC and system audio settings.

---

### Post by sethanath2 on 2015-11-07
I forgot to mention to you that watching any DVD would work perfectly with VLC. I only have problem when steaming over the HTTP connection as you would see from my screen shot.

How do I do it without JACK running by the way? Was it running automatically with this OS?

Thanks.

---

### Post by MartyBuntu on 2015-11-08
> **sethanath2 said:**
> I forgot to mention to you that watching any DVD would work perfectly with VLC. I only have problem when steaming over the HTTP connection as you would see from my screen shot.

How do I do it without JACK running by the way? Was it running automatically with this OS?

Thanks.

I don't believe JACK starts up at log in, unless you've specifically configured JACK or some other process that requires JACK to start at boot.

---

### Post by CrocoDuck on 2015-11-08
Everything works on mine setup. Which version of VLC are you using? Also, when the stream is playing, have a look at the audio options. Maybe they get reseted for some weird reason.

---

### Post by sethanath2 on 2015-11-29
> **CrocoDuck said:**
> Everything works on mine setup. Which version of VLC are you using? Also, when the stream is playing, have a look at the audio options. Maybe they get reseted for some weird reason.

I tried a different Youtube video, and it works now with sound for an entire streaming. I am using VLC 2.1.6 Rincewind.

Also, do you happen to know how to make VLC streams an entire Youtube video, instead of playing some of the contents at a time?
On Youtube website, I would click pause, wait until an entire video is finished with the downloading, and click play afterward for better experience.

I cannot do the same with VLC as it would just stop entirely.

Thank you.

---

### Post by CrocoDuck on 2015-12-01
> **sethanath2 said:**
> 

Also, do you happen to know how to make VLC streams an entire Youtube video, instead of playing some of the contents at a time?



I never looked into as my connection is fast enough to allow me to watch the vast majority of the videos smoothly, without needing to pre-buffer. You could bypass the problem using a web browser extension to download youtube (and other sites) videos.

I am using VLC 2.2.1 at the moment and everything is pretty smooth. You could check whether there is some known bug on your version. I couldn't find any [bug]("https://trac.videolan.org/vlc/wiki") for your version on the tracker, but maybe it is worth to have a deeper search.

---

