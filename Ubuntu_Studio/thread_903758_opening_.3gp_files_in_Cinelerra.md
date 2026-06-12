---
title: "opening .3gp files in Cinelerra"
date: 2008-08-28
forum: Ubuntu Studio
---

### Post by daniel3ub on 2008-08-28
Hi, pals.

I have some .3gp files I want to use in a Cinelerra project.
1) Could someone please tell me what to do to get these files working on Cinelerra?

2) Is there a way to open these files directly in Cinelerra, without the need to convert them to another format?

3) If I HAVE to convert them, what packages and or commands do I need? I've tryed mencoder:
```
mencoder 18-01-08_0135.3gp lavc -ofps 29.97 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=650 -oac mp3lame -lameopts vol=0,1 -of avi -o 18-01-08_0135.avi
```

but I get the following output:
```

....
Pos:  52.2s    783f ( 0%) 364.69fps Trem:   0min   0mb  A-V:0.000 [137:0]
1 duplicate frame(s)!
Pos:  52.3s    784f ( 0%) 364.65fps Trem:   0min   0mb  A-V:0.000 [137:0]
1 duplicate frame(s)!
(a lot of these lines, since the beginning...)
File not found: 'lavc'0%) 364.44fps Trem:   0min   0mb  A-V:0.000 [137:0]
Failed to open lavc.
Cannot open file/device.
```

Then I get the AVI file created, but it doesn't seem like an AVI, and when I try to open it in Cinelerra I get a black movie file.

Thanks for your help!

---

### Post by Creative2 on 2008-08-28
no cinellera sucks formats (blender can open them...that cuz i use blender)

i know cinellera handle ogg 
so:
ffmpeg2theora

ffmpeg2theora -v 10 -a 10 -x 720 -y 576  INPUT -o OUTPUT 

x= 720 is X resolution 
y= 576  is Y resoltion 
v qualiy max = 10
a quality = 10

---

### Post by daniel3ub on 2008-08-29
can I edit movies in blender like I would in cinelerra?
With transactions, effects and so on?

---

### Post by Creative2 on 2008-08-29
---->[http://www.blender.org/education-help/](http://www.blender.org/education-help/)
you can do basic transition but if you get plug in i think it's fine too
i haven't tested yet because i didn't need before
just try it... if you get some problem with audio -------->[http://ubuntuforums.org/showthread.php?t=750064](http://ubuntuforums.org/showthread.php?t=750064) anyway i have choosen blender for my video editing
you could try kdenlive i dunno if accepts 3gp tooo if you get some troubles---------->[http://ubuntuforums.org/showthread.php?t=791355](http://ubuntuforums.org/showthread.php?t=791355)

---

### Post by daniel3ub on 2008-08-29
Wow, thanks a lot! I'll try it!

---

