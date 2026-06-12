---
title: "JVC Everio GZ-MS95SE - .mod problem"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by drorata on 2010-01-10
If you got to this thread, then you probably already know that there is a problem with the JVC Everio. The files are being saved in the .mod format, which is apparently some variation of MPEG2. Nevertheless, in my case, I just changing the file's suffix into .mpeg didn't do the trick. I still got the **interlace**!

When opening a .mod file using *KINO*, the software automatically converted the file into .DV file. Here there was no interlace, but the file size doubled itself.
If a .dv file is needed the, I found that using *ffmpeg* one can easily convert the .mod into .dv:
```
ffmpeg -i inputfile.mod -deinterlace -target dv outputfile.dv
```

But this wasn't the right solution for me. I don't need high quality videos, and I was happy with the default results of the JVC. If only I could get rid of the interlace.

After many attempts, I came out with the following code, aiming at converting the .mod files into .mpeg files:

```
ffmpeg -i inputfile.mod  -deinterlace -acodec ac3 -ab 384k -b 8900k -s 720x576 -f mpeg outputfile.mpeg
```

This was satisfying! Nice video/sound quality. **BUT**, when I uploaded it to *YOUTUBE*, there was **no** sound.

The final version of conversion that I came out with, at least up until now, is:
```
ffmpeg -i inputfile.mod -deinterlace -ab 384 -b 8900k -s 720x576 -f mpeg outputfile.mpeg
```

This conversion maintain a good video/sound quality, and when uploading to YOUTUBE everything is smooth.

The last step, with some help of my friend Tobias P. was to automate the procedure. For that Tobias wrote the following *Python* script:
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import os,sys

if len(sys.argv)>1:
    for infile in sys.argv[1:]:
        outfile = os.path.splitext(infile)[0]+".mpeg"
        cmd = 'ffmpeg -i "%s" -deinterlace -ab 384k -b 8900k -s 720x576 -f mpeg "%s"' % (infile, outfile)
        print cmd
        os.system(cmd)
else:
    print "usage: %s FILENAME" % sys.argv[0]

```

I have located the file in ~/.gnome2/nautilus-scripts and linked it to /usr/bin; thus I have it in the context menu of nautilus. In addition, this script, enables a batch conversion of the form:
```
jvc2mpeg *.mod
```

A the moment, this is the solution I am using. If you find it useful - then the pleasure is mine. In case you have some comments, ideas or improvements, I will be happy to know them.

---

### Post by tripower on 2010-07-16
I don't see a .mod file but i do see an .mts file. Any solutions.

---

### Post by drorata on 2010-07-29
Sorry but I don't know this kind of file. Are you using a JVC camcorder?

---

### Post by haggus on 2010-09-06
I had to change the jvc2mpeg *.mod command. My files are .MOD upper case. Thanks for the script now I can convert my Disneyland videos.

I just have to add this method is way faster than the kino import method.

---

### Post by drorata on 2010-09-07
It is nice to have such a feedback! Thanks!

---

### Post by MickoD on 2011-03-14
I have to say mate, this is genius. Thank you so much. I've been looking for a non JVC Prop. way of doing this for some time now with the specific requirement that it had to be non-Windows. Kudos to you and Tobias for this solution :)

I'm your newest fan!!!

Thank you so much.

---

### Post by SoggyCornflake on 2011-11-11
> **tripower said:**
> I don't see a .mod file but i do see an .mts file. Any solutions.
Looks like you can use the same script just change the MOD extension to .MTS.

---

