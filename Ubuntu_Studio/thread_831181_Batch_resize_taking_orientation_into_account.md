---
title: "Batch resize taking orientation into account"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by harck on 2008-06-16
Hello,

I'm using convert (part of ImageMagick) to resize my pictures in batch before uploading them. However, I've discovered something very annoying:

when resizing a bunch of picture to 600x400 for example (using convert -resize 600x400), the pictures which are "landscape" oriented will effectively be resized to these dimensions, whilst the "portrait" oriented pics will be resized to 269x400, instead of 400x600 as expected.

Is there an option for convert to take the orientation into account when resizing?

Thank you!

---

### Post by marialice on 2008-06-16
Are the source images all the same size? Then resize with a percentage instead of an absolute value.

---

### Post by harck on 2008-06-16
Yes that could have been an option, but sometimes I crop my pictures before batch-resizing them...

---

### Post by marialice on 2008-06-16
Then that doesn't work :)

I usually use [phatch](http://photobatch.stani.be/) for simple batch image processing over the commandline, so I checked what that program did in your case. Well, it did exactly the same :)

But... it was an easy fix. See attached file. If you place this file in ~/.phatch/actions the scale action will have an extra option "keep orientation". If I understood you right, this does what you were looking for.

---

Edit:
I came across a bash script:
[http://ubuntuswitch.wordpress.com/2007/10/01/create-thumbnails-giving-attention-to-the-orientation/](http://ubuntuswitch.wordpress.com/2007/10/01/create-thumbnails-giving-attention-to-the-orientation/)
(Haven't tested it)

---

### Post by aimpau on 2008-06-18
Thanks for the link btw. Just what I needed for Open Movie editor.

---

### Post by harck on 2008-06-18
I get an error with the "add-on" to phatch, but the shell script seems to do the job.

Thanks!

---

### Post by marialice on 2008-06-18
I'm glad the script worked :)

Sorry I left a mistake in that script, my lesson learned: "leave a file alone after testing, or test again". Can you do me a favour and try again?

---

