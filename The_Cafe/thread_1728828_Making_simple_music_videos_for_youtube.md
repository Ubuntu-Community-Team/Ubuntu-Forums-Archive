---
title: "Making simple music videos for youtube"
date: 2011-04-14
forum: The Cafe
---

### Post by slackthumbz on 2011-04-14
And I do mean simple, we're talking 1 jpeg + an mp3 here. I found pitivi and one or two other gui suites a total pain to do this so I knocked up a perl script (code [here]("http://www.thumbnail.org.uk/cgi-bin/archive/post/1301666641")) to streamline the process. This uses mencoder and exiftools so you'll need them installed too.

Hopefully this will be useful to a few people :)

---

### Post by leviathan8 on 2011-04-14
After I've done a video project on PiTiVi, I realized that .ogv is actually incompatible with YouTube. So I grabbed KDEnLive, recreated the project, selected rendering for Web sites -> YouTube and I successfully finished it. Imho, PiTiVi is a bit overwhelming for new users, in special those who create videos for YouTube.

---

### Post by slackthumbz on 2011-04-15
Well, the other problem I found was that the project rendering took forever (quite literally between 1 and 2 hours) in all of the gui applications I tried. My script usually completes in under 5 seconds.

---

### Post by lisati on 2011-04-15
Remember to be aware of copyright issues. In some cases, Youtube will recognize a piece of music in a soundtrack and ask you to change it.

---

