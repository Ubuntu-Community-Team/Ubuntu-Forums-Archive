---
title: "Accidently deleted files"
date: 2012-01-25
forum: Security
---

### Post by Resilldoux on 2012-01-25
Hi,

That s right, I should have backed-up my files more often... But anyway, since I didn't I'd like to get my files back.

This happened on my ubuntu home server (so no gui) and I tried to do this with foremost, but as it so happens, I want to retrieve my *.wav *.jpg *.cue and *.log files. The first two are not really a problem because you can define these with foremost, but the *.cue and *.log files are not that easy it seems.

Does anyone know how to retrieve these deleted files?

---

### Post by kherring7383 on 2012-01-25
Sorry, I don't have a quick fix for you but a search of the internet took me to this webpage. 

Check it out maybe it will help.

[http://ubuntumanual.org/posts/357/recover-your-deleted-files-in-ubuntu](http://ubuntumanual.org/posts/357/recover-your-deleted-files-in-ubuntu)

---

### Post by /dev/random/username on 2012-01-25
I've heard that scalpel is somewhat better at file carving than foremost, however I haven't used them.. maybe this can help you -http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html-

---

### Post by Resilldoux on 2012-01-25
Thanks, I tried scalpel as well, and like foremost it also comes with a config file that you can edit to add extra extensions etc. The thing is that I don't really get how to get it to look for the cue and log files.

---

### Post by Resilldoux on 2012-01-26
I finally got most of my files through trial and error using foremost and photorec (part of testdisk).

It seems scalpel has difficulties accessing my /dev/dm-0, which is my LVM volume which is weird considering that scalpel is based on foremost and foremost had no difficulties with my LVM volume.

I'm still missing my wav files, but I think that will turn out just fine.

Thanks so far and I'll let you guys know.

---

### Post by /dev/random/username on 2012-01-26
Good to hear you've made progress

---

