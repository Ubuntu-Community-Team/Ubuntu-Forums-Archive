---
title: "&quot;bake&quot; together 2 files to one"
date: 2008-09-30
forum: Ubuntu Studio
---

### Post by KanineN on 2008-09-30
Hello!

I have two files that I want to "bake" together to 1. The files are one part of a movie. The second movie start exactly after the first. Now I want to know if it is possible to bake together two files to 1. I don't want any delay. It shouldn't be possible to notice that it is two files that I have "baked" together.

---

### Post by IanW on 2008-09-30
try ```
cat movie1 movie2 > movie
```

---

### Post by MusicMastaMike on 2008-09-30
The above code only works if both files are mpeg's.  If they're not, you have to convert them to mpeg first using mencoder or ffmpeg.

---

### Post by aeiah on 2008-10-01
i use:
```

mencoder -forceidx -oac copy -ovc copy -o output.avi film_cd1.avi film_cd2.avi

```

the forceidx flag will stop any syncing issues. the video and audio is copied, not reencoded, so its fairly quick. it works on anything that's correctly encoded. its best to review the output.avi file though and see if the 2nd half has audio that is in sync before doing anything with it i guess. i only use it when converting to dvd though. if i just want the convenience when watching an avi movie i make sure mplayer loads both files and plays one after the other with this script
```


#! /usr/bin/python

import sys, os, optparse, os.path

from optparse import OptionParser
parser = OptionParser()
parser.add_option("-i", "--input", action="store", type="string", dest="video")
(options, args) = parser.parse_args()

s = options.video
t = s.strip().replace('cd1', 'cd2')
cd2 = t.strip().replace('CD1', 'CD2')
if s == cd2:
        os.system('''gmplayer "''' + s +'''"''')
else:
        os.system('''gmplayer -idx "''' + s + '''" "''' + cd2+'''"''')


```

although that'll only work if your video files have cd1 and cd2 in the name, or CD1 and CD2. i drop it in my /usr/bin, make it executible, and set all videos to open with the script instead of with gmplayer directly.

---

### Post by KanineN on 2008-10-01
Can you do it if the two files a .flv? 


And when I convert videos to my mobile the quality get bad. How do I make it better? What code do you use when you convert to phones?

---

### Post by aeiah on 2008-10-01
im not sure about .flv. why not give it a try? if its from youtube you can download a greasemonkey script that will show a direct link on the youtube page to the highest available quality .mp4 file for that specific video. you should be able to join these .mp4 files if not the .flv but i think ive joined .flv before too.

as for your mobile, it depends on what mobile it is and what the optimal settings for it are. a lot of automatic scripts will probably just convert to safe low quality settings so more phones are supported.

---

