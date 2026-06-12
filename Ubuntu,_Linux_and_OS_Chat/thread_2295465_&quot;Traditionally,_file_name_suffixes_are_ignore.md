---
title: "&quot;Traditionally, file name suffixes are ignored&quot;"
date: 2015-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-09-18
> Traditionally file name suffixes are ignored on Unix systems. (Source: [https://wiki.debian.org/MIME](https://wiki.debian.org/MIME)).

After reading [https://wiki.debian.org/MIME](https://wiki.debian.org/MIME) and [http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html](http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html) I get the impression that determining file types isn't a trivial task (compared to using file extensions). Anyone has some background information on how or why the decision to (some extent) ignore suffixes was reached?

---

### Post by bashiergui on 2015-09-18
I can rename any file to be whatever extention I like. For instance I can rename "picture.png" to "picture.pdf". That doesn't make it a pdf, though. What determines the true extension is the hex header and footer of the file. This link gives the hex headers for a ton of known filetypes.

[http://www.garykessler.net/library/file_sigs.html](http://www.garykessler.net/library/file_sigs.html)

If you base the filetype on the headers of the file, then you will always get the right one, regardless of the extension showing.

---

### Post by CharlesA on 2015-09-18
Pretty much nailed it ^.

Linux doesn't care about the extension. It can usually determine what file type it is, but the extensions are more for humans.

---

### Post by v3.xx on 2015-09-18
I have wondered if removing .png & .jpeg would have any negative effect.  I have done a few, but have never tried a couple of thousand.

I guess its alright then.

---

### Post by buzzingrobot on 2015-09-19
Unix, and then Linux, have file systems and user tools that can identify type regardless of name.

Windows originally was an extension to DOS. The file system used by DOS had far fewer capabilities.  Extensions were used to identify file types. AFAIK, they are still essentially cosmetic and their presence or absence has no impact on a file.

---

### Post by SeijiSensei on 2015-09-19
You can use the **file** command to identify a file the same way the OS does.

```

$ file test.mkv
test.mkv: Matroska data
$ mv test.mkv test.mp4
$ file test.mp4
test.mp4: Matroska data
$ file image.jpg
image.jpg: JPEG image data, JFIF standard 1.01
$ mv image.jpg image.png
$ file image.png
image.png: JPEG image data, JFIF standard 1.01

```

Changing the suffix obviously doesn't matter.

Using the file command in scripts is much more reliable than relying on filename extensions.

---

