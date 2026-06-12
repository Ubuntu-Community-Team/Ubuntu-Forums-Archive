---
title: "Checkinstall Experience"
date: 2006-03-06
forum: The Cafe
---

### Post by BoyOfDestiny on 2006-03-06
Well, this is basically a small story/rant in regard to checkinstall vs the "proper" method of packaging...

Currently checkinstall is broken in Dapper, so I tried using dh_make and dpkg-buildpackage... However only 1 of 3 of my packages worked with that template, I tried a lot of tweaking to no avail (I know this is likely due to my inexperience). Sadly for the package produced properly, it did not catch the proper dependencies... 

After wasting an hour or so recompiling... I decided to download the latest checkinstall (1.60) and give it a go... Worked like a charm. I know people consider it a hack, and it doesn't work with certain packages (keep in mind I'm not an official package maintainer, nor do I build 'critical' packages).

My conclusion is that most people don't like the lack of dependency checks... However, one can pass a parameter to modify the control file before building (yay I learned something). From here I can add which packages it can overide or replace (for example advmame and advmenu share documentation, with Replaces: I can avoid doing a -force-all). As for manually adding dependencies, since the binary is built first (make)
For example:

objdump -p /home/*****/Desktop/zsnes | grep NEEDED

then I can manually add them into the control file...

I just wanted to share this since checkinstall seems looked down upon. For regular users that want to install something on their machine (that is non-critical, and not in the official repos), I recommend a checkinstall over a make install. You can see your package in synaptic, and if you take the time, you can make it deal with dependencies, play nice or replace other packages...

Thanks for reading!

Checkinstall homepage:
[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

---

