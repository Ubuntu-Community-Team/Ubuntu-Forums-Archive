---
title: "Question about mencoder"
date: 2008-10-01
forum: Ubuntu Studio
---

### Post by DarchAengel on 2008-10-01
I have been using Mencoder to extract and re-encode videos with subtitles.  I have basically two things I can't seem to find any info on doing.  First how do I adjust my code so that the subtitles are all bold.  The size is fine but they are a little faint, especially when I shrink the file to PSP format.  The  other thing I need to is raise the volume on a file I have.  For whatever reason the fansubbers recorded the sound so low that I have to blast my speakers to hear it.  I know it is them since it is only their work that I have a problem with.  Other groups have perfect volume.  This is the line of code that I am using to do all this.

```

mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 -sub "subtitles.srt" "exact file name" -o video.avi

```

Any help would be greatly apreciated.

---

### Post by aeiah on 2008-10-02
for bold, use the -font flag and specify a font that is bold, including the path to the font.

as for the volume, try something like :vol=9

```


mencoder -oac mp3lame -lameopts cbr=128:vol=9 -ovc xvid -xvidencopts bitrate=1200 -sub "subtitles.srt" -font '/path/to/font.ttf' "exact file name" -o video.avi

```

some people have noted that mencoder will ignore the font options and use the default font as specified in the .mplayer directory or possibly the .mplayer/conf file. if this is the case then either delete the font that's there (and specify a system font for mplayer usage) or replace the fonts at ~/.mplayer/subfont.ttf and ~/.mplayer/font with a bold font.

---

