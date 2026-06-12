---
title: "The sound quality in Linux (ubuntu 9.04) is amazing!"
date: 2009-07-11
forum: The Cafe
---

### Post by Quake on 2009-07-11
I have to say that I'm blown away by the Ubuntu's 9.04's sound quality is just amazing.
I'm running Banshee, Alsa (No pulseaudio Virus) and the sound is much better than Windows. 

Maybe Creative's drivers are to be blamed (I have a Sound blaster audigy) but the music come to life. I have a 5.1 system and it's like I'm surrounded by the music. And the bass is not overwhelming.

What's your experience regarding the sound quality?

---

### Post by izizzle on 2009-07-11
I would have to disagree. I have an Audigy 2 ZS with a Logitech 5.1 THX surround system and the audio sounded slightly more clearer in Windows. Nonetheless, the audio is still VERY nice.

---

### Post by Redache on 2009-07-11
> I would have to disagree. I have an Audigy 2 ZS with a Logitech 5.1 THX surround system and the audio sounded slightly more clearer in Windows. Nonetheless, the audio is still VERY nice.

Have you tried playing with the Alsa Mixer? By Default it tends to be set at a lower Volume than full (Don't ask me why).

I think the command is

```
 alsamixer-gui
```

It's something along those lines anyway.

It could be that your Soundcard has Proprietary Enhancements built into the Windows Driver that is making it sound more clear. I'd try fiddling with the EQ to see if you get an improvement.

---

### Post by PurposeOfReason on 2009-07-11
> **Redache said:**
> Have you tried playing with the Alsa Mixer? By Default it tends to be set at a lower Volume than full (Don't ask me why).

I think the command is

```
 alsamixer-gui
```It's something along those lines anyway.

It could be that your Soundcard has Proprietary Enhancements built into the Windows Driver that is making it sound more clear. I'd try fiddling with the EQ to see if you get an improvement.
Alsamixer is not an EQ.

---

### Post by Quake on 2009-07-11
I normally use alsamixer, these are my sound settings. View the screenshot to view my settings.

---

### Post by Redache on 2009-07-11
> Alsamixer is not an EQ. 	

I'm aware. I meant the EQ in whatever audio software he's using.

---

### Post by Gizenshya on 2009-07-11
I strongly suspect that it is an equalization issue.  The quality of the amplifiers, speakers, and the initial recording quality would have a far greater effect on sound quality than an OS change.  That stuff is usually just splitting hairs, unless it is an EQ issue.  Even you said that "and the bass is not overwhelming" (which implies EQ settings changed).  I bet if you change the EQ settings (or get something to do it) you'll be even more satisfied.  Every one of those settings needs to be changed for your speaker system and your environment.  Unless there is an ungodly amount of distance between source and your receiver, I highly doubt you would even be able to tell the difference between a headphone Jack-to-RCA connector and an optical connection.  I'm an audiophile, and one of my hobbies is installing high quality A/V equipment (for friends and family... and myself).  I've been DEEP into it for than a decade.  All the hype about some new sound card, new cables, and all that other crap is just that.  Hype.  Google "placebo effect" :p  Chances are you're using MP3 format files anyway, which is a lossy format.  That makes more of a difference than anything you mentioned (changing soundcards or OS).  Again, get an EQ!

With computer-sourced signals, I prefer to do all the analyzing and EQing on the computer, as it takes out physical devices from the circuit (which necessarily must add interference).

---

### Post by Viva on 2009-07-11
I have a similar experience. I had to boot into winblows recently and the sound quality was very poor compared to ubuntu.

---

### Post by racerraul on 2009-07-11
> **Gizenshya said:**
> I strongly suspect that it is an equalization issue.  The quality of the amplifiers, speakers, and the initial recording quality would have a far greater effect on sound quality than an OS change.  That stuff is usually just splitting hairs, unless it is an EQ issue.  Even you said that "and the bass is not overwhelming" (which implies EQ settings changed).  I bet if you change the EQ settings (or get something to do it) you'll be even more satisfied.  Every one of those settings needs to be changed for your speaker system and your environment.  Unless there is an ungodly amount of distance between source and your receiver, I highly doubt you would even be able to tell the difference between a headphone Jack-to-RCA connector and an optical connection.  I'm an audiophile, and one of my hobbies is installing high quality A/V equipment (for friends and family... and myself).  I've been DEEP into it for than a decade.  All the hype about some new sound card, new cables, and all that other crap is just that.  Hype.  Google "placebo effect" :p  Chances are you're using MP3 format files anyway, which is a lossy format.  That makes more of a difference than anything you mentioned (changing soundcards or OS).  Again, get an EQ!

With computer-sourced signals, I prefer to do all the analyzing and EQing on the computer, as it takes out physical devices from the circuit (which necessarily must add interference).

Indeed... most people that have no idea what the term "sound quality" is (is there even a definition?) perceive improved sound as a rise in volume.

To be able to get to the bottom of the myths, there needs to be a source of referrence measured.  Followed by a measurement of the same source playing through Windows & 9.04.  Any clipping of the signal IMO would go down as a lesser playback of the source.

And you can bet your hind ends that there are people that perceive an improvement in "sound quality" while listening to a track with as much as 5-10% clipping.

As has already been said... its hard to improve the quality of the source without and EQ and even then, that used improperly will ruin things just as well.

I'm calling BS... were are the measurements?  Whose ears are better than whose?  well you see where this is going :lolflag:

---

### Post by Quake on 2009-07-11
> **racerraul said:**
>  I'm calling BS... were are the measurements?  Whose ears are better than whose?  well you see where this is going :lolflag:
Come on, I have never said I was a professional audiophile. FAR from it . I don't use an EQ so the only settings I touch is the bass and treble settings. 
I use Windows XP to game and sometimes, I play music. And I find that even with the treble to the maximum, it doesn't match alsa's treble. 

It may be a placebo effect... but I use both OS and everytime, I enjoy linux' sound quality more than Windows. Maybe it's a matter of the codecs being used... but I'm only relating my experience.

---

### Post by Mazza558 on 2009-07-11
Sound's good for me, except on my Dell laptop it's quiet compared to how loud it can go on Windows.

---

### Post by racerraul on 2009-07-11
> **Quake said:**
> Come on, I have never said I was a professional audiophile. FAR from it . I don't use an EQ so the only settings I touch is the bass and treble settings. 
I use Windows XP to game and sometimes, I play music. And I find that even with the treble to the maximum, it doesn't match alsa's treble. 

It may be a placebo effect... but I use both OS and everytime, I enjoy linux' sound quality more than Windows. Maybe it's a matter of the codecs being used... but I'm only relating my experience.

It wasn't an attack at you, just posing a strong argument against the very unlikely possibility.

You have to understand, that the term "sound quality" is rather poor as there is no standard definition as to what it is. So when something is perceived as better what are we talking about?  a stronger signal and if so, is there any clipping?

A stronger signal can be quantified as better sounding and can be measured, and could probably be traced back to better drivers using the HW available... but we can't even say that is exactly the case in this instance.

See where I'm going?

---

### Post by racerraul on 2009-07-11
> **Mazza558 said:**
> Sound's good for me, except on my Dell laptop it's quiet compared to how loud it can go on Windows.

I can say that yes... the analog outputs on my dell laptop are rather weak.  This I attribute to the HW rather than the OS.

---

