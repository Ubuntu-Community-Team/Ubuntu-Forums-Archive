---
title: "A General question, please"
date: 2007-04-06
forum: Ubuntu Christian Edition
---

### Post by keithp on 2007-04-06
I am completely confused. (At my old age, my usual state!)

I would like to do some Bible study at home, and have two alternatives. 

I could buy a book to use in conjunction with my Bible, or I could use UbuntuCE. But I know nothing about the CE version of Ubuntu and its Bible study software :(  

With all the other programs on the UbuntuCE CD, there can't possibly be room for the whole Bible on it. So, is the software just a studying aid, and one needs to use it in conjunction with a Bible? If so which version is it associated with? I still prefer the Authorized Version. Or is it just a front-end to download the appropriate verses and commentary for the day?

Bible software appears to be a choice of E-sword, Gnomesword, or Bible Time.   

Searching the forum, googling, and reading the release notes don't appear to provide an answer.

In other words, how does one do Bible study using UbuntuCE?

Many thanks, and apologies again for having to ask such a very basic question.

Keith

---

### Post by mysticrider92 on 2007-04-06
Ubuntu CE includes GnomeSword with the entire Bible in two different translations (KJV and DRV by default). There is also an installer for e-Sword which is another good full Bible study program. For both of these, you can download and install modules, which include different Bible translations, commentaries, study guides and the like. 

If you want to just see what it has, download the CE live cd (the 6.10 Edgy one is probably best), and boot it up. You will see the default Ubuntu CE desktop and be able to try the Bible software (in the accessories section of the start menu).

---

### Post by keithp on 2007-04-06
Mysticrider92

Thank you for the explanation regarding UbuntuCE. I appreciate it.

I will download it, now that I know it's what I need.

I am on capped broadband here, and didn't want to use 700MB of my month's allowance downloading it, if it wasn't of use to me. That's why I asked for details of UbuntuCE.

Keith

---

### Post by mysticrider92 on 2007-04-08
I have attached some screenshots of the Bible software (GnomeSword, Bible Memorizer, and e-Sword) so you can get an idea of what they have. These are on my heavily changed desktop that looks nothing like the default CE.

---

### Post by david_kt on 2007-04-09
> **keithp said:**
> Mysticrider92

I am on capped broadband here, and didn't want to use 700MB of my month's allowance downloading it, if it wasn't of use to me. That's why I asked for details of UbuntuCE.

Keith

That is what I think we need to make an option to install:

```
sudo apt-get install ubuntuCE-desktop
```


So that people could easily convert from any ubuntu to ubuntu CE, without the need to re-donwload the whole file system. Or is it already available?

I have written a simple how to as well to install E-sword in wine (which supposed to work perfectly without the need of windows box), in case people just need e-sword on top of any ubuntu. It complete with all link required to download necessary dlls :

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Actually first I posted it in general forum, but somebody advice me to post it in ubuntu christian forum.

DK

---

### Post by mysticrider92 on 2007-04-09
> **david_kt said:**
> That is what I think we need to make an option to install:
```
sudo apt-get install ubuntuCE-desktop
```
So that people could easily convert from any ubuntu to ubuntu CE, without the need to re-donwload the whole file system. Or is it already available?
We have the convert_me script which will do the same as a .deb, but a meta-package may be an idea for future consideration. Also, I am not sure if keithp is using Ubuntu yet, though it did sound like he had heard of it before.

---

### Post by mhancoc7 on 2007-04-09
Yes, the convert_me script is used for this. The reason that there is no meta-package is due to the fact that some of the configurations can not be done via a meta-package.

Jereme

---

### Post by david_kt on 2007-04-12
Could I make dual boot for example ubuntu CE and kubuntu, or ubuntu CE and ubuntu?

DK

---

### Post by mysticrider92 on 2007-04-14
> **david_kt said:**
> Could I make dual boot for example ubuntu CE and kubuntu, or ubuntu CE and ubuntu?

DK

You can just install the kubuntu-desktop from Synaptic or ichthux-desktop from the Ubuntu CE installer (in the System>Administration menu). You can easily dual-boot, but it is easier to just install those and choose from them in the 'Session' menu on the login screen.

---

### Post by Anonii on 2007-09-25
Since the guy is on capped broadband and every kilobyte costs, why not suggest him to download just the Bible software instead of downloading the whole 700MB monster.

EDIT: Just noticed that the thread is terribly old. Wrong search criteria; excuse me.

---

### Post by jonathonblake on 2007-09-25
[QUOTE=keithp]
With all the other programs on the UbuntuCE CD, there can't possibly be room for the whole Bible on it. [/quote]

GnomeSword, which can be used from the LiveCDC, includes Douay-Rheims translation of the Bible, the KJV, Matthew Henry's Commentary, and Naves Topical Bible.

If you installed Ubuntu CE to a hard drive, then adding additional resources is trivial.  
For GnomeSword,the sequence is ">Edit >Module Manager".
Other Sword Project front ends use a similar sequence.
I don't use Sword Project Front Ends.  (GnomeSword, BibleTime.)

> So, is the software just a studying aid, and one needs to use it in conjunction with a Bible? If so which version is it associated with? 

It is a studying aid.  Bible translations are included when you install the program.  Additional translations are available for installation.
(I have installed 400+ Bibles for use within e-Sword.)

Somebody else can cover Sword Project front ends.
The following is applicable to e-sword only.

The default installation of e-Sword includes the  KJV. 

At least one version of the ASV is available.  I don't remember which one. ( For a list of resources available for e-Sword, take a look at *Currently Available e-Sword Modules* and *The e-Sword Module Database* available from [http://ww.esnips.com/web/eSwordFAQs/](http://ww.esnips.com/web/eSwordFAQs/) )

> In other words, how does one do Bible study using UbuntuCE?

Install the Bible Study program, and then do everything on the computer.

With e-Sword, you can wrote notes related to the verse in the Study Note section, highlight or underline the verse, or write the results of a word analysis (or anything else you want to) in a topical file.

The basic instruction manual on using e-Sword, can be found at 
[http://www.e-sword.net/training.html](http://www.e-sword.net/training.html)

Additional documentation on using e-Sword includes:
* e-Sword as a Spiritual Journal;
* The Potential of e-Sword;
* Where to obtain e-Sword support;
 All of those documents should be in  [http://ww.esnips.com/web/eSwordFAQs/](http://ww.esnips.com/web/eSwordFAQs/) 

(Disclaimer:  I wrote the lists of e-Sword resources, and most of the the documentation at eSwordFAQs.  )

xan

jonathon

---

