---
title: "[question] basic file server"
date: 2009-07-29
forum: Server Platforms
---

### Post by caue.rego on 2009-07-29
I hope I'm not discussing this in the wrong place. But since this is my favorite technical forum and the one I know with the most variated topics subjects, I'll just go ahead and try it.


Here is what I believe it must be a very common scenario, and basically what I need. A *nix server (no windows, please) that is able to, among other things:

- host files for any kind of client (such as windows, macintosh, ubuntu, etc) both for guest access and logged.
- make regular backup, like *time machine*, flyback, backintime, etc.
- give a local tool for searching the files very much like google *GDS*, spotlight or even vista capacities.
- access it through VNC at very least.
- some kind of user domain, after all it will give logged access.
- bonus: something like xdmcpp


Those are just general non-restrictive guide-lines. They're not to be taken literally. Rather, just as illustrative, since I'm trying to draw a picture here.

It's easy to build a linux server working great with ssh and sftp. Really easy to setup, server side. But I want it to work with windows share, windows network, mac network, any machine to be able to access files there in any kind of way. Make it simple for user, not for the server. Everything will be backed up any fcking way, and easily searchable through a web interface, at least.

Samba will most likely be part of the hosting, of course, but that's not the question. What partition would be best to store the files? Well, my question is actually if there's already any solution for this out there yet. And I guess not. So...

I was thinking about using an old apple machine, power pc or something, and it has been my best bet for this, but I'd prefer to use ubuntu or something less restrictive.

I've been trying ubuntu server and line commands, but it's just too much hassle (such as in [http://ubuntuforums.org/showthread.php?p=7694917#post7694917](http://ubuntuforums.org/showthread.php?p=7694917#post7694917) ), even if I do know a lot about it, and read through manuals. Also not doing so good with regular ubuntu desktop because it misses so many packages and config.

Linux-wise I'm having best luck with Super OS, and I'll most likely use reconstructor afterward and setup a nice livecd to have a secure and fast way to leave it up and running if anything happens to the installed system, which I only see one reason to keep on a hard disk: updating patches.

But I haven't tried much more yet. I know there are options out there, including debian itself, but I'm not looking for options. I'm looking for a very basic thing and also to be simple to install and configure. Like routers are nowadays (thanks linksys). By the way, here's a very good example of a router I admire and it follows the kind of thought I'm urging to find in a simple file server: [http://www.fon.com/en](http://www.fon.com/en)

---

### Post by cariboo on 2009-07-29
Have a look at [Freenas]("http://www.freenas.org/index.php?option=com_frontpage&Itemid=22") it will run from a usb device, and has a web based management interface. It has all of the features you are looking for.

---

### Post by ugm6hr on 2009-07-29
I would also recommend FreeNAS as a basic home file server.  Set up SMB and NFS to allow access from any OS easily.

---

### Post by caue.rego on 2009-07-30
Thanks, I'll give it a shot and keep you informed on how it goes.

---

### Post by caue.rego on 2009-07-30
It may be too early to say this, but I've been trying to configure freenas and, although I still don't have it up and running, I couldn't find anything for **snapshot backups** (closer thing was raid, but i won't be using it for now), and even less for **finding files** (closer thing was a search function in the quiexplorer file manager). _Both as described before_, of course.

Anyone have better experience with this? Because, other than that, it seems pretty much like what I was looking for! :)

---

### Post by caue.rego on 2009-10-16
I ended up giving up on the whoe NAS thing. And I realize we don't need a "*basic*" file server. I guess the right word there would be "simple". It's very different.

And we still can't do it up to now.

The conclusion I came to is plain simple: it seems like it needs to be **google**. I've tried alternative searching methods, and they're just too slow or incomplete (**beagle**, tracker, strigi) and there's no sense or need to host files (or any data) that can't be found!

**Deskbar-Applet** reminds me of **Spotlight**, and there's also the more common **Tacker**'s Desktop Search which is also similar, but all of those don't offer remote search, not even for intranet. I don't know, maybe macserver would do that? Anyway, as far as I recall, **GDS for windows** does that. Why linux GDS can't? :(

Anyway, still searching for a **solution**.

---

### Post by ugm6hr on 2009-10-17
This is not a simple fileserver at all... Most fileservers do exactly that - serve files.

Searching is performed from your networked desktops.

If you want to be able to search from a web broswer, with the searching performed on the server, this is much harder.

I wonder if it would be possible to install an open source web search application (there are some out there) - see [http://www.searchtools.com/index.html](http://www.searchtools.com/index.html) to index local files, and then install a web server (for LAN use) with an index page that is simply a file list.

This should achieve what you want, provided that you store all shared files within the www folder (i.e. they will be within your "website").

Good luck.

---

### Post by cariboo on 2009-10-17
Have a look at htdig, it is in the repositories. It is a web based search engine, that should do what you need. It is a bit complicated to set up, but once done it should do what you want.

You are really limiting your self by not taking advantage of the command line tools available. there are more and more gui apps for setting up a server, but I personally feel that you that you can't diagnose a problem properly if the only experience you have is using a gui to set things up.

BTW what you want to do is way beyond a simple file server. I would almost suggest you may be better off purchasing a copy of Windows Home Server.

---

### Post by caue.rego on 2009-10-18
Thanks, **cariboo907** and **ugm6hr**! I will sure try those suggestions, and post results.

I would buy Windows Server, we are willing to pay for good service or solution, that's why I'm insisting on Google. But going Microsoft, as you've implied, isn't much reliable. We, as a technology company, plan on growing up more and more, so I believe it's good to start from the beginning with a good structured basis.

If we ever want to grow we can't trust our servers on Microsoft, or we will have to keep paying them more and more, until we either can't afford anymore and they buy us, or .

And I'm not afraid going to the command line at all. But you have to use GUI in many cases if you want faster results. Just as an example, it's often a lot easier to move multiples selected files clicking on icons than writing an extensive list of names, even with tab completion. Some operations go as far as being too hard to be just written to ever be done. Others, in lack of a better GUI or no good idea on how to make the interface graphical, are still better done on the feared texting mode.

As for "simple file server" I meant for the user. Google is simple.

---

