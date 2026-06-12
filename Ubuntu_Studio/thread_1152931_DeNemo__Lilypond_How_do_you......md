---
title: "DeNemo / Lilypond How do you....."
date: 2009-05-08
forum: Ubuntu Studio
---

### Post by podsgrove on 2009-05-08
I cannot find in the documentation for either DeNemo or Lilypond how to make first-time and second-time bars for repeated phrases. Does anyone know how to do it either directly in Denemo or by adding it later in Lilypond?

---

### Post by Stochastic on 2009-05-08
Lilypond documentation should be here: [file:///usr/share/doc/lilypond/html/Documentation/index.html](file:///usr/share/doc/lilypond/html/Documentation/index.html) (on your own computer)

or here: [http://lilypond.org/web/documentation](http://lilypond.org/web/documentation) (online)


is this what you're trying to do:[IMG]http://lilypond.org/doc/v2.13/Documentation/user/84/lily-a3807773.png[/IMG]

this is the code for the above image: ```
\repeat volta 4 { c4 d e f }
\alternative {
  { d2 e }
  { f2 g }
}
c1
```

Take a look in section 1.4 in the Notation Reference page for more info.

---

### Post by NoBugs! on 2009-10-18
If you have the latest denemo 0.8.8 you can click Measure -> Repeat Bar to add a repeat.

---

### Post by rshann on 2009-10-19
The 0.8.8 gives you the repeat barlines, the 0.8.10 now testing gives you first and second time bars from the Measure menu. With older versions you have to insert the LilyPond - see in the File->Open Example to see how.

---

