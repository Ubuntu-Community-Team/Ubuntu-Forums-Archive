---
title: "OGMRip - higher resolution?"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by cyprys on 2009-11-01
I'm trying to rip a DVD image to MKV file (x264) and the highest resolution I can set for the output is 704x304 (it can be up to 704x432 but the image is 16:9) which means it was scaled down (originally OGMRip opens the movie in a 1024* pixels width window and the movie properties says it's 1920x1080).

How to put a value higher than 704 as a width for the output file in OGMRip? Is this mencoder restriction? Should I use other software? Does ffmpeg allow to rip files to higher resolution? I want the image to be of as good quality as possible and don't want to loose anything.

Do you know any better ripping software for Ubuntu? I've got a HD camcorder and want to keep the movies as HD as possible.

For now I'm just copying the stream to .mkv but it keeps the file 3.7 GB big and 25-30 minutes long. That's not really an option since I saw those MKV files 4.7GB big and over an hour long.

edited:
Workaround is to create new OGMRip profile that encodes the stream but doesn't scale at all (it keeps the original resolution of the movie). To do so, go:
**Edit -> Profiles**, find a profile that suits you, for example **"PC, High Quality"** -> make a **Copy** of it -> **Edit** -> in **Video** tab find **More options** and set **Scaler** to **No Scaling**

If there's a "No Scaling" option set already, you may need to choose something else and then choose "No Scaling" again as for some reason it doesn't refresh correctly. Then: **OK**.

From now on you can use this profile to encode into whatever format you want keeping the original resolution (I use mkv as a container for x264 and I can get about 90 minutes of HD on one DVD).

---

