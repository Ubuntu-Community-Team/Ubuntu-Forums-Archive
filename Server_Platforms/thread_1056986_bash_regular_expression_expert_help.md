---
title: "bash regular expression expert help"
date: 2009-02-01
forum: Server Platforms
---

### Post by inphektion on 2009-02-01
based on this:
[http://ubuntuforums.org/showthread.php?p=6656926](http://ubuntuforums.org/showthread.php?p=6656926)

I now see I have a file like this:
```

^MClone: 0% done.^MClone: 1% done.^MClone: 2% done.^MClone: 3% done.^MClone: 4% done.^MClone: 5% done.^MClone: 6% done.^MClone: 7% done.^MClone: 8% done.^MClone: 9% done.^MClone: 10% done.^MClone: 11% done.^MClone: 12% done.^MClone: 13% done.^MClone: 14% done.^MClone: 15% done.^MClone: 16% done.^MClone: 17% done.^MClone: 18% done.^MClone: 19% done.^MClone: 20% done.^MClone: 21% done.^MClone: 22% done.^MClone: 23% done.^MClone: 24% done.^MClone: 25% done.^MClone: 26% done.^MClone: 27% done.^MClone: 28% done.^MClone: 29% done.^MClone: 30% done.^MClone: 31% done.^MClone: 32% done.^MClone: 33% done.^MClone: 34% done.^MClone: 35% done.^MClone: 36% done.^MClone: 37% done.^MClone: 38% done.^MClone: 39% done.^MClone: 40% done.^MClone: 41% done.^MClone: 42% done.^MClone: 43% done.^MClone: 44% done.^MClone: 45% done.^MClone: 46% done.^MClone: 47% done.^MClone: 48% done.^MClone: 49% done.^MClone: 50% done.^MClone: 51% done.^MClone: 52% done.^MClone: 53% done.^MClone: 54% done.^MClone: 55% done.^MClone: 56% done.^MClone: 57% done.^MClone: 58% done.^MClone: 59% done.^MClone: 60% done.^MClone: 61% done.^MClone: 62% done.^MClone: 63% done.^MClone: 64% done.^MClone: 65% done.^MClone: 66% done.^MClone: 67% done.^MClone: 68% done.^MClone: 69% done.^MClone: 70% done.^MClone: 71% done.^MClone: 72% done.^MClone: 73% done.^MClone: 74% done.^MClone: 75% done.^MClone: 76% done.^MClone: 77% done.^MClone: 78% done.^MClone: 79% done.^MClone: 80% done.^MClone: 81% done.^MClone: 82% done.^MClone: 83% done.^MClone: 84% done.^MClone: 85% done.^MClone: 86% done.^MClone: 87% done.^MClone: 88% done.^MClone: 89% done.^MClone: 90% done.^MClone: 91% done.^MClone: 92% done.^MClone: 93% done.^MClone: 94% done.^MClone: 95% done.^MClone: 96% done.^MClone: 97% done.^MClone: 98% done.^MClone: 99% done.^MClone: 100% done.

```

I only want the last percentage that may have been completed.  So now I want to loop through this file seeing how many "Clone:" instances there are and deleting all but the last i guess by egrep'ing them out based on some regular expression that matches "Clone: xx%".

Any help here?

edit: oh and i can get rid of the ^M's with
```
sed -e 's/^M//g' ghetto.out
```

---

### Post by unutbu on 2009-02-01
This will match any line with "Clone: ... done." in it, and remove all but the last one:

```
sed -e 's/.*\(Clone: .* done.*\)*Clone: \(.*\) done./Clone: \2 done./' ghetto.out
```

It will leave unmatched lines alone, so it should be safe to run this on ghetto.out, as long as the Clone line is on a line by itself. If it isn't perhaps try

```
sed -e 's/\(Clone: .* done.*\)*Clone: \(.*\) done./Clone: \2 done./' ghetto.out
```

---

### Post by inphektion on 2009-02-01
Perfect.  Thank you.

---

