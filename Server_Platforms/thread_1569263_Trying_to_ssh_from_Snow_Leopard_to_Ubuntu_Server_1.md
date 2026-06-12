---
title: "Trying to ssh from Snow Leopard to Ubuntu Server 10.04.1..."
date: 2010-09-06
forum: Server Platforms
---

### Post by waloshin on 2010-09-06
Trying to ssh from Snow Leopard to Ubuntu Server 10.04.1...

And of course i reinstalled Ubuntu last night and the RSA host key has changed so how do I change the host key on my Macbook to match the Ubuntu Server so I can ssh into my server?


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is


Please contact your system administrator.
Add correct host key in /Users/myusername/.ssh/known_hosts to get rid of this message.
Offending key in /Users/myusername/.ssh/known_hosts:2

Now the problem is I click on Mac osx then Users/ then my username/???? then there is no .ssh folder?

---

### Post by 0004tom on 2010-09-06
Are you enabling hidden floders in finder?

---

### Post by waloshin on 2010-09-06
> **0004tom said:**
> Are you enabling hidden folders in finder?

Thanks you!

Fix for everyone in the future:

Open up terminal then type:

defaults write com.apple.finder AppleShowAllFiles TRUE
killall Finder

And to hide the folder again just type:

Fix for everyone in the future:

Open up terminal then type:

defaults write com.apple.finder AppleShowAllFiles FALSE
killall Finder

---

