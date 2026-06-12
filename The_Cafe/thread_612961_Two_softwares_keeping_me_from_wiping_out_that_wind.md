---
title: "Two softwares keeping me from wiping out that windows partition…"
date: 2007-11-14
forum: The Cafe
---

### Post by cyneuron on 2007-11-14
Hello everyone&#8230;.

I am a long time Ubuntu user, and I am very happy with the computing experience I get on my Ubuntu Gutsy with that its stability, beauty of Compiz Fusion, no tension of viruses, and lots of other things awesome Linux has inherent in it. . I have almost all the softwares I will ever need except the two which i need most of time.

These two softwares are keeping me from wiping out that Windows Partition from my hard disk.

These are :


1. A Streaming Video Downloader

This software is really important for me. I download a lot of educational videos from websites like University of Berkeley Webcasts, MIT World Videos, Research Channel Lectures, and other streaming videos, to see offline. These videos are streamed in Real Video format.

I use Net Transport on Windows XP, which is really excellent software for downloading these streaming videos. It downloads these streaming videos just like a Download Manager like Flashget downloads normal files from web.

In Linux there is no equivalent software for this purpose. There is a way described to download these videos from command line using mplayer :

mplayer -dumpstream "<url>" -dumpfile <file>


(Taken from this webpage : [Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_Rip_Streams_With_MPlayer") )

This method works. But this is really tedious and unreliable process. You can&#8217;t waste your time in writing the whole command every time you want to download a video. And what if you want to pause it and resume sometime later. You can&#8217;t do this. And you can&#8217;t download lots of video at one time by this method.

I have tried to install Net Transport in Ubuntu using Wine, but it doesn't even starts up in Wine, or in other words it doesn't work in Wine.

I think someone should/can easily make a GUI app which may download streaming real video using this mplayer command just like Net Transport and other Windows software do.

And i think, lots of people must be in need of such a software, seeing the increasing trend of online educational lectures being made available on Internet by so many Universities across world. 


2.	A Good Download Accelerator / Manager.

For the problem I have faced regarding this I had made a thread here :

[Why can't there be a good Download Manager/Accelerator For Ubuntu ?]("http://ubuntuforums.org/showthread.php?p=3757976#post3757976")

&#8220;I wanted to download few heavy videos (like 250 MB) from Google video. for this i needed a download manager.

I could not use:

1. Firefox own Download Manager as i needed to pause and resume downloads, sometime even after closing Firefox or restarting Ubuntu.

2. DownThemAll for same reasons as above...

I downloaded Gwget from Ubuntu repos and installed flashgot extension in Firefox.

Now when i sent download link to Gwget via flashget, Gwget didn't process the link and showed error "Can't write file" while even the firefox download manager and DownThemAll, both were able to download the .mp4 file.

Story doesn't end here....

I started looking for other download manager.

Aria Download Manager : There were no buttons when i opened the program. I don't know why. But the same problem was there with Aria in Ubuntu Feisty as well.

D4X: same problem as with Gwget...

wxDownloadFast : not available in Ubuntu repo.....Gutsy package not available, neither on getdeb.net, nor on its official website....feisty and edgy package are unstable when installed in Gutsy....though it was the only one which could start the download....

Kget: I am on GNOME (most of us are ).... i didn't want to install loads of KDE libs on my Ubuntu GNOME system....

Finally i had to boot into Windows XP and download files using Flashget....

I a really frustrated with this experience....though it hasn't shaken my belief in Ubuntu....

I am surprised as if why isn't there a good download manager/accelerator available in Ubuntu ?

Flashget is such an awesome Download Manager/Accelerator in Windows. It is free. so why can't they or someone else port it to Linux.

I have filed a bug on Gwget website about this odd problem of Gwget being not able to process the download link from Google video.&#8221;

Till the time I get these two software on my Ubuntu, i will   have to bear with Windows XP&#8230;..

God, I want to be completely Ubuntufied&#8230;.Two more apps please&#8230;&#8230;is anybody listening&#8230;..

---

### Post by Rinzwind on 2007-11-14
Isn't WINE an option?

I've never needed any of these 2 (I generally download with torrents).
But you are right. I've yet to see good alternatives :) :)

---

### Post by cyneuron on 2007-11-14
> **Rinzwind said:**
> Isn't WINE an option?

I've never needed any of these 2 (I generally download with torrents).
But you are right. I've yet to see good alternatives :) :)

I edited my post later. Have tried with Wine. Net Transport doesn't work under Wine....

---

### Post by DoctorMO on 2007-11-14
Sounds like you need some development doing, question though: why don't you pay for it to be done for you? a firefox extension shouldn't cost that much.

---

