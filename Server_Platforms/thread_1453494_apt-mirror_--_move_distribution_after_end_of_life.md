---
title: "apt-mirror -- move distribution after end of life"
date: 2010-04-13
forum: Server Platforms
---

### Post by surfer on 2010-04-13
i have a complete local ubuntu mirror; nicely kept in sync by apt-mirror. unfortunately, i need to keep some of the old releases as well. [http://old-releases.ubuntu.com]("http://old-releases.ubuntu.com") kindly provides those.

with the upcoming end-of-life of intrepid ibex, i would like to move the packages for intrepid on my mirror to the directory i use for the old-releases, without having to download these approximately 30GB from the original server.

is there a way to move distributions in a local mirror? apt-move seems only capable of rearranging the packages in /var/cache/apt/archives/ .

any help would be highly appreciated!

---

### Post by surfer on 2010-08-18
bump.

---

### Post by stlsaint on 2010-08-18
Is this something your looking for? [AptonCD]("http://aptoncd.sourceforge.net/")

---

### Post by surfer on 2010-08-18
i don't think that will help.

to be more explicit:

i have two directory trees, one contains a copy of [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) and the other one a copy of [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/).

if a release reaches its end-of-life i'd like to just copy the relevant files from the current-releases tree to the old-releases tree (instead of having to download everything for that release).

how do it do this?

---

### Post by stlsaint on 2010-08-18
As far as i know if it reaches end of life than you need to copy those packages you want individually from the old repo. Also what packages are you wanting to keep that are from a release that is no longer supported that isnt in current releases?

---

### Post by surfer on 2010-08-18
we still have machines with old releases (e.g. dapper) running (not connected to the internet). i do not need special individual packages, but the whole mirror as long as these machines are not updated.

'copy individually'? i'm talking about the whole mirror. either i write a script myself (what i try to avoid), or find an existing one... or download all the packages for a release again...

---

### Post by stlsaint on 2010-08-18
[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

---

### Post by surfer on 2010-08-19
> **stlsaint said:**
> [http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

that looks promising! thanks!

come to think of it... the copying part could just be done with [FONT="Courier New"]apt-mirror[/FONT] using the local repository as source. and the clean script should then be able to delete the unneeded release.

---

### Post by surfer on 2010-08-19
i just found this script [here]("http://goonmill.org/static/"). it does something along the lines of what i need... the output is just not very usable. but it's a good starting point anyway!


***** OOPS, WRONG THREAD. SORRY! *****

---

