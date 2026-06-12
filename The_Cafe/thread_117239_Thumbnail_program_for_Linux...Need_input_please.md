---
title: "Thumbnail program for Linux...Need input please"
date: 2006-01-14
forum: The Cafe
---

### Post by PapaWiskas on 2006-01-14
I am going on my 1st month of being completely Windoze free....

My wife has been watching me run Ubuntu on my laptop and is very interested in dumping Windoze as well.  She has a website that she takes pictures of her items, and then takes those items and uses a program called Thumbs Plus.  It basically uses a batch process to make thumbnailed images of the pictures in a specified directory.  The thumbnail size is configurable.  You can also specify the output directory if you want to.

She wants to switch to Linux, but she needs the same types of programs she uses now in Windoze.

Thanks for any input you could offer.

---

### Post by JimmyJazz on 2006-01-14
there dozens of ImageMagick scripts that do this (with extremly good image quality too)
[http://www.cit.gu.edu.au/~anthony/graphics/imagick6/](http://www.cit.gu.edu.au/~anthony/graphics/imagick6/)

---

### Post by Viro on 2006-01-14
I don't know if this will do, but gThumb Image Viewer that comes with Ubuntu has a function that generates a web album. Perhaps that is similar to what you're trying to achieve?

---

### Post by amohanty on 2006-01-14
So let us say you have the pics in a folder called /home/wifey/pics

First install ImageMagick via:
> sudo apt-get install imagemagick

Thenwrite a bash script:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

to use the ImageMagick convert utility:
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

to do whatever you want. :)

HTH
AM

PS: I do this all the time for my pics that I download from my camera but which are too big to be uploaded to fotki. I would start by reading the guides, creating a script adn posting here if you have any problems with the script or the utility.

---

### Post by odrop on 2006-01-14
If you use KDE/Konqueror you also have another easy option.

Open the directory where all pics you want to thumbnail are, then Tools->Create Image Gallery.

It looks like it has all the options your wife uses and more.  It'll even create a html page with links to all the thumbnails for you.  Pretty nifty extension.

---

### Post by ice60 on 2006-01-14
hi, i can't find the lecture but this guy does something with Python and thumbs. i can't remember exactly what he covers but it might help.
[http://video.google.com/videoplay?docid=-7090155776944147308&q=lecture](http://video.google.com/videoplay?docid=-7090155776944147308&q=lecture)
if you are interested, when you go to the link click on "More from this user" to find the video i'm talking about, all i know is it very likely to be one of the "programming with Python and Tkinter" links

OT. if you search for lectures at google videos there's lots of great stuff like Richard Stallman lectures, Linux lectures etc. maybe i'll start a thread about it.

---

### Post by Rinzwind on 2006-01-14
Hey making thumbs is VERY easy. While I was looking around the web I ran into the codesnippet I put inside the code-tag. 
(Do you have Python with the PIL module installed? BOTH are inside synaptic btw.)

With this little program:
```
#!/usr/bin/env python

import sys
import Image
 
def thumb(image):
	size = list(image.size)
	size.sort()
	image = image.crop((0, 0, size[0], size[0]))
	image = image.resize((100, 100), Image.ANTIALIAS)
	return image
 
if __name__ == '__main__':
 
	image = Image.open(sys.argv[1])
	image = thumb(image)
	image.save("T"+sys.argv[1])
```

the image 'sample.jpg' is turned into a thumbnail called 'Tsample.jpg'. If you want something else you just need to change the 'image.save' command.
Just save it with a name like thumbnail.py. chmod it to 777 and you are almost done: all you need is to do is call it with an imagename like:

./thumbnail sample.jpg 

I posted some more snippets regarding manilulating pics here:
[http://python.xgn.com.br/viewtopic.php?id=41](http://python.xgn.com.br/viewtopic.php?id=41)


Btw: this codesnippet does 1 picture at a time but I can't imagine that reading a  whole dir with JPGs is that hard to add :)

---

### Post by PapaWiskas on 2006-01-14
This forum never ceases to amaze me...such quick and a plethera of responces.

OK...here is the deal.  I am going to go through each one of these suggestions and try and figure out the easiest one for her to use.  She does not mind using Linux but she is not really interested in having to configure a bunch of stuff, she just wants to use it and go.  I would be the one who maintains it, which wont be as hard as maintaining a Windoze box.

Keep the suggestions coming and I will post back soon on what I find out.

Thanks everyone.

---

### Post by PapaWiskas on 2006-01-14
Ok....I am not a stupid person, but I am very new to Linux.  I have spent the last hour going over this stuff....and my head is spinning.  It really makes me realize how much of a dummy Windoze has made me.

I am not a coding type person, I was really hoping for a program in Linux that would let me do two things with images in a batch fashion.

1.) Let me define the size of the thumbs.
2.) Let me configure the prefix name of the thumbs.

Imagemagick sounds really cool, but I dont understand how to use it, and it is installed on my system, but from the looks of it, it does not have a GUI.  And since I am kinda stupid....I guess I need a GUI.

I could learn all of this....but that would take some time.....how much I am not sure...and I really want my wife off of Windoze as well.

I guess guys, I should have specified I need something simple for the sake of saving time.  I know, I know....us Windoze converts are a pain in the keister....;)

---

### Post by drizek on 2006-01-15
hte konqueror method mentioned above is very simple. have yo ufigured out how to use synaptic by now? if so, download kdebase and kdelibs, then open konqueror and then "Open the directory where all pics you want to thumbnail are, then Tools->Create Image Gallery."

im not sure how much control it will give you over the prefixes, but im sure someone can give you a link to another program that will handle that.

---

### Post by PapaWiskas on 2006-01-15
Well I installed KDE....and got more stuff in my menus than I would like.  I actually booted into KDE.  I like Gnome much better....KDE has WAY to much stuff in the menu system....anywhoo....no biggie, all that could be edited.  So I went back to Gnome and used Konquerer as described.

Is there a way to get it to save as a .gif or are the only options .jpg and .png?  

Otherwise I do like the solution making thumbs this way, way more efficient.

Thanks everyone.....

---

### Post by amohanty on 2006-01-15
> Is there a way to get it to save as a .gif or are the only options .jpg and .png? 

GIFs use the LZW compression algo which is patented by Unisys and thus apps are not able to use it legally in many countries. PNG was developed to get around this and is in many ways better, also it is an open format so there are no legal issues. Moreover all browsers (afaik - please make sure) support it so it shouldnt be a problem.

SOme info on the formats:
[http://www.w3.org/QA/Tips/png-gif](http://www.w3.org/QA/Tips/png-gif)
[http://www.webopedia.com/DidYouKnow/Internet/2002/JPG_GIF_PNG.asp](http://www.webopedia.com/DidYouKnow/Internet/2002/JPG_GIF_PNG.asp)

HTH
AM

---

### Post by PapaWiskas on 2006-01-15
thank you

i did not know this

settles that:D

---

### Post by drizek on 2006-01-15
ya, png is much better.

glad it worked for ya.

---

### Post by stani on 2007-12-21
Try Phatch for generating your thumbnails:
[http://photobatch.stani.be](http://photobatch.stani.be)

Here is a link to a tutorial for making thumbnails:
[http://www.digg.com/linux_unix/Make_SLICK_thumbnails_for_thousands_of_images_with_1_click](http://www.digg.com/linux_unix/Make_SLICK_thumbnails_for_thousands_of_images_with_1_click)

---

