---
title: "Google Earth on Linux"
date: 2005-09-27
forum: The Cafe
---

### Post by Master Shake on 2005-09-27
Has anyone gotten Google Earth to work on Linux, say through WINE?

---

### Post by jyank on 2005-09-27
Nope.  I've tried with wine a cvswine and always get an error upon installation.  I even tried it with cedega, cedega gave me a different error, but still wouldn't install

---

### Post by TrailerTrash on 2005-09-27
I tried it with CrossOver and a no-go....I really like Google Earth and use it on my crappy ole Xp system:eek: 
Other than that..I do hope oneday it will be a Linux version out. :smile:

---

### Post by GeneralZod on 2005-09-27
I'm wondering if Google would allow people to create an Open Source client.  The Google Maps API is, I think, freely available (though Javascript only...?), but the terms and conditions stipulate that the client may not obscure any ads that Google want to add.  I wonder if anyone has ever approached them about this?

---

### Post by UbuWu on 2005-09-27
Try [World Wind 2D]("http://ww2d.berlios.de/")... it is still very new and buggy, but looks promising!

---

### Post by YourSurrogateGod on 2005-09-27
[Here](http://code.google.com/apis.html#earth) is their API, so if someone knows how to make it work in Linux, knock yourself out.

---

### Post by 23meg on 2005-09-27
[http://earth.google.com/earth_fusion.html](http://earth.google.com/earth_fusion.html)

google earth fusion seems to work in linux; but i think it just works for entering new geographical data.

---

### Post by UbuWu on 2005-09-28
Another nice one:

apt-get install earth3d :razz:

(only works on breezy)

---

### Post by whiterabbit on 2005-09-29
[QUOTE=UbuWu]Another nice one:

apt-get install earth3d :razz:

(only works on breezy)[/QUOTE]Just noticed this one. Cheers.

---

### Post by heimo on 2005-09-29
[quote=UbuWu]Another nice one:

apt-get install earth3d :razz:

(only works on breezy)[/quote] 
Nice!
homepage with some screenshots: 
[http://earth3d.org/]("http://earth3d.org/")
[http://sourceforge.net/project/screenshots.php?group_id=107449](http://sourceforge.net/project/screenshots.php?group_id=107449)

---

### Post by -Rick- on 2005-09-29
[QUOTE=UbuWu]Another nice one:

apt-get install earth3d :razz:

(only works on breezy)[/QUOTE]

Indeed pretty cool :)
Although images(of Holland) are way less detailed than those from Google Earth.

---

### Post by mokeyjoe on 2005-10-20
I posted this in another thread but I guess its at home here. Google working on Google Earth for Linux:

[http://www.computerworld.com.au/index.php/id;1401986683;fp;16;fpid;0]("http://www.computerworld.com.au/index.php/id;1401986683;fp;16;fpid;0")

Anyone heard about this?

---

### Post by LinuxWiz83 on 2005-10-31
Earth3d is not even close to google earth because you can not enter the address, city, state, country like google earth. Well from what i notice it is very slow and it is only viewing maps and zooming in on the location you click on but you can not find your exact location that way. I am not saying it sucks just that have a lot of improvement.

---

### Post by angrykeyboarder on 2005-10-31
[quote=GeneralZod]I'm wondering if Google would allow people to create an Open Source client. The Google Maps API is, I think, freely available (though Javascript only...?), but the terms and conditions stipulate that the client may not obscure any ads that Google want to add. I wonder if anyone has ever approached them about this?[/quote]

Considering Google runs on Linux I'm hopefull that we'll see Google Earth on Linux before too long.

---

### Post by LinuxWiz83 on 2005-11-15
Yea i know it is being development but i have yet to come across when though but like you said it will be soon though.

---

### Post by suoko on 2005-11-17
What about  this?
[http://gentoo-wiki.com/HOWTO_Install_GoogleEarth_with_wine](http://gentoo-wiki.com/HOWTO_Install_GoogleEarth_with_wine)

Is that true?
I answer. It's true !!!
I couldn't belive it! 
add following line to your /etc/apt/sources.list before 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
and do an 
sudo apt-get update && sudo apt-get upgrade

Than just follow the instructions !!
Good luck

---

### Post by blastus on 2005-11-17
How is Google Earth different from Google Maps?

---

### Post by Master Shake on 2005-11-18
For one, it covers the whole eart.  Two, its  in 3 dimensions.  IE, you can zoom in on a mountain, and instead of being a flat sattelite  photo, you can actually view the mountain in three dimensions. Three, it shows 3-d represntations of famous buildings (Although its kinda buggy.  The Luxor in Las Vegas looks like a huge  block instead of a pyramid) 

I know there's others, but its a program that one really needs to see for one's self.

I am looking forward to the Linux version.

---

### Post by xmastree on 2005-11-18
For me the bigest difference is the seamless zooming. With google maps if you zoom in the screen goes blank while the individual squares load. With google earth the whole thing just gets larger, then slowly becomes clearer. Like downloading an interlaced image file.

Then there's the keyhole bbs thing. Somebody will spot something and post a downloadable link, which will take you to exactly the same view they had when they created it.

---

### Post by Jade Robbins on 2006-06-12
They just released Google Earth for linux, but it's definetly a beta. I might have to surf some of the forums for 3d help because it's slower than molasas!

---

### Post by KanRiNiN on 2006-06-12
I tried to install it but received a segmentation fault.  Any ideas?  If you could provide me with a command to log the errors since I don't know how to do that, I'd pastebin them.  The splash screen displays fine though :-/.  Could the fault be due to using ATI drivers?

---

### Post by halfvolle melk on 2006-06-12
It's running fine here with the ATi 8.25.18 drivers. I just downloaded it, chmod -x GoogleEarth.bin and install it.

---

### Post by cbudden on 2006-06-12
Running slow when using XGL, but fast with xorg.

---

### Post by xmastree on 2006-06-12
Woo Hoo! Works right out of the box for me. :D 

[ATTACH]11127[/ATTACH]

And it seems faster than the Windows version too.

---

### Post by _mobius_ on 2006-06-12
I fired it up no problem with "sh GoogleEarth.bin" and it installed happily.  When I run it looks like the attachment.

---

### Post by peacerist on 2006-06-15
Hi,

I have the same situation as _mobius_ has on Ubuntu Breezy on amd64 with nvidia video card. Tiles mixed up.

But when I connect to my 64-bit machine from a remote 32-bit using "ssh -Y" everything works fine.

Hope some comes with a solution.

---

### Post by nalmeth on 2006-06-15
Works out-of-the-box.
Sweet

---

