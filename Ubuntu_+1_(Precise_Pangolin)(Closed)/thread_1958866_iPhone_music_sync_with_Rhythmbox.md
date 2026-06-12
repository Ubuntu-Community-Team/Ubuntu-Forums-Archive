---
title: "iPhone music sync with Rhythmbox"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by grj23 on 2012-04-15
Hi

I started a link in the multimedia forum here:
[Multimedia forum link]("http://ubuntuforums.org/showthread.php?t=1957227")
and someone suggested that I should post it here, so here it is.


I feel like this should work, but somehow for me it never has, and I don't understand what I'm doing wrong.

I would like to copy music from my library (Ubuntu 12.04 Beta) onto my iPhone 4. Here's what happens (and has been happening for about 2 years (with 10.10), and is the only reason I keep a windows partition somewhere in the house):
1. I plug the iPhone in with USB
2. It detects it fine, noting that there are photos and music on the device and offering to open up the relevant bits.
3. On the photos front it's fine, and it also opens up showing the file structure.
4. I open Rhythmbox, and my iPhone shows there, all present and correct
5. I ask it to sync, and it shows me how the iPhone memory will be before and after (I check the library box)
6. It then spends some time copying the music across. In the end, the iPhone in Rhythmbox has all the songs in it and seems to have worked fine.
7. When I go to the iPhone, under Music it says "No Content".
8. In general the memory space is then gone and undeleteable until I restore the whole thing using iTunes.

The phones are not jail-broken. I've tried this on iPhone 3 and 4 and various different iOS. I've used 10.10 & now 12.04. 
I tried to follow the instructions 
[here]("http://askubuntu.com/questions/78535/how-to-install-libimobiledevice") but the repository is not found:
Code:
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
(ditto with maverick).  However, it seems that libimobiledevice2 is installed and up-to-date, so I don't think this is the issue.

Most of the (surprisingly few) queries about this have someone point to this [supposedly up-to-date wiki]("https://help.ubuntu.com/community/PortableDevices/iPhone") which clearly hasn't been updated in two years and does not deal with this problem.

The thing I don't get is that the phone has been freshly installed, the ubuntu has been freshly installed, everything appears to work fine, and then something at the last second just fails.

Ideally I could get it to work in the manner described above, but with a happier final step. What should I be trying? Should I push to get the latest libimobiledevice (is there a repository for that)? Should I go for the jail-break route (hopefully not, and anyway, I think it might not be possible just yet because I updated one of the phones to 5.1 or whatever the latest thing is, and in the other forum, someone with a jail broken phone was similarly unsuccessful)?

It was exactly the same for my wife's iPhone 4 with 4.1 (I think), and for mine on 4.0 (before I updated it).

I have this image of millions of happy iPhone-Ubuntu users out there who don't get this problem? Is that the reason for the lack of complaints on this issue, or is it that most people don't even bother to try the non-windoze/mac route?  

Really would appreciate any advice and or links to anything helpful.

G

So I thought I'd add a few more details. 
Firstly, my entire collection is mp3 (thanks to the wonder of Sound Converter).

Secondly I saw some links suggesting getting rid of a file called gconf.xml in a hidden director in your home. 
That location doesn't exist in 12.04, and the file exists is a similar location but removing it makes no difference. A [blog]("http://mildred-of-midgard.dreamwidth.org/59465.html") found some other way of fiddling with this gconf.xml, but similar fiddling did not work for me. Although it was done in a state of complete ignorance, so if you're better at this stuff please have a go and post back!

Lastly, my iPhone is showing several GB of 'other' (read corrupt music) in Rhythmbox and in iTunes (on my work computer where I don't have any music and it's not the assigned computer, so I can't do much with it). 

Does anyone else share this experience, or know of a cunning step that I'm missing?

Thanks

---

### Post by neu5eeCh on 2012-04-15
One word: NO.

You can interpret that however you want. Even on the windows side, I get the same error when using Mokeys Audio (which is what I use to manage my library). At the end of the day, I have to point iTunes to my folders and use iTunes as the go-between. You can thank Steve-effing-Jobs for this. He used to have (and probably still has) sleepless nights at the thought that someone was escaping the apple-sphere. He had his devs deliberately sabotage all efforts to bypass ITunes. Why? Because Jobs wanted to sell you stuff. They're not selling you an iPod, they're selling you a product that will get you into their store and any and all efforts to bypass this store will be dealt with by whatever means necessary. 

So, just think of it as the Hunger Games. Once you're in Apple's arena, you can't get out.

---

### Post by grj23 on 2012-04-15
Thanks for that. Should we update the wiki to reflect this. It's a little deceptive right now and many man hours could be saved for people on the future to just state this up front. 

I'd be happy to have iTunes in Ubuntu. Ah, apple. The flowers hide the barbed wire well.

---

### Post by Hoverboy on 2012-04-17
It actually is possible, but it's a somewhat tedious process. Essentially the issue is that when you sync an idevice all of your files are renamed into meaningless combinations of letters and then reorganized arbitrarily into folders. iTunes then writes the information about what you've synced to a database that can be read by your iPod app. Apple changes the format and structure of the database with every new hardware tier they put out, which is why the iPhone 4 is still unsupported but most other idevices are.

Anyway, that being said, what you can do is "trick" the iPhone 4 into using the same database as the last generation, which then enables it to be synced it pretty much every popular Linux media player. I never tried it with Rhythmbox, but it worked in Banshee and Clementine.

I figured out how to do it from reading these two posts, primarily the second one, the first one is just sort of an introduction to what he's trying to do. (literally, only two informative posts I found out of what must have been thousands): 

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

These posts are pretty old, he's actually talking about getting the iPhone 3 to work when there was only iPhone 2 support, but very little has changed, at least as of when i did this last fall on iOS 4.1. It's possible things have changed since the release of iOS 5, but I tend to think it won't matter. Either way, hope it helps you out!

Edit: There's actually a third post dealing specifically with the iPhone 4: [http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/](http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/)

---

