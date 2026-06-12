---
title: "Open source in multiverse"
date: 2013-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by kd5vdo on 2013-11-22
Howdy!

My understanding is that some of the software in the multiverse repository is open source even if its licensing is not free. For example, maelstrom, if I remember correctly, is open source, but there are issues with the license on the graphics. Regardless, I don't want to introduce closed-source software to my systems, but I don't have Stallman Syndrome either. Does anyone know of a good way to enable multiverse but restrict it to packages with source? Also, any ideas why they would lump all this software into one repo instead of separating out open-source/non-free from plain vanilla non-free?

---

### Post by lykwydchykyn on 2013-11-23
I guess in theory you could just enable a source repository, and install things from it using "apt-src" or "apt-get source".  Otherwise, you're going to have to do the legwork yourself, if the distinction is that important to you.

---

### Post by grahammechanical on 2013-11-24
This wiki page page explains that in Ubuntu the repositories are

Main: Officially supported software

Restricted: Supported software that is not available under a completely free license.

Universe: Community maintained software, i.e., not officially supported software.

Multiverse: Software that is not free.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

"Free" is used in this context

[http://www.ubuntu.com/about/about-ubuntu/our-philosophy](http://www.ubuntu.com/about/about-ubuntu/our-philosophy)

If I understand the definition of Free and Open Source Software then software is not 'free' if the source code is not 'open.'  The Software and Updates utility describes multiverse as "software restricted by copyright or legal issues." And we find that this is different from proprietary video drivers which are in the Restricted repository, even though the source code of the drivers is not open.

Regards.

P.S. What is the issue with Maelstrom? It is now released under the Creative commons license. And here is the source code.

[http://www.libsdl.org/projects/Maelstrom/source.html](http://www.libsdl.org/projects/Maelstrom/source.html)

[http://en.wikipedia.org/wiki/Maelstrom_(1992_video_game)](http://en.wikipedia.org/wiki/Maelstrom_(1992_video_game))

It does require something called Simple DirectMedia Layer which has the zlib license. which says

> Permission is granted to anyone to use this software for any purpose,
  including commercial applications, and to alter it and redistribute it
  freely, subject to the following restrictions:

  1. The origin of this software must not be misrepresented; you must not
     claim that you wrote the original software. If you use this software
     in a product, an acknowledgment in the product documentation would be
     appreciated but is not required.
  2. Altered source versions must be plainly marked as such, and must not be
     misrepresented as being the original software.
  3. This notice may not be removed or altered from any source distribution.

[http://www.gzip.org/zlib/zlib_license.html](http://www.gzip.org/zlib/zlib_license.html)

---

### Post by kd5vdo on 2013-11-27
Thanks for the replies guys. I'm not entirely sure what the problem is with maelstrom, I just remember it was in the multiverse repo despite being open source.

---

