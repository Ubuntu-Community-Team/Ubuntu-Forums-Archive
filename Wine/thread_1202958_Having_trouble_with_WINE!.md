---
title: "Having trouble with WINE!"
date: 2009-07-02
forum: Wine
---

### Post by briansurgery on 2009-07-02
It just won't work. I mean, I know very little about the program, and their website doesn't do much to help. How do I get it to load programs for me? It automatically took control to install Yahoo Messenger, but now I click on the desktop icon, and nothing happens.

Also, WINE doesn't read my entire Windows drive. I have some files I'd like to pull over, but WINE should do that, right?

---

### Post by synapsys on 2009-07-02
It would be a good idea to use pidgin for your instant messaging, as it is natively supported in ubuntu.

Wine is not in charge of 'seeing' your windows drive. You need to mount it, which will put an icon on your desktop. Click the icon and you will be able to copy over files. To mount easily, go to 'Places' and click the windows partition.

---

### Post by Archimedes0212 on 2009-07-02
I think you are a little misinformed about what WINE does exactly.  It is NOT a windows 'viewer' or 'emulator'

Basically it is a set of libraries that simulate key functions in windows, allowing some windows programs to open, run, function, etc in a linux environment.

With this being said, I am going to strongly emphasize the SOME part of my last statement.  There is no guarantee that it will work.  As the post before mine suggested, I would strongly recommend finding a native linux alternative - there are plenty of them out there and they work marvelously!

I once tried to install iTunes via WINE - it worked, but eventually it started wreaking havoc on my computer.  Things that I have gotten to work via WINE are things like DVDShrink and other various small programs.  However, with some searching, I've found equivalent linux alternatives (ie: DeVeDe for DVDShrink)

I guess long story short, give some programs a shot - they may just work with WINE.  Otherwise, look for a linux alternative.  There are plenty to choose from (even just looking in Add/Remove programs)

Good Luck

---

### Post by sdlynx on 2009-07-02
Agreed with the above two posters.

Pidgin is a great alternative to Yahoo Messenger.  And WINE only creates an environment in which you can run windows programs, it does not actually use your windows partition (which you must mount separately).  If you want to use the programs you have on windows you will have to reinstall them through WINE, and even then it is possible they will not work as WINE is not a perfect windows emulator.

Good luck,
sdlynx

---

### Post by philcamlin on 2009-07-02
wine is a fake windows drive you cat see any windows apps unless you mount it never the less run them :)

---

### Post by briansurgery on 2009-07-04
Okay. The only reason I tried to get Yahoo Messenger to work is the lack of a Webcam function in Pidgin. Is there any IM alternative for Ubuntu that supports Webcam?

---

### Post by Mia1990 on 2009-07-04
Kopete supports web cams

---

### Post by chepe263 on 2009-07-05
Fist, i didn't read all the replies. Second, why don't use Pidgin? If you don't like pidgin you also can use meebo.com. It's better if you make a new launcher because .lnk doesn't work. For the windows drive why just don't go to /media/[win_c]/ ???? it's easier!!


chepe263
ubuntu 9.04

---

