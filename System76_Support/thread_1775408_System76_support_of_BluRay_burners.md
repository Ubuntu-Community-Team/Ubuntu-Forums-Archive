---
title: "System76 support of BluRay burners"
date: 2011-06-04
forum: System76 Support
---

### Post by RedRat on 2011-06-04
Will System 76 support BluRay burners or are they now doing it? 

I just visited the hardware/laptop forum and a person their was echoing an earlier complaint of mine that there was precious little support for HD movies. I have a HD video camera and a lot of taped film of my Grandkids. I would like to edit it and then burn it to BluRay disks. I know that many of the new Windows 7 laptops now come with BluRay players and some with burners. Does (or is) System 76 following suit? How about editing programs in Ubuntu for HD and BluRay?

I am not interested in copying commercial BluRay disks since their costs outweigh and possible advantage. Further, I view most movie releases only once and only very rarely wish to see them a second time, yet alone a third time. My personal view is that such copying ain't worth it.

---

### Post by gordintoronto on 2011-06-04
I'm not with System 76.

If your camera saves on tape, and only has Firewire output, you are probably out of luck. I would be delighted if people show me that I'm wrong about that.

You can buy a blu-ray burner on Newegg and install it in just about any modern PC.

If your camera saves to SD card or a hard drive, and has a USB connector, you should be able to copy HD video to your computer, edit it in Cinelerra and save it to blu-ray using Nero for Linux. Cinelerra has quite a learning curve, but "Cinelerra for Grandma" is terrific, and there are many tutorials on Youtube.

---

### Post by RedRat on 2011-06-04
> **gordintoronto said:**
> I'm not with System 76.

If your camera saves on tape, and only has Firewire output, you are probably out of luck. I would be delighted if people show me that I'm wrong about that.

You can buy a blu-ray burner on Newegg and install it in just about any modern PC.

If your camera saves to SD card or a hard drive, and has a USB connector, you should be able to copy HD video to your computer, edit it in Cinelerra and save it to blu-ray using Nero for Linux. Cinelerra has quite a learning curve, but "Cinelerra for Grandma" is terrific, and there are many tutorials on Youtube.
I have been able to move HD video from my Canon HD video camera, 1080p, via a 1384 firewire to an older Windows XP machine and use Adobe Premium video editing software as of about a year ago. However, I was not able to move it to my Ubuntu 8.04 machine and edit it HD. Actually getting stuff off tape is not that bad, it just does it in real time.

I do not have a BluRay burner but I  now have a System 76 laptop running 10.04 and it has the horsepower to probably edit HD video. Back about a year or so ago, Cinelarra looked like it was heading into HD territory and I played about with it for a while. It does seem to have a steep learning curve but at that time it did not handle HD under 8.04, perhaps now it does under 10.04. I will look into that.

My real question though is can I get a BluRay burner into my Serval Pro????

---

### Post by gordintoronto on 2011-06-05
In late 2009 I bought my first video camera. It was HD, but that was all it had going for it. It made great videos of things happening 10 or more feet from the camera, in bright sunshine. I had no trouble at all editing the video in Cinelerra. (4 GB of memory, 3.1 GHz dual-core CPU.)

The initial setup steps described in Cinelerra for Grandma make a huge difference!

I realized "widescreen" was irrelevant to the kind of videos I take, so I bought an SD camera which is immensely better.

If your Serval Pro is a desktop machine, it should take about three minutes to install a blu ray burner.

---

### Post by RedRat on 2011-06-05
> **gordintoronto said:**
> In late 2009 I bought my first video camera. It was HD, but that was all it had going for it. It made great videos of things happening 10 or more feet from the camera, in bright sunshine. I had no trouble at all editing the video in Cinelerra. (4 GB of memory, 3.1 GHz dual-core CPU.)

The initial setup steps described in Cinelerra for Grandma make a huge difference!

I realized "widescreen" was irrelevant to the kind of videos I take, so I bought an SD camera which is immensely better.

If your Serval Pro is a desktop machine, it should take about three minutes to install a blu ray burner.
No the Serval Pro is a laptop, that was why I was asking. I have an older WinVista HP Pavillion that just had the hard drive go south, I might try doing it on that machine and add 10.04. Doesn't quite have the horsepower of the Serval Pro (I-7 intell and 6Gb memory), but maybe I can get it work. My old Windows XP machine in now some 7 years old and needs replacing. I do know that Bluray takes a bit of horsepower so I don't know about how well that older Pavillion will do. Might just replace it with a newer machine and not waste anymore time.

---

### Post by gordintoronto on 2011-06-06
I'm surprised no one from System76 has jumped in here. I fool around with desktop hardware all the time, and actually started with an empty case for my current computer, but I have never attempted to modify laptop hardware.

You can actually buy an external (USB) blu-ray burner, but I'm not sure how well they work.

---

### Post by RedRat on 2011-06-06
> **gordintoronto said:**
> I'm surprised no one from System76 has jumped in here. I fool around with desktop hardware all the time, and actually started with an empty case for my current computer, but I have never attempted to modify laptop hardware.

You can actually buy an external (USB) blu-ray burner, but I'm not sure how well they work.
The problem here is the data transfer rate. BluRay disks, if memory serves, are about 25-35Gb, transferring data at 1-5 Mb or even 100 Mb per sec will take a long time. Perhaps the new USB 3 can do this quicker, but I don't know the transfer rates for this new form.

---

### Post by gordintoronto on 2011-06-07
Exactly!  I'm not sure that USB 2.0 can transfer data fast enough to burn at 1.0 times the nominal transfer rate for blu-ray.

---

### Post by isantop on 2011-06-08
Sorry about the slower responses lately. Yesterday we did a lot of moving around, and the servers and internet access were down through the afternoon. 

Support for blu-ray in Ubuntu is really the problem here. Blu-ray discs use a very strict encryption scheme that is very different from the method used on DVDs. This hasn't yet been implemented in any multimedia programs used in Ubuntu, so because of the lack of support, we don't provide options to have them installed yet. As the support develops, we will begin offering it as an option.

---

### Post by RedRat on 2011-06-08
> **isantop said:**
> Sorry about the slower responses lately. Yesterday we did a lot of moving around, and the servers and internet access were down through the afternoon. 

Support for blu-ray in Ubuntu is really the problem here. Blu-ray discs use a very strict encryption scheme that is very different from the method used on DVDs. This hasn't yet been implemented in any multimedia programs used in Ubuntu, so because of the lack of support, we don't provide options to have them installed yet. As the support develops, we will begin offering it as an option.

Thanks for the reply. However, I guess I am not too clear on exactly how the BluRay disks operate. What I want to do is to write to the disks a bunch of files of my own. I have some HD video that I made and not trying to copy commercial movies or other encrypted material. You mean to say that even my own files are then encrypted when they are written to a BluRay disk??? That sounds very strange. I certainly understand commercial movies etc, but for our own home data files and backups, why would that be necessary? There is something here I am missing obviously.

---

### Post by gordintoronto on 2011-06-08
You're right, if you burn some data on a blu-ray disk, it should not be affected by the encryption of commercial blu-ray movies.

---

### Post by Flyers2391 on 2011-06-10
Yeah, it looks like you should be able to with a blu-ray drive:

[https://help.ubuntu.com/community/CdDvd/Burning#Burning%20a%20DVD%20or%20Blu-Ray%20Disc](https://help.ubuntu.com/community/CdDvd/Burning#Burning%20a%20DVD%20or%20Blu-Ray%20Disc)

I'm still having issues with my own DVDs, even after following instructions, but if you are just interested in writing files & backing up data it appears you should be set.

---

