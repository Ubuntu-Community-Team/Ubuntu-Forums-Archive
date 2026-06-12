---
title: "Steam disk space issue"
date: 2009-05-01
forum: Wine
---

### Post by Jesst3r on 2009-05-01
Greetings all,

First of all, I should mention that I'm quite the Linux noob, so bear with me if I missed something obvious.  I've tried searching these forums and Google for my answer, but haven't really found anything.

I'm trying to get Steam working in Ubuntu 9.04 with wine 1.0.1.  I have Steam and a bunch of games installed on my Windows partition.  To avoid reinstalling all the games, I followed the instructions from [http://www.techenclave.com/gaming/run-orange-box-games-linux-without-104844.html](http://www.techenclave.com/gaming/run-orange-box-games-linux-without-104844.html) to get Steam to look at my windows partition's SteamApps folder.

Everything was working fine.  I got Steam installed, logged into my existing account and then exited to finish the instructions.  The problem is that once i created my symlink to the Windows SteamApps folder, I got an error about not having "enough disk space available to run this game." This happens while Steam is logging into my account, not even when I'm trying to play a game.  

According to df -h $HOME, I have 26G available.  Even if it was running off /, I still have 15G available there as well.  

Did I do something wrong?  Is there a way to show wine that I actually do have lots of space left?  Should I just bite the bullet and attempt installing the games over again?  I'd really like to avoid that, so getting the symlink thing working would be best.

Thanks for all your help!

---

### Post by asdfoo on 2009-05-02
> **Jesst3r said:**
> Greetings all,

First of all, I should mention that I'm quite the Linux noob, so bear with me if I missed something obvious.  I've tried searching these forums and Google for my answer, but haven't really found anything.

I'm trying to get Steam working in Ubuntu 9.04 with wine 1.0.1.  I have Steam and a bunch of games installed on my Windows partition.  To avoid reinstalling all the games, I followed the instructions from [http://www.techenclave.com/gaming/run-orange-box-games-linux-without-104844.html](http://www.techenclave.com/gaming/run-orange-box-games-linux-without-104844.html) to get Steam to look at my windows partition's SteamApps folder.

Everything was working fine.  I got Steam installed, logged into my existing account and then exited to finish the instructions.  The problem is that once i created my symlink to the Windows SteamApps folder, I got an error about not having "enough disk space available to run this game." This happens while Steam is logging into my account, not even when I'm trying to play a game.  

According to df -h $HOME, I have 26G available.  Even if it was running off /, I still have 15G available there as well.  

Did I do something wrong?  Is there a way to show wine that I actually do have lots of space left?  Should I just bite the bullet and attempt installing the games over again?  I'd really like to avoid that, so getting the symlink thing working would be best.

Thanks for all your help!

Running apps from NTFS partitions is not supported.  Please don't do this.  NTFS under Linux doesn't support the necessary features for Wine to work properly.

---

### Post by cogadh on 2009-05-02
Rather than try and deal with potentially messy symlinks to NTFS partitions, copy your entire Steam directory from Windows into your /home/<username>/.wine/drive_c/Program Files directory. After it finishes copying, delete the ClientRegistry.blob file (from the copy, not the original). Launch the Wine copy of Steam and log in. The .blob file will be recreated and all of your games will be fully downloaded, but will likely need an integrity check before they will launch. Note that if you happen to have any of the Steam games that have SecuROM activation limits on them, this may count as a new activation (if it works at all).

---

### Post by Jesst3r on 2009-05-02
Well I got it to work with a different method.  I went into my Windows partition and created a backup of the games I'd want to play.  I saved this to my NTFS drive, booted back into Linux and copied it over to my home directory.  Running the backup exe through wine let me install the games without having to redownload everything.  Now I have duplicate installations, but at least I didn't have to spend hours downloading everything.

Thanks for your help!

Now I just have to figure out how to make TF2 not crash when sound is enabled...

---

