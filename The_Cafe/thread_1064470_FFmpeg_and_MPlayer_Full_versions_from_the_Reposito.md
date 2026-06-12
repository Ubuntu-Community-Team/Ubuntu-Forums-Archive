---
title: "FFmpeg and MPlayer: Full versions from the Repository?"
date: 2009-02-08
forum: The Cafe
---

### Post by andrew.46 on 2009-02-08
Hi,

I am hoping to generate some discussion, hopefully not too heated, about the pros and cons of the Ubuntu Repositories hosting full and up-to-date copies of FFmpeg and MPlayer.

In my view the 'pros' are easily seen. Have a look anywhere in these forums and people can be seen struggling with the limitations imposed on these amazing pieces of software by Ubuntu/Debian. Sure there is a path around these problems, raise your hand Medibuntu and also raise your hands those who have written guides for the svn MPlayer and the svn FFmpeg. (I acknowledge here that I have written a popular guide for compiling the svn MPlayer and downloading a full codec pack.) But these guides are complex and I am sure that the average Ubuntu user would be happier using apt-get rather than ./configure and these average users are currently being short-changed with apt-get.

The 'cons' are not hard to find as well. I believe in the United States and some other countries there is a problem with copyright law with some of the codecs involved in both FFmpeg and MPlayer. As well 'releases' of both MPlayer and FFmpeg are few and far between leaving something of a moving target for package managers to organise for their distros.

I do not expect this issue will be solved in this forum but I would be keen to hear the views of others, fully aware that current policy is unlikely to change.

Andrew

---

### Post by Polygon on 2009-02-08
the average user is not going to be using ffmpeg and mplayer, as they are both pretty advanced programs when there are far simpler alternatives which they will most likely be using, like avidemux and vlc.

---

### Post by SunnyRabbiera on 2009-02-08
well adding medibuntu isnt that hard though yes there should be amore direct way of adding it then the terminal.

---

### Post by FakeOutdoorsman on 2009-02-08
> **Polygon said:**
> the average user is not going to be using ffmpeg and mplayer, as they are both pretty advanced programs when there are far simpler alternatives which they will most likely be using, like avidemux and vlc.
I disagree.  WinFF is a popular GUI for FFmpeg that is often mentioned in this forum, so FFmpeg is being used by "average" users, although they may not know it.  Also, VLC uses libavcodec, which is part of the FFmpeg family, for all video and audio decoding.  Avidemux uses parts of libavcodec, but it is integrated within the program.

---

### Post by andrew.46 on 2009-02-09
Hi Polygon,

Not trying to gang up on you here:

> **Polygon said:**
> the average user is not going to be using ffmpeg and mplayer, as they are both pretty advanced programs when there are far simpler alternatives which they will most likely be using, like avidemux and vlc.

Fakeoutdoorsman has mentioned several programs that use FFmpeg and this would be a good time to mention the frontend for MPlayer: SMPlayer which is always a better program when it does not have to rely on the aged version of MPlayer available in the Ubuntu Repository.

But can I also say that there will always be those who wish to at least make a start with the *actual programs* FFmpeg and MPlayer, programs whose complexity I believe is often a little exaggerated. These people need to have access to the *full* program to learn properly and if only this were available with a simple apt-get this learning would be so much easier.

Andrew

---

### Post by Polygon on 2009-02-09
i dont get why you are arguing about this when you know its impossible for the full mplayer to be included in the ubuntu repos. 

and they have access to the full program, except for decoders which ubuntu does not have legal rights to distribute. they play free/open formats fine.

---

### Post by andrew.46 on 2009-02-10
Hi Polygon,

> **Polygon said:**
> i dont get why you are arguing about this when you know its impossible for the full mplayer to be included in the ubuntu repos. and they have access to the full program, except for decoders which ubuntu does not have legal rights to distribute. they play free/open formats fine.

No not arguing just having a good old fashioned discussion about the various issues involved :-).

Just to mention a couple more issues: Both FFmpeg and MPlayer are gearing up for a 'dual' release within a week which I guess means that Ubuntu will no longer have a reason to keep using the ancient version of MPlayer at least in the repository. Not sure how that fits in with the release of Jaunty Jackalope?

And finally I would also like to mention the Slackware experience. Rather than package a weakened, older version of either FFmpeg and MPlayer and rather than face potential legal problems with some decoders Slackware chose not to distribute either program. This approach is more sensible than it might seem at first reading and it leaves the keen to pursue these programs with the superlative Slackware compiling environment to back them up. Better this way than distributing only parts of both programs?

Andrew

---

### Post by 3rdalbum on 2009-02-10
FFMPEG is a full version in the Ubuntu repositories - you just have to install the "unstripped" packages.

The version of MPlayer is ancient though, and Ubuntu really should use a good svn version. Switching to a new Mplayer solved one persistent kernel panic and allowed me to play ripped Blu-rays.

---

### Post by qazwsx on 2009-02-10
So Ubuntu should simply divide their repos. In EU all patented formats would be available just like that but not in USA. I think Debian does it?


Anyways it is a great shame to see rc2 version of mplayer in Ubuntu repos.


I compile them on weekly basis.:)



MPlayer ouperforms all the players clearly. No question about it. Xine does lot of frame droppings on SD 50 fps 576p 3200 kbps H.264 but that is not even close with MPlayer.

---

