---
title: "Determine if screen is locked in c++/bash"
date: 2014-10-23
forum: Ubuntu Application Development
---

### Post by wardexter on 2014-10-23
Hi,

I'm trying to figure out the best way to determine if the screen is locked or not.
So far i've figured out this works:
     gdbus call -e -d com.canonical.Unity -o /com/canonical/Unity/Session -m com.canonical.Unity.Session.IsLocked

But this call only works on some pc's. I have two pc's that have this method call. All my other pc's don't have it. Don't know the reason why, but they are all ubuntu 14.04LTS with latest updates. So they should be as good as identical.

Since this is not a consistent way of determining screen lock, I'm trying to figure out another option, but I'm out of ideas.

Is there any API available that can do this or any other utility?
I will use it from a Qt application, so an API would be nice, but a system call is also an option.

Thanks!

---

