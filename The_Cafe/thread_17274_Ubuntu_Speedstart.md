---
title: "Ubuntu Speedstart"
date: 2005-02-27
forum: The Cafe
---

### Post by Quest-Master on 2005-02-27
***EDIT*: Speedstart now v0.45, with dynamic package parsing and fixed bugs.**

I've been spreading Ubuntu a lot with friends and especially throughout a indie game creation and programming community called Gaming World. Most have liked Ubuntu much more than any other Linux experience, but some told me they would've liked a fast and easy way to install things like MP3 support, plugins, codecs, fonts, P2P apps., etc. without having to manually go through the many applications of Synaptic or apt-get. I am also a frequent reinstaller of Ubuntu, so I thought being able to reinstall needed programs automatically would be nice. Some people also thought automatically rewriting the sources.list to enable universe, multiverse, and marillat would also be cool, so I have added support for that too.

So, I learned Python and tried to create a tool to do this. Thus, Ubuntu Speedstart is born and is now certainly in a usable state. Currently, it only has a terminal interface, but a GTK GUI is coming up soon.

A great feature now implemented in v0.4 is dynamic package parsing; sort of like playlists. Just write a text file and list all of the packages you'd like to automatically be installed, pass it on to Speedstart, and it'll do all of the work for you while you continue on your business. This one will be a real help for whenever I reinstall, or I could just write text files for friends which could contain all the packages I think they need.

Automated compilation is also coming in v0.5. Commonly used programs which cannot be found in the apt repositories or do not work properly will be automatically compiled; an example being MPlayer, or having to set up Java, something which is sometimes painful for newcomers. Dependencies will all be resolved, and of course, everything will be compiled while you do you work.

I've applied for a home at Sourceforge, but I'm currently hosting it on my own webspace.

[http://208.53.170.194/~pixelrev/speedstart-v0.45.tar.gz](http://208.53.170.194/~pixelrev/speedstart-v0.45.tar.gz)

To go through the preliminary script which fixes up your default sources.list, run a:

$ sudo python prelim.py

To run the installer, enter in the terminal:

$ sudo python installnew.py

To run dynamic package parsing, enter:

$ sudo python dynpp.py

Feel free to look through the code, learn from it, whatever. I've aimed to also write friendly docs, something many open-source projects today lack. People who will mainly benefit from those are newcomers to Ubuntu, such as friends who I have passed this out to. v0.5 will mark the coming of automatic compilation. Leave any comments you have too. It's worked pretty well for people I've handed it out too so far.

---

### Post by Yukonjack on 2005-02-27
Thanks will have a peek at it :)

---

### Post by TravisNewman on 2005-02-27
dpkg/dselect/apt/whatever else have a great feature called get-selections. You can run
dpkg --get-selections >> make.up.a.filename 
to get a list of all currently installed packages. When you reinstall, change "get" to "set" and reverse the arrows to << and it imports that list, then you can use dselect to install all the packages that you had at the time you made the file.

I'm not saying your project is pointless because of this, but maybe extending your app to support --get and --set -selections and running dselect would help. It'd be handy for newer users to be able to use a graphical interface to use --get-selections, because it's a powerful tool, but some would be scared of the command line.

---

### Post by Quest-Master on 2005-02-27
[QUOTE=panickedthumb]dpkg/dselect/apt/whatever else have a great feature called get-selections. You can run
dpkg --get-selections >> make.up.a.filename 
to get a list of all currently installed packages. When you reinstall, change "get" to "set" and reverse the arrows to << and it imports that list, then you can use dselect to install all the packages that you had at the time you made the file.

I'm not saying your project is pointless because of this, but maybe extending your app to support --get and --set -selections and running dselect would help. It'd be handy for newer users to be able to use a graphical interface to use --get-selections, because it's a powerful tool, but some would be scared of the command line.[/QUOTE]

Whoa, that's cool. I don't think it makes the project useless, as I am still handing this out to many newbies from GW learning Ubuntu. I just thought you guys might like to check it out.

I will certainly add this in a soon-to-come version. As I said before, I should have GTK interface up and running along with the curses interface too. Good to see a few comments coming from you guys.. more would be appreciated though. :)

---

### Post by TravisNewman on 2005-02-27
Hey, I'm just glad people are making things for the community! And since I don't really have enough time to do so, I provide suggestions and just hope I don't annoy people ;)

---

### Post by CowPie on 2005-02-27
> **Quest-Master]***EDIT*: Speedstart now v0.4, with dynamic package parsing.**

I've been spreading Ubuntu a lot with friends and especially throughout a indie game creation and programming community called Gaming World. Most have liked Ubuntu much more than any other Linux experience, but some told me they would've liked a fast and easy way to install things like MP3 support, plugins, codecs, fonts, P2P apps., etc. without having to manually go through the many applications of Synaptic or apt-get. I am also a frequent reinstaller of Ubuntu, so I thought being able to reinstall needed programs automatically would be nice. Some people also thought automatically rewriting the sources.list to enable universe, multiverse, and marillat would also be cool, so I have added support for that too.

So, I learned Python and tried to create a tool to do this. Thus, Ubuntu Speedstart is born and is now certainly in a usable state. Currently, it only has a terminal interface, but a GTK GUI is coming up soon.

A great feature now implemented in v0.4 is dynamic package parsing said:**
> http://208.53.170.194/~pixelrev/speedstart-v0.4.tar.gz[/url]

To go through the preliminary script which fixes up your default sources.list, run a:

$ sudo python prelim.py

To run the installer, enter in the terminal:

$ sudo python installnew.py

To run dynamic package parsing, enter:

$ sudo python dynpp.py

Feel free to look through the code, learn from it, whatever. I've aimed to also write friendly docs, something many open-source projects today lack. People who will mainly benefit from those are newcomers to Ubuntu, such as friends who I have passed this out to. v0.5 will mark the coming of automatic compilation. Leave any comments you have too. It's worked pretty well for people I've handed it out too so far.

Hey that;'s really cool!  I will defintiely try it.

---

### Post by mark on 2005-02-27
[QUOTE=panickedthumb]Hey, I'm just glad people are making things for the community! And since I don't really have enough time to do so, I provide suggestions and just hope I don't annoy people ;)[/QUOTE] panickedthumb doesn't have the time, and I don't have either the time or the skills (usually, just my big mouth!) - but I think this kind of participation is a great idea!

---

### Post by Quest-Master on 2005-02-27
Thanks again guys. I've updated it to v0.45 with a couple of bug fixes. And, I've gotten some more motivating comments from people who I've given it out to. :D

---

### Post by Tubuntu on 2005-02-28
Good job! 


 =D>

---

### Post by jdong on 2005-02-28
Great work, but I see a few bugs/issues:


1: try/except. Please be more specific in your 'except' clauses. Just blank 'except' will catch everything from CTRL+C to Python dying of a segmentation fault. Catch IOErrors if you're worried about the write failing.

2: os.system("apt-get update") should do _some sort_ of check for success/failure. Note that no exception is raised when a os.system'ed command returns a non-zero value.

3: prelim.py: last few lines: Making a typo with "yes" would be a pain. Make it loop there until user types in Yes or No.

4: Check for root access with posix.getuid(). Don't assume that the user would use sudo.

5: dynpp: security flaw (shell escape): os.system's concatenation doesn't check for suspicious shell characters, such as semicolons. Not a big deal.

6: dynpp: Is the class really necessary ;)



Most of these aren't big issues, except catching too much. In some cases, like IOError's you might as well let Python bomb you out, as if "sources.list" didn't write, you sort of can't go on anyway!

Also, perhaps there should be some rollback capabilities, such as read()'ing the old sources.list and restoring it in case of an exception.


Again, wonderful work overall! I've got a similar program, Ubuntu APT Helper, going. Feel free to take whatever snippets of code you find helpful. Most likely, APT Helper will turn out to be a more mature way of generating sources.list.

[http://ubuntuforums.org/showthread.php?t=17336](http://ubuntuforums.org/showthread.php?t=17336)

---

### Post by jdong on 2005-02-28
BTW,  if you are (like me) just beginning to learn python, check out WxPython as your GUI toolkit of choice. It's much more worth your time.

---

### Post by Quest-Master on 2005-02-28
Thanks a ton jdong. I'll be sure to work all of those bugs out in soon to come future versions. Feedback has been going pretty well now. :D

I know some more try/excepts are needed, as well as returning more specific errors too. Most of the try/excepts were just added in 0.45 to at least inform the user of their wrong choices. In dynpp.. well, I just had the class in there for the heck of it. :P

Also, about wxPython, that is exactly what I am going to be using. It requires a lot less code compared to PyGTK, and has wxGlade for rapid GUI generation too. I'm just waiting for Hoary to be released, since the wx's on Warty currently use GTK1.. really ugly. :P

---

### Post by jdong on 2005-02-28
[QUOTE=Quest-Master]I know some more try/excepts are needed, as well as returning more specific errors too. Most of the try/excepts were just added in 0.45 to at least inform the user of their wrong choices.[/QUOTE]

No, that's not what I'm saying.

Let's use this snippet as an example:
```

try:
x=raw_input("You better type in a number!>>");
print "Sum of your input and 5 is: ",int(x)+5

except:
print "Not a number"

```

The "except" clause catches WAAAY too much! Let's say the user presses CTRL+C to get out of your program. Python will print "Not a number".

Let's say that RAM corruption causes Python to crash. It'll print "Not a number". Out of RAM? "Not a number".

Catch just the exceptions possibly raised, with except ErrorName:.

---

### Post by Slapdash on 2005-03-01
Wow dude sounds like an AWESOME little app. esp. from a  V. 0.5  perspective.
Autocompile install. Man!
Good luck with the Development.

I will use it when it has the Gui ;)

Thanks

---

### Post by Quest-Master on 2005-03-01
Yeah, automatic compilation for the latest MPlayer and MPlayer plugin is really going to help some friends of mine out. Of course, there'll be many more apps. that have not yet been packaged as .debs and are of some use too. :)

---

### Post by axcairns on 2005-03-05
[QUOTE=Quest-Master]Yeah, automatic compilation for the latest MPlayer and MPlayer plugin is really going to help some friends of mine out. Of course, there'll be many more apps. that have not yet been packaged as .debs and are of some use too. :)[/QUOTE]
 Looks good dude. One small bug - the menu option #'s seem out of whack in the Mozilla plugins sub-menu. Pressing 3 (Mozplugger) is rejected as invalid.

Looking forward to 0.5

Cheers,

Allan

---

### Post by vassalle on 2005-03-06
one problem though.. the marillat reps dont seem to work.. ive been getting these errors..  W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Caching complete.

Im using Hoary dist gotten from Linux Magazine if that matters.. Some help please ?

---

### Post by Quest-Master on 2005-03-06
[QUOTE=vassalle]one problem though.. the marillat reps dont seem to work.. ive been getting these errors..  W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Caching complete.

Im using Hoary dist gotten from Linux Magazine if that matters.. Some help please ?[/QUOTE]
 Ick, Speedstart is currently only for Warty users. :o

You'll need to open up your /etc/apt/sources.list and delete everything under:

# Sources generated by Speedstart

Or something along those lines. You'll need to remove them because the Warty repositories Speedstart users will collide with those on Hoary. I'm going to create a Hoary version for Speedstart as soon as the preview release is made public.

Also, axcairns.. thanks for the heads up. I'll look into it.

---

### Post by vassalle on 2005-03-06
[QUOTE=Quest-Master]Ick, Speedstart is currently only for Warty users. :o

You'll need to open up your /etc/apt/sources.list and delete everything under:

# Sources generated by Speedstart

Or something along those lines. You'll need to remove them because the Warty repositories Speedstart users will collide with those on Hoary. I'm going to create a Hoary version for Speedstart as soon as the preview release is made public.

Also, axcairns.. thanks for the heads up. I'll look into it.[/QUOTE]
 owh.. okay.. my bad then.. but is it not possible to add the marillat repos when using hoary without having these errors.. btw, ive deleted all the warty repos in my sources.list.. kinda realise something was fishy when i wanted to install nvidia-glx when apt recomended me to download another kernel.. LoL.. GJ btw, cant wait for the Hoary Speedstart release..

---

### Post by gylf on 2005-03-06
Looks good, as others have said.

A couple comments: if you plan on having it install java (or similar programs), just make sure the license agreement is displayed and accepted.  Automating the download and execution of the official java .bin should be sufficient (as it displays the license and makes the user accept).  You shouldn't have any legal problems so long as your not distributing the software yourself and are just giving others a way of getting it through the standard legal channels.  Of course, always read the licensing agreements of the software just in case.

For more info on this topic check out the thread [here on including software in the distro.](http://ubuntuforums.org/showthread.php?t=17582&page=1&pp=10)

---

### Post by Quest-Master on 2005-03-06
[QUOTE=gylf]Looks good, as others have said.

A couple comments: if you plan on having it install java (or similar programs), just make sure the license agreement is displayed and accepted.  Automating the download and execution of the official java .bin should be sufficient (as it displays the license and makes the user accept).  You shouldn't have any legal problems so long as your not distributing the software yourself and are just giving others a way of getting it through the standard legal channels.  Of course, always read the licensing agreements of the software just in case.

For more info on this topic check out the thread [here on including software in the distro.](http://ubuntuforums.org/showthread.php?t=17582&page=1&pp=10)[/QUOTE]

Thanks -- those will definitely come in handy once I begin including software of that kind. :)

---

### Post by UbuWu on 2005-03-06
Great idea this!

---

### Post by UbuWu on 2005-03-11
When is the GTK GUI coming?

---

### Post by UbuWu on 2005-03-20
Is there any progress on speedstart??

---

