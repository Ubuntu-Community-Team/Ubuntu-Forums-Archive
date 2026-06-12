---
title: "Ffmpeg error: img_convert deprecated"
date: 2008-10-15
forum: Ubuntu Studio
---

### Post by Obsurd on 2008-10-15
Hi guys, sorry if I posted this in the wrong forum but ffmpeg does go in multimedia, doesn't it? 

Anyway, I've been trying find the solution to this for the past 4 hours on the Web, no luck.

I've installed SDL and LAME beforehand then I installed ffmpeg from Ubuntu's Sypnatic's Package Manager. 

Even though I know the problem, Ubuntu's downloaded the latest version of ffmpeg for me that does not support img_convert anymore, I have to try to compile a C program, named 'test.c' using ffmpeg that uses img_convert.

Here's the very frustrating problem while compiling: 

              $gcc -o test test.c -lavformat -lavcodec -lavutil -lz -lm `sdl-config - 
-cflags --libs` 

The error output is: 

              test.c: In function 'main': 
              test.c:137: warning: 'img_convert' is deprecated (declared at                    
/usr/include/ffmpeg/avcodec.h:2575) 



I saw the patches online but I don't know how to use them and this is my real first time playing with Ubuntu.

Anyone have an older version of ffmpeg?

Btw, I'm using Linux Ubuntu 8.04.

---

