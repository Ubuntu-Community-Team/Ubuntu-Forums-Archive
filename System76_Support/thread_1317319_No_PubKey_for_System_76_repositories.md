---
title: "No PubKey for System 76 repositories?"
date: 2009-11-06
forum: System76 Support
---

### Post by bill516 on 2009-11-06
Tom, I need a Linux lesson, I think.  I have upgraded to 9.10.  A bad disk forced me to do this by upgrading from 8.10 to 9.04 to 9.10 - definitely not the way to spend an afternoon!

All works well, seemingly.  So now I need to add the updated 9.10  System 76 driver to my system.  I attempted to follow the HowTo at the System 76 site, but the tabs at System/Administration/Software Sources have changed slightly.  I cannot add the planet76 repository by simply clicking a box.

So I added it manually by typing "deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./"
This seemed to work.  It produced the planet 76 listing with a properly checked box.

Then I clicked the "UpDate" Button to renew listings and got the following"

"W:GPG error: http: //planet76.com./ Release:  The following signatures couldn't be verified because the public key is not available.  No pubkey 176A5C84ED67C9ED"

I believe I have to supply that key.  Where do I get it and how do I do it?

Assuming all this works, do I then get the new driver as one of several updates through the normal Ubuntu system?  (which appears to hae changed somewhat from 8.10)

---

### Post by thomasaaron on 2009-11-06
To fix the GPG key error, please run the following command:

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by bill516 on 2009-11-06
Thank you, Tom, that turned the trick.

Bill

---

