---
title: "Use ImageMagick for PDF thumbnails"
date: 2007-08-28
forum: Tutorials
---

### Post by Friik on 2007-08-28
Hi!

The thumbnail-images of various file types has always been a very useful feature for me, especially since it supports not only images and text, but file types such as PDF as well. However, some of the more complex PDF-files look weird in Evince, so they're them (afaik).
You'll see what I mean if you look at this one:
[img]http://img408.imageshack.us/img408/376/bild1ru2.png[/img]
(Similar PDF files can be found [here](http://www.n-mag.de), just in case any German-speaking person is interested ;) ).

There's already a howto here at ubuntuforums.org about PDF-thumbnails using gs, but the thumbnails created by this script don't seem to know anything about anti-aliasing. Though, they already look much better than the one created by evince-thumbnailer:
[img]http://img441.imageshack.us/img441/9813/bild2nw8.png[/img]

There it is, the background image :)! Anyway, the quality could still be improved, so I decided it would be best to make use of ImageMagick instead of using Ghostscript directly.

If you don't have ImageMagick installed yet, type
```
sudo apt-get install imagemagick
```
into a command line. Ghostscript should already be installed on your system - if not, you should install the package "gs-esp".

Just copy the following code and save it (as root) as "pdfpreview.sh" in /usr/bin .
```
#!/bin/sh

TMP=$(mktemp -d /tmp/pdfpreview.XXXXXX)
SIZE=128
IN=$1
OUT=$2

IN=$(echo $IN | sed 's/file:\/\///')

convert -geometry x$SIZE $IN[0] $TMP/0000001.jpg

mv $TMP/0000001.jpg "$OUT"

rm -rf $TMP
```
Make sure to make this file executable and accessible for ordinary users:
```
sudo chmod +rx /usr/bin/pdfpreview.sh
```

Now all you have to do is to open your gConf editor and find the entry:
desktop > gnome > thumbnailers > application@pdf
There, you've got to change the value of "command" to the following:
```
/usr/bin/pdfpreview.sh %u %o
```

If you don't want to log out in order to see the effect, you can type in a terminal:
```
cd
rm -r .thumbnails
killall nautilus
```

That's it :)! This way, the thumbnail looks much better, doesn't it?
[img]http://img248.imageshack.us/img248/903/bild3bp6.jpg[/img]

It's not only this particular PDF thumbnail that looked weird using evince-thumbnailer. I've got the impression that every single thumbnail looks slightly better now, thanks to anti-aliasing and the nice border around the image :)^^.

---

### Post by Infinite Indefinite on 2011-09-29
Thank you so much.  This is a great replacement for evince-thumbnail, which can sometimes 'run amok' as someone noted on the following thread:

[http://ubuntuforums.org/showthread.php?t=1001614]("http://ubuntuforums.org/showthread.php?t=1001614").

Incidentally, one can also make the script operational for all users with the command:

```
sudo chmod a+rx /usr/bin/pdfpreview.sh
```

However, I found that in order to keep GNOME thumbnailing in this way, it was necessary to create the following schema file (labelled as pdfpreview.schemas)

```
<gconfschemafile>
<schemalist>

<schema>
<key>/schemas/desktop/gnome/thumbnailers/application@pdf/enable</key>
<applyto>/desktop/gnome/thumbnailers/application@pdf/enable</applyto>
<owner>pdfpreview.sh</owner>
<type>bool</type>
<default>true</default>
<locale name="C">
<short></short>
<long></long>
</locale>
</schema>


<schema>
<key>/schemas/desktop/gnome/thumbnailers/application@pdf/command</key>
<applyto>/desktop/gnome/thumbnailers/application@pdf/command</applyto>
<owner>pdfpreview.sh</owner>
<type>string</type>
<default>/usr/bin/pdfpreview.sh %u %o</default>
<locale name="C">
<short></short>
<long></long>
</locale>
</schema>

</schemalist>
</gconfschemafile>
```

After creating the file, copy it to /usr/share/gconf/schemas, i.e.

```
sudo cp pdfpreview.schemas /usr/share/gconf/schemas
```

and then activate it:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/pdfpreview.schemas
```

Then logout and login to see the results.

In some cases, one might prefer the evince thumbnail, in which case, the following command should re-introduce it for a single thumbnail:

evince-thumbnailer -s 128 [**name of file to thumbnail**].pdf ~/.thumbnails/normal/[**name of thumbnail to replace**].png

To prevent the thumbnailer rewriting it:

sudo chmod -c a-w ~/.thumbnails/normal/[**name of thumbnail to replace**].png

(*Sometimes this might not suffice, in which case one should go to the thumbnail file, right-click, select Properties, and in the Permissions Tab, change access settings to Read Only.*)

For certain files (in this case, fables.pdf), the new thumbnailer will generate a blank page; upon testing, I find the following error message:

> **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
Segmentation fault (core dumped)
convert: Postscript delegate failed `fables.pdf'.

This seems to be an issue with ghostscript.
-----------------------------------------------------

*Incidentally, I drew on the following code regarding **OpenOffice 2** thumbnails to create the schema file:*

[http://ubuntuforums.org/archive/index.php/t-76566.html]("http://ubuntuforums.org/archive/index.php/t-76566.html")

---

### Post by Infinite Indefinite on 2011-11-02
Sometimes, the line '**convert -geometry x$SIZE $IN[0] $TMP/0000001.jpg**' will uncover some errors in the pdf file, and will start registering some warnings before either repairing or ignoring them.  This can take a second or two, but can result in the thumbnail process not being finished when the next command takes place - resulting in a generic icon instead of a thumbnail.

To avoid this add the following line after the convert command:

```
sleep 3s
```

This short three second delay generally gives ImageMagick enough time to sort out various errors and correct them before moving on.

---

