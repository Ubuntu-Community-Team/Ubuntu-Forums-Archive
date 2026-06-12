---
title: "Anyone using the &quot;gimp-for-painters&quot; patch? (instructions inside)"
date: 2009-12-28
forum: Ubuntu Studio
---

### Post by MetalMusicAddict on 2009-12-28
["gimp-for-painters"]("http://sourceforge.jp/projects/gimp-painter/releases") is a patch that adds two more tools that help in making images that feel more like using a paint brush.

[HERE's]("http://www.gimpstuff.org/content/show.php/2nd+test+with+gimp+painter?content=101868") another link about it.

It's actually pretty easy to apply the .diff to the ubuntu package.

In a terminal and with your source repos open it *should* be something like:
```
[SIZE="1"]sudo apt-get install cdbs -y && sudo apt-get build-dep gimp -y && apt-get source gimp && wget http://iij.dl.sourceforge.jp/gimp-painter/41325/gimp-painter--20090715.diff -P ~/gimp-2.6.7/debian/patches && cd gimp-2.6.7 && debuild binary && cd && sudo dpkg -i gimp-data_2.6.7-1ubuntu1_all.deb gimp_2.6.7-1ubuntu1_i386.deb[/SIZE]
```

[SIZE="1"](you only need the resulting "gimp" and "gimp-data" packages)[/SIZE]

The above command should then give 2 new tools in your toolbox. (will look like another [paintbrush and ink tool]("http://2.bp.blogspot.com/_3HEoCxevdTo/SeN0mrAa-tI/AAAAAAAAADU/tgruAzobdxY/s320/screen-capture-1+copia.jpg")) This is all best used with a pressure tablet.

These instructions also work for Karmic and Lucid but can be applied to earlier versions like gimp-2.6.6 and such. Also remember to pin gimp and gimp-data in Synaptic if you don't want an update to overwrite your version.

I would imagine that the GIMP devs are looking at a sane way to integrate this. Anyone with solid info please post.

---

