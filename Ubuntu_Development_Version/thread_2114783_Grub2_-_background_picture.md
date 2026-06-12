---
title: "Grub2 - background picture"
date: 2013-02-11
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-11
For those readers that use grub2 with a simple, but modified background picture.
If you have a DE background picture of your own, like most us do, it also seems pretty nice to use the same picture for the grub2 background.
In additon to that I use the three set backround in my GS DE, where background pictures are changed according to the clock time.

However, for the DE background I can use a png or jpg picture, among others.
But grub2 only accepts a png image (from /boot/grub/).
A jpg is not recognized.
Why is that.

---

### Post by cecilpierce on 2013-02-11
Don't know why, thats only one reason I still use burg, lot easier to change things.

---

### Post by cariboo on 2013-02-11
I just set up the background image in grub using the attached image, which is a .jpg. You may want to check if the image you are using is actually a jpeg, and not something else.

```
# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
	if set_background_image "${background}"; then
		exit 0
	fi

```

according to /etc/grub.d/05_debian_theme the file types in the above snippet are valid

---

### Post by Harry33 on 2013-02-11
> **cariboo907 said:**
> I just set up the background image in grub using the attached image, which is a .jpg. You may want to check if the image you are using is actually a jpeg, and not something else.

```
# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
    if set_background_image "${background}"; then
        exit 0
    fi

```according to /etc/grub.d/05_debian_theme the file types in the above snippet are valid

That's funny.

For me grub2 just won't accept jpeg.
I am using this version of grub2 (2.00-12ubuntu1)
I tested it this way.
First I took the png image that is working fine (from /boot/grub/).
Then I opened it with gimp and exported it as jpeg.
With the same file name (but with jpg extension) I moved it into /boot/grub/).
Then deleted the png image and run "sudo update grub".
Grub found that jpeg image OK when configuring grub.
But after that, the grub menu does not have a background image.

Everything works fine after changing the image to the same, but a png image.

---

### Post by grahammechanical on 2013-02-11
> But after that, the grub menu does not have a background image.

I have downloaded grub2 splash images through the Software Centre and they are in tga format.

I have found that sometimes Nautilus does not pre-view an image. It shows a monitor screen with a black background without the image. If I select one of those images to go into /boot/grub then the Grub background image is black.

I like to give all my installs their own Grub background image so I know immediately which Ubuntu has taken control of Grub. Yesterday I installed 12.04.2 and downloaded the Grub2 splash images. Nautilus only showed the actual images of two of the files. The rest were black. So, I choose one of those two and that one was presented as the background image. If I had choosen one of those images that were not displayed then the grub background would have been black. I am sure of it.

This image that you are using, is Nautilus displaying it? Or just a black screen?

Regards.

---

### Post by Harry33 on 2013-02-11
> **grahammechanical said:**
> I have downloaded grub2 splash images through the Software Centre and they are in tga format.

I have found that sometimes Nautilus does not pre-view an image. It shows a monitor screen with a black background without the image. If I select one of those images to go into /boot/grub then the Grub background image is black.

I like to give all my installs their own Grub background image so I know immediately which Ubuntu has taken control of Grub. Yesterday I installed 12.04.2 and downloaded the Grub2 splash images. Nautilus only showed the actual images of two of the files. The rest were black. So, I choose one of those two and that one was presented as the background image. If I had choosen one of those images that were not displayed then the grub background would have been black. I am sure of it.

This image that you are using, is Nautilus displaying it? Or just a black screen?

Regards.

Yes it shows very well in Nautilus. I have never experienced any problems with Nautilus showing image thumbs.
If it is thumbs you are talking about.
I use eog to show the actual images, not thumbs.

---

### Post by Cavsfan on 2013-02-11
That is odd. I have had to edit a photo with Gimp before and re-scale it and then export it.
It was a .jpg and it would list with **sudo update-grub **but, not display until editing it.

Here is my current jpg in /boot/grub/ with Raring and grub 2.00:

[[IMG]http://ompldr.org/taDI4aA[/IMG]]("http://ompldr.org/vaDI4aA/DSCN2492.JPG")

And I agree with cariboo907:

As per /etc/grub.d/05_debian_theme, all of these picture formats are supported *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA

---

### Post by Harry33 on 2013-02-12
> **Cavsfan said:**
> That is odd. I have had to edit a photo with Gimp before and re-scale it and then export it.
It was a .jpg and it would list with **sudo update-grub **but, not display until editing it.

Here is my current jpg in /boot/grub/ with Raring and grub 2.00:

[[IMG]http://ompldr.org/taDI4aA[/IMG]]("http://ompldr.org/vaDI4aA/DSCN2492.JPG")

And I agree with cariboo907:

As per /etc/grub.d/05_debian_theme, all of these picture formats are supported *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA

Wait a minute.

Are you suggesting that grub2 won't accept a Gimp made image
- if it is a png and exported as a jpg (without editing)
- if it is a jpg, first rescaled and then exported as a jpg (without editing)?

And that grub2 only accepts a Gimp made image
- if it is first edited and then exported as a jpg?

---

### Post by Cavsfan on 2013-02-12
> **Harry33 said:**
> Wait a minute.

Are you suggesting that grub2 won't accept a Gimp made image
- if it is a png and exported as a jpg (without editing)
- if it is a jpg, first rescaled and then exported as a jpg (without editing)?

And that grub2 only accepts a Gimp made image
- if it is first edited and then exported as a jpg?


I am suggesting that simply editing the picture with Gimp sometimes _*helps*_ Grub to show the picture.
I have ran the command **sudo update-grub** and it's output listed the picture however upon boot that picture did not show up.
So I would edit that picture with Gimp. Clicking on Image, then Scale and then maybe changing Quality Interpolation from Cubic to Linear.
Then exporting that picture as a .jpg file that it *then* showed up at boot time.

This hasn't always been necessary. Most of the time the .jpg picture just appears like it should. 

But, from time to time I have found through trial and error that if it is listed in the output of **sudo update-grub2** but, not at boot time,
*sometimes* editing it with Gimp automagically makes it then appear at boot time. ;)

This is all mentioned in the green link in my signature.

---

### Post by grahammechanical on 2013-02-12
I wonder. Could it be that Grub has a very specific definition of what is a jpeg compressed image, whereas, the specification has been broadened out?

Or, saving an image with the .jpg extension does not in fact save the file as a jpeg compressed image, whereas, exporting the image as jpg file does compress it as a jpeg file?

Regards.

---

### Post by zika on 2013-02-12
> **grahammechanical said:**
> Or, saving an image with the .jpg extension does not in fact save the file as a jpeg compressed image, whereas, exporting the image as jpg file does compress it as a jpeg file?I'd bet on that that You might be very true on this... Been there, seen that... Not with Grub, of course...

---

### Post by Cavsfan on 2013-02-12
> **grahammechanical said:**
> I wonder. Could it be that Grub has a very specific definition of what is a jpeg compressed image, whereas, the specification has been broadened out?

Or, saving an image with the .jpg extension does not in fact save the file as a jpeg compressed image, whereas, exporting the image as jpg file does compress it as a jpeg file?

Regards.

I have no idea. I do know that this has happened to me since Lucid Lynx 10.04 with Grub 1.98.
Sometimes it happens and sometimes it does not. I usually use a .jpg file as that is usually what I have available.
But, as **Cariboo907** stated, any picture file *should* work.
Using custom font colors in 05_debian_theme is dependant on a picture (one of the types mentioned by **Cariboo907**) being in /boot/grub/.
Line 108 of 05_debian_theme tests if there is a picture and if there is font colors present after line 108, they will show at boot time.

So basically if the output of **sudo update grub** displays the picture name and the custom font colors show at boot time, the picture should also appear.

Likewise if you have custom font colors after line 108 in 05_debian_theme and no picture in /boot/grub/, the custom font colors should _not_ show at boot time.

The custom font colors are mentioned in section 4.2 of the green community wiki link in my signature.

Also, keep in mind that if you change pictures, you must remove the other as it looks for the 1st one it finds and goes with it.

---

