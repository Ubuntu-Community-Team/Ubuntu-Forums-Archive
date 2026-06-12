---
title: "Suggest new software to be included in standard distribution?"
date: 2016-12-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Elmi77 on 2016-12-23
Hi,

I would like to see the process control / HMI software from [https://sourceforge.net/projects/oapc/?source=directory](https://sourceforge.net/projects/oapc/?source=directory) included in the standard Ubuntu distribution. Unfortunately I'm neither the maintainer of this software nor in any other way involved in development.

So: would there be there a way to suggest such a software?

Thanks!

---

### Post by ian-weisser on 2016-12-23
You don't need to be a developer, maintainer, nor involved with the project to package software.
As long as the license is compatible with Debian, you -or anybody else- can package for Debian and Ubuntu.

The OpenAPC folks have gone to the trouble of creating their own deb repositories, don't make the source code available, and don't discuss the license on their website. It's possible that their license is incompatible. It's also possible that they are awaiting a volunteer like you to become their Debian maintainer.

Can you suggest software? Yes, by filing a wishlist bug at launchpad.net. 
Requesting this way is likely to be ignored: The number of volunteer packagers is small, and the list of such drive-by requests is very large.

After you figure out the license, the best way to get your favorite software into (or updated in) Debian/Ubuntu starts for you at [http://mentors.debian.net](http://mentors.debian.net).

---

