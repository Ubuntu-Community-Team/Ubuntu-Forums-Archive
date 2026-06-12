---
title: "Virus removal"
date: 2010-01-17
forum: Security
---

### Post by driebel on 2010-01-17
Hi there, I have Dell XPS m1530, Intel dual core processor, 3 GB RAM, nVidia GEForce 256 MB video card.  I dual boot Vista and Hardy.

Last night, I noticed a serious slowdown in my computer's ability to play a blu-ray disc.  I looked at the usual suspects, unecessary programs running and virii.  Under Vista, Norton couldn't find any issues, but when I ran Clamscan under Ubuntu, I found 5 infected files:

./Dell/MediaDirect/Kernel/BD/VideoFilter/cl264dec.ax: Trojan.Crypt-280 FOUND
./Dell/MediaDirect/Kernel/BD/VideoFilter/cldabc.dll: Trojan.Crypt-280 FOUND
./Dell/MediaDirect/Kernel/BD/VideoFilter/cldabcd.dll: Trojan.Crypt-280 FOUND
./Dell/MediaDirect/Kernel/BD/VideoFilter/cldorz.dll: Trojan.Crypt-280 FOUND
./Dell/MediaDirect/Kernel/BD/VideoFilter/cldorzd.dll: Trojan.Crypt-280 FOUND

----------- SCAN SUMMARY -----------
Known viruses: 698363
Engine version: 0.94.2
Scanned directories: 5664
Scanned files: 44121
Infected files: 5
Data scanned: 8998.31 MB
Time: 1788.070 sec (29 m 48 s)

After directing some creative vocabulary towards one of my OSs, I contacted Dell, and they verified that I can safely remove all five of these files, they aren't legitimate files that have been infected, I can go ahead and wipe them out.

So how should I go about doing this?  Is rm sufficient?  I was thinking of using shred, but the man page mentions certain file systems that shred does not work under.  I'm quite a newbie, so I'm not sure if Vista is one of these.  Would I shred those files, only to discover that some sort of journaling has kept copies of these Trojans elsewhere?

Any help appreciated.  How do I terminate these things with extreme prejudice?

Dave

---

### Post by Settwi on 2010-01-17
Dave, you could directly delete the files from your harddisk, and then just 'Secure Empty Trash' I know it can be done in OSX, and i'm pretty sure i got it to work on x/kubuntu, too.

---

### Post by Tp2357 on 2010-01-17
I'd personally delete them from ubuntu, as a lot of viruses I have run into in the windows world have programming that doesn't allow them to be deleted. (It'll come up with an error with 2-3 hex addresses....) After the delete, also make sure to secure empty trash, and run another scan.

EDIT: Make sure you have NFTS Read/Write/Delete drivers, (if necessary), then navigate there using the command line (reply if you need help) then use the mdel command ([http://www.oreillynet.com/linux/cmd/cmd.csp?path=m/mdel,%20mdeltree](http://www.oreillynet.com/linux/cmd/cmd.csp?path=m/mdel,%20mdeltree)) to delete the files. 

Good luck!
tp2357

---

### Post by running_rabbit07 on 2010-01-17
Chances are these trojans are backed up in a restore point. I am not sure how to turn off system restore in Vista but in XP you had to rightclick on My Computer within the start menu, then click properties and then click system restore and turn it off. Once that is done redelete the files, then turn system restore back on so that it can make a new restore point.

I have fought the backed up virus before. Nothing as annoying to delete one, then see it again the next time the AV does a scan.

---

### Post by Tp2357 on 2010-01-17
[http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/disable-system-restore-in-windows-vista/)

Master of the search-fu.

---

### Post by driebel on 2010-01-17
Awesome, thanks so much to everyone.  Tp, can you clarify the difference between mdel and rm a bit?  I've manipulated files on my Vista partition before using both Nautilus and the command line, but always using rm.  I installed mtools just now, and will certainly use it if it's superior, but I'd like to understand the difference.

My current plan:
1.  Boot back into Vista
2.  Turn off system restore and delete all the restore points.
3.  Boot back into Ubuntu
4.  mdel some Trojans.
5.  Run several virus scans, probably in both OSs.

Again, thanks to everyone who replied, you are awesome!

EDIT:  TP, you also mentioned that I should verify I have NTFS drivers.  I know my Vista partition is NTFS, and I'm able to access/edit files on it from within Ubuntu, does that imply I have these drivers?

---

### Post by CharlesA on 2010-01-17
I would suggest scanning with something like BitDefender as ClamAV is kinda known for falsepositives.

Googled some of those files and they look like they are used for CyberLink's playback of Bluray.

---

### Post by driebel on 2010-01-17
Charles,

Wow.  I found your reply literally seconds before I was about to delete those files.  I'm looking around my self, but I think you may be right.
What is particularly irksome about this is that I specifically asked Dell's tech support people this exact question.  The fact that they seem to have flat out dropped the ball is going to get them a very thorough letter very soon...
I'll check out DitDefender.

---

### Post by CharlesA on 2010-01-17
I've got BitDefender running on my Ubuntu server (serving files to windows boxes) it's quite good at catching bugs and I haven't had nearly as many false positives as I did with ClamAV.

---

### Post by Tp2357 on 2010-01-18
> **driebel said:**
> Awesome, thanks so much to everyone.  Tp, can you clarify the difference between mdel and rm a bit?  I've manipulated files on my Vista partition before using both Nautilus and the command line, but always using rm.  I installed mtools just now, and will certainly use it if it's superior, but I'd like to understand the difference.

My current plan:
1.  Boot back into Vista
2.  Turn off system restore and delete all the restore points.
3.  Boot back into Ubuntu
4.  mdel some Trojans.
5.  Run several virus scans, probably in both OSs.

Again, thanks to everyone who replied, you are awesome!

EDIT:  TP, you also mentioned that I should verify I have NTFS drivers.  I know my Vista partition is NTFS, and I'm able to access/edit files on it from within Ubuntu, does that imply I have these drivers?

mdel is for deleting in microsoft partitions. 
( [http://en.wikipedia.org/wiki/Mtools](http://en.wikipedia.org/wiki/Mtools) )

As to your second question, not always. Ubuntu is pretty good about reading NFTS, but can have issues when writing nfts. Go to the software center, (Applications => Ubuntu Software Center) then type in NFTS write, install a package that will work for you.

Hope this helps!

Edit: Also, your plan looks very good. May I recommend that you back-up your system (vista) after you delete the Restore Points? I know that you will still have trojans, but It beats losing all that data.. :)

---

### Post by BigCityCat on 2010-01-18
I was reading this thread and installed bitdefender via their repository after requesting a key on their website. I was able to scan my ntfs and was amazed at how well it worked. Nothing found by the way.

adding the repository and install

[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

You still have to request a home use key.

[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

---

### Post by driebel on 2010-01-20
Again, thanks to everyone, this thread was very useful.

After Charles suggested that these might be false positives, I checked with cyberlink, the company that wrote my BD player.  They confirmed that yes, these are completely legitimate files, and they are essential to the player.  My system is virus free, always has been.

I called Dell's tech support back, both to register my displeasure at their tech staff's ignorance and to point this out to them so it can be added to their knowledge base/training program as a known issue.  They were extremely unhelpful.  No one I could speak to knew how to contact their own organization to leave feedback of this nature.  _Extremely_ frustrating.

Customer Service:
Dell tech support:  F
Ubuntu Forums: A+

---

### Post by CharlesA on 2010-01-20
Gotta love commercial tech support zombies.

---

### Post by Tp2357 on 2010-01-20
Glad we could be of assistance.

---

