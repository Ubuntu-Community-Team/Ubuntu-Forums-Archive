---
title: "new pc issues: audio / video, etc"
date: 2009-08-11
forum: System76 Support
---

### Post by readerbee on 2009-08-11
Hi:

I recently purchased (last month) a new pc from System76, the Serval and am just now getting to more fully test it since it took me until now to get setup for internet access, our new ISP had a 3wk backlog for new installs.

Yesterday, I tried to perform several actions, all of them failing to perform. I'm not sure why these problems occurred being new to Ubuntu/Linux & this being a brand new computer.

Actions & the problems that occured:

- no audio at all - tried to access a few online radio stations & also tried to play a music CD 
- no video at all - tried to access C-Span & YouTube
- no graphics - tried to access an online game, Yoville

For most of these a prompt came up asking if I wanted to search for a compatible plugin. I would say yes, and it would seek to find a plugin yet would return with a failed message response.

I'm not sure what to think but feel I ned help getting these problems resolved. Any/all input would be greatly appreciated. I was planning to simply call System76 direct, but in looking for customer support - noted reference to this site.

Another thing that keeps happening, typing this had proven itself to be a challenge as the keys kept jumping all over the page opposed to continous typing in a steady stream.

Thanks in advance.. looking forward to getting these matters resolved.

readerbee

---

### Post by gila_monster on 2009-08-11
Hi, readerbee!

I'm going to open here and say that "no video|audio|graphics at all" should actually be "no video|audio|graphics in my browser." Is this correct? The problems are actually related to browser plugins?

If so, the problem isn't actually as big as it might appear. 

You need to be aware that on Linux systems (particularly Ubuntu, because you never run as 'root,' which is the administative account), asking the browser to seek and install plugins does not work. Since it is doing so in the normal user account rather than running as root, it will not be able to install software on its own. You'll have to do that yourself, directly.

Fortunately, this is not very difficult. We just need to determine what you need. What browser were you using? Did the browser, when complaining about the plugins, happen to mention what was missing or what codec it was trying to find? I suspect you will need Flash at least (I'm a little surprised that didn't work out of the box, though), and a couple of other things.

Depending on the sites involved, you may need to install ubuntu_restricted_extras. (I am presuming you are running Ubuntu as installed when shipped, rather than Kubuntu or Xubuntu.) That alone may resolve your issues. Be aware, however, that doing so means you will not be using purely free/open source software, and depending on where you live, it may even be illegal, strictly speaking. Different countries have different rules about it.

---

### Post by readerbee on 2009-08-11
Yes, I'm using Ubuntu - Jaunty Jackalope 9.04 as it was pre-installed prior to purchase.

Everything I had attempted to do was via the Firefox 3.0.13 browser with the exception of playing a CD, 

I've attempted again to play a CD - Rythmbox Music Player opened but could not play the CD. The message received stated: "MPGEG-1 layer 3 (MP3) decoder plugin is required to play this stream, but not installed."

For the radio, I was in Firefox when I first attempted to access a station on the net. My second attempt was via Rythmbox Music Player & I did get a message about there being 2 plugins avaliable for download but also got a message regarding legal issues if I were to download them, so I did not.

---

### Post by jdb on 2009-08-11
> **readerbee said:**
> Hi:

I recently purchased (last month) a new pc from System76, the Serval and am just now getting to more fully test it since it took me until now to get setup for internet access, our new ISP had a 3wk backlog for new installs.

Yesterday, I tried to perform several actions, all of them failing to perform. I'm not sure why these problems occurred being new to Ubuntu/Linux & this being a brand new computer.

Actions & the problems that occured:

- no audio at all - tried to access a few online radio stations & also tried to play a music CD 
- no video at all - tried to access C-Span & YouTube
- no graphics - tried to access an online game, Yoville

For most of these a prompt came up asking if I wanted to search for a compatible plugin. I would say yes, and it would seek to find a plugin yet would return with a failed message response.

I'm not sure what to think but feel I ned help getting these problems resolved. Any/all input would be greatly appreciated. I was planning to simply call System76 direct, but in looking for customer support - noted reference to this site.

Another thing that keeps happening, typing this had proven itself to be a challenge as the keys kept jumping all over the page opposed to continous typing in a steady stream.

Thanks in advance.. looking forward to getting these matters resolved.

readerbee

You might find this link useful:

[http://knowledge76.com/index.php/Installing_Restricted_Formats]("http://knowledge76.com/index.php/Installing_Restricted_Formats")

jdb

---

### Post by jeamer on 2009-08-13
jdb's link should solve all your plugin needs, leading to audio (more specifically, playing mp3's) and video (sounds like you need flash). 

In terms of the keys jumping all over the place, believe it or not but it's likely that your hands are brushing the trackpad while you type. I had this issue for a while until I either deliberately placed my hands on either side of the trackpad while typing or used an external keyboard/mouse combo (which I recommend, especially with the Serval, which is more of a stationary laptop anyways). Another option is it looks like an option to "Disable the trackpad while typing" is on the way: 

[http://ubuntuforums.org/showthread.php?t=1160268&page=3](http://ubuntuforums.org/showthread.php?t=1160268&page=3)

which would be great!

Good luck, hope your Ubuntu experience is a good one!

---

