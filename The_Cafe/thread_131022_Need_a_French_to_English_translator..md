---
title: "Need a French to English translator."
date: 2006-02-15
forum: The Cafe
---

### Post by mips on 2006-02-15
Hi,

A few people seem to be having problems with Intel e1000 LAN adapters in Ubuntu.

There is a wiki available for this but it is in French. [http://wiki.ubuntu-fr.org/materiel/e1000](http://wiki.ubuntu-fr.org/materiel/e1000)

I know you can use a online translator but they are not always accurate and sometimes seem to loose the meaning during translation.

Would someone like to translate it please ?

Merci beaucoup / Thank you

---

### Post by linuxden on 2006-02-15
Mips,

Am half french and half english, fluent in both... Willl look into it... if its not too long.... I am real busy at the moment...

Let you know swiftly...

Au revoir

---

### Post by linuxden on 2006-02-15
Mips, 

When do you need it done for?? Its not too long, but am currently watching a movie with my gf... Its late over here in europe...

Could have it for tommorrow evening at the latest...

Let me know if i should start....

---

### Post by mips on 2006-02-15
Thanks!

---

### Post by mips on 2006-02-15
[QUOTE=ubuntulifestyle]Mips, 

When do you need it done for?? Its not too long, but am currently watching a movie with my gf... Its late over here in europe...

Could have it for tommorrow evening at the latest...

Let me know if i should start....[/QUOTE]

Tomorrow evening would be more than I expected!

Enjoy the movie!

---

### Post by linuxden on 2006-02-15
[QUOTE=mips]Enjoy the movie![/QUOTE]

Thanks, Its sooooooooo boring!!! Its legally blond 2... I am so not amused!! lmao!!!

Oh do i get to have my name at the bottom of the translation?? lol

Have a good evening...

---

### Post by mips on 2006-02-15
Post it as a HOWTO in the Customisation & tips forum, add a reference/link to the original wiki page and take credit for the translation :mrgreen: 

Time for me to go watch Navy NCIS...

G'night

---

### Post by xequence on 2006-02-15
>  Its legally blond 2... I am so not amused!! lmao!!!

I liked that movie.

---

### Post by linuxden on 2006-02-16
[QUOTE=xequence]I liked that movie.[/QUOTE]

Its ok to watch i have had worse, Legally blond 1 anyone?? LMAO!!!

Sorry Its just that i prefer movies that let me have a good laugh every 5 minutes, instead of a movie that lets me giggle idioticly every 10 seconds....

But hey, Variety is the spice of life!!!

---

### Post by linuxden on 2006-02-16
Mips,

How to is posted, waiting for approval...

---

### Post by mips on 2006-02-16
Hi,

Thx but where is it, I did a search for posts under your name but did not see it ?

Link ?

---

### Post by linuxden on 2006-02-16
[QUOTE=mips]Hi,

Thx but where is it, I did a search for posts under your name but did not see it ?

Link ?[/QUOTE]

Dude, when you post a how to it needs to be approved.... for some reason...

Still waiting for the approval...I guess.

---

### Post by mips on 2006-02-16
:oops: Sorry, aware of that but forgot about it, how blind.

Could you possibly post it in the networking forum so long, that way people can test it out.

Thanks

---

### Post by linuxden on 2006-02-16
[QUOTE=mips]:oops: Sorry, aware of that but forgot about it, how blind.[/QUOTE]

No need to :oops:... 

For sure... I am not sure if i still have it edited, for here... It took me a while to write it as a post after having spent time writting it in Writter....

will check to see and then post it in networking...

---

### Post by mips on 2006-02-16
Thanks, that would be nice.

---

### Post by linuxden on 2006-02-16
[SIZE="4"]**Summary:**[/SIZE]

This guide will take you through the installation of the E1000 driver for Intel's integrated network card the &#8220;Intel Pro 1000 series&#8221;.

[SIZE="4"]**Introduction:**[/SIZE]

Why do you need to install these drivers?

Some processors on recent &#8220;Intel&#8221; motherboards do not detect the integrated network cards. The chips on these motherboards support up to 1GB/s.
The Ubuntu driver is obsolete for these cards, this means that in order to get the card working you will need to install the latest driver.

Due to the nature of this driver, you are probably reading this &#8220;how-to&#8221; on another computer, you might want to print it now or keep it easily accessible.
[SIZE="4"]
**What you will need:**[/SIZE]

An Internet connection ;o) (get hold of another computer)

We need to download a few files before we can start. In fact you will need to download 4 files.

I recommend you Burn them to CD or any other external storage device, you could even put them on a shared partition you have access to, since you probably wont have access to an Internet connection in your Ubuntu install. 
The 1st of these files is of course the driver itself, you will find it either on Intel's website in the support section or on [sourceforges e1000 driver page]("http://sourceforge.net/projects/e1000").

The 3 other files are to install the gcc-3.4 compiler, it is needed to install the driver, since the default Ubuntu install comes as standard with the gcc-4.0 compiler(gcc-4.0 is not backwards compatible).

 [COLOR="Red"][SIZE="5"][CENTER]Do not install using gcc-4.0 you will get errors![/CENTER][/SIZE][/COLOR]

These are the links to the files:

[gcc-3.4-base]("http://packages.ubuntu.com/breezy/devel/gcc-3.4-base")
[cpp-3.4]("http://packages.ubuntu.com/breezy/interpreters/cpp-3.4")
[gcc-3.4]("http://packages.ubuntu.com/breezy/devel/gcc-3.4")

I will describe the installation of these 3 packages later on, you should not get any dependency problems with these 3 packages.

Before we start find out your kernel number, do this by typing in a terminal
```
 uname-r
``` 

write it down you will need it later on.

[SIZE="4"]**Installation:**[/SIZE]

Unzip the  driver.

Install either using synaptic or apt-get the following packages:

linux-headers- (my kernel version) for example with the current Ubuntu Kernel :
```
sudo apt-get install linux-headers-2.6.12-10-386
```
**binutils:**
```
sudo apt-get install binutils
```
**build-essential:**
```
sudo apt-get install build-essential
```

**In a terminal window:**

```
cd
``` to the directory where the 3 .deb packages are.
```
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
```
then:
```
cd
```to the  /e1000-6.3.9/src directory where you unzipped the driver and type:
```
sudo make install
```

Do not get worried by all the output on the terminal window while compiling, its normal.
Once compiled type:
```
sudo modprobe e1000
```  
Your network card should now be recognised , you can activate it in the Ubuntu network settings.
**Note(s):**
during this how to I assumed the GUI was fully functional, how ever, it is possible to do so without the GUI by simply issuing the commands in a terminal.

If you update to the new kernel, it might be necessary to recompile the driver. (Be careful Automatic updates could install the new kernel at any time.) If  you install the new kernel just follow this how to again, this time using your new kernel number.

Translated and adjusted for the English language by [Ubuntulifestyle]("http://linuxden.org"). You can find the original how to here.  Originally written by &#8220;cooky&#8221; for the [www.ubuntu-fr.org](www.ubuntu-fr.org) forums.

---

### Post by linuxden on 2006-02-16
:oops: posted it in the wrong forum... should i repost it in networking or should i wait untill its a howto?

---

### Post by mips on 2006-02-16
Dont worry, it's ok. i'll search the for the posts of people having problems and point them here for now.

Thanks again for the translation, much appreciated!

---

### Post by JNasci7906 on 2006-04-26
hey all....i just switched to linux and have tried this fix countless times already, using the drivers specified and the newest ones...im confused as to why they arent lettin linux recognize my onboard card...suggestions?

---

