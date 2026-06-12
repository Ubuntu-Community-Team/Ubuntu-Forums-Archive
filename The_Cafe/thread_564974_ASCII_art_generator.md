---
title: "ASCII art generator?"
date: 2007-10-01
forum: The Cafe
---

### Post by proalan on 2007-10-01
I used to use a program in windows that converted images into ascii art, are there any ASCII art generators about in the linux world?

---

### Post by saulgoode on 2007-10-01
[The GIMP]("http://gimp.org/")

---

### Post by yabbadabbadont on 2007-10-01
My search only turned up windows/dos and online converters.  If you have one that you like from Windows/DOS, you could see if it will run using WINE or DosBox/DOSEmu.

---

### Post by FranMichaels on 2007-10-01
> **proalan said:**
> I used to use a program in windows that converted images into ascii art, are there any ASCII art generators about in the linux world?

[http://libcaca.zoy.org/](http://libcaca.zoy.org/)
[http://aa-project.sourceforge.net/](http://aa-project.sourceforge.net/)

Ubuntu has both. :)

You can even watch videos in ascii on the fly using these too :lolflag:

---

### Post by ValPaliy on 2008-05-13
> **proalan said:**
> I used to use a program in windows that converted images into ascii art, are there any ASCII art generators about in the linux world?
Try [JavE]("http://linuxhelp.wordpress.com/2006/05/19/jave-a-versatile-editor-for-creating-ascii-art/"), it's Java-based.

P.S. This is my first post here, and I want to say thanks - I am relatively new to Ubuntu, your forums have helped me a lot already - keep up the good work!!!

---

### Post by aaaantoine on 2008-05-13
> **saulgoode said:**
> [The GIMP]("http://gimp.org/")

What he said.

1. File -> Save a Copy
2. From the file type drop-down, select ASCII art.
3. From there, you get to choose between plain text, HTML, and a bunch of other options.

If you have a big picture, you should resize it beforehand.  The GIMP's ASCII art tool treats 1 pixel as 1 ASCII character.

---

### Post by Dr Small on 2008-05-13
Maybe I am missing something, but I don't have a "ASCII Art" option. Could you provide a screenshot?

---

### Post by saulgoode on 2008-05-13
You need to click the Select File Type triangle to display the available options.

[IMG]http://www.imageox.com/image/259366-tmp.png[/IMG]

---

### Post by Dr Small on 2008-05-13
> **saulgoode said:**
> You need to click the Select File Type triangle to display the available options.

[IMG]http://www.imageox.com/image/259366-tmp.png[/IMG]
Thanks. That's what I thought. Apparently I don't have that. :(

---

### Post by aaaantoine on 2008-05-14
That's a bit different from my view.  You can also find it here:

[img]http://img255.imageshack.us/img255/7909/screenshotsaveacopyofthlo4.png[/img]

---

### Post by Sporkman on 2008-07-26
I just wrote an online one:

[http://sporkforge.com/imaging/ascii.php](http://sporkforge.com/imaging/ascii.php)

FYI, this runs on a dedicated Ubuntu server. Note the speed & stability! :)

(grumble grumble everybody recommends debian centos bsd over ubuntu server grumble...)

---

### Post by aktiwers on 2008-07-27
> **Sporkman said:**
> I just wrote an online one:

[http://sporkforge.com/imaging/ascii.php](http://sporkforge.com/imaging/ascii.php)

FYI, this runs on a dedicated Ubuntu server. Note the speed & stability! :)

(grumble grumble everybody recommends debian centos bsd over ubuntu server grumble...)
I like it!

If you have pictures of a dude with sunglasses on your server, thats me!  :D

---

### Post by Sporkman on 2008-07-27
> **aktiwers said:**
> I like it!

If you have pictures of a dude with sunglasses on your server, thats me!  :D

Great, glad you like it!

Pics aren't saved, so if the fed ever shuts me down for using Linux, you won't be implicated visually!

---

### Post by chris4585 on 2008-07-27
I so did not know gimp did that, thanks!

---

### Post by Toshibawarrior on 2008-12-17
> **aaaantoine said:**
> What he said.

1. File -> Save a Copy
2. From the file type drop-down, select ASCII art.
3. From there, you get to choose between plain text, HTML, and a bunch of other options.

If you have a big picture, you should resize it beforehand.  The GIMP's ASCII art tool treats 1 pixel as 1 ASCII character.

I did this and I just get scrambled letters vertically aligned that don't look anything like the picture...did I do something wrong?...

I'm using the GIMP that comes with Intrepid Ibex...

Can anyone help me with this?

---

### Post by Super TWiT on 2008-12-21
Me too.  I get the same thing, but I am using the Ubuntu 8.04.

---

### Post by Eisenwinter on 2008-12-21
```
sudo apt-get install figlet
```
```
figlet <text>
```

Done.

---

### Post by Super TWiT on 2008-12-21
I figured out the problem.  I was opening up the file with abiword.  Duh! It put the stuff on multiple pages. Sometimes I think I should see a shrink...

---

### Post by MikeTheC on 2008-12-22
You mean like this...

```
               -... .                   
            ..==;===:... .              
           .:==;;;;;====:.              
         .:===;;;=;=;;;=;==.            
        .:=;=;;=;;;;;=;;=;==..          
       .:==;;;=;;=::=;;=;;;;=.          
       ===;;=;;;=;;.-=;;;;=;;;.         
     .:=;;;;;;=;;-==.-;=;=;;=;:         
    .:==;;;=;=;;=;.-:::;;;;=;;;         
    .__ssss_c:-:=;=;.- :==;;;=;:        
  _yQQQQWWWQQQmw,=;;=:. =;;=;;;=        
  mQQ8VVHQWQQQQQQma;-==:.=;;;=;;:       
 :T!aawawawQQQQQQQQQw/-=.:=;=;;=;       
 _yQQWWQWWQQQQQQQQQQQQg/:.=;;;=;;.      
<QQQQQQQD???TVQQQQQQQQQQa :=;=;;;.      
]QQQQP"`      -?QQQQQQQQQk.=;;;=;:      
]WQP'           .?WWQQQQQQ/;=;=;;=      
-W[                ?QQQQQWL:;;;;=;.     
 -                  -$WQk4Q/;=;=;;.     
                     .4QQc$L.=;;;=:     
                       4QQa4;;;=;;:     
                       .4QQw`;;;;=:     
                         4QQa ==;;=.    
                         -QQQc-;=;=:    
                          )WQQ,;:<aa/   
                           4QQL jWWWQm, 
                           -QQfjWWQQQQm 
                            )U:QWQQQQQQ/
                            . ]QQQQQQQQ[
                             .]QQQQQQQQ[
                              )QQQQQQQQ(
                               QWQQQQQQ'
                               )WQQQQQE 
                                "QWQQF  
                                  ""^   
                                        
                                        
```

---

### Post by bruno386 on 2009-01-18
Sporkman

thanks
sick ascii gen :D

---

### Post by MaxIBoy on 2009-01-18
Try throwing something together using aalib (available in the repos.) Aalib is like openGL, only it outputs text.

To get an idea of the power of aalib, try this:
```
sudo apt-get install bb
su 
bb
```
Unfortunately, it has to run as root ("sudo" doesn't work,) otherwise it freezes just as the music starts. Weird.

---

### Post by ded38fr on 2009-05-20
If you want an ASCII art generator, just for text:
[INDENT][http://www.desmoulins.fr/index_us.php?pg=scripts!online!asciiart]("http://www.desmoulins.fr/index_us.php?pg=scripts!online!asciiart")[/INDENT]

Or, the Bovine version:
[INDENT][http://www.desmoulins.fr/index_us.php?pg=scripts!online!cowsay]("http://www.desmoulins.fr/index_us.php?pg=scripts!online!cowsay")[/INDENT]

And to create signatures:
[INDENT][http://www.desmoulins.fr/index_us.php?pg=scripts!online!boxes]("http://www.desmoulins.fr/index_us.php?pg=scripts!online!boxes")[/INDENT]


Enjoy ;)

---

### Post by alfresco_0101 on 2009-09-26
> **Eisenwinter said:**
> ```
sudo apt-get install figlet
``````
figlet <text>
```Done.


Thanks it works like Charm...Gr8!

---

### Post by brpylko on 2011-04-20
if anyone is still checking this [http://www.glassgiant.com/ascii/](http://www.glassgiant.com/ascii/) is a good one.

---

