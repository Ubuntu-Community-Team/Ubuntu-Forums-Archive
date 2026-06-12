---
title: "Says a folder is sync'd, but it isn't listed"
date: 2010-08-21
forum: Ubuntu One (CLOSED)
---

### Post by Sageth on 2010-08-21
I did some searching, but haven't found a good solution to this problem I'm having.  While there are a lot of issues with syncing between my desktop and netbook (we'll get to them another time), I am really trying to get two folders from my desktop to sync to Ubuntu One.  I followed the reinstall steps here a few times ([http://ubuntuforums.org/showthread.php?t=1297076](http://ubuntuforums.org/showthread.php?t=1297076)) and it has almost fixed the problem.

My last issue is that my .mozilla folder won't sync at all.  If I right click on it in Nautilus, I get a greyed out "stop syncing with Ubuntu One."  I can't stop it and can't start it.  If I do u1sdtool --list-folders, then this folder isn't shown.  I've tried disconnecting, reconnecting, and a lot in between.  

My question is, is there a config file or something like that where maybe this .mozilla folder is still set up that I can just delete?  Clearly, it thinks it's set up when it isn't and I'm not sure if there's somewhere on the filesystem that can be checked or cleared.  One thing I did notice when I was going through the instructions above is that I don't have a .share folder and thus no /local/ubuntuone under that.  Could that be a problem?

---

### Post by ellis rowell on 2010-08-22
My experience with sync'ing is that it's only the data files which sync. I have saved data files into the Ubuntu One folder, it sync's with the cloud and if I then use the other computer the data files are sync'd on that.

---

### Post by Sageth on 2010-08-22
Thanks, I understand that.  Basically, the files won't sync.  It says that they are, but when you --list-folders, the folder doesn't show up.  I can't stop the folder through Nautilus (it's greyed out) and I can't start the folder through the command line (it's not listed).  I feel like I'm basically screwed.

---

### Post by ellis rowell on 2010-08-23
I have just tried drag and drop with a picture into the Ubuntu One folder. It was updated on the cloud and when I deleted it, it was deleted on the cloud. Do you have a Ubuntu One folder on your desktop, it should be there. That sync's with the cloud.

---

### Post by Sageth on 2010-08-23
I appreciate the help, but I'm clearly not explaining this right.  

I'm syncing a folder at /home/username/.mozilla/
When I hit the drop down, it's greyed out and says "stop syncing" -- so I can't stop it. 
When I go to one.ubuntu.com, the folder isn't there.  I can't do anything with it.

The client thinks it's syncing, but it's not.  The folder doesn't show up on the cloud and I can't stop sharing it in nautilus.  

Tomorrow when I'm home, I'll put screenshots up if I need.  That might illustrate better.

---

