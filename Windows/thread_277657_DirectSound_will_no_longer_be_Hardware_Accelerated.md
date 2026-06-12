---
title: "DirectSound will no longer be Hardware Accelerated in VISTA?"
date: 2006-10-15
forum: Windows
---

### Post by Quake on 2006-10-15
[http://openal.org/openal_vista.html](http://openal.org/openal_vista.html)

I don't know what Microsoft is thinking but I really think this is a step backward. Why? Yes, OpenAL will now now replace it to have Hardware accelerated sound and have EAX effect but... I still wonder... why did Microsoft choose to do so?

---

### Post by Dr. C on 2006-10-15
Could this be related to the DRM requirements for protected audio to meet the Advanced Access Content System (AACS) specification? It may be necessary to give up hardware accelerated sound in order to have DRM that meets the requirements of the MPAA and RIAA.

---

### Post by Rhapsody on 2006-10-15
If that's so, then Microsoft may be shooting themselves in the foot here.

> With Microsoft's decision to remove the audio hardware layer in Windows Vista, legacy DirectSound 3D games will no longer use hardware 3D algorithms for audio spatialization. Instead they will have to rely upon the new Microsoft software mixer that is built into Windows Vista. This new software mixer will give the users basic audio support for their old Direct Sound games but since it has no hardware layer, all EAX® effects will be lost, and no individual per-voice processing can be performed using dedicated hardware processing.

EAX has become the de facto standard for real-time effects processing. It has been incorporated in hundreds of games and has become the method of choice for game developers wanting to add interactive environment effects to their titles. Some of the best selling games of all time use the EAX extensions to DirectSound 5.0 and beyond, including Warcraft3, Diablo2, World of Warcraft, Half Life, Ghost Recon, F.E.A.R. and many others. Under Windows Vista, these games will be losing the hardware support that came as standard under the previous Windows Operating Systems, and will no longer provide real-time interactive effects, making them sound empty and lifeless by comparison to the way they sound on Windows XP.

We all know the really big reason for using Windows is gaming, and this change will set Vista behind XP for the current generation of games. Is this how far Microsoft is willing to go for DRM?

---

### Post by Dr. C on 2006-10-16
> **Rhapsody said:**
> If that's so, then Microsoft may be shooting themselves in the foot here.

We all know the really big reason for using Windows is gaming, and this change will set Vista behind XP for the current generation of games. Is this how far Microsoft is willing to go for DRM?

I guess Microsoft is betting the future on DRM

---

### Post by siki_miki on 2006-11-06
At least this may finally fuel OpenAL development. Hopefully others will start to contribute and will create extensions which are not creative-only-EAX-etc. stuff.

It is funny how 3D graphics progressed and in the same time 3D audio actually went backwards (after A3D), thanks to Creative and their fake 3D, called EAX.

What Loki planned for OpenAL unfortunately never ender up there because of their demise. So in 2006 we still lack what was already possible almost decade ago, i.e. OpenAL currrently only allows positional 3D and doppler effect as a base functionallity.

I hope rest of the industry or open source movement will take things in their hands and start developing stuff that was supposed to be in long time ago. 3D geometry aware audio, with occlusions, reflections, material propagation and reverberation is not actually a new concept.

---

### Post by RJARRRPCGP on 2006-11-28
> **Rhapsody said:**
> If that's so, then Microsoft may be shooting themselves in the foot here.



We all know the really big reason for using Windows is gaming, and this change will set Vista behind XP for the current generation of games. Is this how far Microsoft is willing to go for DRM?

Expect audio stutter-city! :evil:

Now it's likely that the following is going to be required now:

Athlon=2.5 ghz minimum

Pentium 4=4.0 ghz minimum

Core 2 Duo=2.5 ghz minimum

For the same games that only required the following:

Athlon=1.4 ghz minimum

Pentium 4=3.0 ghz minimum (The Pentium D is the same)

Core 2 Duo=1.4 ghz minimum (same with the Pentium III and Pentium M) 

This likely means that you're required to overclock just for the audio to play right! 

It's possible that even a Core 2 Duo E6300 (1.8 ghz) isn't sufficient.

Same goes with an Athlon 64 X2 3800+.

---

