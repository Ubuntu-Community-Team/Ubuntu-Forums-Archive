---
title: "How get to know an exact source of a GPL application installed via a package manager?"
date: 2020-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by umaxik on 2020-05-02
Hello, all!

I am a little confused with the world of Linux, GPL and open sources, so I have got to the quesion. Let us suppose:


[LIST=1]
[*]My current OS is Ubuntu 19.04 that is installed some time ago. It is official version, well documented, etc.
[*]There is Muon package manager that helped me to install xSane. An official version of xSane for the official version of Linux. Ok, now I have xSane.
[*]xSane is GPL, so its source is somehow published.
[/LIST]

Now, how to get to know the exact origin of the source? And, as the origin is within some repository, what is an exact milestone in this repository?

Thanks a lot!

---

### Post by CatKiller on 2020-05-02
19.04 is no longer supported, and hasn't been since January. 20.04 LTS will be supported for 5 years. 

The repositories that hold the binary packages also hold the source code for those packages. Those are the deb-src entries in your sources.list. I think it's *apt-src* that will download the source code, and I think the downloaded source code gets put in the current directory.

Obviously there are other upstream places to get the source code from, which is how the package maintainers got the source code in the first place. *Where* that source code is, and how it's organised, will vary from project to project.

---

### Post by Hwæt on 2020-05-02
It's also worth mentioning that you can generally search for the package online (or look at the package metadata to find a website) and get the source from there. This is also a great way to find the community that makes it and see if you'd like to contribute, as well.

---

### Post by umaxik on 2020-05-03
My source.list points to some components in  [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/). But I cannot find 19.04 here, only LTS version prior and after 19.04.

There is xsane: [http://ru.archive.ubuntu.com/ubuntu/pool/universe/x/xsane/](http://ru.archive.ubuntu.com/ubuntu/pool/universe/x/xsane/)
It seems to be sources for .998 and .999 together with binaries. I believe, if my xsane is 0.999, here should be source files for my exast xsane.

Nevertheless,  'apt-source install xsane' does not work (message: "You must put some  'source' URIs in your sources.list"), though I enabled all 'deb-src'  lines in sources.list.

---

### Post by umaxik on 2020-05-03
Yes, xsane is here: [https://gitlab.com/sane-project/frontend/xsane.git](https://gitlab.com/sane-project/frontend/xsane.git)

I try to understand how teams public their code, share it, interchange it, etc. For instance: given that Ubuntu team got some sources of xsane from sane-project for building Ubuntu 19.04. Then the questions:

1. Which exactly version did they get?
2. I can suppose that they tuned it a bit for Ubuntu 19.04. Do they make a push request to sane-project to be sure their changes are committed and a next version of Ubuntu does not require the same patches?

---

### Post by CatKiller on 2020-05-03
19.04 is unsupported. Repositories don't hang around indefinitely after a release goes End-of-Life. 

Those questions are entirely package specific. Some package maintainers put more information on Launchpad than others do. 

Most Ubuntu packages come from Debian rather than further upstream, and then get applied whichever patches the package maintainer feels best suit the goals of Ubuntu. Bug fixes and the like are going to go upstream, but a lot of the patches are just going to be changing default settings.

---

