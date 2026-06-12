---
title: "exporting WMP ratings to Linux"
date: 2007-12-06
forum: Windows
---

### Post by DouglasAWh on 2007-12-06
It appears at least in the past you could export your library as XML using WMP: [http://www.microsoft.com/windows/windowsmedia/knowledgecenter/howto/MediaInfoExp.aspx](http://www.microsoft.com/windows/windowsmedia/knowledgecenter/howto/MediaInfoExp.aspx)

I've been using Ubuntu on my laptop for a while and am about to make the switch to Linux on the desktop too (potentially Fedora, but maybe Ubuntu).  There are two things that have held up the switch.

1) I have a huge WMP library and I use ratings extensively and I don't want to lose that.

2) I use three monitors (I used to use 4, but lightning killed one).  I have NEVER gotten dual monitors (much less tri) to work on Linux.  This is one of the reasons I'm thinking about going to Fedora, because their dual monitor support is supposed to be better.

The monitor issue opens up a bag of worms, and I'm ready to just give up on that, but if someone can tell me a media player on Ubuntu or Fedora that will accept whatever WMP exports, that would be awesome.  Of course, I'll have to keep the music in the same file structure.  If anyone can tell me if 11 still exports that would be helpful too.

Thank you!

---

### Post by DouglasAWh on 2008-02-18
I've been poking around and WMP has a feature called "maintain my star ratings as global ratings in files."  However, in Vista (at work), when I do this, neither iTunes nor musikCube pick up those ratings.  My box has given me so many problems lately I am really wanting to take it to Linux, but I really cannot lose my ratings.  I find it very hard to believe no one has had this issue in the past.  Thanks!

EDIT: it appears this can be done Windows to Windows: [http://tinyempire.com/shortnotes/files/windows_media_player_ratings.htm](http://tinyempire.com/shortnotes/files/windows_media_player_ratings.htm)

EDIT2: something like [http://jrmwillis.googlepages.com/home2](http://jrmwillis.googlepages.com/home2) from Windows to Linux would be nice...

---

### Post by DouglasAWh on 2008-02-21
I got this response on mozillazine.org

> 
Look for files in your Linux system "x-MS-*" and "MS-*" and "vnd.*" to find what meta, wmp, wmv and other media support files exist.There was a recent update to "rythym box" which helped cross platform transfer. You might also want to do a search in the repos (turn them all on).


Anybody care to comment?

---

### Post by Kementari on 2008-02-21
I solved this issue by using playlists. While not a very techy solution, nor one that would be convenient to use on a regular basis, it worked.

1. Create a playlist of all songs with each rating, either by sorting your collection by rating, or by use of auto playlists.
2. Open playlists in Linux. This may require editing them (i.e. I had to change file paths using kate's replace from D:\Music to /media/secondary/Music)
3. Change ratings in linux media player.

As long as the directory tree of your music folder is intact, you should be fine. Play counts were lost, along with any other stats, but I didn't care much about those.

---

