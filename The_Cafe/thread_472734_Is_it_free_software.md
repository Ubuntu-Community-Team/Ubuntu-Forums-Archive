---
title: "Is it free software?"
date: 2007-06-13
forum: The Cafe
---

### Post by Ozor Mox on 2007-06-13
A thought occurred to me today...

I really like the idea behind free software. I started with Firefox on Windows, and slowly it has spread across my computer taking over one application at a time until eventually it displaced the operating system altogether, leaving my computer entirely proprietary free...

Well actually, I know it isn't. There's proprietary firmware and drivers, to make things work better, but then I don't consider myself to be a free software zealot who considers proprietary software the work of the devil, I'm just a supporter of free software. I'd rather use it, and I will use it where I can.

But how do I know that what I'm running is free? The free software and open source definitions can be clearly found on GNU, FSF, or OSI's websites, as can the licenses that software must be released under to be considered free/open source. For an individual piece of software, that's fine. If it's under the GPL for example, I know it's free software. What about an entire operating system though? I know Ubuntu's preferred license is the GPL, but it's such a vast collection of software that it must be covered by many licenses that I do not understand for software components that I do not understand.

I like the ideals of free software the most, but I don't like how Stallman criticises the open source initiative's standpoint on things. It's obvious that certain individuals and organisations will not be interested in the deep ethics of the idea, and in order for them to accept the software they need to be looking at its technical benefits.

Is it "possible" to support both free and open source software (idealogies) at the same time? Are they the same anyway? Is there no need to care? I feel like I should care, because these are the very reason what I'm using exists. It's not like a company has produced all this software, people have produced it, because they believe in these things...or maybe its just the open source (technical) side they believe in after all. If I was using a Mac or Windows, I just use it. Company produces software, I pay my money, end of story. Here, it's...communities produce software, company brings it together, I pay no money but maybe I feel I should be doing *something* for it...

Anyway, these are just general musings about free software. There's no real point to this, other than maybe "how do I know for sure software I use is free and/or open source software?"...and possibly "are you actually interested in the ideals of free and/vs open source software, or do you just use it?" if you want to answer a question, answer those!

At least this isn't another topic on why Windows or Mac are better/worse/different in this/that way than Ubuntu :popcorn:

---

### Post by stmiller on 2007-06-13
A vanilla Ubuntu install has all free software. That's why you must 'fetch' the nvidia or ati drivers yourself.

---

### Post by az on 2007-06-13
That's a great question.

Debian has a guideline called the DFSG (Debian Free Software Guidelines)  It basically describes what a license needs to do to be compliant with the GPL.  Anything that can protect your freedoms as well as the GPL is DFSG-compliant.  Anything in Ubuntu main and Universe is DFSG-compliant.  Software in the restricted and multiverse repo is not.

---

### Post by jrusso2 on 2007-06-13
If a Vanilla Ubuntu install is all free software then why would anyone need to develop GNU Sense?

---

### Post by capecove on 2007-06-13
Interesting...

Here is my take on it; warning, long and windy road ahead. :)

My personal philosophy is that everything in the world revolves around a persons self government. The choices a person makes are the direct result of their own self goverment. For example, a person who chooses to drink and drive. Tt wasn't the fault of his manager who may have told him earlier in the day that he was fired. 

Open source software is something that can succeed (long term) when the users have good self government. We have to consider how important it is for us to take the open source software and do something that benefits the entire community surrounding that open source movement. If there is not some manifestation of profibility (not solely financial in scope mind you), the movement will fail. In other words, open source software is a potentially wonderful thing but only if the people using it/creating it do things to improve and support it.

Freeware is a little different story. I have used many freeware programs. I will continue to use them as the years go by but I select them carefully. For example, when I was using Windows I usually had a Pegasus Mail installation. I was using it since my first days on the 'net and still enjoyed using it for many reasons. Now I am generally a Thunderbird mail guy but would be willing to change that if I don't like to course the software development/community development starts taking.

---

### Post by v8YKxgHe on 2007-06-13
> If a Vanilla Ubuntu install is all free software then why would anyone need to develop GNU Sense?

Ubuntu as it is, _does_ contain non-free software in a base install. These are mostly AFAIK wireless drivers. The next release of Ubuntu will also include a new .... thing (like Xubuntu, Kubuntu) that will be 100% free and is working with gNewSense on that.

---

### Post by christhemonkey on 2007-06-13
To find out what packages installed are non-free in any sense install the program vrsm.
```
sudo apt-get install vrms 
```

Then run it:
```
vrms 
```

---

### Post by matthinckley on 2007-06-13
```
matt@yamato:~$ vrms
               Non-free packages installed on yamato

linux-server              Complete Linux kernel on Server Equipment.
unrar                     Unarchiver for .rar files (non-free version)
  Reason: Modifications problematic

  2 non-free packages, 0.6% of 339 installed packages.
matt@yamato:~$

```

why is linux-server listed as non-free? isn't it just a meta-package?

---

### Post by az on 2007-06-13
> **matthinckley said:**
> ```
matt@yamato:~$ vrms
               Non-free packages installed on yamato

linux-server              Complete Linux kernel on Server Equipment.
unrar                     Unarchiver for .rar files (non-free version)
  Reason: Modifications problematic

  2 non-free packages, 0.6% of 339 installed packages.
matt@yamato:~$

```

why is linux-server listed as non-free? isn't it just a meta-package?

That's a bug.  It's interesting.

The linux-generic metapackage is in the restricted repo, because it depends on linux-image-generic and linux-restricted-modules, the former is in main and the latter is in restricted.  If you wanted a completely DFSG-free kernel, you would remove the linux-restricted-modules packages you have installed on your system.

That would also remove the linux-generic metapackages, but leave the linux-image-generic metapackages intact (which are needed for upgrades)

The server kernel does not have any restricted-modules associated with it.  I guess the autobuilders put linux-server the same as linux-&#285;eneric, and put it in restricted, although it does not contain dependencies from the restricted repo.  Perhaps this is there in the even that there is one day a linux-server-restricted-modules package?

---

