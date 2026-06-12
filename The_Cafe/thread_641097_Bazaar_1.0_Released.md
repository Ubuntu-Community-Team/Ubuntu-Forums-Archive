---
title: "Bazaar 1.0 Released"
date: 2007-12-15
forum: The Cafe
---

### Post by 23meg on 2007-12-15
Canonical has just announced the 1.0 release of the [Bazaar]("http://bazaar-vcs.org") version control system.

[Press release]("http://www.ubuntu.com/news/bazaar-v1-release")
[Linux-Watch article]("http://www.linux-watch.com/news/NS7185318863.html") 

Bazaar has matured into a very usable, simple, yet powerful VCS in a pretty short time. If you want to quickly try it out, here are two guides for beginners:

[http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html)
[https://wiki.ubuntu.com/Bazaar](https://wiki.ubuntu.com/Bazaar)

---

### Post by kripkenstein on 2007-12-15
Thanks for posting that, this is very exciting.

I've used subversion not only for coding but for keeping versions of documents I write and collaborate on with other people. After reading the introduction to Bazaar, it looks like I might switch, it really has some great features.

Being written in Python is a big plus as well, as it'll be easier to write code that interfaces with it.

---

### Post by 23meg on 2007-12-15
You're welcome. It's indeed a big bonus that it's written in Python; the only real downside is that it's not the fastest performing VCS, perhaps due to that.

I recall you had written a personal versioning app; I'd love it if you based it on Bazaar, for example.

---

### Post by kripkenstein on 2007-12-15
> **23meg said:**
> I recall you had written a personal versioning app; I'd love it if you based it on Bazaar, for example.
Heh, you have a good memory :)

About that project, there wasn't much interest in it, and it didn't go very far. But using Bazaar now, it occurred to me that most of the things I wanted to do there could be implemented as a wizard or plugin in the Bazaar GUI (Olive). I'm looking into this now to see if its feasible.

---

### Post by Mateo on 2007-12-15
read the entire front page there and i still have no idea what this thing does.

---

### Post by kripkenstein on 2007-12-15
> **Mateo said:**
> read the entire front page there and i still have no idea what this thing does.

Well, if you know what CVS and SVN are, then this is like them, only better. In particular, because it is distributed - you can commit changes locally, maintain independent branches that re-merge later on, and so forth. Lots of flexibility, and **very** useful for open-source development.

If you don't know what CVS and SVN are, then perhaps you don't need to know what this is either ;) (But basically all of these are version control systems - they keep a list of all prior versions of files, make sure multiple people collaborating on the same files don't step on each other's toes, etc.)

---

### Post by Mateo on 2007-12-15
Yeah I figured out that cvs stands for version control system but i have no idea what that means.

your explanation helps.  it is like apt-get then?

---

### Post by kripkenstein on 2007-12-15
> **Mateo said:**
> Yeah I figured out that cvs stands for version control system but i have no idea what that means.

your explanation helps.  it is like apt-get then?
Well both apt-get and cvs/svn can grab packages from a server and bring them to your computer. Another similarity is that they can both keep your local version up-to-date with the latest on the server.

But apt-get just brings it, cvs/svn do much more. Cvs/svn can also let you push changes back up to the server. This lets many people collaborate at the same time on developing a single application.

---

### Post by maniacmusician on 2007-12-15
VCS: [http://en.wikipedia.org/wiki/Version_control_system](http://en.wikipedia.org/wiki/Version_control_system)

CVS: [http://en.wikipedia.org/wiki/Concurrent_Versions_System](http://en.wikipedia.org/wiki/Concurrent_Versions_System)

SVN: [http://en.wikipedia.org/wiki/Subversion_%28software%29](http://en.wikipedia.org/wiki/Subversion_%28software%29)

Bazaar: [http://en.wikipedia.org/wiki/Bazaar_%28software%29](http://en.wikipedia.org/wiki/Bazaar_%28software%29)

---

### Post by Mateo on 2007-12-15
> **kripkenstein said:**
> Well both apt-get and cvs/svn can grab packages from a server and bring them to your computer. Another similarity is that they can both keep your local version up-to-date with the latest on the server.

But apt-get just brings it, cvs/svn do much more. Cvs/svn can also let you push changes back up to the server. This lets many people collaborate at the same time on developing a single application.

hmm, that's interesting. However, if I am working on a file on my computer, how do I know that someone else isn't work on the same file on their computer?  If I upload mine, don't they have to redownload the file and look for the changes to insert their own code?

---

### Post by yatt on 2007-12-15
Bazaar is alright, I just find it horribly slow when compared to others like git.

---

### Post by 23meg on 2007-12-15
> **Mateo said:**
> hmm, that's interesting. However, if I am working on a file on my computer, how do I know that someone else isn't work on the same file on their computer?  If I upload mine, don't they have to redownload the file and look for the changes to insert their own code?

With a distributed VCS such as Bazaar, you "commit" changes locally, and later (optionally) publish them to a remote location, where others can publish theirs too. In distributed systems, no single location is more or less important than others. You work on your local copy, publish changes, others to so too, and if they like your changes, others can "pull" them from you.

To keep up to date, so that there won't be too many conflicts with others' copies, it's a good idea to occasionally "merge" changes from the parent branch to your local copy.

This may help you understand the distributed paradigm better:

[Intro to Distributed Version Control (Illustrated)]("http://betterexplained.com/articles/intro-to-distributed-version-control-illustrated/")

---

### Post by 23meg on 2007-12-15
> **kripkenstein said:**
> 
About that project, there wasn't much interest in it, and it didn't go very far. But using Bazaar now, it occurred to me that most of the things I wanted to do there could be implemented as a wizard or plugin in the Bazaar GUI (Olive). I'm looking into this now to see if its feasible.

But what's good about Pevo is its simplicity, and task-specificness. A full-blown Bazaar GUI with Bazaar-specific terminology is good for, for example, coordinating complex merges with many people. I'd prefer a simpler interface, with as little reference to common VCS terms as possible for simple, local operations. 

Actually, the notion of having a separate GUI application for versioning is awkward in a sense. I perform general tasks related to files in the file manager, and going back to a specific version of a file is a file operation too, so ideally, I should be able to do it in the file manager.

---

### Post by kripkenstein on 2007-12-16
> **Mateo said:**
> hmm, that's interesting. However, if I am working on a file on my computer, how do I know that someone else isn't work on the same file on their computer?  If I upload mine, don't they have to redownload the file and look for the changes to insert their own code?
Yeah, this is an issue. Because of this, early versioning systems used to require that you 'check out' a file from the server, and then no-one else could 'check out' that same file. So only one person would work on it at the same time, preventing the problem you mention.

However, it turns out that this is very inefficient. Modern systems (like SVN) **do** let multiple people work on the same file at the same time. They then 'merge' the files in a smart way. For example, if person A fixes a bug in function F1, and person B writes a new function F2, then a smart merging method can combine these changes in the same file without hassle. That is, the latest version of the file would contain both bugfixes to F1 and the new F2. This works surprisingly well.

The only problem is if both person A and person B work on the same lines of code in the same file. Then the system would warn them and they would have to merge things manually. But, this is fairly rare in practice.

---

### Post by kripkenstein on 2007-12-16
> **23meg said:**
> But what's good about Pevo is its simplicity, and task-specificness. A full-blown Bazaar GUI with Bazaar-specific terminology is good for, for example, coordinating complex merges with many people. I'd prefer a simpler interface, with as little reference to common VCS terms as possible for simple, local operations. 

Yeah, I agree. The goal of Pevo was to be much simpler than normal versioning GUIs. But perhaps that simplification could be a wizard inside such a GUI... still thinking about it.
> 
Actually, the notion of having a separate GUI application for versioning is awkward in a sense. I perform general tasks related to files in the file manager, and going back to a specific version of a file is a file operation too, so ideally, I should be able to do it in the file manager.
Yes, perhaps it should all be integrated into the file manager. One reason for Pevo stalling is that I never had a good idea about how exactly to implement the ideas.

---

### Post by 23meg on 2008-01-16
Looks like [TimeVault]("https://launchpad.net/timevault") will soon have Nautilus integration.

---

