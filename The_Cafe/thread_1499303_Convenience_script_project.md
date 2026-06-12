---
title: "Convenience script project"
date: 2010-06-01
forum: The Cafe
---

### Post by tom.swartz07 on 2010-06-01
Hi all!

I know I posted a long while back when I was in the planning stages of this project, but now that I have it (somewhat) up and running, I would like to ask for help!

I have created a Launchpad project called Code Monkey. [Found HERE.]("https://edge.launchpad.net/codemonkey/") This project aims to create a source for small, user created scripts that perform "mild to moderately complex" tasks from the command line.
For example, I have a script that was modified from a post on OMG!Ubuntu! months ago that allows users to fix the dreaded Missing GPG key problem. Another script will check the system and report information about the hardware's support for Compiz effects. There is currently about 10 of such scripts.


Here is where you guys come in- I am looking for people that would like to help add to and manage this project! 
Many of these scripts are still in their infancy, and much of the documentation is lacking. I am hoping that with some added exposure and a few helping hands, this project could really go somewhere! (Provide a troubleshooting source for the Forums?)

Please feel free to contact me or join the Code Monkey Developers group on Launchpad!

---

### Post by tom.swartz07 on 2010-06-01
Does it look like a good idea?

To be completely honest, any feedback would be awesome.

---

### Post by K.Mandla on 2010-06-01
Have you considered adding snippets from sites like [http://blog.commandlinekungfu.com/](http://blog.commandlinekungfu.com/) or [http://commandlinefu.com?](http://commandlinefu.com?)

Also, the remarks for the x64 Flash installer, gmail.sh and gReader.sh scripts say the programs are intended to backup files via rsync. I think maybe that's off-target. ;)

---

### Post by tom.swartz07 on 2010-06-01
> **K.Mandla said:**
> Have you considered adding snippets from sites like [http://blog.commandlinekungfu.com/](http://blog.commandlinekungfu.com/) or [http://commandlinefu.com?](http://commandlinefu.com?)
I originally got some of the ideas for the scripts from those sites! I have em updated on my google reader, so I always catch the newest ones! :P

> 
Also, the remarks for the x64 Flash installer, gmail.sh and gReader.sh scripts say the programs are intended to backup files via rsync. I think maybe that's off-target. ;)
hogeez- I didnt even realize that! 
SEE!!! This is exactly why I was hoping for a few extra sets of eyes and hands. :P
I guess they were carried over as artifacts when I copied the GPL licence info to the other scripts....

---

### Post by K.Mandla on 2010-06-01
By the way, no disrespect to Ubuntu users, but some other distros tend to attract rabid scripters, for what I have seen. You might get ideas by visiting other forums (Arch and Gentoo come to mind) and asking blankly what scripts people use regularly and why, and if anyone offers anything useful, ask for their permission to use it in your package.

---

### Post by tom.swartz07 on 2010-06-01
> **K.Mandla said:**
> By the way, no disrespect to Ubuntu users, but some other distros tend to attract rabid scripters, for what I have seen. You might get ideas by visiting other forums (Arch and Gentoo come to mind) and asking blankly what scripts people use regularly and why, and if anyone offers anything useful, ask for their permission to use it in your package.

Good idea!
I know Ubuntu is more biased towards GUI, but there is still a lot of scripting that can occur. It never occurred to me that I could ask the other distros. 

Youre awesome. :D

---

### Post by tom.swartz07 on 2010-06-01
Although, any help from the forums here would still be awesome too! :D

---

### Post by K.Mandla on 2010-06-01
Also, I don't know what exactly you're using as criteria for inclusion, but the [sed home page]("http://sed.sourceforge.net/") has a gargantuan list of [one-liners]("http://sed.sourceforge.net/sed1line.txt") and short scripts that do all kind of nifty things to files. 

[awk one-liners]("http://www.google.com/#hl=en&source=hp&q=awk+one-liners") are famous too.

---

### Post by tom.swartz07 on 2010-06-01
> **K.Mandla said:**
> Also, I don't know what exactly you're using as criteria for inclusion, but the [sed home page]("http://sed.sourceforge.net/") has a gargantuan list of [one-liners]("http://sed.sourceforge.net/sed1line.txt") and short scripts that do all kind of nifty things to files. 

[awk one-liners]("http://www.google.com/#hl=en&source=hp&q=awk+one-liners") are famous too.

Cool- Ill check it out.

Its not really focused on one-liners, but more precisely focused on slightly larger (average a dozen lines-ish?) that could accomplish a task that would otherwise be unwieldy to do.

For example, you looked at the X64 flash installer. It does a number of simple one-line tasks, such as removing old versions of flash, updating the system and installing the newest version of Flash for the x64 system. All of them are relatively simple to do, but the script automates it and completes the task in 1/10 of the time!

Things like that, you know?

---

### Post by W3ird_N3rd on 2010-06-01
I registered a branch and thought I could just copypaste my crappy script to the interwebs but it looks like it's not that easy.

Since my crappy ghetto script is probably not worth spending hours on to figure out bazaar, I'll just pastebin it here. :P

[SAFEDAWG](http://pastebin.org/300308)

---

### Post by tom.swartz07 on 2010-06-01
> **W3ird_N3rd said:**
> I registered a branch and thought I could just copypaste my crappy script to the interwebs but it looks like it's not that easy.

Since my crappy ghetto script is probably not worth spending hours on to figure out bazaar, I'll just pastebin it here. :P

[SAFEDAWG](http://pastebin.org/300308)

HAHA!
It was awfully hard to figure out how to use Bazaar.
Once you get it set up, though its REALL easy.
```
bzr commit
bzr push lp:branchname
```
boom. done.

---

### Post by kgas on 2010-06-02
You can also collect good information from Arch Linux forum. For eg
[bashrc](http://bbs.archlinux.org/viewtopic.php?id=50235) and [command line](http://bbs.archlinux.org/viewtopic.php?id=56646&p=1)

---

### Post by Penguin Guy on 2010-06-02
> **tom.swartz07 said:**
> HAHA!
It was awfully hard to figure out how to use Bazaar.
Once you get it set up, though its REALL easy.
+1 to that, it took me forever to get it working, but once I had it was actually quite simple.

I've joined your Launchpad team (great work setting it up and everything) and have been meddling with a few of your scripts - if all goes well I'll upload some code soon.

Something really weird just happened and I just had to post it right away: When editing one of your scripts I was using [FONT="Courier New"]mktemp[/FONT] and it created the file '/tmp/tmp.jshBr0oR9Q' - spookey :o.

---

### Post by Penguin Guy on 2010-06-03
Right; I've uploaded a new 'earthwallpaper' script (sorry about those few merge mistakes) and it seems to work okay, if you accept the merge I've got a few more ideas for the script (maybe 'earthwallpaper' and 'bing_wallpaper' can be merged into one script?).

I also couldn't help noticing that in most of the scripts, the license is bigger than the code :???:

And what's up with the 'banana' function?
```
$ ./compiz-check --banana
```

---

### Post by tom.swartz07 on 2010-06-03
> **Penguin Guy said:**
> Right; I've uploaded a new 'earthwallpaper' script (sorry about those few merge mistakes) and it seems to work okay, if you accept the merge I've got a few more ideas for the script (maybe 'earthwallpaper' and 'bing_wallpaper' can be merged into one script?).
I had that idea back when I originally started the two, but I never got around to making it so that they both worked into one script!
No worries about the names, just as long as the whole branch is mirrored and there are no naming conflicts its perfectly fine!
> 
I also couldn't help noticing that in most of the scripts, the license is bigger than the code :???:
haha- in some cases, yeah- the bash scripts in particular are relatively short, but they really accomplish tasks that would otherwise be kinda difficult to do manually. Such is the cost of having a GPL license on it..


Try running the code with the banana argument? Its mostly just for giggles, like ```
 apt-get moo 
```

---

### Post by Penguin Guy on 2010-06-05
Just wanted to give this thread a bump - see if we can get some more people to join our ever-increasing ranks (so far: me and Tom). Also wanted to point out my [Launchpad group]("http://ubuntuforums.org/group.php?groupid=771") which, I was surprised to find, already has 9 members.

---

### Post by tom.swartz07 on 2010-06-13
Just giving this thread a publicity bump.

The project has made great strides with help from Josh and other users.

I have recently updated the one-off download package on the main page, so if you have recently downloaded the .tar file there, please be aware that those versions are woefully out of date.



Also, its never too late to jump in and help! Even if you cant program that well, we could still use help! Many hands make light work! :D

---

