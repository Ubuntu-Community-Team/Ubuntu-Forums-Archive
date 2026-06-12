---
title: "[FIXED] ffmpeg not producing sound in flv"
date: 2008-09-06
forum: Ubuntu Studio
---

### Post by dev.null on 2008-09-06
I've seen this "fixed" in other posts, but no one lists the step by step fix and you end up having to go off to other posts or keep searching around to piece it all together. I've been banging my head on this one for a day so I figure I'd help you guys out with a one-stop-shop how-to.

Problem: ffmpeg converts different formats audio and video without a problem, but when you go to output flv (flash) for whatever reason you only see one stream, the video, and you can't ever get the audio to work.

Solution, you need to install ffmpeg from medibuntu and the associated packages.

1. Setup the medibuntu repository on your box:

The steps are here: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

But I encapsulate them here:

Ubuntu 8.10 "Intrepid Ibex":
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 8.04 "Hardy Heron":
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 7.10 "Gutsy Gibbon":
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 7.04 "Feisty Fawn":
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 6.10 "Edgy Eft":
```
sudo wget http://www.medibuntu.org/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 6.06 "Dapper Drake":
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```

2. Then add the GPG key:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If you're asked to accept the package even though it's not authenticated, tell it yes.

3. Now remove your current ffmpeg:
```
sudo apt-get remove ffmpeg
```

4. Now re-install it:
```
sudo apt-get install ffmpeg
```

5. And now for the related tools:
```
sudo apt-get install libavcodec-dev libavcodec1d libavformat-dev libavformat1d libavutil-dev libavutil1d libpostproc-dev libpostproc1d libswscale-dev libswscale1d
```

6. And here's an example of how to convert an avi to flv:
```
ffmpeg -i ${AVI} -b 600k -r 30 -ab 128k -ar 44100 -s 512x384 -ac 2 -y ${FLV}
```

You should see this when it runs, this is how you will know it's outputing both audio and video:

```
...
Output #0, flv, to 'capture_final_1.flv':
  Stream #0.0: Video: flv, yuv420p, 512x384, q=2-31, 600 kb/s, 30.00 fps(c)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
...

```

---

### Post by Creative2 on 2008-09-06
mmm i have kubuntu 8.04 ffmpeg installed from medibuntu repository and stop and it works fine :O

---

### Post by p.herewini on 2008-10-22
Thank you, your instructions fixed my problem:

I was trying to convert a .mov to .flv but was getting no audio. 
The audio codec was adpcm_ima_qt.
Working fine now.

---

### Post by zenith001 on 2008-10-23
[Crusher](http://www.crusher.south.am)[Jaw Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Jaw-Crusher/Jaw-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Cone-Crusher/Cone-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/HPC-Cone-Crusher/HPC-Cone-Crusher.html)[Impact Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Impact-Crusher/Impact-Crusher.html)

---

