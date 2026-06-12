---
title: "Can anyone walk me through an Ubuntu/Drupal 6 problem?"
date: 2012-05-27
forum: Server Platforms
---

### Post by ubersoft on 2012-05-27
I really hope someone here is an Ubuntu/Drupal 6 guru, because I'm stuck trying to troubleshoot this problem, and I think it's going to take someone good at both to figure this out.

So, background. My site, eviscerati.org, runs on Drupal 6 on top of Ubuntu. Very recently I upgraded Ubuntu Lucid (10.04) to Precise (12.04), with apparently no issues whatsoever. Which, to be honest, made me a little nervous.

ON the Drupal side of things, I use the CCK filefield module to allow me to upload my graphics (pictures associated with specific articles, and webcomics) as well as podcasts (in mp3 format) to various nodes. Before the upgrade, it all worked perfectly. After the upgrade, I can continue to upload the graphics but I time out uploading the mp3 files. The primary difference between these two are file sizes: on a bad day my graphics are around 120K in size, and the smallest podcast I have is a 5.5mb mp3 file.

Here's what happens when I try to upload an mp3 file:

I use the filefield widget to select the, click the upload button. In firefox, the little spinner widget spins forever but nothing happens--the file is never transferred. In chromium or chrome (depending if I'm trying this in Linux or Windows 7), it actually starts to report the file progress but freezes at 1% then reports the page has crashed.

I don't think it's a client-side problem because it occurs in windows and linux, and I can sftp files to the site just fine.

I have made sure that my php settings (specifically upload_max_filesize, post_max_size, and memory_limit) are large enough to account for the file sizes, and have also checked the suhosin.ini file, which seems ok, but I admit other than suhosin.memory_limit I wouldn't know what to look for.

Is there anyone here who is familiar with Drupal 6 and Precise who might know why this was working in Lucid but not in Precise?

---

