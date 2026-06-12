---
title: "FFMPEG Not Found"
date: 2012-02-28
forum: Server Platforms
---

### Post by Cluster_1 on 2012-02-28
Hi

I've been working on this issue for several hours now and I've finally decided to ask for some help 

I am running a wordpress site and i would like it to stream video if possible, I have installed ffmpeg and its located at /usr/local/bin/ffmpeg 

However when I add that path to to the said plugin for wordpress I get FFMPEG Not Found.

Am I missing a step, i followed a step-by-step isntructional guide.

---

### Post by ruffEdgz on 2012-02-28
Since Wordpress used the php web language, did you install the php extention for ffmpeg?
```

sudo apt-cache search php5-ffmpeg

```

If you just download the package called 'ffmpeg', its not used for php but for your local machine:

Short quote about the package:
> 
Multimedia player, server, encoder and transcoder


Description about the package 'ffmpeg':
> 
This package contains the ffplay multimedia player, the ffserver streaming server and the ffmpeg audio and video encoder. They support most existing file formats (AVI,
 MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3, DV...).


Hope this helps.

---

### Post by Paddy Landau on 2012-02-28
In addition to ruffEdgz's comments, how did you install ffmpeg? It is in the repository, so you should be able to just install it through the Ubuntu Software Centre.

It is a bit confusing as to whether you are trying to run the WordPress site from your own Ubuntu server, or get WordPress on a remote server to use your local ffmpeg.

---

### Post by Cluster_1 on 2012-02-28
> **Paddy Landau said:**
> In addition to ruffEdgz's comments, how did you install ffmpeg? It is in the repository, so you should be able to just install it through the Ubuntu Software Centre.

It is a bit confusing as to whether you are trying to run the WordPress site from your own Ubuntu server, or get WordPress on a remote server to use your local ffmpeg.

I'm trying to get WordPress working from my own server here at the house, I host my web sites here.  I've installed php5-ffmpeg & ffmpeg both earlier this morning and this wordpress plugin is still unable to locate the install in /usr/bin by running the command which ffmpeg

I've been working on it for awhile now and I probably should take a break from it a bit.

Both ffmpeg & php5-ffmpeg were installed via the repo's.

---

### Post by Cluster_1 on 2012-02-28
Just an update, the author of the plugin claims that it doesn't use php5-ffmpeg but ffmpeg me and him are working on why it is not functioning properly he released a patch a few days ago. I'm thinking I may have to build ffmpeg from source for it to work with his plug-in. 

I feel better that I got some food into me, hopefully this day will get better.

---

### Post by Paddy Landau on 2012-02-28
Hmm, compiling ffmpeg is not a small thing, as it affects several other things.

I did this once, following a how-to somewhere on this forum, and I wished I hadn't!

Have you installed ubuntu-restricted-extras with all the add-ons (from the Ubuntu Software Centre)?

---

