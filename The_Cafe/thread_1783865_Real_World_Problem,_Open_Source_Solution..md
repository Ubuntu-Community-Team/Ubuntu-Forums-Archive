---
title: "Real World Problem, Open Source Solution."
date: 2011-06-16
forum: The Cafe
---

### Post by irv on 2011-06-16
I was having a real world problem and was having trouble finding a solution, but found the answer not in Windows, but Linux. I believe this is because of community development. Let me tell you the problem and the solution.

**[COLOR="Red"]Problem:[/COLOR]**
I have a teaching ministry in our locale county jail, and they do not allow me to bring my laptop into the jail. Now I download college lectures and need to use them so I need to burn them to a DVD. Normally this would not be a problem but because of the video format (m4v or mp4) you can not just burn them to a DVD. You first have to convert them to a .mov file then build a menu and create a .iso file.

To add to this, I need to download them via iTunes which calls for me to use Windows. So while I was in windows I used a program call DVD creator 6 by ImToo. It took over 2 hours to convert and burn each DVD. I could only get two lectures on a disc and I had 30 of them to do. You do the math.

When I got done and started to use them, they started to play OK but as you got into the lecture the sound and video was not in sync. I had to start all over again. 

**[COLOR="Red"]Solution:[/COLOR]**
This time I used open source. I used DeVeDe to convert the videos and create a .iso file. And then I used k3b to burn them. But now this time it only took about an hour for each one and I could get three lectures on a disc and everything was in sync.

And as a side note using the DVD creator 6, seeing I was using a trial version I had to put up with a water mark on the video. After this, do you think I was going to buy it. If the product was high quality and did the job right, I would have purchase it. Lets never take for granted the high quality we have is some of our open source software. 

Linux and open source solved another Real World Problem.

---

### Post by forrestcupp on 2011-06-16
DeVeDe and K3b are definitely awesome resources.

But the method you were using in Windows was definitely not the best choice for doing it in Windows.

---

### Post by irv on 2011-06-16
> **forrestcupp said:**
> DeVeDe and K3b are definitely awesome resources.

But the method you were using in Windows was definitely not the best choice for doing it in Windows.

I am sticking with open source, but I am curious on what you would have used. I have been away from windows for a few years, (only go back to it when I have too), so I don't know what's good and what's not.

---

### Post by forrestcupp on 2011-06-16
> **irv said:**
> I am sticking with open source, but I am curious on what you would have used. I have been away from windows for a few years, (only go back to it when I have too), so I don't know what's good and what's not.

First of all, I would never convert them to .mov format. I would convert to mpeg2, preferably with split audio and video files. That is the native DVD format. If you convert to .mov, the software will still have to convert it again to mpeg2, so you're really wasting time.

But in Windows, I personally use Vegas Pro and DVD Architect, which cost me a lot of money. But before I bought that, I used a lot of freeware and even open source software to do these things. One of the best freeware video converters I've found for Windows is called Super. It can convert about anything, and in some cases, it can keep the original stream without having to recompress it.

I also used DVDauthor with the DeVeDe frontend in Windows. Then, current versions of Windows can burn iso images, and if you're in Windows XP, which can't burn them, you can use a freeware program like ImgBurn.

There are all kinds of free of charge options in Windows, too. My main point was that there's no way I would convert to .mov to burn a DVD when I could just go ahead and convert once to the native mpeg2 format.

---

### Post by irv on 2011-06-16
> **forrestcupp said:**
> First of all, I would never convert them to .mov format. I would convert to mpeg2, preferably with split audio and video files. That is the native DVD format. If you convert to .mov, the software will still have to convert it again to mpeg2, so you're really wasting time.

But in Windows, I personally use Vegas Pro and DVD Architect, which cost me a lot of money. But before I bought that, I used a lot of freeware and even open source software to do these things. One of the best freeware video converters I've found for Windows is called Super. It can convert about anything, and in some cases, it can keep the original stream without having to recompress it.

I also used DVDauthor with the DeVeDe frontend in Windows. Then, current versions of Windows can burn iso images, and if you're in Windows XP, which can't burn them, you can use a freeware program like ImgBurn.

There are all kinds of free of charge options in Windows, too. My main point was that there's no way I would convert to .mov to burn a DVD when I could just go ahead and convert once to the native mpeg2 format.

Very interesting stuff. First the reason I said .mov files is because this is the format I thought that the conversion process produces. I am on the road right now and do not have a DVD to look at but I thought it was a .mov file that it produces.

Does DeVeDe convert the video to a mpeg2 file? Can you tell I am a little new at this. I don't have to work with video files that often so I don't know a lot about it. All I know is I ended up with something that worked for me and it got me out of hot water with the inmates.

---

### Post by koleoptero on 2011-06-16
A similar pay-for-it program in windows to devede is convertxtodvd and it's actually even simpler and (in my experience) much faster than devede. It even burns the disk for you directly.

---

### Post by ctrlmd on 2011-06-16
Rofl

---

### Post by user1397 on 2011-06-16
Devede works pretty good I hear.  Another open source option is [tovid]("http://ubuntuforums.org/showthread.php?t=183936") (you can customize menus and the like quite a bit more, but it might be a little harder to use than devede or other similar programs, especially if you use the command line which is usually recommended as the GUIs are still a bit alpha).

---

### Post by forrestcupp on 2011-06-16
> **irv said:**
> Very interesting stuff. First the reason I said .mov files is because this is the format I thought that the conversion process produces. I am on the road right now and do not have a DVD to look at but I thought it was a .mov file that it produces.

Does DeVeDe convert the video to a mpeg2 file? Can you tell I am a little new at this. I don't have to work with video files that often so I don't know a lot about it. All I know is I ended up with something that worked for me and it got me out of hot water with the inmates.
.mov is Apple's compressed video file format that's associated with Quicktime. It's similar to being Apple's version of .wmv.

Are you maybe thinking of **m2v**? Video on a DVD is in MPEG-2 format usually in a .vob file container. Usually to mess with it, you need to *demux* it into separate MPEG-2 video and audio streams. The video stream is usually in a file container called .m2v and the audio ends up being either an .mp2 or .wav or something. DeVeDe is a graphical front-end for DVDauthor, and I'm pretty sure it takes .m2v's and .mp2's and creates an .iso with those and whatever menu information you give it. Sometimes .m2v files have video and audio in one file.

If DeVeDe is converting other types of video files, I'm sure that's what it's converting it to.

---

