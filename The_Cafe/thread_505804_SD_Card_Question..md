---
title: "SD Card Question."
date: 2007-07-20
forum: The Cafe
---

### Post by Roasted on 2007-07-20
Got a little problem... my parents are on vacation in South Carolina. My mother took 200-300 pictures on her Panasonic Lumix digital camera, which inside was a 1 GB Kodak SD Card. She did nothing out of the ordinary, and randomly the camera said the card was unable to be read, format y/n. She said no, and called me. I said no, don't call them. She said well it won't let me take any pictures. I said well, go to a CVS and see if their computer can read your card. If it can, burn the images to a CD, format the card, and continue taking pictures for the remainder of the vacation, that way you have the old pictures on disc and are able to continue using the camera.

The CVS computer, however, was not able to read the card. So the question remains, what can we do? Being that I have a Linux computer, do you think I will have a greater chance of recovering the images from the SD card than the CVS machine did?

On Monday, ironically, I start a forensics and security class at college, where it's based around retrieving data from hard drives and retrieving erased data. I emailed the instructor of that class whom I know pretty well and asked if he could help. He said as long as the card can be recognized as a storage device, there's a good chance he can retrieve the images. However, no promises.

So, what do you guys think? What happened to the card? What are the chances, based on the information I've given you, of retrieving the images off of the SD card?

---

### Post by LookTJ on 2007-07-20
Have you tried mounting the camera onto Ubuntu Linux to see if it would work?

---

### Post by Roasted on 2007-07-20
Taylor, I'm unable to do so because she is not home from South Carolina yet. I'm just doing a little research ahead of time to see whether or not the photos are likely to be recovered from either mounting in Linux or using forensic software.

I mean, the card wasn't formatted... so the pictures should be there... right? There's no logical reason that I can see that the pictures would... POOF, gone, just like that. But like I said, nobody knows yet. My mom has no computer in SC and she won't be home for another 16 hours or so. So whenever she gets back I'll do what I can, but like I said right now I'm just looking for a very educated guess on what to expect.

---

### Post by LookTJ on 2007-07-20
Well, just to let you know, I'm not SD expert. Also SD cards should be like(I mean by work like usb drives) usb drives right? If not formatted, the pictures are expected to be there.

---

### Post by macogw on 2007-07-21
It's possible the filesystem on the card is corrupted.  I'm not sure how it'd happen, but given that they are FAT16, I bet turning it off right as it's trying to take/save a picture could mess with it a bit.  The pictures wouldn't all be corrupted then (a few might), I don't think, but the part of the file system that tells the computer where to look on the card to find the rest of the data could be messed up so that it can't tell where the pictures are or even that there are pictures there.  I don't know how this would work on an SD card, but on a hard drive the data can (theoretically, and if you're trying to prove someone had child porn even though the hard drive was shot a few times with a gun but there's still some chunks of the platters that are readable, it's what they'd do) be read with a microscope, bit by bit.  It's also probably possible to go through the bits of the card to look for whatever pattern would denote the start of a file (assuming no fragmentation which would be a nightmare) and then copy the chunk that makes up the file onto a storage device which is working.

This post is almost 100% conjecture.  I have just about no knowledge in this field, except "shooting your hard drive will not keep you from being incriminated, the only way to be SURE the data is 100% is to melt the platters completely" thanks to there being people out there who need to make sure no one ever knows what was on their computer.

---

