---
title: "Renumbering image sequence"
date: 2008-11-24
forum: Ubuntu Studio
---

### Post by rylleman on 2008-11-24
My animation software spits out frames numbered after their frame number in the software so sequences can have numbering starting at other frames than 1 (Scene10_0023.png - Scene10_0253 for example).

FFmpeg only accepts image sequences if their numbering starts at 1.

I can renumber the sequences using some GUI renaming app. like GPrename but I want to do it through the terminal since I'm creating a bash-script that should rename sequences and convert them into movies using FFmpeg.

So how do I do this? (Renaming the above example to Scene10_0001.png - Scene10_231.png)

---

### Post by jrib on 2008-11-24
```
i=1; for x in *; do echo mv $x ${x%_*}_$i; i=$(($i + 1)); done
```

First attempt.  Don't know if ffmpeg cares about leading 0's.  Does it?

---

### Post by jrib on 2008-11-24
> **jrib said:**
> Don't know if ffmpeg cares about leading 0's.  Does it?

```
i=1; for x in *; do echo mv $x ${x%_*}_$(printf "%06d" $i); i=$(($i + 1)); done
```
with padding

Hmm, I may also be assuming that * lists the sequences in the correct order which your shell may or may not do.  So watch out for that.

---

### Post by rylleman on 2008-11-24
Thanks,
that did just what I wanted and I haven't encountered any ordering issues.
Now I shall only figure out how to keep the extension. (The format could differ so just adding ".png" won't do).

---

