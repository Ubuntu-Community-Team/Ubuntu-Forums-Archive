---
title: "Heads up! GPU acceleration support in trouble!"
date: 2010-10-13
forum: The Cafe
---

### Post by RJARRRPCGP on 2010-10-13
[http://www.conceivablytech.com/3421/business/microsoft-patents-gpu-accelerated-video-encoding/](http://www.conceivablytech.com/3421/business/microsoft-patents-gpu-accelerated-video-encoding/)

Looks like GPU acceleration could be over for the open source world.

---

### Post by PaulReaver on 2010-10-13
intel added the gpu mpeg2 accelaration in the gma 900, 3 months before microsoft's patent was granted so intel can fight the patent

manufacturing/publishing is a form of patent...in intel's favor

it's whether they would counter sue best buddies microsoft???


that's just intel, nvidia and ati might have had products before then..

---

### Post by NightwishFan on 2010-10-13
I doubt it. Half the open source drivers already implement that. They wont be able to get rid of it.

---

### Post by PaulReaver on 2010-10-13
I like the avatar nightwish ... 

kicking it old school dracula B movie styleee... much better than that robert patterson muck :) :) :)

---

### Post by NightwishFan on 2010-10-13
Thanks :) Lee is the man.

---

### Post by siimo on 2010-10-13
Learn to READ.  This is a patent for encoding, not decoding.  You guys are all talking about decoding.

---

### Post by NightwishFan on 2010-10-13
Ah I see. I really just skimmed the article because I knew that it was probably useless information anyway. Regardless Apple and NVidia already implement functions to do normal processing on a GPU... (If that is what that means).

---

### Post by PaulReaver on 2010-10-13
> **siimo said:**
> Learn to READ.  This is a patent for encoding, not decoding.  You guys are all talking about decoding.

No, it wouldn't be too intelligent to be able to do one without being able to do the other now would it?  All I did was write that there was precedence in Intel's favour.

If you are going to insist on being pedantic I AM TYPING/HAVE TYPED, NOT TALKING.

---

### Post by siimo on 2010-10-13
Nope.  There is a difference.  With encoding, speed does not matter, unless you encode lots of video like YouTube.  As without it, it will just take longer time to encode.  But with decoding, speed is important as it affects watch-ability of the video, especially on low powered systems.

Most of the GPU acceleration currently is just used for decoding, not encoding. There does not seem to be a lot of software / information available on GPU powered encoding at the moment it is fairly new.

---

### Post by PaulReaver on 2010-10-13
Where did anyone write that Intel drivers didn't support encoding? 
Where did I write the word playback?
All I did was write that there was precedence of MPEG2 GPU acceleration in Intel's favour, and that Microsoft would have a hard time proving otherwise.

for a second time you seem to be reading your own fictitious version of other peoples posts......"Learn to READ" lol.  Irony is obviously lost on you!!!

you're looking for an argument where no difference of opinion exists.

---

### Post by cascade9 on 2010-10-13
Stuffs me how somebody can patent an 'invention' but not show it working. The abstract for the patent is worryingly vauge as well- 

> **Abstract** A video encoding system uses both a central processing unit (CPU) and a      graphics processing unit (GPU) to perform video encoding. The system      implements a technique that enables the GPU to perform motion estimation      for video encoding. The technique allows the GPU to perform a motion      estimation process in parallel with the video encoding process performed      by the CPU. The performance of video encoding using such a system is      greatly accelerated as compared to encoding using just the CPU. Also,      data related to motion estimation is arranged and provided to the GPU in      a way that utilizes the capabilities of the GPU. Data about video frames      may be collocated to enable multiple channels of the GPU to process tasks      in parallel. The depth buffer of the GPU may be used to consolidate      repeated calculations and searching tasks during the motion estimation      process. 


[http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=7,813,570.PN.&OS=PN/7,813,570&RS=PN/7,813,570](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=7,813,570.PN.&OS=PN/7,813,570&RS=PN/7,813,570)


The last line is complete *waving fist* *skull* storm cloud* *waving fist*- 

> Although the invention has been described in language specific to structural features and/or methodological steps, it is to be understood that the invention defined in the appended claims is not necessarily limited to the specific features or steps described. Rather, the specific features and steps are disclosed as preferred forms of implementing the claimed invention. 
[http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=7,813,570.PN.&OS=PN/7,813,570&RS=PN/7,813,570](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=7,813,570.PN.&OS=PN/7,813,570&RS=PN/7,813,570)

I'd be a lot less cynical if microsoft actually made GPUs. As it stands, it looks like intel guesed which way the wind was blowing, and somehow got it patented. 

Seems pretty close in some ways to the old ATI "Rage Theater" chips. While not actually a GPU (its  seperate chip) it shows that as early as 1999 ATI (and possibly nvidia + others) were already thinking about getting video hardware to encode and decode video. 

ATI and nVidia should dispute this patent...but they probably wont. They cant afford to annoy the elephant in the room........

---

