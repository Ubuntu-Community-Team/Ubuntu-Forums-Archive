---
title: "Linux Home Server"
date: 2009-03-21
forum: Server Platforms
---

### Post by ugm6hr on 2009-03-21
I've just started toying with the idea of a proper home server, rather than just a media server / HTPC.

I'm surprised no one else is interested in Amahi (only a handful of threads mention it here).  It looks brilliant, and has better (and more) features than Windows Home Server.

The [Amahi]("http://amahi.org/") website mentions future support for Ubuntu, although I think I recall this being said over a year ago.  [It doesn't look hopeful]("http://forums.amahi.org/viewtopic.php?f=9&t=83&p=346").  The [Ubuntu Home Server]("http://www.ubuntuhomeserver.org/") project appears to have gone dormant, with a new (presumably Ubuntu-based project) in the form of [Satega]("http://satega.org/") having been created.  Just have to wait for evidence of progress...

Given Fedora's desktop (rather than server) focus, and its short support cycles, I would have thought Ubuntu (especially LTS) would be a much better base for Amahi.  It is a shame that the Amahi project couldn't be better supported by our community.

Anyway, as for my personal project: I think I'll just experiment with Ubuntu for the time being...

I can see how Ubuntu Server + ebox + citadel + mediatomb would replace most of Amahi's functionality, albeit with slightly less automation.  The one thing missing from this combo is an automated network backup solution that can be managed from within the server web interface.

Any tips or advice welcome.

---

### Post by HermanAB on 2009-03-21
Well, there are Linux distributions with very good wizards which allow you to set anything up with a few clicks of a mouse, so an upstart like Amahi doesn't have much of a fighting chance against the likes of Fedora, Mandriva and Suse which have been doing it for many years.  Even on Ubuntu, setting up a home server is not particularly hard.

Cheers,

Herman

---

### Post by MrWES on 2009-03-21
I'd recommend the howto's found at:

[http://www.howtoforge.com]("http://www.howtoforge.com")

Bill

---

### Post by ugm6hr on 2009-04-04
After a short period fiddling with ebox, I started investigating other options.

ClarkConnect is a very similar piece of software, which appears a little slicker with its interface.  However, I didn't give it a try, since it is trying to achieve the same enterprise goal as ebox.

I found FreeNAS to be different.  While it's name suggests it is a simple NAS software, it is *perfect* for a home server.

I saw it here: [http://lifehacker.com/5162026/best-home-server-software](http://lifehacker.com/5162026/best-home-server-software)

It runs as a LiveUSB (128MB USB stick - 32MB is not actually large enough for the latest version - I tried), is based on FreeBSD (not Linux).  The documentation is a little bewildering for the average home user, and the freenas home page doesn't help change that.

However, none of these changes the fact that I downloaded and copied the USB image to USB in under 20 minutes, booted and set up the network within a further 5 minutes, and have now got a SMB & NFS server, fuppes uPNP server, basic internal web server and scheduled transmission torrent downloader after another half hour.

I haven't yet have time to try all these features, but assuming they work as advertised, I am very happy with this.

Perhaps when I actually need the calendar and wiki, I might consider retrying Ubuntu server again, but until then, FreeNAS is just too simple not too use!

In fact, I've decided to document what I did for future reference (and perhaps to help others): [http://homeserver.wikidot.com/](http://homeserver.wikidot.com/)

I am now sorely tempted by the Viglen MPC-L (£79) to run my new server for its power-saving features, and keep my HTPC separate.

---

### Post by KermitJr on 2009-10-12
I know this is a bit outdated, but for anyone reading, the backup solution to complete the bill might be backuppc.  The pooling dedupe is great and it's pretty much all server side (just needs access to the clients over the network).

[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

Also, if you want to the hilt- bacula but more complex and no deduping.

Both are in repos.

Cheers,
KermitJr

---

### Post by pwrstick on 2009-10-14
I'm very excited by the prospect of FreeNAS and BackupPC running on a home server!

Years ago I created a file server using Ubuntu, and mdadm for RAID.  It's worked great (had one hard drive failure, RAID worked just fine for the rebuild).  A very stable server.

Recently I've wanted to do more though... so I'm considering rebuilding.  Seeing as FreeNAS has so many things already working with it at install (I'm checking out the VM they offer on their web page) I think I'm going to give it a try.  It's that or pay $600.00 for a Windows Home Server :P

I'm curious though - has anyone tried BackupPC on FreeNAS?  I've found some tutorials, but just curious of user experience.

Cheers

---

