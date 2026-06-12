---
title: "Convert a lot of svg files to png"
date: 2008-04-27
forum: Ubuntu Studio
---

### Post by garfieldpbj on 2008-04-27
Hi.

I've used octave to print a lot of svg files - how is the easiest way to convert all of them to png?

(I know that octave "normally" can print as png directly, but I have had some problems with that: [http://www.nabble.com/gdImageStringFT%3A-Could-not-find-open-font-while-printing-string-values-of-mean-with-font-Helvetica-td16906817.html](http://www.nabble.com/gdImageStringFT%3A-Could-not-find-open-font-while-printing-string-values-of-mean-with-font-Helvetica-td16906817.html) - and have not got a solution yet, so I need to do it this other way around! :( )


Can anyone help me?

/Peter

---

### Post by mcduck on 2009-02-18
Imagemagick can do that, and I remember Inkscape also having a command-line option for this purpose (it sure can do it in GUI but if you have lots of files to convert then command line is easier).

Both are available in Ubuntu's repositories.

edit: yep, I remembered right about Inkscape. Something like this should work fine to convert every .svg file in current directory to .png:
```
for f in *.svg; do inkscape -f "$f" -e "$f".png; done
```

..or with Imagemagick:
```
for f in *.svg; do convert "$f" "$f".png; done
```

I suppose from these two tools Inkscape should have better support for latest .svg versions, but with basic .svg files both should work fine.

---

