---
title: "A Basic Question On Ubuntu Studio 64 Installation"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by -kg- on 2008-11-01
I haven't been able to find this particular information anywhere I've looked:

I am interested in installing (or upgrading my present installation to) Ubuntu Studio 64.  I presently have 8.04 installed, so if I fresh install I will install the 8.10 version; otherwise I will upgrade to 8.04 (unless someone here might give me reason to upgrade my present installation to 8.10 first?).

I understand that if you have separate / and /home partitions, all software, etc. installation is done in the / partition (is this correct?).  I understand the concept (I plan on primarily editing video files, though I might do audio files also) that I'm going to have to have a rather large /home partition, or perhaps a separate "/media" partition, to store project files (not a problem, since I have an internal SATA drive at 1 TB and an external drive, also at 1 TB, let alone my hd0 drive at 400 GB).

Anyway, my question is this:  Considering the above is true (i.e., software, etc., is installed in /), how large should I make / for a decent installation of Ubuntu Studio, with some room for future expansion?  If I decide to upgrade my present installation (leaving my other software intact), how much more room should I give to /?

Like I said, hard drive space is not a problem, but I don't want to go *overboard* with it (though I could with no problem at all).  I like to run a tight ship on my computers, but at the same time I don't want to not have enough space and have problems with the installation or upgrade.

Thanks!

---

### Post by duffrecords on 2008-11-03
First of all, you may want to wait on the Intrepid Ibex.  They are working out [some problems]("http://ubuntustudio.org/8-10_release_note") with the realtime kernel, so stick with Hardy Heron for now (in fact, 64 Studio is still using the 2.6.21 kernel because its realtime performance is better than in the newer versions).  Besides, new Ubuntu releases tend to have a fair amount of bugs that are gradually fixed over the following months, and you'd probably rather just start editing and mixing instead.

Technically, 6-8 GB would probably be the minimum for /.  You might get away with less if you knew specifically which packages you do and don't want, but since you're working with multimedia it's good to have ample space for your /tmp directory.  For example, if you set your CD or DVD burning software to cache the data on your hard drive before burning, it will typically store it in /tmp.  You could even put /tmp on its own partition; that way you're more likely to have a large, contiguous block of free space instead of having system files mixing with it.  Also, it's a good idea to make your partitions somewhat larger than you expect you'll need.  You may have heard that Linux file systems don't suffer from fragmentation like FAT32 or NTFS but in fact they do if your partition starts to get near its capacity.  The last thing you want when working with audio/video is a slow hard drive.  Go big; you've got plenty of space.

Also, remember that in addition to / and /home you will need to allocate a partition for swap.  There's a lot of discussion about how much swap is necessary but most people recommend using twice the amount of RAM you have as a general rule of thumb.  It seems like overkill when you have upwards of 2GB or more, but if you ever want to make your computer hibernate, it's going to need somewhere to put all that data.

---

### Post by barisurum on 2008-11-03
> I understand the concept (I plan on primarily editing video files, though I might do audio files also)

  If this is the case I suggest keeping an eye on the [COLOR="Red"]lumiera[/COLOR] project. It's based on Cinelerra, but the team is rewriting all the code so that it won't have all those painful bugs cinelerra had. The bugs had keeped me from taking video seriously in linux for a while. And I didn't check the new versions of cinelerra after that (I was so dissapointed). But its possible when the new lumiera will be released, linux community will have a powerful video authoring app in their hands.

  [http://lumiera.org/](http://lumiera.org/)
  [http://cinelerra.org/](http://cinelerra.org/)

---

