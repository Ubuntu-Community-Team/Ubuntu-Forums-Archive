---
title: "how to -question- edit public url address at  &quot;ubuntu one&quot;"
date: 2013-05-19
forum: Ubuntu One (CLOSED)
---

### Post by anisterra on 2013-05-19
Hello,  

I wonder if it is possible to edit the public url address of a published file in ubuntu one.
I found no examples searching internet. 
I am trying to share a list of files with an html index and would like to have for href a "public url address " that contains the name of the pdf file. 

Anybody knows sthg about this?
Thank you in advance.

---

### Post by Irihapeti on 2013-05-20
It's not possible to edit the public URL.

If you're sharing the filenames in a document, you could do something like this:

```
<a href="http://ubuntuone.com/public-url">real-file-name.pdf</a>
```
where "public-url" is the random string of characters in the U1 filename.

Then the reader sees the real file name but goes to the correct link when they click on it.

---

### Post by anisterra on 2013-05-21
Thank you :)

I think I am doing something odd but is working fine for me... 
[http://ubuntuone.com/5Q4HOg8fOAxcMu9lNeudVz](http://ubuntuone.com/5Q4HOg8fOAxcMu9lNeudVz)

If you see some similar use of the U1 please let me know.

---

### Post by Irihapeti on 2013-05-22
That's looking good.

I noticed that the default character coding (in my browser) was Windows-1252. I needed to set it to UTF-8 for all the special characters to display properly.

You can add ```
    <meta charset="utf-8">
``` to the <head> section of the html document and that should cause it to use UTF-8 straight away.

Then, on the other hand, it could just be some quirk in my browser.

---

### Post by anisterra on 2013-06-03
Thanks for the tip :) 
I've removed all non english characters from the text as I needed a quick solution, but now I will add your code suggestion and see what happens.
I am a teacher so I need a very easy way of sharing files that are updated frequently.  I think I found in U1 a pretty useful solution. I was happy to find that after editing documents the public url remained unchanged :)

---

