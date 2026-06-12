---
title: "demux and rip single files using vobcopy"
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by hurtstotalktoyou on 2008-06-02
Hi, all.

Normally I just use DVD Decrypter in Wine to rip DVDs to separate audio and video streams, or as single VOB files (as opposed to multiple VOB files in a VIDEO_TS folder).  However, DVD Decrypter only works with physical discs; it does not detect iso files mounted using gmountiso.  So, I am now considering migrating from DVD Decrypter in Wine to Linux's native vobcopy.

Now, I know how to rip exact copies of DVDs using vobcopy, but I do not know how to demux, or turn off file splitting.  What I need to do is rip a mounted iso of a video dvd to two files, one containing the entire video stream, and one containing the entire audio stream.  These must be demuxed (not *.vob files).  Is this possible with vobcopy, and, if so, how do I do it?

Thanks!

---

### Post by eye208 on 2008-06-03
VOB (aka. MPEG-2 program stream) is a containerless format, i.e. you can just concatenate two VOBs into one.

Vobcopy will only do the decryption. To extract the elementary streams from the VOB you need additional demuxing tools, e.g. Avidemux, MPlayer/MEncoder or FFMPEG. For example, MPlayer can extract streams using the -dumpstream parameter.

If your goal is to transcode the VOBs to high quality MPEG-4 AVIs or similar, there's a detailed guide for MEncoder:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html)

---

### Post by JEDIDIAH on 2008-06-03
> **eye208 said:**
> VOB (aka. MPEG-2 program stream) is a containerless format, i.e. you can just concatenate two VOBs into one.

Vobcopy will only do the decryption. To extract the elementary streams from the VOB you need additional demuxing tools, e.g. Avidemux, MPlayer/MEncoder or FFMPEG. For example, MPlayer can extract streams using the -dumpstream parameter.

If your goal is to transcode the VOBs to high quality MPEG-4 AVIs or similar, there's a detailed guide for MEncoder:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html)

I generally separate the extraction from the transcoding. If you are pulling something off of optical media, that tends to be pretty quick whereas transcoding takes forever (relatively speaking).

Research Google for the various options for mencoder. There are quite a lot of them and a number of people have published recipes based on their experiences.

---

