---
title: "Is it possible to enjoy 5.1 or Dolby Atmos audio using headphones under Linux ?"
date: 2021-02-13
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2021-02-13
There is a solution available for the Windows platform. Please read this >>> [https://developer.dolby.com/blog/dolby-atmos-for-headphones/](https://developer.dolby.com/blog/dolby-atmos-for-headphones/)
Is there an equivalent available for Linux ?

---

### Post by mastablasta on 2021-02-15
this seems like EAX. 

for 5.1 you need more speakers, other stuff is just fake using various tricks to get surround sound. i've seen it work on wine games sometimes. other times you get a weird echo. not sure where to try it out out on new native game. i don't have any of the new ones.

---

### Post by linuxyogi on 2021-02-15
@mastablasta
I cant use home theater speakers. The buildings in the locality that we live in are very close to each other. I use a wireless bluetooth headphone for movies. I am looking a way to enhance the audio while using headphones. I use speakers for music but not for movies & the reason is difficult to explain but will try.

In movies the recording of the audio track is made in such a way that the difference between the volume of the dialogue & special effects is very wide.
Suppose I raise the volume to a level where I can hear the dialogues clearly & then there is an explosion or a thunderstorm the volume of the explosion or thunderstorm is much louder than the dialogues.

You understand what I mean ?

---

### Post by mastablasta on 2021-02-16
got it. i am just saying i'v eseen similar things work sometimes and not at others. i am not sound expert to know what makes them work only sometimes.

re: movies - i think that has to do with multiple audio channels. i believe those can be set up. but then again i never tried it. i use Kodi on RPi and would sometimes have that issue and other times not.

---

### Post by Shibblet on 2021-02-17
It all has to do with decoding/downmixing.  Ultimately, most headphones are 2-channel.  Left and Right.  Any Dolby Digital AC3-5.1 tracks, or DTS 5.1 (and higher) must be "downmixed" before they are sent to your 2-Channel headphones.

So, Yes, you can enjoy the sound recorded... but without an actual Home Theater system with the right number of speakers, and a decoder (amplifier / receiver), you will not be able to "hear" the separation of sound into 5.1 to 11.2 channel sound systems.

---

### Post by SeijiSensei on 2021-02-17
> **linuxyogi said:**
> In movies the recording of the audio track is made in such a way that the difference between the volume of the dialogue & special effects is very wide.
Suppose I raise the volume to a level where I can hear the dialogues clearly & then there is an explosion or a thunderstorm the volume of the explosion or thunderstorm is much louder than the dialogues.
My Yamaha receiver has a bunch of preset audio profiles. I can also control the level of each speaker. Sometimes I'll make the center channel much louder than the sides, then turn the overall volume down. (Sometimes I turn the center channel down to eliminate annoying chatter like sports announcers!)

---

### Post by linuxyogi on 2021-02-18
> **Shibblet said:**
> It all has to do with decoding/downmixing.  Ultimately, most headphones are 2-channel.  Left and Right.  Any Dolby Digital AC3-5.1 tracks, or DTS 5.1 (and higher) must be "downmixed" before they are sent to your 2-Channel headphones.

So, Yes, you can enjoy the sound recorded... but without an actual Home Theater system with the right number of speakers, and a decoder (amplifier / receiver), you will not be able to "hear" the separation of sound into 5.1 to 11.2 channel sound systems.

AFAIK all the virtual surround solutions that are available use a thing called HRTF. Its definitely not as good as a real multichannel setup but people who are for some reason stuck with 2 channel an surely benefit from it. Read about HRTF here >>> [https://en.wikipedia.org/wiki/Head-related_transfer_function](https://en.wikipedia.org/wiki/Head-related_transfer_function)

> **SeijiSensei said:**
> My Yamaha receiver has a bunch of preset  audio profiles. I can also control the level of each speaker. Sometimes  I'll make the center channel much louder than the sides, then turn the  overall volume down. (Sometimes I turn the center channel down to  eliminate annoying chatter like sports announcers!)

You will laugh at me but the fact is I use headphones to watch movies so I don't care about the levels.

---

### Post by Shibblet on 2021-02-18
> **linuxyogi said:**
> AFAIK all the virtual surround solutions that are available use a thing called HRTF. Its definitely not as good as a real multichannel setup but people who are for some reason stuck with 2 channel an surely benefit from it. Read about HRTF here >>> [https://en.wikipedia.org/wiki/Head-related_transfer_function](https://en.wikipedia.org/wiki/Head-related_transfer_function)

That's interesting...  The whole idea of being able to listen to things like Dolby Atmos, or DTS EX, is to have the separated sound, and multiple speakers around your room.  But the industry is aware that most people listen with just stereo television speakers, or on their tablets and phones.  That's why downmixing is so important.  A pair of earbuds, or even over the ear headphones, have great range in sound, but still only two channels.

> **linuxyogi said:**
> You will laugh at me but the fact is I use headphones to watch movies so I don't care about the levels.

I won't laugh, but I will disagree... I think you mean "channels," not "levels."

If you cannot hear dialogue over top of background music and sound effects, then you truly will not enjoy what you are watching.  So, the "levels" do need to be "mixed" correctly.

---

