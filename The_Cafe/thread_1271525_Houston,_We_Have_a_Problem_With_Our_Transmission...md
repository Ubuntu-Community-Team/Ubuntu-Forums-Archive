---
title: "Houston, We Have a Problem With Our Transmission..."
date: 2009-09-21
forum: The Cafe
---

### Post by coldReactive on 2009-09-21
[http://linuxmint.com/download.php](http://linuxmint.com/download.php)

Torrents give the error: "Unregistered torrent pass."

That's too bad, oh well. Can't help seed.

---

### Post by lovinglinux on 2009-09-21
That's probably because the torrent [http://www.linuxmint.com/torrent/LinuxMint-7.iso.torrent](http://www.linuxmint.com/torrent/LinuxMint-7.iso.torrent) includes a Pirate Bay tracker, which is a sinking ship. It seems the other tracker (linuxtracker.org) is not tracking that particular torrent.

Open the torrent preferences and delete the trackers and replace them with [http://tracker.openbittorrent.com:80/announce](http://tracker.openbittorrent.com:80/announce)

You can also check other trackers for this torrent at [http://www.torrentz.com/e6d127825ea38b231ce59eac0d15ddd66ee46284](http://www.torrentz.com/e6d127825ea38b231ce59eac0d15ddd66ee46284)

Or try [this torrent](http://linuxtracker.org/index.php?page=torrent-details&id=bed75a0f59418a69babfd093a983c9efa5705080)

---

### Post by pwnst*r on 2009-09-21
> **coldReactive said:**
> [http://linuxmint.com/download.php](http://linuxmint.com/download.php)

Torrents give the error: "Unregistered torrent pass."

That's too bad, oh well. Can't help seed.

not sure how you even stuck with *nix if that's the kind of effort you put forth.

---

### Post by oboedad55 on 2009-09-21
> **coldReactive said:**
> [http://linuxmint.com/download.php](http://linuxmint.com/download.php)

Torrents give the error: "Unregistered torrent pass."

That's too bad, oh well. Can't help seed.

I'm seeding with that torrent as we speak. Try it again.

---

### Post by coldReactive on 2009-09-21
> **lovinglinux said:**
> That's probably because the torrent [http://www.linuxmint.com/torrent/LinuxMint-7.iso.torrent](http://www.linuxmint.com/torrent/LinuxMint-7.iso.torrent) includes a Pirate Bay tracker, which is a sinking ship. It seems the other tracker (linuxtracker.org) is not tracking that particular torrent.

Open the torrent preferences and delete the trackers and replace them with [http://tracker.openbittorrent.com:80/announce](http://tracker.openbittorrent.com:80/announce)

You can also check other trackers for this torrent at [http://www.torrentz.com/e6d127825ea38b231ce59eac0d15ddd66ee46284](http://www.torrentz.com/e6d127825ea38b231ce59eac0d15ddd66ee46284)

Or try [this torrent](http://linuxtracker.org/index.php?page=torrent-details&id=bed75a0f59418a69babfd093a983c9efa5705080)

When I added openbittorrent, it hesitated for a moment. Then the x64 torrent gave me the error again. The x86 torrent is not doing anything, no peers, can't get peers, it's just idle.

Why do you ask, even though I just added the tracker this new torrent? Because, the torrent resetted its trackers. When I looked at the properties and the tracker tab for both, their trackers were reset back to thepiratebay and linuxtracker. That new torrent in the last link works though, thanks. But do you also have an x64 version?

---

### Post by lovinglinux on 2009-09-21
> **coldReactive said:**
> When I added openbittorrent, it hesitated for a moment. Then the x64 torrent gave me the error again. The x86 torrent is not doing anything, no peers, can't get peers, it's just idle.

Check the troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

> **coldReactive said:**
> Why do you ask, even though I just added the tracker this new torrent? Because, the torrent resetted its trackers. When I looked at the properties and the tracker tab for both, their trackers were reset back to thepiratebay and linuxtracker. That new torrent in the last link works though, thanks. But do you also have an x64 version?

I don't use Transmission, so I can help that much. It shouldn't be resetting the trackers tho. I suggest you try Deluge, which the best BitTorrent client IMO.

I don't have an x64 version of that torrent. In fact I'm not even downloading it. I just searched for the previous one to help you. I'm sure you will be able to find it at [http://linuxtracker.org](http://linuxtracker.org)

---

### Post by coldReactive on 2009-09-21
Thanks, I'll just remove mint from my seeding queue and stay with angels online, ubuntu and arch linux torrents, as they work.

---

### Post by Enigmapond on 2009-09-21
I had similar problems with Transmission...that and others. I use now Deluge which, I agree, is the best client IMHO and there are a lot more options and control in this application. I recommend you switching and you will see a noticeable difference.

Cheers!

---

### Post by MasterNetra on 2009-09-21
> **Enigmapond said:**
> I had similar problems with Transmission...that and others. I use now Deluge which, I agree, is the best client IMHO and there are a lot more options and control in this application. I recommend you switching and you will see a noticeable difference.

Cheers!

+1 I even use it on windows lol, got some gtk baggage but meh its worth it.

---

### Post by Charles Kerr on 2009-09-22
I've downloaded that Linux Mint 7 iso torrent [several times to benchmark Transmission]("http://pastehtml.com/view/090621g11KlBWM.html"), so I was surprised to read this thread.  I re-downloaded the .torrent from your link just now and gave it a try, and here's what I found:

In short, the error is with the .torrent file on the Linux Mint download page.  It's old and its announce URL list points to two invalid addresses:

[LIST=1]
[*][http://tracker.thepiratebay.org:80/announce](http://tracker.thepiratebay.org:80/announce)
[*][http://linuxtracker.org:2710/announce](http://linuxtracker.org:2710/announce)
[/LIST]
tracker.tpb.org is an ex-tracker. linuxtracker.org's URL is broken too -- that's the one returning the error message.  Installing Deluge or KTorrent won't solve this, but you're welcome to try. ;)

What *will* fix things is downloading a .torrent with fewer broken announce URLs and more working ones.  The front page of [http://www.linuxtracker.org/](http://www.linuxtracker.org/) has [this one, which looks much better]("http://linuxtracker.org/index.php?page=torrent-details&id=bed75a0f59418a69babfd093a983c9efa5705080"):


[LIST=1]
[*][http://linuxtracker.org:2710/00000000000000000000000000000000/announce](http://linuxtracker.org:2710/00000000000000000000000000000000/announce)
[*][http://www.h33t.com:3310/announce](http://www.h33t.com:3310/announce)
[*][http://tracker.openbittorrent.com:80/announce](http://tracker.openbittorrent.com:80/announce)
[*][http://tracker.publicbt.com:80/announce](http://tracker.publicbt.com:80/announce)
[*][http://tracker.bittorrent.at:80/announce](http://tracker.bittorrent.at:80/announce)
[/LIST]

When I loaded this one in Transmission 1.75, it started working instantly.

I've forwarded this along to Clem so that they can fix the Mint download page.

---

### Post by eaglemob on 2009-09-22
[B]Hehe i have a different problem, I download at speed about 2,3Mb/sec. 
But i can't seed. I try everything, and it just doesn't work.
I have no firewall behind. To seed i have to got in windows Crap :(


[/B]

---

### Post by lovinglinux on 2009-09-23
> **eaglemob said:**
> [B]Hehe i have a different problem, I download at speed about 2,3Mb/sec. 
But i can't seed. I try everything, and it just doesn't work.
I have no firewall behind. To seed i have to got in windows Crap :(
[/B]

See the Troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

