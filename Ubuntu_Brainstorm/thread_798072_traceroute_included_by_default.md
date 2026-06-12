---
title: "traceroute included by default"
date: 2008-05-17
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-17
The core network tool of traceroute (a tool similar to ping) isn't included by default.

Should it be?

---

### Post by Mr A Mouse on 2008-05-17
Ooh--that's one of my biggies, especially if I'm diagnosing a network problem or tracking down a spammer. On the other hand, IIRC traceroute functionality is included in the Network Tools panel under System > Administration, and there is a problem of trying to fit too much stuff on a CD.

---

### Post by CrazyGuy123 on 2008-05-17
It's a bad sign for ubuntu if the CLI is loosing features in favour of GUI ones...  We don't want to end up with a microsoft CLI!

Thanks though for pointing that out - I never bother looking for network stuff in the gui really because I presume the command line ones will be easier and quicker to find and use.

---

### Post by Mr A Mouse on 2008-05-17
Hmmm ... good? Bad? I'm not comparing to an MS OS, so I guess my standard of comparison is "What do the users want?" If the majority of users want the GUI functionality instead of command line, I'm all for giving the users what they want.

---

### Post by CrazyGuy123 on 2008-05-17
Ah yes - I was a bit offtopic there.

anyway - I've added a poll to gague support.

---

### Post by Mr A Mouse on 2008-05-17
Cool--though I would ask one of the mods to include a neutral response.

---

### Post by ghindo on 2008-05-18
Isn't it already included by default?  Under Network Tools?

---

### Post by CrazyGuy123 on 2008-05-18
In fact, after thinking about this a bit more, I've changed my mind a bit:

A graphical only tool isn't really good enough, because you can't use a graphical tool when you're connected remotely through ssh, or when you don't have ubuntu-desktop installed (ie. a server), or when for some reason X or gnome is broken.

---

### Post by Orra on 2008-05-18
Guys, although **traceroute** isn't included in the default install, **tracepath** is. And according to that package's description,

> The tracepath utility is similar to the traceroute utility, but also attempts to discover the MTU of the path.

But there's more. The Network Tools utility is a GUI wrapper around command line tools. See for yourself; search for "tcptraceroute" in the [source code]("http://svn.gnome.org/viewvc/gnome-nettool/tags/gnome-nettool-2-22-0/src/traceroute.c?revision=753&view=markup"). So no need to fret about GUI tools being included instead of CLI ones. :)

Just one more thing—turns out the Ubuntu package modifies the Network Tools code to use tracepath instead of traceroute. Which makes sense, as it can't use traceroute, as that isn't installed!

---

### Post by chrisccoulson on 2008-05-18
Orra is correct, Ubuntu installs tracepath by default instead of traceroute. I only realized this when I wanted to use traceroute a while ago and realized it wasn't installed

---

### Post by CrazyGuy123 on 2008-05-19
ah cool.

what about a symlink from traceroute to tracepath for those of us who like to be able to use the same commands on all our linux systems?  (and it will save headaches for those other admins like me that had never discovered tracepath)

---

### Post by Orra on 2008-05-20
> **CrazyGuy123 said:**
> ah cool.

what about a symlink from traceroute to tracepath for those of us who like to be able to use the same commands on all our linux systems?  (and it will save headaches for those other admins like me that had never discovered tracepath)
Yeah, agreed. A symlink would make the command much more discoverable.

---

### Post by smartboyathome on 2008-05-20
Does it use the same flags, though? I think it may be a little different (ie, it may use -n instead of -m).

---

### Post by CrazyGuy123 on 2008-05-20
yep and also tracepath seems to come up with substantially different results from traceroute.  For example tracepath seems to be blocked by some ISP between me and google.com, whereas traceroute is fine - which is odd considering they're both IMCP traffic.

---

