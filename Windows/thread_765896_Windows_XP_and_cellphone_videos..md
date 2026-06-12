---
title: "Windows XP and cellphone videos."
date: 2008-04-24
forum: Windows
---

### Post by bill_dotson on 2008-04-24
When I copy my cellphone videos over to my Desktop in XP, I can view the video, but the audio is not being played.  I have Windows Media Player 11 installed, the latest VLC player (with support for all the video and audio codecs it can support included), the latest version of Miro (formerly Democracy Player) and ffdshow (with the default codecs chosen).  Even after a reboot after I installed ffdshow it is still doing this.  

I think the problem here is with the AMR codec.  However, when I transcode the .3gp videos in say, .wmv files, I can hear the sound perfectly.  What is the deal with the AMR audio stream?  I thought ffdshow included support for that.  I am going to install quicktime (ugh) and run it in there; I hear QuickTime supports the AMR codec.

I tried dealing with these files in Ubuntu Gibbin, but even after installing mplayer with the default codecs I still could not even play the video, and since AMR has so many restrictions on it, support is non-existent in GNU/Linux.

---

### Post by sayakb on 2008-04-26
VLC plays 3gp fine for me. Try the K-Lite mega codec pack or Vista codecs pack. They would have the ffdshow codec you mentioned, plus some more of the required codecs.

---

### Post by NilsE on 2008-04-26
I use mplayer on both Ubuntu and XP for 3gp and mp4 videos with no problems.  WMP 11 does the same as you explained, good picture no sound.

---

### Post by Jiraya on 2008-04-29
> **bill_dotson said:**
> When I copy my cellphone videos over to my Desktop in XP, I can view the video, but the audio is not being played.  I have Windows Media Player 11 installed, the latest VLC player (with support for all the video and audio codecs it can support included), the latest version of Miro (formerly Democracy Player) and ffdshow (with the default codecs chosen).  Even after a reboot after I installed ffdshow it is still doing this.  

I think the problem here is with the AMR codec.  However, when I transcode the .3gp videos in say, .wmv files, I can hear the sound perfectly.  What is the deal with the AMR audio stream?  I thought ffdshow included support for that.  I am going to install quicktime (ugh) and run it in there; I hear QuickTime supports the AMR codec.

I tried dealing with these files in Ubuntu Gibbin, but even after installing mplayer with the default codecs I still could not even play the video, and since AMR has so many restrictions on it, support is non-existent in GNU/Linux.

I use K-Lite Mega Codec Pack ([http://www.free-codecs.com/download/k_lite_Mega_Codec_Pack.htm](http://www.free-codecs.com/download/k_lite_Mega_Codec_Pack.htm)) and Media Player Classic that cames with it. Try to uninstall all codecs you've installed before, restart the computer and install K-Lite.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

