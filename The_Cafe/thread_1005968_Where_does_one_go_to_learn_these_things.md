---
title: "Where does one go to learn these things"
date: 2008-12-08
forum: The Cafe
---

### Post by Silvernail on 2008-12-08
I would like to learn to use Imagemagick better. All I can find are overviews of the different options.

For instance I would like to use the option '-morph'. All I can find is what it does. Not how to code the line. One place it says to use 'mogrify' and another to use 'convert'.

Can anyone point this old dog to a place where he can learn some new tricks?

TIA
dave

---

### Post by fwojciec on 2008-12-08
Imagemagick is not a single program but rather a collection of tools.
Man page for the whole thing is available when you type "man ImageMagick", but there are also separate man pages for individual utilities: "man mogrify", "man convert", etc.  In either case, man pages would be the first resource I'd try.

---

### Post by saulgoode on 2008-12-08
> **Silvernail said:**
> One place it says to use 'mogrify' and another to use 'convert'.
They are basically the same except that 'mogrify' will modify the original file, while 'convert' produces a modified copy.

> **Silvernail said:**
> Can anyone point this old dog to a place where he can learn some new tricks?

I would suggest reading some of the documentation on the [tutorials page]("http://www.imagemagick.org/Usage/").

You might also experiment with the interactive interface; i.e., the 'display' command.

---

### Post by Silvernail on 2008-12-08
The manuals I've been reading for years and did so again.

This all started here.
Several weeks ago I shot some footage of a parade.  The day before the parade I shot some footage of the same area with no humans in it. I want to fade the parade into the empty street sort of sereal like.

I posted in the gimp usernet group because gimp has a morph routine. No success.
I googled 'imagemagick morph' and got several paths to this web site.

Reading here does not tell me what I want to know.

Todays adventure started here.

using```
mplayer -vo png mvi_350.avi
``` I converted the video to frames 
Starting here 00000001.png and ending 00000209.png

Then used gimp to convert to xcf extension. Tried gimp morph. no success.
Tried it on the png extension. nada
Tried it on the avi extensions, nada

Tried ```
convert -morph 200 *.png

```on the png extensions. If something happened I could not find it.

Found this script in an old archive I had.

```
#!/bin/bash
 ## This script takes three arguments, the directory of the source
 ## images, the directory for the result images, and the value to
 ## multiply the alpha channel by.
 ## E.g. assuming the script file is named transparent.sh
 ## transparent.sh ~/Media ~/Media/Transparent 0.75
 ## If the result image directory is given as a relative filepath, it
 ## will be created within the source image directory.
 ##
 ## Further improvements that could be made are:
 ##    - To put in a -h or --help option
 ##    - To allow recursive searching of a directory.
 ## The second could be achieved by replacing the second for file
 ## statement with
 ##   for file in `find $1 -iname *.$suffix`
 ## though this would make the logic of the convert line more complex
 ## if the relative structure of the input directory was to be
 ## reproduced in the output directory.
 ## Additionally, this script doesn't do any sanity checking to ensure
 ## that an input file can't be overwritten by an output file.
 ##
 ## Copyright GPL v2, 2006, Joal Heagney
 ##

 pushd $1
 mkdir -p $2
 for suffix in jpg jpeg JPG JPEG gif GIF tif tiff TIF TIFF png PNG
 do
    for file in *.$suffix
    do
      convert $file -channel Alpha -fx 'u*$3' $2/`basename $file $suffix`.png
 ## Note that the convert and $suffix`.png should be all one line
    done
 done
 popd


```
Then
```
./transparent.sh backfade backfade/fadeout 0.75

```
I get these errors:
> convert: missing an image filename `/*..png'.
convert: unable to open image `*.TIF': No such file or directory.
convert: missing an image filename `/*..png'.
convert: unable to open image `*.TIFF': No such file or directory.
convert: missing an image filename `/*..png'.
convert: unable to parse expression `$3'.
convert: unable to open image `/00000001..png': Permission denied.
convert: unable to parse expression `$3'.
convert: unable to open image `/00000002..png': Permission denied.
convert: unable to parse expression `$3'.

I understand not finding TIF etc.

but reading arguement # 3
And
Permissions are > -rwxrwxrwx 1 dave dave    834182 2008-11-23 22:52 000209.png


I'm confused and I'm going to bed.
If you can help, thanks.
If you can point me where to go, thanks.
Dave

---

### Post by cammin on 2008-12-09
Use absolute paths for the input and output directories.

---

### Post by Silvernail on 2008-12-09
Are you saying that this line:
```
 convert $file -channel Alpha -fx 'u*$3' $2/`basename $file $suffix`.png

```

should look like this:```

 convert ~/Photos/2008/11/23/$file -channel Alpha -fx 'u*$3' $2/`basename ~/Photos/2008/11/23/$file $suffix`.png

```

---

