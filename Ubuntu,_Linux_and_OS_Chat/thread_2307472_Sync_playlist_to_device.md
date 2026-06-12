---
title: "Sync playlist to device"
date: 2015-12-25
forum: Ubuntu, Linux and OS Chat
---

### Post by agough on 2015-12-25
Evening all...

I have a .xspf playlist containing hundreds of songs scattered over various drives and directories. Is there any kind of Linux software that can copy all of these files onto a mounted memory stick? The reason I can't just cp the files is, as I say, they're flipping everywhere (not my fault! Blame Dad... :-\") and it'll take me forever...

I've tried VLC, Amarok, Audacious... etc. and none of them seem to have the simple feature of "sync playlist to device" that Windows Media Player had.

Perhaps I'm just being stupid, but I've tried many combinations of search terms on Google and nothing's come up. Thanks for your help guys! :)

---

### Post by agough on 2016-01-02
...I'll take that as a no! :mrgreen:

Anyway, here's the hacky-version:

1) Export your playlist to some kind of xml-based file, e.g. .xspf

2) Open your playlist with a spreadsheet editor, delete everything except the file paths. Chop and change the cells around so that all the cells with file paths are in one row (don't know if there's an easy way to do this in Open/Libre Office, I use Excel on Wine, with cut and special-transpose-paste).

3) Export/save as .csv (comma separated values file)

4) Open the .csv with a text editor and copy the single line of text in it. You now have a bunch of file paths separated with commas that can be fired into a terminal like so (note the curly brackets are needed for multiple files):

```
cp {all,of,the,files} /media/user/whatever/device/
```

Note that if the music files in the playlist contain things like brackets and stuff in percent codes, you'll need [https://en.wikipedia.org/wiki/Percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding) to help you (don't forget to use escape back slashes) turn them back into unix paths.

Have fun! I did, and that was with "only" 100 songs... :)

---

