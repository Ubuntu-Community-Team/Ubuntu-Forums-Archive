---
title: "what?"
date: 2007-07-22
forum: Ubuntu Backports
---

### Post by Chymera on 2007-07-22
yes, i have read the the whole post at [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291) but i still dont get it:

1) WHAT are backports? eg. how does one look, where is it located
2) how can i use backports?

---

### Post by angryfirelord on 2007-07-22
Backports are simply used to update a few packages. See, in a version of Ubuntu, the package versions stay the same. The only updates that come through are just security updates, which is not the smae as actually upgrading the package. The backports, however, will give you a newer version of that package. 

To use them, go into your /etc/apt/sources.list file and take out the # sign in front of the lines that say feisty-backports.

Or, go to Synaptic-->Settings-->Repositories and enable them.

---

### Post by Chymera on 2007-07-23
10q, thats the information i was missing. On the other hand, when gutsy gibbon comes out, and if i upgrade to it, all the apps will be up-to date again, right? (and, of course they will become out-of-date until the release of h-h)

Will enabling backports make upgrading to gutsy gibbon easier?


Edit: Ok... ive looked under synaptic/settings/repositories and saw that most of the stuff was already checked. Under "ubuntu updates" (in the updates tab) the "security updates" box was checked with a V and the "recommended updates (fiesty updates)" with a -. I checked the latter with a V and got the following notification. (the last of the entries under ubuntu updates contained the word backpotrs in it so i checked that too, and got yet again the same message)

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

After that i closed synaptic and did indeed get noted about some updated. Whats with that error?

---

### Post by angryfirelord on 2007-07-23
You didn't import the key. Try running this command:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Now you shouldn't get that error.

---

### Post by Chymera on 2007-07-23
ok, worked fine, 10x again :) ...

But whats with the key? what function does it have, if i got notified of those updates even without it?

---

### Post by angryfirelord on 2007-07-23
The key basically tells apt that it's a trusted source. Without it, you'd get that annoying error message, so it's always best to install it.

---

### Post by Chymera on 2007-07-24
ah ok... it thought the error message would be an omen of a lot of problems to come, not the problem itself

---

