---
title: "Ubuntu 15.04 RC release date"
date: 2015-04-19
forum: Ubuntu Development Version
---

### Post by polochamps on 2015-04-19
[URL="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-April/001133.html"]Can we still expect RC today?

Source: https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-April/001133.html[/URL][URL="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-April/001133.html"]

> **Stéphane Graber**[/URL]> stgraber at ubuntu.com        
    _***Thu Apr 16 22:19:41 UTC 2015***_[URL="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-April/001133.html"]

Hello everyone,

So as of a bit over an hour ago, we've entered the Final Freeze in
preparation for the release of Ubuntu 15.04.


As usual, this means that you should refrain from uploading any seeded
package which doesn't contain a release critical fix. If you're unsure
about whether you should be uploading a package or not, please get in
touch with the release team in #ubuntu-release.

Unseeded packages will still get auto-accepted until the bot is turned
off shortly before release.


[U][B]As for images, we're expecting the first run of candidate images to
happen late tomorrow before most of us leave for a weekend of travel.[/B][/U]


On behalf of the Ubuntu Release Team,

Stéphane Graber[/URL][URL="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-April/001133.html"]



[/URL]

---

### Post by kc1di on 2015-04-19
there will be no RC as such if you want to have the latest available you can go to the daily build. found [here:]("http://cdimage.ubuntu.com/daily-live/current/") Or just wait for the final which is scheduled for April 23rd.  If you have the latest release and have kept it updated you'll be there anyway.

---

### Post by coffeecat on 2015-04-19
Vivid Vervet [Release Schedule]("https://wiki.ubuntu.com/VividVervet/ReleaseSchedule") and what they say about Release Candidate in the link from that page:

[https://wiki.ubuntu.com/ReleaseCandidate](https://wiki.ubuntu.com/ReleaseCandidate)

If you want to be slightly ahead of the game before the final release rush, simply keep your ISO up to date with zsync from the daily build page here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You'll find that updates to the ISOs no longer happen between 24-48 hours before final release. If you've updated to the last available daily build and compare the md5sum of that to the published md5sum of the final release ISO when that becomes available, you'll find they are the same. Although your ISO of the last available daily build will have a different filename, it is the final release.

I've done fresh installations with the daily build 24 hours before final release for the past few releases, and by doing so I have had shiny new installations before the servers get hammered by all the people wanting the final release ISOs.

---

### Post by Elfy on 2015-04-19
Just as an aside - that current image is out of date, there was a 17.1 turn up later on the 17th. 

The most up to date image downloads are generally available at the iso tracker.

[http://iso.qa.ubuntu.com/qatracker/milestones/338/builds](http://iso.qa.ubuntu.com/qatracker/milestones/338/builds)

[http://cdimage.ubuntu.com/daily-live/20150417.1/](http://cdimage.ubuntu.com/daily-live/20150417.1/)

---

### Post by polochamps on 2015-04-19
Thanks guys! 
I thought there would be such an announcement like what they did with the Alpha and Beta releases.

Was waiting for an RC on this page.

[http://cdimage.ubuntu.com/ubuntu/releases/15.04/](http://cdimage.ubuntu.com/ubuntu/releases/15.04/)

> [h=1]Index of /ubuntu/releases/15.04[/h] 
[LIST]
[*][ Parent Directory]("http://cdimage.ubuntu.com/ubuntu/releases/")
[*][ alpha-1/]("http://cdimage.ubuntu.com/ubuntu/releases/15.04/alpha-1/")
[*][ alpha-2/]("http://cdimage.ubuntu.com/ubuntu/releases/15.04/alpha-2/")
[*][ beta-2/]("http://cdimage.ubuntu.com/ubuntu/releases/15.04/beta-2/")
[/LIST]


[IMG]http://www.omgubuntu.co.uk/wp-content/uploads/2015/01/ubuntu-release-schedule-revised.jpg[/IMG]

---

### Post by ptn107 on 2015-04-19
Using the 64-bit Ubuntu MATE iso from [_here_]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/20150417.1/vivid-desktop-amd64.iso").  No problems other than the "won't restart at the end of the install" problem everyone else has.

This is the 20150417.1 64-bit iso
md5: 719922cf31542a29be59b59ec751423d

Works like a charm.  Just use zsync as mentioned above to keep your iso updated.

---

