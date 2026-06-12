---
title: "ffmpeg audio video not insync"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by DesiSinger on 2008-07-06
Hello,

I'm new to ffmpeg and it sure does have lots of options.

The following is what I tried and the conversion was successful, but audio runs way ahead of the video. Any suggestions?

ffmpeg -threads 1 -y -i "movie_in.avi" -f mp4 -vcodec mpeg4 -maxrate 700000 -b 700000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec mp3 -ab 192 -s 320x240 -aspect 4:3 "movie_out.mp4" 2>&1 | perl -ne '$/="\r";$| = 1;if (/Duration: (\d+): (\d+): (\d+)/) { $max=($1*3600+$2*60+$3) }; if (/time=(\d+)/) { printf "%d\n",($1/$max*100);} print STDERR $_;'

Obviously, I did not come up with the whole string. Someone helped me out online with ffmpeg.

Any suggestions in getting the audio video insync?

Thanks.
:guitar:

---

