---
title: "Anybody interested in putting together a serious team to build a Ubuntu/Puppy Hybrid?"
date: 2009-12-15
forum: The Cafe
---

### Post by HappinessNow on 2009-12-15
Anybody interested in putting together a serious team to build a Ubuntu/Puppy Hybrid?

reference this post:

[http://ubuntuforums.org/showthread.php?t=1354727](http://ubuntuforums.org/showthread.php?t=1354727)

code named: Wildehond

The reasons are obvious why this would be beneficial, a Ubuntu based distro that is also a Puppy Linux derivative...the speed and size of Puppy utilizing apt-get and debs...you can have your cake and eat it to!

Please let me know here, or PM me directly.

---

### Post by Exodist on 2009-12-15
I would if I wasn't going back to college and need to spend all my free time studying. I have to keep a high GPA to keep my college money.

---

### Post by HappinessNow on 2009-12-15
> **Exodist said:**
> I would if I wasn't going back to college and need to spend all my free time studying. I have to keep a high GPA to keep my college money.ahh good point I am back to the University in 3 weeks myself and have to do the same, maintain a high GPA.

I would love to help put this together, but like yourself wouldn't have much time to devote due to school. Thus the concept of a team to help build this.

---

### Post by JBAlaska on 2009-12-15
Sounds like a worthy project, but between my attempt using a Tiny Core, Debian, LXDE Hybrid and testing Lucid.. I really don't have the time.

I love puppy though! All the best on this project!
John

---

### Post by -grubby on 2009-12-15
Is it Ubuntu stripped down, or Puppy with apt?

---

### Post by HappinessNow on 2009-12-15
> **-grubby said:**
> Is it Ubuntu stripped down, or Puppy with apt?
It is Puppy Linux with Apt, read more here:


[http://bkhome.org/woof/index.html](http://bkhome.org/woof/index.html)

particularly this portion:

> **Multiple distros**

The design of Woof is intended to be so flexible that packages from any distro can be processed. At the time of writing Woof is supporting Debian, Ubuntu, Slackware, Arch, T2 and Puppy. I am considering adding one of the RPM-based distros.

**Easy upgrade**

I find this one particularly exciting. The Ubuntu releases are named Intrepid, Jaunty, Karmic, etc. Puppy can be built from whatever is the current one When they bring out the next release, all that Woof needs is the name of the release and Woof will then download all the packages and build a new Puppy Linux. It may take a couple of hours fixing some package names, but the idea is a developer in one day can have a brand new release of Puppy.

**The end result**

...is Puppy Linux! What I mean is that you end up with something that has the speed, compactness and all the ease-of-use features of Puppy Linux, nothing sacrificed. Even building from Ubuntu packages, we get a 99MB (or thereabouts) live-CD, a fast Puppy that runs in RAM, all of the Puppy applications and all of the tools and familiar desktop.[http://bkhome.org/woof/index.html](http://bkhome.org/woof/index.html)

---

### Post by Chilli Bob on 2009-12-15
I like the idea of a minimum install ubuntu (as per Psycocats tutorial) with JWM and the lightweight apps used in Puppy.  I have tried doing this before, with some success, but usually run out of time and motivation.

---

### Post by JBAlaska on 2009-12-15
[COLOR="Blue"]Edit: You guys beat me to it lol;[/COLOR]

This [Link]("http://bkhome.org/woof/index.html") Kina sums it up.

---

### Post by HappinessNow on 2009-12-15
> **Chilli Bob said:**
> I like the idea of a minimum install ubuntu (as per Psycocats tutorial) with JWM and the lightweight apps used in Puppy.  I have tried doing this before, with some success, but usually run out of time and motivation.
Did you try this using Woof?

---

### Post by HappinessNow on 2009-12-15
> **JBAlaska said:**
> [COLOR="Blue"]Edit: You guys beat me to it lol;[/COLOR]

This [Link]("http://bkhome.org/woof/index.html") Kina sums it up.
 That's OK Thanks for the link... at the end of that link is this:

> **Who should use Woof?**

This is an important question to ask. Someone who is a "Linux newbie" might read this page and think that Woof looks pretty exciting. Yes it is, but a certain level of Linux commandline expertise and knowledge of hard drive partitions is required.

Actually, it is not difficult, and as the GUI gains more features it is going to make building custom puppies easier and easier.

But, even if you do have the technical know-how to use Woof, is it the best choice for you? There is another alternative for creating a custom live-CD, and that is the CD-Remaster program (see the 'Setup' menu in Puppy). That's an even easier way to do it, although somewhat more restricted. Certainly the remaster-CD option is better for those less knowledgeable about Linux at the commandline level.

The great majority of users will want neither Woof or the CD-Remaster. One of the available live-CDs built by me or another Puppy developer, will be all that most people need. Users have the Puppy Package Manager and the SFS files to add any extra required functionality.

It is those who want to build their own custom Puppy or derivative of Puppy, that will be considering Woof or the CD-Remaster.

**Future**

Binary compatibility with a major distro has one obvious advantage: access to all the packages in its repositories. Well, we do with any version of Puppy, but when the core files of Puppy are built from that distro then we have the prerequisites already in place. Most importantly, we have the packages that were used to compile other packages -- in other words we avoid mismatches of libraries that were configured differently and are the wrong versions.

Also, if a particular package needs more prerequisites to be installed, they will be available on the repositories. We don't have to go through a very tedious and failure-prone process of compiling dependencies from source.

The new Puppy Package Manager (PPM) has been completely rewritten by me to work in this multiple-distro environment. The PPM can handle packages from any of the distros supported by Woof.

Items on the todo list;
Automatic dependency management in the Woof build scripts.
Building-in the locale files for your choice of languages.
Documentation to be a separate SFS file.
Many more features for the GUI.

**One thing, I think that Woof is going to spawn a whole new lot of "puplets" (Puppy derivatives)!**[http://bkhome.org/woof/index.html](http://bkhome.org/woof/index.html)

---

### Post by Chilli Bob on 2009-12-15
> **&#20170 said:**
> Did you try this using Woof?


No, last time I looked at Woof it was still very experimental.  Maybe over Christmas I will have another look at it.  I'm still not compfortable running as root all the time on my main PC, but may try building a Woof from Ubuntu for USB use.

(I know there are pleanty of arguments on Puppy forums re: why it is safe to run as root.  It just doesn't feel right to me.)

---

### Post by HappinessNow on 2009-12-15
> **Chilli Bob said:**
> No, last time I looked at Woof it was still very experimental.  Maybe over Christmas I will have another look at it.  I'm still not compfortable running as root all the time on my main PC, but may try building a Woof from Ubuntu for USB use.

(I know there are pleanty of arguments on Puppy forums re: why it is safe to run as root.  It just doesn't feel right to me.)no worries, perhaps your spin on it could be that it doesn't run as root to have a true Ubuntu-isk appeal/feel.

---

### Post by JBAlaska on 2009-12-15
> **Chilli Bob said:**
> No, last time I looked at Woof it was still very experimental.  Maybe over Christmas I will have another look at it.  I'm still not compfortable running as root all the time on my main PC, but may try building a Woof from Ubuntu for USB use.

(I know there are pleanty of arguments on Puppy forums re: why it is safe to run as root.  It just doesn't feel right to me.)

You can do all the dev / build right in a virtual machine "Virtualbox", takes the security issue right out of the equation.

---

### Post by The Toxic Mite on 2009-12-15
Hey! This sounds like an interesting project! I'm on a school computer though, so I can't access the project's website (f**k WebSense ;/)
 
Anyway, I'm definitely going to help out :)
 
-TTM-

---

### Post by HappinessNow on 2009-12-15
> **The Toxic Mite said:**
> Hey! This sounds like an interesting project! I'm on a school computer though, so I can't access the project's website (f**k WebSense ;/)
 
Anyway, I'm definitely going to help out :)
 
-TTM-Awesome! I think if enough of us pull together we can squeeze enough time to help come up with a polished hybrid and the 'Wildehond Concept' will come to fruition with Woof.

---

### Post by Pyux on 2009-12-15
[http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/](http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/)

Its been done. Its called Upup. Its pretty neat actually. Give it a go and test it with them aye. :)

---

### Post by Chilli Bob on 2009-12-15
> **Pyux said:**
> [http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/](http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/)

Its been done. Its called Upup. Its pretty neat actually. Give it a go and test it with them aye. :)

Downloading now.  Will let you know what I think tomorrow.

---

### Post by Chilli Bob on 2009-12-15
Hmmm... looks like there may be a way around my paranoia of running as root in puppy.

[http://puppylinux.org/news/puplets/puppy421multiuseriso/](http://puppylinux.org/news/puplets/puppy421multiuseriso/)

And more......

[http://www.murga-linux.com/puppy/viewtopic.php?t=47410](http://www.murga-linux.com/puppy/viewtopic.php?t=47410)


I think this would be an essential inclusion for an Ubuntu-Puppy.

---

### Post by HappinessNow on 2009-12-15
> **Pyux said:**
> [http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/](http://puppylinux.org/news/puplets/upup-from-woof-the-puppy-linux-builder/)

Its been done. Its called Upup. Its pretty neat actually. Give it a go and test it with them aye. :)Thanks for the link

> **Chilli Bob said:**
> Hmmm... looks like there may be a way around my paranoia of running as root in puppy.

[http://puppylinux.org/news/puplets/puppy421multiuseriso/](http://puppylinux.org/news/puplets/puppy421multiuseriso/)

And more......

[http://www.murga-linux.com/puppy/viewtopic.php?t=47410](http://www.murga-linux.com/puppy/viewtopic.php?t=47410)


I think this would be an essential inclusion for an Ubuntu-Puppy.
Awesome.

---

