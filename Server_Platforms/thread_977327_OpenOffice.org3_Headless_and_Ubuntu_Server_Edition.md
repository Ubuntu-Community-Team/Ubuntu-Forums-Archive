---
title: "OpenOffice.org3 Headless and Ubuntu Server Edition"
date: 2008-11-10
forum: Server Platforms
---

### Post by tohir on 2008-11-10
Has anyone managed to get OpenOffice3 working in Ubuntu Server Edition as a headless server.

I downloaded it from OpenOffice.org, extracted it, dpkg -i *.deb.

Some additional packages required were: 

apt-get install libxext6 libsm6 libfreetype6

But it died as soon as it started:

soffice -headless -accept="socket,port=8100;urp;" -nofirststartwizard&

---

### Post by twistedtwig on 2008-11-10
Possibly a stupid question but how do you use OpenOffice on a headless box?

Curious as to what the goal is.

Thanks and GL

---

### Post by tohir on 2008-11-10
> **twistedtwig said:**
>  how do you use OpenOffice on a headless box?

Curious as to what the goal is.


The purpose is to use it as a document conversion server. It automatically converts documents on demand from .doc => .odt => .pdf, whatever you want.

Most popular approach is using jodconverter:

See - [http://www.artofsolving.com/opensource/jodconverter](http://www.artofsolving.com/opensource/jodconverter)

Software using OpenOffice.org as a server include:

- KnowledgeTree - [http://wiki.knowledgetree.com/KnowledgeTree_3.5.*_-_Performing_a_Source_Only_Install](http://wiki.knowledgetree.com/KnowledgeTree_3.5.*_-_Performing_a_Source_Only_Install)
- OpenMeetings [http://code.google.com/p/openmeetings/wiki/OpenOfficeConverter](http://code.google.com/p/openmeetings/wiki/OpenOfficeConverter)
- Alfresco - [http://www.alfresco.com/](http://www.alfresco.com/)

I have it working with OpenOffice.org 2.4.1, that's real easy. We want to use OpenOffice.org 3 since it will allow for MS Office 2007 files (.docx, etc).

---

### Post by twistedtwig on 2008-11-10
Thats very cool!

---

### Post by Thirtysixway on 2008-11-11
I may recommend that setup to my school district.  They've been looking around for an easier way to create .pdf files.

---

### Post by Hoppiesbox on 2008-11-26
Any progress on this? 

This should get your server going if you installed the openoffice.org-headless package

```

/usr/lib/openoffice/program/soffice -headless -accept="socket,port=8100;urp" -nofirststartwizard -display 0.0  &

```

I'm at a bit of a loss as to how to get the documents to be converted still though

---

### Post by Hoppiesbox on 2008-12-02
After installing via the method you mention above, the command 

```
/opt/openoffice.org3/program/soffice -headless -accept="socket,port=8100;urp" -nofirststartwizard -display 0.0  &
```

Seems to get me going - but because we're talking openoffice.org3, the -display 0.0 should be unnecessary, and the -nofirststatwizard doesn't seem to be an issue either so

```
/opt/openoffice.org3/program/soffice -headless accept="socket,port=8100;urp" &
```

To do a conversion manually at the command line(assuming you have jodconverter in /opt:

```
java -jar /opt/jodconverter-2.2.1/lib/jodconverter-cli-2.2.1.jar infile.doc outfile.pdf
```

Now if Drupal would realize that the server is working...It's currently in denial :(

---

### Post by Sesshomurai on 2009-01-07
Hi,
  Sorry to revive this old thread, but I'm trying to use openoffice3.org on Ubuntu 8.10 in server mode to do conversions too.

I'm using the python oood daemon with openoffice-python/openoffice-interact[1] and found that it wouldn't work unless I installed the package openoffice.org, even though I had installed openoffice3.org already.

When I try some conversions, it works for .docx, but not for .xlsx or .pptx,
giving the error:

    return self._desktop.loadComponentFromURL(url, target, 0, properties)
com.sun.star.lang.IllegalArgumentException: URL seems to be an unsupported one.

[1] [http://pypi.python.org/pypi/openoffice.interact/0.1](http://pypi.python.org/pypi/openoffice.interact/0.1)

How are others using openoffice3 server mode? 

btw, the oood daemon is nice because it spawns many soffice servers and exposes only 1 socket port.

---

### Post by Stepin on 2010-08-31
Hello. I don't understand, i'm trying to install OpenOffice 3 with Ubuntu 10.4 LTS but can't get it working.

- I download the tar.gz file from openoffice.org
- Extract with tar xvzf 
- lunch the dpkg -i *.deb from the new directory, everything seems to work (besides the openoffice.org3-dict-blablabla that requires javaldx or something)

Then, i need to run it in headless mode. First thing, i had to figure that the god damn software was installed in /opt/openoffice.org3 and not /usr/lib like all the scripts where refering too.

So, whenever i lunch : 
- /opt/openoffice.org3/program/soffice.bin i got "No Such file or directory"

And when i lunch-
- - /opt/openoffice.org3/program/soffice i got "The Program Soffice is currently not installed. You can install it by typing apt-get install openoffice.org-common"

Well, i don't know the difference between soffice and soffice.bin, plus i don't understand why if the .bin is there, it said "no such file" ! Moreover, soffice is not installed, but i ran the dpkg -i over all the deb.

The whole thing is really hard, because i don't have internet, so i can't run the apt-get install command. I only got my Ubuntu ISO file image that i made a copy in /media/

Thanks for your help.

---

### Post by pbwest on 2010-12-03
Here are the packages I have installed.
ii  openoffice.org-base-core 1:3.2.0-7ubuntu4.1 office productivity suite -- shared library
ii  openoffice.org-common   1:3.2.0-7ubuntu4.1 office productivity suite -- arch-independen
ii  openoffice.org-core         1:3.2.0-7ubuntu4.1 office productivity suite -- arch-dependent 
ii  openoffice.org-draw        1:3.2.0-7ubuntu4.1 office productivity suite -- drawing
ii  openoffice.org-emailmerge 1:3.2.0-7ubuntu4.1 office productivity suite -- email mail merg
ii  openoffice.org-math        1:3.2.0-7ubuntu4.1 office productivity suite -- equation editor
ii  openoffice.org-style-galaxy 1:3.2.0-7ubuntu4.1 office productivity suite -- Galaxy (Default
ii  openoffice.org-writer       1:3.2.0-7ubuntu4.1  office productivity suite -- word processor

List of files is attached.

---

### Post by JeshurunDaniel on 2012-01-31
easiest way is to ```
apt-get install jodconverter
```. It will automatically install the required OO packages.

---

