---
title: "apt-get-torrent"
date: 2006-05-02
forum: The Cafe
---

### Post by brentoboy on 2006-05-02
I have a crazy idea:  use bittorrent for downloading debs through apt-get

it would have to be optional, becuase it might not be advantageous in some cases, but it would really help the community becuase durring the major upgrade  days, there would be lots of seeds for download.

instead of apt-get, you could just call apt-get-torrent update (or whatever)
inside /etc/apt/ you would have a bittorrent.conf file that controls the torrent settings.

you could configure synaptic to use torrents or "normal" get.

then, the server just needs to have a bunch of torrent files, even the index of what is available on the server (the stuff you download when you call apt-get update) would be torrents.

with something like this, the community gives back to itself, and we share the cost of the network servers offering the repositores, without having to donate $ all the time in order to pay our dues.

people with nice internet connections could configure their apt-torrent settings to save the debs and keep offering them back to the community after they are done downloading.

anyway, it was a crazy idea, so I figured I'd share.
what do you guys think?

---

### Post by ashrack on 2006-05-02
good idea!

---

### Post by Master Shake on 2006-05-02
Not a bad idea at all.

---

### Post by cbudden on 2006-05-02
Quite a good idea, but what about when people clean out their caches?  Or do you think people would just not do that? Good Idea though :)

---

### Post by Engnome on 2006-05-02
Not bad at all. But maybe share would be better. Shares first advatage is that it is anonymous. Not much use here maybe but to accomplish this it uses a system where everyone has a cahce, (atleast 1GB)  that they share, if someone requests a file in your cache you send it to them.  The cache is encrypted in some weird way so not even u know whats in there (not of use here either) but the idea with a share might be good. Imagine everyone had a cache with .debs decided by some main server. Wich .debs one would have would be decided by how many there are who wants it.

---

### Post by brentoboy on 2006-05-02
Engnome,

i'm not familiar with share as you describe it.

isnt that what bittorrent does, except, torrent is more chaotic, it isnt centrally managed, so if one node is down, there isnt a bottleneck of people waiting for what they should be sharing.

whatever is in highest demand is available from everyone who hasnt cleared it from their apt cache (of course, you would have settings that let you limit how many people can leach off of you at a time)

I bet my upgrade would come down at 500 kbps instead of 125 kbps if we used torrents, and I wouldnt feel like I was sucking the ubuntu server dry, instead I would feel like I was helping all those other people who are pulling it down that fast too.

---

### Post by brentoboy on 2006-05-02
there could even be a maintenance program that manages the files offered by your torrent cache based on what you most recenly downloaded, and what is getting the most requests.

you set the size of your cache, and it just manages what would be best for the community.  and for people who feal especially benevolent towward a particular package, they could set it up to always keep it in the cache.

---

### Post by ashrack on 2006-05-02
[QUOTE=brentoboy]Engnome,
I bet my upgrade would come down at 500 kbps instead of 125 kbps if we used torrents, and I wouldnt feel like I was sucking the ubuntu server dry, instead I would feel like I was helping all those other people who are pulling it down that fast too.[/QUOTE]
I know exactly how U feel! Thats way I also DL UBUNTU images only from torrents and seed to about 500% on my poor connectoin 1024/256

---

### Post by Turgon on 2006-05-02
Good idea. It might get a little unstable, but that should be a big problem since the main repos still will be open.

---

### Post by Kvark on 2006-05-02
If this is done and the repository servers seed the torrents then there is no point in keeping the normal download method because torrent would never be slower then normal download. The worst case with torrent would be that no one else then the servers seeds the package you want so you would download from the servers only which is exactly the same as a normal download.

Since there is no need to keep the normal download method. Just change apt-get, aptitude and whatever else accesses the repositories to use a torrent program instead of wget or whatever they currently use to download packages.

Make a part of the package manager run in the background to seed from the cache and add options in synaptic to limit how much bandwidth (bytes or share ratio per day/week/month depending on what the user wants) it uses to seed. I think a fair default would be "max 1:1 share ratio". With a lower default average users will be leechers without knowing it. While a higher default could be seen as exploiting average users without their knowledge.

---

### Post by ashrack on 2006-05-02
KVARK
I believe that both methods would than be required because not all ppl can have TORRENT because of their FW or ROUTER... I believe this is also the reason why when U DL UBUNTU images U have torrent and normal DL link option

---

### Post by brentoboy on 2006-05-02
I'm for what kvark is saying, but my background in software release backup plans says that there is no reason to completely dismantle the existing setup until the new one shows it is superior in reality and not just theory.

enable the old way from the command line like this...

apt-get -old_way install packagename
so that a guy with torrent firewall issues could still get things on the http port etc.

but I agree, it should completely take over.
the server woud maintain an active seed for every package.
the popular packages would get the performance boost from the community.

---

### Post by brentoboy on 2006-05-02
[QUOTE=ashrack]KVARK
I believe that both methods would than be required because not all ppl can have TORRENT because of their FW or ROUTER... I believe this is also the reason why when U DL UBUNTU images U have torrent and normal DL link option[/QUOTE]

and I thought that the http download option was just for those windows users who are too scared to setup a torrent downloader, because it might be "complicated." and they might mess up "their internet".
 :-)

---

### Post by Kvark on 2006-05-02
[QUOTE=brentoboy]I'm for what kvark is saying, but my background in software release backup plans says that there is no reason to completely dismantle the existing setup until the new one shows it is superior in reality and not just theory.

enable the old way from the command line like this...

apt-get -old_way install packagename
so that a guy with torrent firewall issues could still get things on the http port etc.

but I agree, it should completely take over.
the server woud maintain an active seed for every package.
the popular packages would get the performance boost from the community.[/QUOTE]
Good point. Perhaps that should be a default fallback. If it fails to use the torrent then it automatically tries the old way too before giving up and throwing an error.

---

### Post by brentoboy on 2006-05-02
ok, to sum up:

We want apt-get (and all apt based getting) to use bit torrent technology instead of just wget style downloading.

This could be manually disabled using a flag in the apt-get statement.
It would automatically use the old way if the torrent style download generated an error, or timed out (firewall issues)
It could be disabled in the /etc/apt/torrent.conf file as well so that wget technology would be used by default instead of as a fallback method.

Each PC would maintain a cache of seeds for programs they recently downloaded, settings for the size of the cache, how much bandwidth should be used for uploading, and other bit torrent settings would be in /etc/apt/torrent.conf

The ubuntu servers would still have all the downloads available (so that the old way would still work)
those downloads would all be seeds, so there would never be a package that wouldn’t have at least one active seed.
Even the current package lists for apt-get update would be torrent downloads.

----
This would be advantageous to users because the downloads would be faster.
It would be advantageous to the ubuntu project, because the cost of the server bandwidth would be lower.
and it would be advantageous to the community because during new release periods, the downloads would be faster, not slower, thus giving newbies a better overall experience when they try ubuntu for the first time after a major release.

It also lets us tightwad users share the wealth by sharing our bandwidth instead of sending in cash, seems less taxing, but still is a valuable contribution.
---

any more ideas before I run off to development threads, and post a request?

---

### Post by christhemonkey on 2006-05-02
If you do get this done and everyone changes to it, it would be very nice if the .deb files were all still on the server for those of us without internet connections/torrent programs.

---

### Post by brentoboy on 2006-05-02
[QUOTE=christhemonkey]...it would be very nice if the .deb files were all still on the server...[/QUOTE]

that is what I mean by the "wget" way of doing things.
wget is the command line app for grabbing a file from an online server using http or ftp like apt-get does today.

I agree, you cant ruin a good thing just for "progress"

---

### Post by Engnome on 2006-05-02
Its not odd you havent heard about share. (almost only japanese ppl there) Although we all just might in the future when the record and movie industry has managed to buy a law to make all p2p stuff illegal. (p2p = warez right? ;) )   

Anyway I think making some solution to seed 50+ packages can be really tricky. How about some way to start seed when the file is requested? Or we might need to completely transfer that to the server, it tells you what to seed and when to meet the demand. 

Also the cache has to contain package that u dont have any use for (like share) so that even the most exotic packages are always available.

---

### Post by jobezone on 2006-05-02
Checkout the apt-torrent project :) at [http://sianka.free.fr/](http://sianka.free.fr/). It's GPL software. This page, [http://sianka.free.fr/documentation.html](http://sianka.free.fr/documentation.html), explains how it works.
Good luck with the project!

---

### Post by brentoboy on 2006-05-02
the website refured above by jobezone says that he has 1000 of the *largest* deb files for debian.  Is that just because those are the slow files to download, or--does anyone know--is wget faster than bittorrent for small files?


it looks like you would also have to use a apt-torrent daemon on the local pc, it would manage your cache, and make it available even if you werent using aptitude at any given time.  It could also listen for requested packages, and manage which ones you keep in your seeding cache.  It would run in the background like azureus when it is minimized.

which brings up a good point, is there already a client-side torrent daemon that keeps downloading and uploading torrents, a daemon as opposed to just an app (like azureus) that has to be started by the user?

---

### Post by aktiwers on 2006-05-02
This wouldnt be good for everyone.

Take me for example.
My ISP has Packed Shaped our connection, so that no P2P traffic can run.  So if  apt-get got replaced with .torrents,  I would be pretty screwed!

But a real cool idea!

---

### Post by brentoboy on 2006-05-02
it seems like it would need to be a question in the installer:  do you want to use traditional apt-get package download method or would you like to enable Apt-Torrent for downloading packages.  With a little bit of description as to what the advantages of each is.

---

### Post by Kvark on 2006-05-02
[QUOTE=brentoboy]the website refured above by jobezone says that he has 1000 of the *largest* deb files for debian.  Is that just because those are the slow files to download, or--does anyone know--is wget faster than bittorrent for small files?[/QUOTE]
Maybe it is necessary to limit the total number of files. To make a server seed 17k torrents it would need a program that is optimized for reading and sending random parts of random files when those parts are requested. Like an FTP server but that only sends small parts at a time, if you have something like that then the number of files doesn't matter much. But I have a feeling that if you run a normal torrent client like Azureus on the servers then you can't make them seed 17k torrents. Just guessing here, I haven't actually tried.

[QUOTE=brentoboy]it seems like it would need to be a question in the installer:  do you want to use traditional apt-get package download method or would you like to enable Apt-Torrent for downloading packages.  With a little bit of description as to what the advantages of each is.[/QUOTE]
Or ask that question when the fallback I mentioned has been used:
"Install successful! ...but the torrent download timed out so normal download was used instead. If you know that you for some reason can not download torrents then disable the torrent download option to avoid waiting for it to time out in the future. But if you think it might be a temporary problem leave the option enabled to benefit from the faster torrent downloads later when the temporary problem is solved.
[disable torrent downloads] [leave it enabled] [leave it on and don't ask again]"

---

### Post by Virogenesis on 2006-05-02
problem with torrents is that they hate routers the amout of times my router needs resetting because of bt isn't even funny.
Another thing is how would we cope with a DDoS?

---

### Post by brentoboy on 2006-05-02
[QUOTE=Virogenesis]a DDoS?[/QUOTE]

What's that?

---

### Post by Kvark on 2006-05-02
[QUOTE=Virogenesis]problem with torrents is that they hate routers the amout of times my router needs resetting because of bt isn't even funny.
Another thing is how would we cope with a DDoS?[/QUOTE]
There must be some way to configure a router so it doesn't have any problems with BT, it can't be impossible.

DDoS, hmm... Download and cache a .tar.gz with all the torrent files from the server with apt-get update. Then if the servers are DDoSed or entirely down for whatever reason use the cached torrents from the last successful apt-get update and download from other users who are seeding. But normal downloads still wouldn't work if the servers are down.
[QUOTE=brentoboy]What's that?[/QUOTE]
If you can't conquer the city then siege it. A Distributed Denial of Service attack is when a cracker infects hundreds or thousands of computers with a trojan and tells them all to keep hammering a server with requests. The server is still secure but it's incomming bandwidth is maxed out so no legit requests can reach it through the traffic jam.

---

### Post by brentoboy on 2006-05-02
[QUOTE=Kvark]Maybe it is necessary to limit the total number of files. To make a server seed 17k torrents it would need a program that is optimized for reading and sending random parts of random files when those parts are requested. [/QUOTE]

Certainly there are torrent servers out there that are designed to seed lots of files at the same time.  If not, it doesnt matter, becuase once you have the main ubuntu repository server(s) offering just .torrent packages, you can use as many servers as you want to share the load, and people dont have to add all the seperate servers to thier sources list.  17 servers ought to be able to handle it, and certianly there is a torrent server daemon out there that can handle seeding 1000 torrents.  (I have no idea what I am talking about here, so someone pipe in and correct me--please)

[QUOTE=Kvark]Or ask that question when the fallback I mentioned has been used:
"Install successful! ...but the torrent download timed out so normal download was used instead. If you know that you for some reason can not download torrents then disable the torrent download option to avoid waiting for it to time out in the future. But if you think it might be a temporary problem leave the option enabled to benefit from the faster torrent downloads later when the temporary problem is solved.
[disable torrent downloads] [leave it enabled] [leave it on and don't ask again][/QUOTE]

I agree that asking too many questions complicates the install, especially when the answer should be a no-brainer, So I would hate to ask the question up front, if most everyone would just say "yes" anyway.  But I can see that for those folks who have BT issues, (like Virogenesis's router) they need an option to avoid it altogether.  Virog... he would hate it because BT would "work" well enough that the PC would keep trying it, and he would get frustrated before it gave up.  So, maybe we could offer a boot param for the install cd that lets them pass a "notorrents" if they know it will cause problems.  and then present your options after the fact--if it encountered a problem.

---

### Post by htinn on 2006-05-02
There are 2 major issues with apt-torrent as I see it:

1) The client would have to support DHT or you would need a really nice tracker to keep track of all those packages. The tracker itself would consume a ton of bandwidth.

2) The packages themselves are too small. The torrent's tit-for-tat method of sharing will not work properly unless the packages are much larger than the standard deb packages. If you package a large group of them together, you're really just becoming redundant.

---

### Post by banjobacon on 2006-05-02
[QUOTE=brentoboy]I have a crazy idea:  use bittorrent for downloading debs through apt-get[/QUOTE]

Crazy idea? So you're saying that this thread is in no way related to the recent [Apple rumor](http://macosrumors.com/20060429A.php) featured on Slashdot and Digg?

---

### Post by brentoboy on 2006-05-02
[QUOTE=htinn]There are 2 major issues with apt-torrent as I see it:

1) The client would have to support DHT or you would need a really nice tracker to keep track of all those packages. The tracker itself would consume a ton of bandwidth.

2) The packages themselves are too small. The torrent's tit-for-tat method of sharing will not work properly unless the packages are much larger than the standard deb packages. If you package a large group of them together, you're really just becoming redundant.[/QUOTE]


what is DHT?

and, what is a "good" size for a torrent?  at what size does it become too small to be practical?
----
maybe the answer is for the apt repository to have either a .deb or a .torrent for each file, (it would have a deb for all of them) for those that had a .torrent, you could configure apt to retrieve it via torrent.

---

### Post by htinn on 2006-05-02
DHT basically gives you a way to run without a tracker. See this for more info:

[http://en.wikipedia.org/wiki/Distributed_hash_table](http://en.wikipedia.org/wiki/Distributed_hash_table)

A good size for a torrent is about 700 MB. :p

EDIT: To answer your question about small torrents, I think the problem is basically more psychological than technical. The problem with a 5 MB file in bittorrent is that it may take only about 2 minutes for someone with a good connection to download. At that point, they may decide to stop sharing. The thing that makes bittorrent succeed is the fact that you mostly leave it running unattended. If you did implement apt-torrent, it would have to factor this in, as well.

---

### Post by brentoboy on 2006-05-02
[QUOTE=banjobacon]Crazy idea? So you're saying that this thread is in no way related to the recent [Apple rumor](http://macosrumors.com/20060429A.php) featured on Slashdot and Digg?[/QUOTE]

no, when I first posted, I thought it was a genuinly new idea (since then I've been shown several ref's)

I was waiting for 294 packages to download after a dist-upgrade, and it occured to me that I could squeze it all in 5 times faster if I had it downloading at the rate my torrents come down.  So, I posted the idea

---

### Post by banjobacon on 2006-05-02
[QUOTE=htinn]DHT basically gives you a way to run without a tracker. See this for more info:

[http://en.wikipedia.org/wiki/Distributed_hash_table](http://en.wikipedia.org/wiki/Distributed_hash_table)

A good size for a torrent is about 700 MB. :p

EDIT: To answer your question about small torrents, I think the problem is basically more psychological than technical. The problem with a 5 MB file in bittorrent is that it may take only about 2 minutes for someone with a good connection to download. At that point, they may decide to stop sharing. The thing that makes bittorrent succeed is the fact that you mostly leave it running unattended. If you did implement apt-torrent, it would have to factor this in, as well.[/QUOTE]
Packages would probably be seeded in the background, not just when people run apt-get.

A possible problem with file sizes, though, is that small packages might not benefit from increased download speeds. In my experience, it generally takes a few minutes for a torrent download to reach its top speed. Most packages are not very large and would probably not ever reach significant download speeds. Perhaps this will result in longer download times.

Or maybe I'm totally wrong.

---

### Post by augied on 2006-05-02
Maybe torrents should only be used for files larger than 5-10MB.  Then only the downloads that would benefit from bittorrent would use bittorrent.

---

### Post by brentoboy on 2006-05-02
[QUOTE=augied]Maybe torrents should only be used for files larger than 5-10MB.  Then only the downloads that would benefit from bittorrent would use bittorrent.[/QUOTE]

I think this ends up being the key to the whole thing.
Apt needs to be smart enough to know (either becuase the server tells it, or becuase it has a setting that sais "files smaller than x just download the old way")

apt would need to be hybrid, you would just call apt-get install, and watch stuff come down like you do already, except it would use torrents for some of them.
--
there are things like the kernel that are large enough to use a torrent for, and the sun java runtime, and the ... well, lots of things.

maybe we could have torrents for the ubuntu-minimal ubuntu-standard ubuntu-desktop each with all their dependancies.  then, when they recompile a new kernel, and all the xorg drivers, and all the base level stuff, we could get the benefit of a torrent for the whole metapackage.

an intelligent, hybrid solution is the only way to get the full benefit of the idea, it would be tweaked at the server end as time went on to find the most efficient way to distribute the bulk of the files.

---

### Post by TheCaptain on 2006-05-02
A helluvalot of files are very small, for anyone who doesn't run a 2400baud modem this would be a LOT slower by simply having seek times.

It's a nice idea if the current FTP servers ever get ovarloaded, but using a failover from your nearest is so far the fastest method i'm aware of.

(kind of like how i get a solid 2M/s from my local download mirror but only 100k from bittorrent, if that, when i download an Ubuntu torrent)

---

### Post by brentoboy on 2006-05-02
[QUOTE=htinn] The thing that makes bittorrent succeed is the fact that you mostly leave it running unattended. If you did implement apt-torrent, it would have to factor this in, as well.[/QUOTE]

yeah you definitly need a background daemon that constantly seeds what is available, based on the percentage of incomming requests for each package.  But certanily this sort of background torrent daemon exists already.  we would have to configure it to only take a small sliver of upload speed from each person, but if everyone had a handful of active seeds trickling out into cyberspace then we would really beef things up

I also noticed that it takes 15+ seconds to get any given torrent to really get up to speed, but if there are lots of available seeds, this comes down quickly.  We would just have to find the right balance to start seeding for several torrents at once in order to get the overall effect to overcome the slow start issue  (or I might just be crazy)

---

### Post by TheCaptain on 2006-05-02
[QUOTE=augied]Maybe torrents should only be used for files larger than 5-10MB.  Then only the downloads that would benefit from bittorrent would use bittorrent.[/QUOTE]

And then you still had to change servers, look in the tracker, connect to and if your transfer is 100mbit like mine it would be way slower.

Static transfer works just fine and there is a multitude of mirrors available.

Would you open any file from any e-mail? well that's kind of what you are asking people to do here, download from non-verified sources.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]
(kind of like how i get a solid 2M/s from my local download mirror but only 100k from bittorrent, if that, when i download an Ubuntu torrent)[/QUOTE]

how "local" is that mirror of yours?
when i torrent a really large file (especially a linux cd from a distro as popular as ubuntu) I get it at 500+kbps

download from a server, even a fast server, I dont think I have ever seen faster than 250kbps.  is that local server in the same building?  :-)

just kidding

but you are right, there is certainly a bandwidth that is not optimal for a torrent download.  but even on my dad's dialup, torrents get up to 30+k if you let them get cooking, and other downloads never get above 4 or 5 kpbs (I would slit my wrists before I went back to that)

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]
Would you open any file from any e-mail? well that's kind of what you are asking people to do here, download from non-verified sources.[/QUOTE]

torrent is pretty secure.
so long as you get the original .torrent file from ubuntu's servers, bit torrent has pretty good mechanisms to make sure you get 100% the same file as what they made the original .torrent from.

I certainly trust it more than I trust http, it isnt even https we are talking about here, just straight "listen in and insert packets as you please" http.

---

### Post by Caligula on 2006-05-02
> If this is done and the repository servers seed the torrents then there is no point in keeping the normal download method

This will be a bit tricky...
The team working on apt will always need to check which packages are actually available on the bittorent, means much more work.
Also they'll need to configure apt-get to automatically detect wether the bittorent download is available, and if not to go for the normal one.

And, the new releases will always need to be as normal downloads, as no one has them yet...

The original idea is great, I have no doubt that a bittorent repository will be a great idea, but it will be open, and we can't control what goes in there, which basically is taking half the security and throwing it to the sea... It definitely wo'nt be as stable, and so on..

What I would suggest is a service like that, but don't "advertise" it, keep it to the experienced users who understand the risks and still want to do it.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]
Static transfer works just fine and there is a multitude of mirrors available.
[/QUOTE]

I think this is *mostly* true.  It is only the large packages that are anoying.  Even with a 200+ list of packages to download, there are really only 10 or 15 of them that take longer than a second or two anyway, but those 10 can take a minite or so each, if they were commin' in at 500 instead of 100 that would finish the whole upgrade in 5 or 6 minutes instead of 20+

and it would take bandwidth requirements away from the main ubuntu repo, which can only be a good thing

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]how "local" is that mirror of yours?
when i torrent a really large file (especially a linux cd from a distro as popular as ubuntu) I get it at 500+kbps

download from a server, even a fast server, I dont think I have ever seen faster than 250kbps.  is that local server in the same building?  :-)

just kidding

but you are right, there is certainly a bandwidth that is not optimal for a torrent download.  but even on my dad's dialup, torrents get up to 30+k if you let them get cooking, and other downloads never get above 4 or 5 kpbs (I would slit my wrists before I went back to that)[/QUOTE]

I'm German, it's from Germany. If i try a torrent it has NEVER gone over 230 and mostly stays around 100, sometimes dipping into 50.

For a dialup, a torrent solution with tracker seek for every file would be hell.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]torrent is pretty secure.
so long as you get the original .torrent file from ubuntu's servers, bit torrent has pretty good mechanisms to make sure you get 100% the same file as what they made the original .torrent from.

I certainly trust it more than I trust http, it isnt even https we are talking about here, just straight "listen in and insert packets as you please" http.[/QUOTE]

You have to be kidding me, i could easily make a tracker torrent file from any old virus i'd like.

You ever wonder why you can get corrupted files from a torrent and redownload and it's not corruped, it's because a seeder did something.

HTTP isn't trusted at all, but the way you download from http can be and in this case it is. You wouldn't apt-get an untrusted http site would you? Well with BT you don't have a choice.

---

### Post by brentoboy on 2006-05-02
[QUOTE=Caligula]This will be a bit tricky...
The team working on apt will always need to check which packages are actually available on the bittorent, means much more work.
Also they'll need to configure apt-get to automatically detect wether the bittorent download is available, and if not to go for the normal one.
[/QUOTE]

yeah, but there is already a debian apt-torrent (someone posted a link earlier to it)  the source is open, so the technology isnt new, it is just the merging of the two code bases that needs to be done (still ,I agree, this would be a significant undertaking)

But putting all the new files out on the servers wouldnt be such a big deal, you would have a script that reads all the debs in each folder, and makes .torrent files out of the sizable ones.

you would probably have to change the index files to know if there was a torrent available for each package, then the client pcs could plan out their attack before it even started downloading stuff.

> 
And, the new releases will always need to be as normal downloads, as no one has them yet...


all torrents start from a single file anyway, and if they are popular (like new packages the day of the release) they are immediatly avaialble from 100+ downloaders, before they ever finish downloading it in the first place.

> 
The original idea is great, I have no doubt that a bittorent repository will be a great idea, but it will be open, and we can't control what goes in there, which basically is taking half the security and throwing it to the sea... It definitely wo'nt be as stable, and so on..


well, the original .torrent definition files would be on the ubnutu server, just like the debs are now, only the masters of the univers would be allowed to add new .torrents, so it is secure, and wouldnt get muddied up by every little newbie with a new deb file.

> 
What I would suggest is a service like that, but don't "advertise" it, keep it to the experienced users who understand the risks and still want to do it.

If the masses arent using it, it will be slow and pointless--the real benefit kicks in when lots of people use it.  Lots of people use it when it doesnt require any special work follow the "just works" philopophy, it works.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]I think this is *mostly* true.  It is only the large packages that are anoying.  Even with a 200+ list of packages to download, there are really only 10 or 15 of them that take longer than a second or two anyway, but those 10 can take a minite or so each, if they were commin' in at 500 instead of 100 that would finish the whole upgrade in 5 or 6 minutes instead of 20+

and it would take bandwidth requirements away from the main ubuntu repo, which can only be a good thing[/QUOTE]

Find another mirror, there are hundreds.

I'd let one of my own servers go on it if it wasn't so busy with CentOS at this time, maybe later.

With a large package list, you will get more wait with bit torrent, you don't get one torrent for your specific update, you get one torrent per package, to find, to connect to tracker, to find users, to connect to users and then finally to download, after tha you are one in the seek times of that package that may be 2.5kb but takes minutes to find anyway.

It's hard to set up and even harder to set up right.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]
You ever wonder why you can get corrupted files from a torrent and redownload and it's not corruped, it's because a seeder did something.
[/QUOTE]

I wasnt aware of that,  but, all the same, couldnt it be fixed by comparing it to an md5 hash after the download is complete.

I have no idea if the current way does that or not, but it seems to me that it should, just becuase a corrupt package could spell bad news if it was an important one.

---

### Post by Caligula on 2006-05-02
"well, the original .torrent definition files would be on the ubnutu server, just like the debs are now, only the masters of the univers would be allowed to add new .torrents, so it is secure, and wouldnt get muddied up by every little newbie with a new deb file."

I thought the whole point is that WE will upload torrents, otherwise what difference does it make? it'll just be the masters' computers...
Or are you talking that we'll send them to them and they'll check them? that means even MORE work...

AN idea I just had, is there a way to disable the sharing of the package at the moment it's changed? so it will keep the original content? that might just work... but there you go about changing stuff in other peoples' computers...

 >  I wasnt aware of that, but, all the same, couldnt it be fixed by comparing it to an md5 hash after the download is complete.  

Then you will need a different system for the md5 files, as you don't want to compare it to a corrupted one...

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]I wasnt aware of that,  but, all the same, couldnt it be fixed by comparing it to an md5 hash after the download is complete.

I have no idea if the current way does that or not, but it seems to me that it should, just becuase a corrupt package could spell bad news if it was an important one.[/QUOTE]

Pretty much all downloads are compared to some kind of hash, md5 being the most common.

But i can give you anything with any hash if i want to, i can use the hash, rearrange the file to fit and deliver it with an install script that will put it back as the exploit i intended it as.

And still, this will be a slower way to download... it's much like the idea of PS2's to use combined power to run a game... via modems. :D

I don't see the point of this, we have something that works just fine and the mirroring system isn't anywhere near taxed to it's full capability, perhaps a multique downloader for larger files would be in order but those already exist, it wouldn't be VERY hard to make them work together, threaded wget's anyone?

It'd save me a second a month i guess.

---

### Post by brentoboy on 2006-05-02
[QUOTE=Caligula]
I thought the whole point is that WE will upload torrents, otherwise what difference does it make? it'll just be the masters' computers...
Or are you talking that we'll send them to them and they'll check them? that means even MORE work...
[/QUOTE]

no, we would download the torrent files, and the way that torrent downloads work, we would also upload the ones that we have downloaded to other people searching the network for that file.

the resulting files would still just be .deb files, you cant add debs now, and in the same way, you wouldnt be  able to add torrents either, but you could host a popular deb file, and some people would get some of that file from you.

> 
AN idea I just had, is there a way to disable the sharing of the package at the moment it's changed? so it will keep the original content? that might just work... but there you go about changing stuff in other peoples' computers...


not quite sure what you mean.  Once a .torrent file is open, it codes for a specific binary file, only that file will be downloaded, even if there is another one out there by the same name.

> 
Then you will need a different system for the md5 files, as you don't want to compare it to a corrupted one...


an md5 hash is only 64 characters (If I remember correctly) and they are all ascii characters, so it could be in the source index file along with the other apt info for each package.  In fact, I bet that a .torrent file has some kind of hash inside of it that could tell you if you got the right file after you are done downloading it.  this part wouldent be hard to implement, becuase there are lots of ways to do it, and comparing hashes to files is childs play.

---

### Post by Caligula on 2006-05-02
>  not quite sure what you mean. Once a .torrent file is open, it codes for a specific binary file, only that file will be downloaded, even if there is another one out there by the same name.

Not that I have much experience, but from my understanding a torrent file is just an automatic link to the content, if that's wrong ignore my posts...

Si if I would leave everything the same but add a nice virus to the package, wouldn't the virus be also downloaded by anybody using my computer as a seed?

about the md5, well...
the md5 is just a file at the server, and the program compares your hash to the one on the server...
In bittorent you don't just have one server, you have seeders, so you need to make sure it's compared to the md5 file on the ubuntu server, not the md5 file on some seed...
For that you'll need to create a system where it automatically checks the md5 with the server, SEPERATED from the bittorent network.

Sounds to me like far too much work, though it's a great idea...

---

### Post by brentoboy on 2006-05-02
ok, here is a summary of how I see it working...

during install, you opt-in or opt-out.  If you have dialup, it just assumes you dont want it.  It would give you a few reasons to try one way or the other.

if you opt in for apt-torrent (hopefully a majority of users with an always on connection will) then apt-torrentd gets installed.  apt-torrentd is a daemon that runs in the background and keeps track of your deb cache, and maintains a list of available torrent files, like any other torrent client.

it would be very very conservative.  perhaps only allowing 2 uploads at any given time, and keeping the upload speed to 1kbps, so that it wont swamp anyone.  if you want to open the upload speed on your pc, you will have to tweak it by hand.

whether you are apting or not at any particular time, the apt-torrentd will be offering debs that you recently downloaded, just like azureus does now after you download a new iso or video or something.

the servers would have .torrent files for the decent size downloads.  your local aptitude would have to be smart enough to know which ones would be best to pull down via torrent.

when you apt-get install a bunch of stuff it looks through the list, and starts immediately seeding the ones that are large enough to pull through torrent, and then starts pulling the others down the old fashioned way.

there would be a handful of permanent server seeds for each major package (courtesy of the dozens of ubuntu mirrors worldwide)

Then the big packages (the ones that make updates last so long) would come down significantly faster, and the others would not be hammpered by waiting for seeds and all of that other stuff that comes with torrents.

we would need to implement a nice hash check against the files, after they come in, perhaps using 2 hash mechanisms for each file (you cant reanrrange a file to have different content and still have the same hash for two differnt hashing mechanisms--or can you--I donno)

I think that so long as we take all this sort of stuff into consideration, we still can go somewhere with this, and it could be positive.

---

### Post by Caligula on 2006-05-02
> even if there is another one out there by the same name.
Sorry, didn't get that properly, I'm tired...:rolleyes: 

Anyway, couldn't you edit the bittorent file? or are you talking about an automatic upload immediately after the download?

---

### Post by brentoboy on 2006-05-02
[QUOTE=Caligula]you need to make sure it's compared to the md5 file on the ubuntu server, not the md5 file on some seed...
For that you'll need to create a system where it automatically checks the md5 with the server, SEPERATED from the bittorent network.
[/QUOTE]

you would need to get the md5 with the package info when you apt-get update, not from the torrent network.  you would also get the .torrent definition file directly from a trusted source.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]no, we would download the torrent files, and the way that torrent downloads work, we would also upload the ones that we have downloaded to other people searching the network for that file.[/QUOTE]

Yeah, but the stop of the seed would be manual or automatic when it's no longer a current file? As updates work, things are only current for so long.

> the resulting files would still just be .deb files, you cant add debs now, and in the same way, you wouldnt be  able to add torrents either, but you could host a popular deb file, and some people would get some of that file from you.

Of course you could, find the tracker, add to the list, anyone could and would as soon as the download is done, or sooner, or otherwise if you get one malicious user, the community is screwed.

> not quite sure what you mean.  Once a .torrent file is open, it codes for a specific binary file, only that file will be downloaded, even if there is another one out there by the same name.

Depends on the open torrent and what any member of the group wants you to get. I'll add an upload with a tracker id that you can download via updates, everyone does eventually, my backdoor is just waiting for me to use it.



> an md5 hash is only 64 characters (If I remember correctly) and they are all ascii characters, so it could be in the source index file along with the other apt info for each package.  In fact, I bet that a .torrent file has some kind of hash inside of it that could tell you if you got the right file after you are done downloading it.  this part wouldent be hard to implement, becuase there are lots of ways to do it, and comparing hashes to files is childs play.

Yikes, you'd get the hash from the malicious user in your example, fortunantly you get the hash from a trusted place today and the file from a trusted place also.

apt-torrent is a recepie for disaster if you have one user with my knowledge but not my good will towards others on board.

---

### Post by brentoboy on 2006-05-02
[QUOTE=Caligula]
Anyway, couldn't you edit the bittorent file? or are you talking about an automatic upload immediately after the download?[/QUOTE]


the torrents that you download would be "hidden" off in some /apt/ folder like the debs are now.  you would never care about them, much less toy around with  them.

but, to answer your question, yes.  with most torrent clients, you start sharing the parts you have downloaded before you even finish downloading the entire file.  

in apt-torrent, it would be even more transparent than that, becuase you would never even see the fact that it was still uploading after you finished your download, it would be hiding in an /apt/folder and the apt-torrentd daemon would just quietly give people access to a few k at a time.

---

### Post by Caligula on 2006-05-02
[QUOTE=brentoboy]ok, here is a summary of how I see it working...

during install, you opt-in or opt-out.  If you have dialup, it just assumes you dont want it.  It would give you a few reasons to try one way or the other.

if you opt in for apt-torrent (hopefully a majority of users with an always on connection will) then apt-torrentd gets installed.  apt-torrentd is a daemon that runs in the background and keeps track of your deb cache, and maintains a list of available torrent files, like any other torrent client.

it would be very very conservative.  perhaps only allowing 2 uploads at any given time, and keeping the upload speed to 1kbps, so that it wont swamp anyone.  if you want to open the upload speed on your pc, you will have to tweak it by hand.

whether you are apting or not at any particular time, the apt-torrentd will be offering debs that you recently downloaded, just like azureus does now after you download a new iso or video or something.

the servers would have .torrent files for the decent size downloads.  your local aptitude would have to be smart enough to know which ones would be best to pull down via torrent.

when you apt-get install a bunch of stuff it looks through the list, and starts immediately seeding the ones that are large enough to pull through torrent, and then starts pulling the others down the old fashioned way.

there would be a handful of permanent server seeds for each major package (courtesy of the dozens of ubuntu mirrors worldwide)

Then the big packages (the ones that make updates last so long) would come down significantly faster, and the others would not be hammpered by waiting for seeds and all of that other stuff that comes with torrents.

we would need to implement a nice hash check against the files, after they come in, perhaps using 2 hash mechanisms for each file (you cant reanrrange a file to have different content and still have the same hash for two differnt hashing mechanisms--or can you--I donno)

I think that so long as we take all this sort of stuff into consideration, we still can go somewhere with this, and it could be positive.[/QUOTE]

alright, you got me convinced...
:D 

great stuff...
unfortunately for me it's not that good, because i'm using a router and my admin doesn't like file sharing...(did somebody say anything about living with my sister's boyfriend?)](*,) ](*,)

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]ok, here is a summary of how I see it working...

during install, you opt-in or opt-out.  If you have dialup, it just assumes you dont want it.  It would give you a few reasons to try one way or the other.

if you opt in for apt-torrent (hopefully a majority of users with an always on connection will) then apt-torrentd gets installed.  apt-torrentd is a daemon that runs in the background and keeps track of your deb cache, and maintains a list of available torrent files, like any other torrent client.

it would be very very conservative.  perhaps only allowing 2 uploads at any given time, and keeping the upload speed to 1kbps, so that it wont swamp anyone.  if you want to open the upload speed on your pc, you will have to tweak it by hand.

whether you are apting or not at any particular time, the apt-torrentd will be offering debs that you recently downloaded, just like azureus does now after you download a new iso or video or something.

the servers would have .torrent files for the decent size downloads.  your local aptitude would have to be smart enough to know which ones would be best to pull down via torrent.

when you apt-get install a bunch of stuff it looks through the list, and starts immediately seeding the ones that are large enough to pull through torrent, and then starts pulling the others down the old fashioned way.

there would be a handful of permanent server seeds for each major package (courtesy of the dozens of ubuntu mirrors worldwide)

Then the big packages (the ones that make updates last so long) would come down significantly faster, and the others would not be hammpered by waiting for seeds and all of that other stuff that comes with torrents.

we would need to implement a nice hash check against the files, after they come in, perhaps using 2 hash mechanisms for each file (you cant reanrrange a file to have different content and still have the same hash for two differnt hashing mechanisms--or can you--I donno)

I think that so long as we take all this sort of stuff into consideration, we still can go somewhere with this, and it could be positive.[/QUOTE]

Hey big guy, as much as i apprecieate your efforts to this item i'd direct you to the bug reporting/bug fixing team, you are trying to fix something that doesn't need to be fixed and by complicating a simple procedure you are setting up a recepie for disaster.

It's done by trusted repos for a reason, it's the same in every distro, don't you think everyone has thought of more efficiant ways to distribute bandwidth during all these years? 

This is the best we can get, if you have great upload speeds, submit your site as a mirror, change anything and it won't work, it's made like this for a reason, the reason spells s.e.c.u.r.i.t.y. 

Absolutely no offense intended, i really do appreciate your efforts.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]Yeah, but the stop of the seed would be manual or automatic when it's no longer a current file? As updates work, things are only current for so long.[/QUOTE]

apt-torrentd could certainly check after you run an apt-get update, and it could see which files are no longer current, and stop seeding them.

if it was really smart, it could even notice which ones you already have installed, and start requesting them for download before you even begin updating.  every time the little update-manager checks for updates, your old files would stop, and you would start offering new versions of the same packages.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]
It's done by trusted repos for a reason, it's the same in every distro, don't you think everyone has thought of more efficiant ways to distribute bandwidth during all these years? 

This is the best we can get, if you have great upload speeds, submit your site as a mirror, change anything and it won't work, it's made like this for a reason, the reason spells s.e.c.u.r.i.t.y. 
[/QUOTE]

I still think that enough info could be downloaded directly from a trusted server that a file could be verified by a series of hash checks and other things such that the end result could still be as trustworthy as things are today.

Even if you had to download each of 10 differnt hash checksums from the real server, you still wont get more than a few K per download, if the other 20 mb come from a torrent, and then each of those 10 differnt hashes verified that it was "safe" you can pretty much bet it is safe.

>  Absolutely no offense intended, i really do appreciate your efforts.

none take whatsoever, its good to have a change to push at a topic from opposing angles, if everyone agrees all the time, nothing ever improves.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]apt-torrentd could certainly check after you run an apt-get update, and it could see which files are no longer current, and stop seeding them.

if it was really smart, it could even notice which ones you already have installed, and start requesting them for download before you even begin updating.  every time the little update-manager checks for updates, your old files would stop, and you would start offering new versions of the same packages.[/QUOTE]

So. you really want to do this? I'm not all that enthusiastic but just for the heck of it i have begun thinking of the security of it, i'd suggest that an official server mandates the update list with GPG checks, tracker info and selected sources for smaller files (mirror system) and larger files (torrents for larger files or larger packages of files).

I don't know how familiar you are with the current apt-get code and i can tell you that the devs are really stingy about any kind of implementation that isn't in their hands but if you're willing to do the functions i'll do the security.

---

### Post by brentoboy on 2006-05-02
[QUOTE=TheCaptain]I don't know how familiar you are with the current apt-get code and i can tell you that the devs are really stingy about any kind of implementation that isn't in their hands but if you're willing to do the functions i'll do the security.[/QUOTE]

well, I was really hoping to subimit a well polished idea to the list of edgy feature requests, but, I could certainly put 4 or 5 hours a week actually doing it, I've never seen the apt-get code, gut I know C pretty well.  I could certainly start studying the code, and highlighting changes that I would make in order to implement it, and then submitting   I think I would enjoy it alot more if I was actually involvoed in it and not just cheering on the home team.

I think I will do just that, first I will organize the list of features that I want to include, and run them by you (well, run them by this post) and then see if I cant get the right security requirements in there as well.  then I will see if the ubuntu team is interested in another dev.

if nothing else, I will just make a really well though out design submission with lots of well rounded ideas worked into it.

thanks for considering the possiblities, I better run, my wife is wondering why I am still out here typing.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=brentoboy]well, I was really hoping to subimit a well polished idea to the list of edgy feature requests, but, I could certainly put 4 or 5 hours a week actually doing it, I've never seen the apt-get code, gut I know C pretty well.  I could certainly start studying the code, and highlighting changes that I would make in order to implement it, and then submitting   I think I would enjoy it alot more if I was actually involvoed in it and not just cheering on the home team.

I think I will do just that, first I will organize the list of features that I want to include, and run them by you (well, run them by this post) and then see if I cant get the right security requirements in there as well.  then I will see if the ubuntu team is interested in another dev.

if nothing else, I will just make a really well though out design submission with lots of well rounded ideas worked into it.

thanks for considering the possiblities, I better run, my wife is wondering why I am still out here typing.[/QUOTE]

Hehe, if you're going to do this you will have to say goodbye to your wife for a while because i know your kind, you'll bet stuck to the keyboard, i know it so well because i have to go pick up my kids in five minutes ago. :D

Splinter up the idea, i'll add to it when i get online, this could be kinda great, an online code project, taking advantages of everyones help, i bet they'll find the errors we don't and reminding us of the things we inevitably forgot.

Anywayz, go take care of your wife now, i'll see ya in this thread later *bookmarked*.

---

### Post by Caligula on 2006-05-02
>  I think I will do just that, first I will organize the list of features that I want to include, and run them by you (well, run them by this post) and then see if I cant get the right security requirements in there as well. then I will see if the ubuntu team is interested in another dev.

Good luck!
I really hope it'll get going.

---

### Post by htinn on 2006-05-03
Looks like just the kind of thing they're looking for in Edgy. :)

---

### Post by Kvark on 2006-05-03
A torrent file contains a checksum for each part of the file. When a part is finished downloading it's checksum is compared to the one in the torrent and if it's not a match then the part is deleted. So you can send a virus to people who request parts from you but as soon as they are done downloading it they'll discover the part you sent them doesn't match the checksum in the torrent and delete it.

So as long as you trust the torrent file you can trust the download. If apt gets torrents only from the servers and only trusted MOTUs are allowed to add torrents to the servers then it is just as secure as today's system.


I am starting to strongly dislike this idea though. At first it sounded very interesting but the more points people bring up the more complicated brentoboy's sum up of the idea gets. If it's going to be a lot more complicated then the current system then it's not worth adding all the problems just to get faster downloads.

---

### Post by htinn on 2006-05-03
I think torrent integration would be difficult to manage and the benefits are not that great right at the moment. The biggest parts of the distros are OpenOffice, KDE libs, and kernel packages. Updates of those packages might best be handled through a short-term bittorrent distro for the first day or so, then through the regular repos.

In the meantime, what might work better than apt-torrent is doing "service packs" through bittorrent every couple of months or so (for people who prefer using CDs to apt-get).

---

### Post by brentoboy on 2006-05-03
[QUOTE=htinn]I think torrent integration would be difficult to manage and the benefits are not that great right at the moment. The biggest parts of the distros are OpenOffice, KDE libs, and kernel packages. Updates of those packages might best be handled through a short-term bittorrent distro for the first day or so, then through the regular repos.

In the meantime, what might work better than apt-torrent is doing "service packs" through bittorrent every couple of months or so (for people who prefer using CDs to apt-get).[/QUOTE]

So you are saying, make a single large file download that contains all the common packages (maybe the ones that are currently installed from the CD) and let people use bittorrent to download the servicepack and then burn it to CD and add the CD to your sources.list and then apt-get upgrade the normal way--except it would be able to find most of the updated packages on the new CD.

---
apt-torrent would be a lot of work, and it would have to make a lot of well thought out decisions depending on each pc's scenario.  Its the sort of nicity that, if it works really well, would make a distro stand out. But if it just mucks up everyones connection and doenst improve things, it could be a big turn off as well.

It has enough potential, if done right, that I expect that once it is done and works, many distro's would start adopting it. -- but who dares be the first one to send it out to the public.
---

I find it apealing becuase then I can give back to the community without any effort on my part.  I switch from a leach to a contributor just by opening up a little bandwidth.  I think that most ubuntu-ers would feel the same way--unless it messes up their internet connection, they would like to give back as well.
---

this whole idea needs a few days of thought before I go printing off code to start reviewing what could be updated.  Im not truly convinced one way or the other, but I still lean to the idea that having apt-torrent in place would be potentially benficial. And I think that it will only  get to be more beneficial as more people move to high speed connections, and the core packages get larger and larger.  Maybe in 5 years, it will be really important, and it would be good to already have a functional system in place that meets the need.  Technology is certainly moving in a direction that will favor apt-torrent in several years (at least for the larger packages).

---

### Post by augied on 2006-05-04
I'm not sure if any one has mentioned this yet, but this could save huge amounts of bandwidth for large, or even small networks.  Think about all of the computers on a network trying to update from one server at the same time versus each computer only downloading a portion from the internet, and the rest from local computers.

---

### Post by ubuntu_demon on 2006-05-05
It's an interesting idea. But the idea is not new. Here is an older thread :

[http://ubuntuforums.org/showthread.php?t=35663&highlight=apt+bittorrent](http://ubuntuforums.org/showthread.php?t=35663&highlight=apt+bittorrent)
Here is more information :

Here is an implementation :

[http://sianka.free.fr/](http://sianka.free.fr/)

---

