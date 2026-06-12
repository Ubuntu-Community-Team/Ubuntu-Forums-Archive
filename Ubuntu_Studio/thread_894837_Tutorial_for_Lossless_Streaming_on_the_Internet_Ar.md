---
title: "Tutorial for Lossless Streaming on the Internet Archive"
date: 2008-08-19
forum: Ubuntu Studio
---

### Post by Samizdat on 2008-08-19
This is my first Ubuntu Forums tutorial, intended mainly for new users but may be of use to the more experienced also.

[SIZE="3"]Tutorial for Lossless Streaming on the Internet Archive[/SIZE]

[SIZE="2"]Three simple steps to creating your own "feature for streaming the lossless files" (on the [Internet Archive)](http://www.archive.org/):

[b]1.

a)[/b] Encode your original .wav format audio show to the FLAC (.flac) file format and to the ogg-FLAC (.oga) file format using one of any number of encoding and/or converting programs, particularly FLAC Frontend* for wine or Windows users -- or if you're a command line bug, using simple commands (presuming you've installed flac on your machine).  

* FLAC Frontend users must make sure replay gain is disabled before encoding to ogg-FLAC.

To create a file named my.flac from one named my.wav, you would use the following code:  
```

flac -8 my.wav
```

[color=red]To create a folderful of .flac files from a folderful of .wav files, use the following code:[/color]

```
flac -8 *.flac
```

To create a file named my.oga from one named my.wav, you would use the following code (the more experienced will want to have a look at the [flac pages](http://flac.sourceforge.net/documentation_tools_flac.html)):

```

flac --ogg -8 -o my.oga my.wav
``` -- note that the "-8" gives best compression, whereas using "-0" gives fastest compression.  I always choose -8, as a few extra seconds spent today means listeners will enjoy the added quality long after I'm gone.

[color=blue]To create a folderful of .oga files from a folderful of .wav files, use the following code:[/color]

```
flac --ogg -8 *.wav
```
  
**b)** Upload your show to the Internet Archive's "Open Source Audio" (or to the "Live Music Archive)."


**2.** At left of the details page of your show, hit the "Edit item," whereupon you will see the "Metadata editor."  Near the bottom of the Metadata editor page, select "Allow only non-lossy derivatives for files in this item." Hit "Submit," then wait for update, which takes a few minutes.


[b]3.

a)[/b] Using the ogg-FLAC (.oga) file download links on your show's details page, create an m3u file.

**b)** Upload the m3u file to the ftp server (by hitting "Edit item," then on the Metadata editor page, hit "Item Manager)."

**c)** Go back to your "Edit item" page and use the "Format" drop-down corresponding to the m3u file to select
"VBR M3U." Hit "Submit" button at bottom of page -- again, the update takes a few minutes.

**d)** Once your details page updates, find the new (VBR M3U) "Stream" link. Use this URL
in your VLC media player to listen losslessly to your show -- what I like to call "learn before you burn."


Example show featuring lossless "Stream" link: [Blasphemous Creation - Shadows of Evil](http://www.archive.org/details/b.c.2008-03-09.flac.studio.demo)

Stay tuned to my next update, where I provide the *super*-new user a short tutorial on creating an m3u file using VLC media player.

Any questions? Here's the place to post 'em![/size]

---

