---
title: "Blender 2.49"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by bindkeeper on 2009-06-05
Hi I'm using Ubuntu 8.04. I downloaded Blender 2.49 it should run out of the box, but when I'm trying to run it I get  
```
 error while loading shared libraries: libpython2.6.so.1.0: cannot open shared object file: No such file or directory
```

---

### Post by bindkeeper on 2009-06-05
Never mined.
I just downloaded the 2.5 python version of blender and it works.

---

### Post by lukeiamyourfather on 2009-06-05
I think there's Python 2.6 in the repositories too, or install it from source using "make altinstall" (so it doesn't overwrite the existing Python). Cheers!

---

### Post by landstander on 2009-06-23
This is all fine and good but...
A good reason for wanting to install 2.49 is because there are very useful scripts that will only run in Blender v2.49, and A good reason to want to run it natively in Ubuntu is because using Wine to run blender can lead to diminished performance and Blender is a performance hungry application.

Short rant:
It would be nice if people who were writing the scripts for blender would, at the very least, make them backward compatible with the stable Blender builds that were in the repositories of most OS's.

Question:
If any one has had any luck getting Blender 2.49 or 2.49a to work natively in Ubuntu please post some information here about how you were able to get around the following error message:
"./blender: error while loading shared libraries: libpython2.6.so.1.0: cannot open shared object file: No such file or directory"

Also, (if any one knows) why isn't "libpython2.6.so.1.0" installed after installing python v2.6.2?
Thanks.

---

### Post by lukeiamyourfather on 2009-06-23
> **landstander said:**
> This is all fine and good but...
A good reason for wanting to install 2.49 is because there are very useful scripts that will only run in Blender v2.49, and A good reason to want to run it natively in Ubuntu is because using Wine to run blender can lead to diminished performance and Blender is a performance hungry application.

Short rant:
It would be nice if people who were writing the scripts for blender would, at the very least, make them backward compatible with the stable Blender builds that were in the repositories of most OS's.

Question:
If any one has had any luck getting Blender 2.49 or 2.49a to work natively in Ubuntu please post some information here about how you were able to get around the following error message:
"./blender: error while loading shared libraries: libpython2.6.so.1.0: cannot open shared object file: No such file or directory"

Also, (if any one knows) why isn't "libpython2.6.so.1.0" installed after installing python v2.6.2?
Thanks.

Just grab the Ubuntu 9.04 package from here assuming you are using Ubuntu 9.04, or just get it from the repositories. If all else fails then compile your own version locally from source and download the necessary dependencies like Python 2.X if you don't already have it. Cheers!

---

### Post by Henrike Corinna on 2009-06-25
Blender is an integrated application that enables the creation of a broad range of 2D and 3D content. Blender provides a broad spectrum of modeling, texturing, lighting, animation and video post-processing functionality in one package. Through it's open architecture, Blender provides cross-platform interoperability, extensibility, an incredibly small footprint, and a tightly integrated workflow. Blender is one of the most popular Open Source 3D graphics application in the world.

---

### Post by landstander on 2009-06-25
lukeiamyourfather,

Thank you for your response. The reason I haven't updated to Ubuntu 9.04 is because the widget based desktop GUI doesn't allow me as much control and tweaking from within the GUI as I have now in v8.04. Or at least thats the impression I got when I used it last. Also I've read that certain programs that I use (can't remember at the moment which ones) are experiencing some bugs under Jaunty leading me to believe its not quite as stabilized as v8.04 yet.

As far as trying to install from sources. Yes I have done that and it doesn't work. Granted my skill at installing things is rudimentary and I haven't yet learned how to deal with strange non-descriptive error messages when running make or make test. For example, in the download section of the Blender website it states that blender v2.49a for Linux "Requires glibc 2.3.6", and when I try to make glibc from source. I get a strange error message about having to "leave a directory", but it doesn't say why. Also I wanted to overwrite my version of Python with v2.6.2 because its newer then the one in the repository for Ubuntu v8.04 but again I got error messages that seemed relevant to glibc not being the version requested in the download section of Blender.

*ranting again, please skip this part unless you like ranting. :) *
(note: this rant is not about any one in this forum and is posted simply to give an idea of my frustration. Again please skip it if you don't like ranting)
This seems to be a wide spread problem in Linux, that any time you try to configure and make a program from source there's always errors, and the error messages are often (or at least in my case) not descriptive enough to track down how to solve the problem. Inevitably I then have to post a question on some forum about the problem, where I then get berated for not fixing it myself or for not reading some cryptic manual that I've read a million times and still doesn't make any sense. Also the first poster was correct about Blender.org saying its supposed to work out of the box. Well as you can see from posts in these forums and others like it, the latest version of blender does not work out of the box. At least, not from source and certainly not in Ubuntu v8.04. Also why should I have to upgrade to Ubuntu v9.04 to solve a problem when v8.04 is still supposed to be in "long term support"? In other words, where is the support for version 8.04?

---

### Post by lukeiamyourfather on 2009-06-25
> **landstander said:**
> lukeiamyourfather,

Thank you for your response. The reason I haven't updated to Ubuntu 9.04 is because the widget based desktop GUI doesn't allow me as much control and tweaking from within the GUI as I have now in v8.04. Or at least thats the impression I got when I used it last. Also I've read that certain programs that I use (can't remember at the moment which ones) are experiencing some bugs under Jaunty leading me to believe its not quite as stabilized as v8.04 yet.

As far as trying to install from sources. Yes I have done that and it doesn't work. Granted my skill at installing things is rudimentary and I haven't yet learned how to deal with strange non-descriptive error messages when running make or make test. For example, in the download section of the Blender website it states that blender v2.49a for Linux "Requires glibc 2.3.6", and when I try to make glibc from source. I get a strange error message about having to "leave a directory", but it doesn't say why. Also I wanted to overwrite my version of Python with v2.6.2 because its newer then the one in the repository for Ubuntu v8.04 but again I got error messages that seemed relevant to glibc not being the version requested in the download section of Blender.

*ranting again, please skip this part unless you like ranting. :) *
(note: this rant is not about any one in this forum and is posted simply to give an idea of my frustration. Again please skip it if you don't like ranting)
This seems to be a wide spread problem in Linux, that any time you try to configure and make a program from source there's always errors, and the error messages are often (or at least in my case) not descriptive enough to track down how to solve the problem. Inevitably I then have to post a question on some forum about the problem, where I then get berated for not fixing it myself or for not reading some cryptic manual that I've read a million times and still doesn't make any sense. Also the first poster was correct about Blender.org saying its supposed to work out of the box. Well as you can see from posts in these forums and others like it, the latest version of blender does not work out of the box. At least, not from source and certainly not in Ubuntu v8.04. Also why should I have to upgrade to Ubuntu v9.04 to solve a problem when v8.04 is still supposed to be in "long term support"? In other words, where is the support for version 8.04?

Heh, I hear you. Just to clarify one thing though the long term support or LTS is exactly that. Its long term support, not long term new software upgrades. This makes the operating system more reliable and better suited in environments where it will be deployed for an extended period of time (schools, businesses, servers, etc.). Whatever comes in the repositories for that release is what stays in there. Support in Ubuntu terms is a fancy way to say patches and updates, but not upgrading anything. For example there's Python 2.5 in 8.04 LTS if I recall correctly even though Python 2.6 is out, but security patches and bug fixes are still applied for Python 2.5, but not upgraded to Python 2.6. The same is applied for Blender or any other package for that particular release. Cheers!

---

### Post by landstander on 2009-06-26
> **lukeiamyourfather said:**
> Heh, I hear you. Just to clarify one thing though the long term support or LTS is exactly that..... Whatever comes in the repositories for that release is what stays in there. Support in Ubuntu terms is a fancy way to say patches and updates, but not upgrading anything....

Thank you for the clarification. Your explanation has made this very clear and will no doubt also help in my experiences moving forward with Linux. So again, I'm very grateful for that eye opening clarification. Thank you.

I would like to correct a misunderstanding that I proclaimed in an earlier post to this thread. I had gotten GNOME and KDE mixed up and said something about not wanting to upgrade due to a "widget based GUI" for the desktop. The newest versions of KDE uses widgets and they seem to have given up on making it an intuitive interface in terms of customizations. While the newest versions of GNOME seem to run much faster and is maintaining its user intuitive environment. This makes upgrading to Ubuntu/GNOME from Kubuntu/KDE much more viable.

In short, I will test out blender v2.49a in Ubuntu v9.04. Currently only blender v2.48a is in the repositories, but there is a deb file on blenders website for installing v2.49 in Jaunty so hopefully that will work because theres a script I want to test out that only runs on blender v2.49a... (sort of a bummer).

Thanks again for your help and clarifications.

---

### Post by philip5 on 2009-07-12
I have (among a bunch of other updated packages) the latest blender 2.49a (for the moment) on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try. In my FAQ you can read how to add my key to verify my packages.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Anyway have fun with Blender!

---

