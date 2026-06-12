---
title: "Bittorrent clients ,QBittorrent ,a Qt based torrent client that looks promissing."
date: 2007-02-23
forum: The Cafe
---

### Post by DjDarkman on 2007-02-23
One day while I was surfing the ubuntu forums ,I found a thread that contained some firewalling problem ,something like this "the firewall blockes qbitorrent" or something like ,that ,I was atrackted by the name for two reasons :

 1) I prefer qt / kde based apps 2) I am in great need of a stable and working torrent client

I downloaded the sourcecode ,and started compiling ,but it needed the original libtorrent that can`t be found in the apt repositories ,it`s available on sourceforge.

I think this torrent client looks promising ,no offence but ktorrent is just isn`t stable enough ,qbittorrent lacks a few features thats true ,but hopefully it will develop in time.It would be realy good to have packagees int the ubuntu repositories of liborrent and qbittorent ,because I think it`s good and reliable enough.

Altough this thread is about qbittorent ,I would ask ,what do you think of the avaialbe gui based torrent clients for linux?

my opinios are :

bittornado : only good for single torrents
azureus : hard to get it work and greately consumes system resources
utorrent over wine : sometimes it can become realy unstable
ktorrent : unstable ,has issues with caching I think
qbittorrent : works ,but needs a few features

---

### Post by Mark C on 2007-02-23
KTorrent 2.1 has been very stable in my KDE system and it starts with KDE.

I tried others like azureus(you said what should be said already), utorrent(great if you are using windows, but rather not)m, bittorrent(can't download more than 1, not enough options) and bittornado(same problem as bittorrent except more options), and I could say ktorrent is the best evar. It's like azureus minus the resource hog, annoyances and unstability. Haven't tried qbittorrent though, I'll wait until it gets in the 64-bit repo.

---

### Post by weatherman on 2007-02-23
ktorrent works fine here as well

---

### Post by Kateikyoushi on 2007-02-23
So far if needs gui transmission, rtorrent in console and have high hopes for the new transmission release and of course deluge which might be the final solution.

---

### Post by karellen on 2007-02-23
ktorrent works fine for me, it's one of the few kde applications that I use on my gnome desktop (besided k3b. quanta plus...)

---

### Post by DjDarkman on 2007-02-23
Don`t know then why does kt works bad for me ,I would make a 64 bit version of qbittorrent a libtorrent (libtorrent is not in the repos eighter) ,but I don`t know packageing.

But in my opinion it would be a good thing to habe both qbt and libtorrent in the ubuntu repositories.

---

### Post by Mateo on 2007-02-23
My problem is that there are 2 options that I consider essential, and almost nothing (except utorrent) have them.  they are:

1) Has to use working directories.  I don't always keep my computer on, or keep torrents running, so some downloads could take weeks or more. I don't want the files to be sitting on my desktop or my ~ folder the whole time.  I'd like them to be tucked away in a hidden folder where I don't have to look at them.

2) Has to move the files when complete. This goes with the above, I want it to move the completed files to ~ or some other directory of my choosing.

I also am strongly in favor of clients with DHT, because it gets up to speed so much quicker than tracker-only torrents.

---

### Post by zachtib on 2007-02-23
> **Kateikyoushi said:**
> So far if needs gui transmission, rtorrent in console and have high hopes for the new transmission release and of course deluge which might be the final solution.

:D 

Deluge actually uses the same libtorrent at qbittorrent, which is annoying because it's not in the repos. (however, i've emailed someone that is packaging it for debian, so cross your fingers) our solution is to compile libtorrent INTO deluge, which allows it to be in ubuntu's repo, but obviously that isn't the optimal solution

---

### Post by CPtAJ on 2007-02-23
ktorrent has been rock solid for me ever since I got it. And my box is downloading torrents 24/7

Never crashed once.

---

### Post by Mark C on 2007-02-23
> **CPtAJ said:**
> ktorrent has been rock solid for me ever since I got it. And my box is downloading torrents 24/7

Never crashed once.

Amen, brother!
On mine too, except for the 24/7 part, just 18/5. But it's rock solid and serviced me very well already.

---

### Post by Ob1 on 2007-02-23
are there any bittorent clients that are native to Linux that are capable of checking if ports are open? (except for Azurues)

---

### Post by DjDarkman on 2007-02-24
> **Ob1 said:**
> are there any bittorent clients that are native to Linux that are capable of checking if ports are open? (except for Azurues)

Why is that so important? If you don`t have a restrictev firewall you won`t have that problem ,and if you have you should know how to set it.

---

### Post by DjDarkman on 2007-02-24
> **zachtib said:**
> :D 

Deluge actually uses the same libtorrent at qbittorrent, which is annoying because it's not in the repos. (however, i've emailed someone that is packaging it for debian, so cross your fingers) our solution is to compile libtorrent INTO deluge, which allows it to be in ubuntu's repo, but obviously that isn't the optimal solution

I think that compiling a lib in a program is a lame solution in all cases ,btw I think qbittorrent`s libtorrent should be in the repos too.

---

### Post by revoltism on 2007-03-04
For me it's bittornado right now. The others are to slow. Maybe it's my configurations i don't know, but all the others are too slow. BitTornado is the only one working good but of course has the lack of a good gui.

---

### Post by nexx on 2007-03-26
I am using gtk-gnutella that I really love and qbittorrent. Gnutella sometimes uploads at 270 kbs.

---

### Post by PartisanEntity on 2007-03-26
> **DjDarkman said:**
> 
azureus : hard to get it work and greately consumes system resources


Hard to get to work? You've got to be kidding, it is up and running in about 2-3 minutes. Install it, launch it, go through the set-up wizard and you are ready to go.

Concerning system resources, runs without taxing my system on my Asus A6K (1.6GHz Turion, 2GB RAM).

---

### Post by [h2o] on 2007-03-26
> **DjDarkman said:**
> I think that compiling a lib in a program is a lame solution in all cases ,btw I think qbittorrent`s libtorrent should be in the repos too.

If it is one (relatively small) library then I much rather have it compiled in than having to download the source and compile it myself. I can give up a few megabytes of space if I can save half an hour of work...

---

### Post by mykalreborn on 2007-03-26
why doesn't anyone ever say anything about deluge? :D it's a stable app, easy on the RAM, with a nice gui. yes it doesn't have all the features Azureus has, but for someone who just wants to get his files it's by far the best. [here]("http://ubuntuforums.org/forumdisplay.php?f=172") is the link to the project.
^_^

---

