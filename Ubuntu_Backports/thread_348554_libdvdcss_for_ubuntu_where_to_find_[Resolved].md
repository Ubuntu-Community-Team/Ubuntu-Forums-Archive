---
title: "libdvdcss for ubuntu: where to find? [Resolved]"
date: 2007-01-28
forum: Ubuntu Backports
---

### Post by quixote on 2007-01-28
The ubuntu-fr.org/plf site seems to have disappeared.  (I don't remember the URL exactly, but you probably know what I mean.  jdong's earlier post in Mar 2005 referred to it.)  

I've tried to compile the source from the VLC site, but get hundreds of warning and error messages. I think I'm missing about fifteen dependencies and the whole thing makes my eyes glaze over.  

It would really, really, really be nice to use adept and have it do it's usual clean and effortless job.  Where can I find a repository with libdvdcss (or libdvdcss2 -- I'm not sure the difference is)? (I'm running edgy.)  Or if there is no repository, is there a site with simple, step-by-step instructions that work?  VLC, much as I love and admire that project, is assuming way more knowledge than I have.

Please help!  I usually get all my movies from archive.org, which works great since my favorite is Buster Keaton.  But now I had to get a dvd for work, I use Ubuntu at home, and I can't even work on this stupid thing that cost me $120!  I'm fit to be tied.  

Assuming I ever get libdvdcss installed correctly, is there any trick to using it?  Will vlc just realize it's there and play the dvd?  Alternatively, what else could I be using besides libdvdcss?  

(Yes, I'm in the US.  No, I don't care what the DMCA says.  Right now I feel like fighting the bastards all the way to the Supreme Court on Fair Use grounds, and claiming damages!)

---

### Post by meng on 2007-01-28
Install libdvdread3
then run
/usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by aysiu on 2007-01-29
PLF has moved:
[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by quixote on 2007-01-30
You folks are life savers!  The method that worked for me was the repository and then using adept.  

Libdvdread3 was already installed on on my system, so I ran the install-css.sh command.  That gave me libdvdcss.deb in /tmp, which was promising, but then I didn't know what to do with it.  Nothing seemed to happen when I ran vlc.  I'm obviously missing a few steps somewhere.

However, the mediubuntu repository was simple enough.  I added it to sources.list like the instructions said, updated, installed ... and suddenly everything worked, the dvd plays, and I can get my work done!

Thank you, thank you, thank you!

---

### Post by alarichall on 2007-02-11
I hope you don't mind me hitching on your thread. I'm very ignorant about Ubuntu. Whenever I try to play DVDs (in Movie Player or VLC media player, for example), I get the message
[INDENT]The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/INDENT]
I have followed the instructions at [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/). I have also installed used Automatix2 to install 'AUD-DVD codecs'. So surely I should have libdvdcss? I'm at a loss for what to do.

I'm using edgy eft, on a Thinkpad T40.

Any advice would be much appreciated.

---

### Post by aysiu on 2007-02-11
Try pasting these commands in the terminal: ```
wget -c http://medibuntu.sos-sts.com/repo/pool/edgy/free/i386/libdvdcss2_1.2.9-2medibuntu2_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
```

---

### Post by quixote on 2007-02-11
Hi alarichall-  I had much the same experience as you: I'd do things that sounded like they should work, but then they wouldn't.  Yes, I was trying to play a so-called "encrypted" dvd on Linux.  I put it in quotes because it was some kind of very weak encryption, and things may be different if you're trying to play something locked up with everything MPAA can hang onto it.

  I "installed" (i.e. I thought I installed) libdvdcss about four times, but for some reason it just wasn't available to vlc.  Just keep trying things -- like aysiu's suggestion -- and once the Ubuntu understands that libdvdcss really is there, everything will suddenly work.  :popcorn:

---

### Post by ricardisimo on 2007-06-12
Medibuntu has [moved.]("http://ubuntuforums.org/showthread.php?t=471089")

---

