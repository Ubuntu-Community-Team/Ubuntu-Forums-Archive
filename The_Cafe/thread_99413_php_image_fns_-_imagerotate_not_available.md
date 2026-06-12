---
title: "php image fns - imagerotate not available?"
date: 2005-12-05
forum: The Cafe
---

### Post by Simon Nuttall on 2005-12-05
Hi this is my first post to these forums.

Presumably because I'm new I can't me post a new thread to what I thought was the right forum for this topic, so apologies if the question below may seem a bit out of place. 

I've really enjoyed spending the past 2 or 3 weeks with ubuntu and learned far more about linux with this distro than all the others I've previously battled with (including suse9.1, fedora 3, and even xebian 1.0.3!) I've managed to solve most of the problems I've had with getting it to run on a compaq evo N400c laptop, including even getting the stubborn winmodem to work) and I was pleased that the sound card and wireless LAN worked without much tweaking. Since then I've setup a LAMP server and am developing my websites farily efficiently with emacs.

And now to my question, any help appreciated!

apache2 reports:

[INDENT]PHP Fatal error:  Call to undefined function:  imagerotate()[/INDENT]

I have php 4.4.0-3 and the GD section reports that GD "version 2.0 or higher" is loaded. Other image functions, such as imagefilledellipse() are working.
Synaptic says I have libgd1-noxpm, libgd2-xpm and php4-gd installed.

[http://uk.php.net/manual/en/function.imagerotate.php]("http://uk.php.net/manual/en/function.imagerotate.php") suggests that 
[INDENT]Note: This function is only available if PHP is compiled with the bundled version of the GD library.[/INDENT]

which implies I have to compile php. 

I'm not sure that I already have the required modules to enable imagerotate, and compiling php sounds like quite a big task, and I don't know if that would fix the problem. I'd be happy to switch to php5 if I knew that would solve it. Any ideas?

---

### Post by invalid on 2005-12-05
It sounds like you just need to add the extension to your php.ini file
```
extension=gd.so
```
Then restart apache, and you should be good to go.

Cheers,
Cb

Edit:
I missed the line where you said > I have php 4.4.0-3 and the GD section reports that GD "version 2.0 or higher" is loaded. by accident.. so this solution may not work for you. My apologies.

---

### Post by Simon Nuttall on 2005-12-05
Dear invalid, thank you for your help, but it was er.... invalid! Yes I already have the gd extension loading as your later comment acknowledged. I'm still stuck though. cheers, Simon

---

### Post by Simon Nuttall on 2005-12-12
Hey, I am still stuck on this question, can anybody help: why isn't imagerotate() available even though I have the gd library loaded?

---

### Post by phfeenikz on 2006-11-27
I'm running into this same problem with both php4 and php5.  I suspect that the PHP packages aren't compiled with the bundled GD.  Judging from the age of this thread I'm not expecting much, but before I move on to another flavor of Linux that suits my needs, I have to at least ask; is there any way to get the imagerotate() function to work with Ubuntu?

---

### Post by cabocom on 2007-02-05
I'm confused :confused: 

I have the same problem that you. I have php 5.1.2 and gd 2.0 or higher.  All options for gd are enabled.  My code written in php can work with images with no problem except when I'm going to use the imagerotate() function.  Then my browser says 

*Fatal error: Call to undefined function imagerotate() in /var/www/maxdomo/comercial/funciones/imprimir.libreria on line 224*

I comment the line and everything work, but I need rotate an image.  

I have looking for the answer of the problem in google and I have found some people with the same problem but many answers:

[LIST]
[*]Uncomment the line of extension_dir in php.ini
[*]Reinstall the gd library
[*]Don't rotate the image
[*]Compile the php library with other options
[*]Compile the gd library with other options, it's seem to be a problem of Debian ([http://www.lugli.org.ar/pipermail/linux/2005-September/059285.html](http://www.lugli.org.ar/pipermail/linux/2005-September/059285.html))
[/LIST]

The three frist don't wrok but I doubt with the last two options because my knowledgement can't do it.  I use Synaptic for everything because I'm a Windows user coverted to a Ubuntu user.

Please admins or Linux gurus, post here how we can recompile the gd library with the correct options 

Thxs

---

### Post by cabocom on 2007-02-05
In Spain we said that if Mahoma can't go the mountain, the mountain goes to Mahoma.  So if you can't use imagerotate because is missing use another function write in php to emulate it.  You can find examples in [http://au2.php.net/manual/es/function.imagerotate.php#48725](http://au2.php.net/manual/es/function.imagerotate.php#48725)

It's a pitty

[-X

---

