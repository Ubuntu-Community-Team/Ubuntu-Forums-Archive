---
title: "Can I browse the Ubuntu One music catalogue in a browser? and other questions..."
date: 2010-08-01
forum: Ubuntu One (CLOSED)
---

### Post by KIAaze on 2010-08-01
Hi,

I have some questions concerning the Ubuntu One music service:

1) Can I browse the Ubuntu One music catalogue in a browser? Or is using Rhythmbox or Banshee a requirement?
Shouldn't people be able to buy the music from any OS, using any software (browser, music player with browser)? (accessing the music store through any browser is really a minimum... Maybe I was just unable to find it.)

2) When I click on "my downloads", it doesn't open any browser window and stays stuck on "Connecting you to the Ubuntu One Music Store...".
There is no way to reload the page or go back inside rhythmbox. :(

Note: I'm using Lubuntu with chromium.

3) Why isn't the music also offered in open formats like OGG or FLAC?

4) Are there any plans for a similar service offering videos (movies and TV series)? :)

---

### Post by afrowildo on 2010-08-03
1) There doesn't appear to be a U1 music site, but the service that supplies music to U1, 7digital.com, does have one, and you can get any track in an un-DRM'd mp3 format for the same price. Unfortunately, purchases made here won't sync with your U1 account, although they do provide a 'locker; into which your purchases are atomically dropped and from which you can download them as many times as you like.

2) I've experienced this problem when purchasing music on the network at work, so it may be a firewall problem. Unfortunately, I couldn't really be any more specific than that as I don't have access to the network infrastructure in order to troubleshoot it.

3) I think this is because 7digital only uses mp3 files, which I think is a licensing restriction imposed by record labels who misunderstand the term 'open', and are a little freaked out by it.

4) Probably not as the TV/Movie studios still force anyone distributing their content to apply DRM to the files. Maybe somewhere down the line, but not any time soon.

Hope this lot helps :)

---

### Post by afrowildo on 2010-08-03
PS

> There is no way to reload the page or go back inside rhythmbox

I've submitted this as a Paper Cut, so perhaps you could follow [this link]("https://bugs.launchpad.net/hundredpapercuts/+bug/613261") and vote it up.

---

### Post by KIAaze on 2010-08-03
Thanks for answering and creating the bug report.

The bug with the browser not opening happened at home for me.
Actually, it did open konqueror the first time, but I changed the default browser (x-www-browser) to chromium and then it stopped working. I can try debugging it eventually.

---

