---
title: "Local repository from DVD images"
date: 2007-09-14
forum: Repositories &amp; Backports
---

### Post by mister_mipps on 2007-09-14
I am trying to make a local network repository from Feisty DVD images.  I have copied the DVDs to my hard drive .  When I run apt-mirror to gather them all into one repository before trying to download any useful updates, I get an error

>>Downloading 33 index files
>>Begin time
>>[2]...[1]...[0]...
>>End time

>>Proceed indexes: [Psh: cannot open file:/media/x-distro/ubu-g//dists...
>>apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 368

My mirror.list contains the line
>>set base_path /media/repo
and
>>deb file:/media/x-distro/ubu-g feisty main restricted

How do I get rid of the //dists problem?

---

