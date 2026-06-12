---
title: "Can someone help with a simple bash script?"
date: 2010-06-07
forum: The Cafe
---

### Post by Yes on 2010-06-07
I have some .ogg music files that I need converted to .mp3.  I've used the command ```
for file in *.ogg;do oggdec -o - "$file"|lame -h -V 4 &#8211;-vbr-new - "$(basename "$file" .ogg).mp3";done
```
before to convert every file in a folder, but I'd like to be able to just run the script and have it convert every .ogg in my Music folder.  My Music folder is set up like Music>Artist>Album>Song.ogg.  Can anyone help me out?

Thank you :)

---

### Post by whiskeylover on 2010-06-07
I don't remember the exact syntax, but google for ...

find dir -name *.ogg -exec ...

---

### Post by alphaniner on 2010-06-07
You could try something like

```
find /path/to/music -name "*.ogg" | while read file
```

'file' would remain your variable.  I think this should work.

---

### Post by koenn on 2010-06-07
[http://ubuntuforums.org/showthread.php?t=415511](http://ubuntuforums.org/showthread.php?t=415511)
and many others

---

### Post by lostinxlation on 2010-06-07
Not sure I understand corretly, but are you saying that you have multiple directories separated for each artists or such and you want to covert all of them at one shot ?
 
Between pushd and popd, you are already in the OGG directory. Replace 'echo $x $y $z' with whatever command(s) you want to run.
 
```

#!/bin/csh
 
foreach file (`find <top music dir> -name "*ogg" -print`)
   set dir=$file:h
   pushd $dir
     echo "changing dir to $dir.."
     set x = $file:t
     set y = $file:r:t
     set z = $y."mp3"
     echo "$x  $y $z"
   popd
end

```

---

### Post by Yes on 2010-06-07
Thank you all, but I found the program ogg2mp3 which has worked wonderfully.

Thanks :)

---

