---
title: "Linux distro downloads"
date: 2011-12-16
forum: The Cafe
---

### Post by millerthegorilla on 2011-12-16
Hey. I have a quick question to ask. I am a dev/programmer and have been so for many years.
I have noticed over the last two to three years of my Linux induction period (after twenty years exclusively with windows) that often distro downloads, whether by torrent or direct download, fail. I most often checksum the isos, but not everyone provides checksum facilities. Ubuntu is one of them (although obtaining a checksum undoubtedly isn't a great problem I don't suppose the average noob desktop user would go to the trouble).
Many of the largest coporate entities on the web have begun recently to introduce 'downloaders'. These small programs download, open a secure connection to the server and then download (with the ability to pause and successfully resume the download) and then check the iso before reporting it as having successfully downloaded.
I greatly suspect that the flawed download problem is not only due to network errors and interference but also due to man in the middle type attacks that are targeted at linux distros.
Why? Simply because I could do it. If it can be done and in doing so offers a commercial advantage, then it will be done.
Linux has most often been associated, quite incorrectly in my opinion, by certain sections of the community at large with a sort of communist ethic. Whether or not this is the case does not matter in any way in reality but unfortunately the existence of this public profile provides the possibility that negative advertising strategies (such as corrupted downloads etc) will be employed.
We are currently living in a world which is beset by financial difficulties. In these times when the economy is overstretched, bullying occurs and an extremist ethic flourishes by necessity to encourage that bullying to exist as a defence strategy. Everyone, currently, is attempting to put the blame on everyone else for the shortfalls in the economy. 
The opensource community have something enormously important to offer the global economy currently. The goal and aspiration of a functioning and healthy economy is to provide an acceptable quality of life for the inviduals therein. Since the early 1990s, the effects of the software industry, and the sudden emergence of a product that is not bound to any other producing part of the economy in any way has meant that the economy has continuously failed us to the extent that many recessions and collapses have occurred. (there are a few other reasons - a lessened ability to predict successfully the outcomes of investment due to the the increased speed of information transmission being one of them)
We would most likely have gone to war many years ago under the same circumstances, but offsetting the conditions we are facing are several mitigating factors. The memory of the second world war and nuclear weapons are small things in comparison to the software and media piracy industry for example, which provide quality of life at nil cost and thereby keep us satisfied to a certain extent.
 
Open source software offers one (although not the only solution) to the software problem (a different type of taxation system is another). All of these points may not be entirely obvious to individuals facing the daily necessity of living up to their reponsibilities in having to satisfy their shareholders expectations or their sales-targets etc. They are not always the most intelligent of people (they do not always have the time to be so).
 
I hope that someone may read my message in a bottle, and consider these points. A distro downloader would be a good idea. Also, a windows open source community initiative would be top as well!
 
Cheers and seasons greetings,
 
James
 
ps - sorry if this isn't light hearted enough.

---

### Post by 3rdalbum on 2011-12-16
TL;DR. Sorry. Your post seemed to get a bit off-topic.

Torrents should not fail unless people stop seeding them.

Every chunk of a torrent is hashed and compared against the hash that the .torrent file stores. If a "man in the middle" attack occured to try and corrupt your download, the torrent program would realise that the chunk was incorrect and try and download it again. After a few failed attempts at that chunk, the torrent client tries downloading from a different seeder.

A torrent download will only fail if, out of everybody still on the torrent, there are one or more chunks that nobody has. Or of course if nobody else is still on the torrent.

---

### Post by coldraven on 2011-12-16
As regards downloads I just go here [http://releases.ubuntu.com/](http://releases.ubuntu.com/) and get the torrent, then I check the md5sum. I have never had a problem and the downloads are fast.

Tip: If you are looking at a checksum on a web-page with Firefox. In a terminal run ```
md5sum ~/Downloads/name_of_download
```then copy the result with Ctrl+Shift+C
then in Firefox press / followed by Ctrl+V, if the checksum matches it will highlight.

Unfortunately I do not think that we can do much to change the way that the world is heading. There are too many greedy people who don't give a hoot about anyone but themselves.
We can only have faith that a better world will emerge from the ashes of this one. I could go on but I'm sure that this forum is not the place to do so.

---

### Post by HermanAB on 2011-12-16
I dunno - I live in a place with quite terrible internet connectivity, yet I have no trouble downloading anything I want from mirrors.kernel.org.

---

### Post by KiwiNZ on 2011-12-16
> **millerthegorilla said:**
> Hey. I have a quick question to ask. I am a dev/programmer and have been so for many years.
I have noticed over the last two to three years of my Linux induction period (after twenty years exclusively with windows) that often distro downloads, whether by torrent or direct download, fail. I most often checksum the isos, but not everyone provides checksum facilities. Ubuntu is one of them (although obtaining a checksum undoubtedly isn't a great problem I don't suppose the average noob desktop user would go to the trouble).
Many of the largest coporate entities on the web have begun recently to introduce 'downloaders'. These small programs download, open a secure connection to the server and then download (with the ability to pause and successfully resume the download) and then check the iso before reporting it as having successfully downloaded.
I greatly suspect that the flawed download problem is not only due to network errors and interference but also due to man in the middle type attacks that are targeted at linux distros.
Why? Simply because I could do it. If it can be done and in doing so offers a commercial advantage, then it will be done.
Linux has most often been associated, quite incorrectly in my opinion, by certain sections of the community at large with a sort of communist ethic. Whether or not this is the case does not matter in any way in reality but unfortunately the existence of this public profile provides the possibility that negative advertising strategies (such as corrupted downloads etc) will be employed.
We are currently living in a world which is beset by financial difficulties. In these times when the economy is overstretched, bullying occurs and an extremist ethic flourishes by necessity to encourage that bullying to exist as a defence strategy. Everyone, currently, is attempting to put the blame on everyone else for the shortfalls in the economy. 
The opensource community have something enormously important to offer the global economy currently. The goal and aspiration of a functioning and healthy economy is to provide an acceptable quality of life for the inviduals therein. Since the early 1990s, the effects of the software industry, and the sudden emergence of a product that is not bound to any other producing part of the economy in any way has meant that the economy has continuously failed us to the extent that many recessions and collapses have occurred. (there are a few other reasons - a lessened ability to predict successfully the outcomes of investment due to the the increased speed of information transmission being one of them)
We would most likely have gone to war many years ago under the same circumstances, but offsetting the conditions we are facing are several mitigating factors. The memory of the second world war and nuclear weapons are small things in comparison to the software and media piracy industry for example, which provide quality of life at nil cost and thereby keep us satisfied to a certain extent.
 
Open source software offers one (although not the only solution) to the software problem (a different type of taxation system is another). All of these points may not be entirely obvious to individuals facing the daily necessity of living up to their reponsibilities in having to satisfy their shareholders expectations or their sales-targets etc. They are not always the most intelligent of people (they do not always have the time to be so).
 
I hope that someone may read my message in a bottle, and consider these points. A distro downloader would be a good idea. Also, a windows open source community initiative would be top as well!
 
Cheers and seasons greetings,
 
James
 
ps - sorry if this isn't light hearted enough.

A download gone wrong is simply that.

A linux distro is just an OS, it is not the great cure all the world has sought for generation after generation.

---

### Post by wolfen69 on 2011-12-16
Whenever possible I try to get iso's from torrents. I never check the md5's of torrents because of the built-in checking capabilities. I don't really see the point of most of the original post though.

---

### Post by haqking on 2011-12-16
I have been downloading for 20 + years.

Whatever the filetype or source if a download is corrupt then you try it again.

I have never had a single instance of a corrupt linux download torrent or otherwise.

Stop using your 50 ft telephone extension cable and acoustic coupler for your internet connection and try again ;-)

As for the rest of it...well umm ?

---

### Post by Paqman on 2011-12-16
Torrents are bombproof. Big distros like Ubuntu are well-seeded, and as mentioned above the process ensures that you get a good download.

---

### Post by oldsoundguy on 2011-12-16
Never a problem with a torrent .. HOWEVER .. burning the ISO at anything faster than the slowest speed possible on my burner has led to coasters.  And I always verify the burn.

---

### Post by BrokenKingpin on 2011-12-16
> **haqking said:**
> 
I have never had a single instance of a corrupt linux download torrent or otherwise.

Same, even when I was on dial-up way back in the day.

---

### Post by drawkcab on 2011-12-16
Torrents are the way to go.  Every so often I get a corrupted image from directly downloading it.

---

### Post by Plumtreed on 2011-12-16
OP sounds like 'classic' troll:popcorn:

---

