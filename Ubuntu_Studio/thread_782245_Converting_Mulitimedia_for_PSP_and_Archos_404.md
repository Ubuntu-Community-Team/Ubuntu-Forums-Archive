---
title: "Converting Mulitimedia for PSP and Archos 404"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by EMCGFX on 2008-05-04
For archos I use mencoder, works like a charm:
(NOTE: replace <file_in.avi> and <file_out.avi>)

```
mencoder -ovc xvid -oac mp3lame -vf scale=320:240 \
-xvidencopts bitrate=128 <file_in.avi> -o <file_out.avi>
```

Example use:
```
mencoder -ovc xvid -oac mp3lame -vf scale=320:240 \
-xvidencopts bitrate=128 video.avi -o test.avi
```


For PSP I use currently, guide from [http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml](http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml)

Which I've created pdf file from the article, if you are interested you can find it here:
[http://www.mediafire.com/?xyumx40xmfj](http://www.mediafire.com/?xyumx40xmfj)


I wan't to use mencoder to due the same thing, but did not have any luck. If you know how, please reply.

---

