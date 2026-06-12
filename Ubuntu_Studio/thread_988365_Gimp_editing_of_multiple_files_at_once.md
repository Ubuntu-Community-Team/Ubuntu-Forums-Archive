---
title: "Gimp editing of multiple files at once"
date: 2008-11-20
forum: Ubuntu Studio
---

### Post by MaindotC on 2008-11-20
If I had a series of pictures that I all wanted to be converted to a specific size, autocropped, and saved in png format, is there a way to do that all at once instead of opening up each file and modifying and saving it individually?

---

### Post by unutbu on 2008-11-20
```
sudo apt-get install imagemagick

```

mogrify overwrites the original image. If you wish to retain the original, use the command 'convert' instead of 'mogrify' or duplicate the directory before using 'mogrify'.



To batch convert to png format
```
mogrify -format png *
```

To batch resize:```

mogrify -resize 600x400 *
```

To batch autocrop:
```
mogrify -trim *
```

For more info:
[http://www.imagemagick.org/www/convert.html](http://www.imagemagick.org/www/convert.html)
[http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

---

### Post by MaindotC on 2008-11-21
Worked like a charm :)  Thank you so much for your help!

---

