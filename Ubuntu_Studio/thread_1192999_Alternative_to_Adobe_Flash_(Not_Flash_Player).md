---
title: "Alternative to Adobe Flash (Not Flash Player)"
date: 2009-06-20
forum: Ubuntu Studio
---

### Post by bridabom73 on 2009-06-20
What can I use that's free and for Ubuntu that is an alternative to Flash? I tried everything here: [http://ubuntuforums.org/showthread.php?t=171567](http://ubuntuforums.org/showthread.php?t=171567) but I couldn't get anything. One you have to compile (and that never EVER works for me, even when I use tons of guides). Open Office doesn't have a Flash program. The one link, I couldn't find any downloads. And the other one I don't understand how to install. Please help! My computer randomly freezes for some strange reason (There's not a single day that it doesn't freeze at least once), and I don't like having to open VirtualBox and wait all that extra time to use Adobe Flash CS4 when I could be using an alternative in Ubuntu. Thanks.

---

### Post by Stochastic on 2009-06-21
The only other solution than what has already been mentioned in the thread you've looked at, is [Haxe]("http://haxe.org").  Unfortunately that's a programming language that can compile into actionscript, so if you're not able to compile anything then I think you're SOL.

Essentially, there would be an alternative in Ubuntu if Adobe opened their copyrights on the flash format.  It's Adobe's doing that has flooded the internet with a non-open format and not published their authoring software for Linux.

You could always wait five years (estimate) for the big browsers to adopt support for SVG graphics SMIL animation standard (from W3C).  By then Inkscape will be able to author them just fine.  But I think that's a little slower than it takes your VM to load.

---

### Post by jimv on 2009-06-21
Try Gnash:

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

You can install it by using this command in a terminal:

sudo apt-get remove flashplugin-nonfree && sudo apt-get install gnash mozilla-plugin-gnash

---

### Post by raboofje on 2009-06-21
> **jimv said:**
> Try Gnash
AFAIK Gnash only provides a player - OP is looking for Flash authoring tools.

> Essentially, there would be an alternative in Ubuntu if Adobe opened their copyrights on the flash format. It's Adobe's doing that has flooded the internet with a non-open format and not published their authoring software for Linux.

There seems to be some improvement there though: the Flex SDK is largely open-source, and they offer a usable fully-open-source (MPL) package (see for example [here](http://opensource.adobe.com/wiki/display/flexsdk/Downloads). 

Their Eclipse-based Flex IDE, 'Flex Builder', is not open-source nor free - I haven't tried it, but iirc it's supported also on Linux.

Flex applications can be compiled to .swf files and executed in the flash player just like any flash app.

---

### Post by bridabom73 on 2009-06-21
Okay. I'll try haXe and Flex SDK.
They didn't work. IDK what Flex SDK is, and haXe is just a single file and I try to open it and nothing happens. I guess I am SOL. =(

---

### Post by Stochastic on 2009-06-23
no need to go through the haxe installer (which you run from command line with sudo privledges), it's in the Ubuntu repositories, just run ```
sudo apt-get install haxe
```But be sure you read the haxe documentation.

---

### Post by rootkowski on 2009-07-21
Hi!

For Flex development I use Komodo Edit and the Flex SDK under mpl. I have a guide on how to set those two up to work together nicely. The guide is at [http://blog.rootkowski.com/get-started-with-flex-development-on-linux/]("http://blog.rootkowski.com/get-started-with-flex-development-on-linux/")

Hope it's useful.  Cheers!

---

### Post by jap1968 on 2009-09-17
Apart from **haXe** you can have a look at the [**AXDT** plugin for Eclipse]("http://netpatia.blogspot.com/2009/09/flash-development-on-linux.html").

---

### Post by tbobker on 2010-06-18
This is a great option. No user interface straight in with the as3. I am going to try this and let you.

---

