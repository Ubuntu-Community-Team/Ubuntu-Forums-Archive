---
title: "Cafe Project: Repackage World of Goo Demo for 64 bit"
date: 2009-02-15
forum: The Cafe
---

### Post by earthpigg on 2009-02-15
Editing this post to contain directions that work. The directions work on both the demo and the full game (which i purchased shortly after playing hte demo :guitar:)

This is how to repackage the World of Goo demo (or any other i386 deb) for amd64.

i took the directions from [here]("http://ubuntuforums.org/showthread.php?t=962835") and modified them.

this quote is from that thread, but modified so it applies to changing an i386 deb to an amd64 one.

> I am reposting this with more visibility. You can easily repackage any i386 deb outside the repos into an amd64 one. The reason you want amd64 packages instead of forcing the i386, is that while the former will show up as an installed package on synaptic, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for the World of Goo demo into an amd64 package:

1. Download the deb version of the World of Goo demo [here]("http://worldofgoo.com/dl2.php?lk=demo").
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder to "goo64" or whatever you want.
4. Open the folder
5. There are 3 files. remove the "debian-binary" file
6. Decompress "control.tar.gz". There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: amd64" (this is the key step of this process)
9. Open the other archive "data.tar.gz". There is a folder "." inside. Open it (double click). Select both the folders (usr and opt) and select uncompress.
10. Remove the files "control.tar.gz" and "data.tar.gz"
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (control, postinst, and postrm); a "usr" folder and an "opt" folder.
12. You are now ready to prepare your amd64 deb folder.
13. From the command line, go to the folder that contains your main goo64 folder you just prepared (again, you can name the folder whatever you want. i chose goo64).
14. type: dpkg --build goo64
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!

---

### Post by earthpigg on 2009-02-15
edit: was talking to myself here, essentially.

---

### Post by earthpigg on 2009-02-15
well then, i solved this by myself.

i needed to put 'amd64' in the control file. 

ill update the origional post when i am done playing with the demo ;)

---

### Post by AlbinoButt on 2009-02-15
> **earthpigg said:**
> 
you can force architecture, but then you wont be able to uninstall it via synaptic.

If you can't use Synaptic, why not just type the following into a terminal:

```
sudo dpkg -r WorldOfGooDemo
```

I got the full version, and using force architecture is all that's needed to install, and sudo dpkg -r WorldOfGoo is all that's needed to uninstall. Does a 64bit package have any advantage over just using those commands?

---

### Post by JackieChan on 2009-02-15
I already own the Wiiware version. :)

---

### Post by earthpigg on 2009-02-16
updated the origional post with directions :)

---

### Post by | MM | on 2009-02-26
> **earthpigg said:**
> 
This is how to repackage the World of Goo demo...


I heart you!

---

### Post by Sealbhach on 2009-02-26
> **AlbinoButt said:**
> If you can't use Synaptic, why not just type the following into a terminal:

```
sudo dpkg -r WorldOfGooDemo
```

I got the full version, and using force architecture is all that's needed to install, and sudo dpkg -r WorldOfGoo is all that's needed to uninstall. Does a 64bit package have any advantage over just using those commands?

Yeah, I force installed mine as well. Works absolutely fine. What's the big advantage about doing it this way? Apart from the Synaptic thing?


.

---

### Post by suclid on 2009-03-08
I force architecture installed World of Goo, but then found out this new method of rebuilding it as amd64, but installed it with the latter method without removing the one I forced installed. Did my second install overwrite the first one? Is there a way to check if the forced install is still on my system?

---

### Post by BigSilly on 2009-03-29
Bumped for a bit of help...

I found [this]("http://2dboy.com/forum/index.php/topic,1464.msg9805.html#msg9805") over on the 2D Boy forums for repackaging the 32 bit World of Goo into 64 bit, and it did the trick beautifully: 

```
#!/bin/sh -e

DEB_IN=$1
DEB_OUT=$2

[ -n "${DEB_OUT}" ] || DEB_OUT=`echo "$1" | sed 's/i386/amd64/'`

if [ -z "${DEB_IN}" ] || [ "${DEB_IN}" = "${DEB_OUT}" ]
then
	echo "Usage: deb-from-i386-to-amd64.sh <input.deb> [<output.deb>]"
	exit 1
fi

TMP_DIR=`mktemp -d`
dpkg-deb -x "${DEB_IN}" "${TMP_DIR}"
dpkg-deb -e "${DEB_IN}" "${TMP_DIR}/DEBIAN"
sed -i 's/i386/amd64/' "${TMP_DIR}"/DEBIAN/control
sed -i 's/Depends: /Depends: ia32-libs, /' "${TMP_DIR}"/DEBIAN/control
dpkg-deb -b "${TMP_DIR}" "${DEB_OUT}"
rm -r "${TMP_DIR}"
```

Thrilled to bits! However, I also have the .rpm that I downloaded from 2D Boy because I dual boot with Mandriva. My question is, does anyone have a similarly easy way to repackage the 32 bit .rpm into 64 bit?

Thanks all. :)

---

### Post by Perfect Storm on 2009-03-29
I don't if it easier, but it's the way I prefer; [http://gaming.gwos.org/doku.php/guides:64bit:worldofgoo](http://gaming.gwos.org/doku.php/guides:64bit:worldofgoo)

---

### Post by BigSilly on 2009-03-29
> **Artificial Intelligence said:**
> I don't if it easier, but it's the way I prefer; [http://gaming.gwos.org/doku.php/guides:64bit:worldofgoo](http://gaming.gwos.org/doku.php/guides:64bit:worldofgoo)

Hmmm. But that's for the .deb again isn't it? I was after something that did the same but for the .rpm. Can anyone help? 

Thanks.

---

### Post by Perfect Storm on 2009-03-29
> **BigSilly said:**
> Hmmm. But that's for the .deb again isn't it? I was after something that did the same but for the .rpm. Can anyone help? 

Thanks.


No sorry. I havn't used/tried a rpm based distro since mid 2004. 

Wonder if it's possible to alter the .deb package as I described and then convert it to .rpm. The alien app should do that for you.

---

### Post by kringle on 2009-05-10
Thank you for tutorial on how to make this 64 bit.  It works great.  While money is tough, I was happy to buy this game and support quality apps for Linux.  I'm also trying to keep as much as possible in 64 bit, so, again, this was great.

---

