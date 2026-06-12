---
title: "Resize jpeg photos"
date: 2016-06-12
forum: Ubuntu Phone and Tablet
---

### Post by J-Linux on 2016-06-12
Hi everyone

Is it possible to resize jpeg files (eg photos taken with the phone camera)? If so, how do you do it?

J-Linux

---

### Post by SeijiSensei on 2016-06-12
There are many options.

I use Kubuntu, so for quick resizings I use the Gwenview app.  You can install it onto vanilla Ubuntu as well.  My guess is that some other image viewers can also rescale.

For a more heavyweight solution, install the [GIMP]("http://www.gimp.org/").  Then open the image and choose Image > Scale Image from the menus.

If you're comfortable with the command line, you can install [Imagemagick]("http://www.imagemagick.org/").  Then use its "[convert -rescale]("http://linux.die.net/man/1/convert")" command to resize the image.

---

### Post by oldfred on 2016-06-12
I install this:

sudo apt-get install nautilus-image-converter

> This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s)
using ImageMagick's convert tool.

---

### Post by ajgreeny on 2016-06-12
Those answers may or may not help depending on where the photos that you want to resize are located; if still on the phone itself I have no idea what might be available, but on your computer it is very easy with those applications mentioned above.

I use Xubuntu, and thunar, its file-manager, has a **Custom-actions** option where I have Resize scripts available from a right click of single or multiple image files.

---

### Post by J-Linux on 2016-06-13
Hi again

Thank you for those replies.

I understand how to resize jpeg photos using Ubuntu on a desktop or laptop. My question is about how to resize jpeg photos on an Ubuntu Touch smartphone (in my case, the Meizu Pro 5).

Is it possible? Or must I transfer jpeg images to a PC if I wish to resize them?

J-Linux

---

