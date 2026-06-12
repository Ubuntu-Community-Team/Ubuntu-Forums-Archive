---
title: "Hard Drive Cannot keep up in ardour"
date: 2011-11-13
forum: Ubuntu Studio
---

### Post by fucow23 on 2011-11-13
I have a big problem with my Ubuntu Studio 11.04 using Ardour.While recording using 8 seperate inputs from a M-Audio 1010LT i get about a quarter of the way through the song i am recording $ it stops saying <Hard drive cannot keep up> Help Please.
Mike

---

### Post by sgx on 2011-11-14
Does it continue recording despite the error? Is the recording flawless
before the error? Can you do the same recording in a windows DAW
without issues? Can you lower the quality settings and get farther into the recording?
Some errors are in error. Ideally, you will not use your system drive
for multi-track recording, and make sure the other drive you use is
under 50% capacity. You can increase your luck by using matched drives,
formatted on the same machine, with the same filesystem.

---

### Post by kayosiii on 2011-11-15
What file system are you recording to - If NTFS it you may be using userspace drivers which slow things down somewhat.

Also how much memory on the system.

---

### Post by fucow23 on 2011-11-17
Hey thanks for the replies. First here is my system setup. My system is a 3.0 gighz pentium/4 gigs mem/500 gig hard drive and a Delta 1010lt.What happens is when recording 8 inputs at the same time it will record perfect but stops recording about half way through. The file system is ext4. I have not tried it in windows but i have tried it in Audacity with 8 channel input and it records all the way through. I record at 44100 16 bit. I just dont understand whats wrong?
Thanks 
Mike

---

### Post by sgx on 2011-11-17
[https://ardour.org/forums](https://ardour.org/forums)

It might be good to join and post the question at the main ardour forum, and supply the ardour and jackd version, and .jackdrc text file.

Pretty strange. If your disk is getting full, and ardour had more stringent 'free disk space' requirements than audacity, that might explain it. If audacity used alsa, while ardour used jackd, maybe
choose jackd for recording/playback in audacity, and see if it then
quits halfway like ardour. Some audacity version are labelled
'portaudio' in qjackctl, and don't appear until you press the
audacity record button. If that happens, press pause in audacity, make qjackctl connections, then press pause again to begin recording using jackd with the portaudio label.

Cheers

---

