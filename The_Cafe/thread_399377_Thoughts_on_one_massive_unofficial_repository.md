---
title: "Thoughts on one massive unofficial repository?"
date: 2007-04-02
forum: The Cafe
---

### Post by plb on 2007-04-02
For those who have used Ubuntu for some time I'm sure you've noticed that there is pretty much a repository for everything. Does anyone else think it would be a good idea to just setup a single massive user contributed repo? Now, of course there would have to be guidelines as we wouldn't want just anyone uploading anything. We would need a team to verify file contents as well as integrity before they are uploaded into the repo. We would also need a reliable server and good amount of space. I think such a thing could seriously benefit the community. Think about all the updated packages between releases that people are always looking for and/or breaking their systems trying to install. 

There should also be e a web page listing all the available packages along with a rating of how well the package works, which version of ubuntu, comments, requests, etc. What do you think?

---

### Post by ssam on 2007-04-02
wont [click'n'run]("http://cnr.com/") provide this quite well.

---

### Post by plb on 2007-04-02
> **ssam said:**
> wont [click'n'run]("http://cnr.com/") provide this quite well.

Isn't this mainly for proprietary software? Also afaik that is run by the "corporate world" whereas this would be run by the Ubuntu community

---

### Post by darrenm on 2007-04-02
Whats wrong with the Ubuntu repositories? Theres lots in there and if you want unsupported then enable the multiverse and universe repo's.

---

### Post by plb on 2007-04-02
> **darrenm said:**
> Whats wrong with the Ubuntu repositories? Theres lots in there and if you want unsupported then enable the multiverse and universe repo's.

There's nothing wrong with them but when a new version of an app comes out people want it e.g. banshee, frozen-bubble, rhythmbox, murrina engine whatever and most people would prefer to install via apt rather than build from source. Now sometimes you can find repo's or even debs floating around the forums but sometimes you can't hence my desire for one unofficial repo.

---

### Post by ssam on 2007-04-02
for new versions of software that is the official repos you can request a backport.

click 'n' run will cover open source software too, and i expect it will often have versions newer than ubuntu. click'n'run's background is no more corporate than ubuntu's.

---

### Post by plb on 2007-04-02
> **ssam said:**
> for new versions of software that is the official repos you can request a backport.

click 'n' run will cover open source software too, and i expect it will often have versions newer than ubuntu. click'n'run's background is no more corporate than ubuntu's.

Well I'll have to wait and see about click n' run but hopefully it is as you're saying it is. As far as requesting backports well just because you request it doesn't mean it's going to happen sadly.

---

### Post by mykalreborn on 2007-04-02
> Isn't this mainly for proprietary software? Also afaik that is run by the "corporate world" whereas this would be run by the Ubuntu community
it's not proprietary software, or not *just* proprietary software. i'm sorry to say this and i don't want to sound disrespectfull, but i've seen this in so many places. this is just ignorance. cnr is not run "by the man". cnr is a wonderfull alternative to software packaging. 
you've probably read this, but just in case: [cnr threads]("http://ubuntuforums.org/showthread.php?t=356211&highlight=cnr")

---

### Post by Nonno Bassotto on 2007-04-02
In any case the universe is already a big central repository mantained by the community. They update packages as often as they can, given the number of people working on it. If you want to contribute, just contact the MOTUs.

---

### Post by aysiu on 2007-04-02
> **plb said:**
> Does anyone else think it would be a good idea to just setup a single massive user contributed repo? Now, of course there would have to be guidelines as we wouldn't want just anyone uploading anything. We would need a team to verify file contents as well as integrity before they are uploaded into the repo. We would also need a reliable server and good amount of space. I think such a thing could seriously benefit the community. Think about all the updated packages between releases that people are always looking for and/or breaking their systems trying to install.  This already exists. It's called the Universe repositories.

---

### Post by kanem on 2007-04-02
> **plb said:**
> For those who have used Ubuntu for some time I'm sure you've noticed that there is pretty much a repository for everything. Does anyone else think it would be a good idea to just setup a single massive user contributed repo? Now, of course there would have to be guidelines as we wouldn't want just anyone uploading anything. We would need a team to verify file contents as well as integrity before they are uploaded into the repo. We would also need a reliable server and good amount of space. I think such a thing could seriously benefit the community. Think about all the updated packages between releases that people are always looking for and/or breaking their systems trying to install. 

There should also be e a web page listing all the available packages along with a rating of how well the package works, which version of ubuntu, comments, requests, etc. What do you think?

That's such a good idea, that it was already done:)This is how the backports repository started a few years ago. It was a mix of non-free stuff that couldn't be included in the official repositories and newer programs that hadn't made it to universe or main yet.

There was some contraversy that I don't remember, but it somehow eventually became an official repository, but also changed it's purpose.

Anyway, it would be nice to have just one repository outside of main. But is it such a hassle to have a few different ones? If it comes in a .deb format, it's pretty much guaranteed that it's in main, restricted, universe, multiverse, commercial or medibuntu. Maybe some of these could be merged?

---

