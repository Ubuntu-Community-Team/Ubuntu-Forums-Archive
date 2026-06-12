---
title: "LÖVE2D having issues running code/packaging"
date: 2013-10-16
forum: Ubuntu Application Development
---

### Post by JayArtist on 2013-10-16
Hi,

I'm keen to get into the Love:
[http://love2d.org/](http://love2d.org/)

But I'm having issues with launching/running code - I'm just not feeling the 'love' :(

I've followed the tuts here and there online, but I'm unable to launch a home-made program.

I'm  using ubuntu 13.04 and installed Love through the Software Centre (so I  haven't done anything weird) - if I launch 'Love' through the menu  (unity) the piggy with hearts appears in a window. If I run the supplied  'examples' with the love extension i.e. "examples.love", they launch  and work fine.

But if I create my own "Hello World" I always get the same error:

[B]boot.lua:335: No code to run
Your game might be packaged wrong[/B].... etc.

Now  I know all noobs probably get the same issue because they package the  external folder when they shouldn't - in this case I haven't, 'main.lua'  is in the root of the archive and should run, but it doesn't.

I've tried two methods to run, one, by double clicking on the file, up pops the error above in a nice blue window.
I've also tried launching from the Terminal in the directory i.e. 'love myapp.love', but the same error.

Any ideas what to do guys?

---

### Post by JayArtist on 2013-10-17
Solved, it was a stupid typo .lau, when it should have been .lua - anyho ;)

---

