---
title: "Commands you had problems with"
date: 2008-01-24
forum: The Cafe
---

### Post by murmel on 2008-01-24
Hello everybody! I'm writing a q/a to some people that've just began using Linux.
But I am having problems with what questions to give them. So here I am, asking you for advice. What commands did you have problems with doing in the beginning of your Linux carriers?
Just write here things you needed and didn't understand how to do,.
Thank you very much!

- Simon

---

### Post by murmel on 2008-01-24
bump =)

---

### Post by TJCIB on 2008-01-24
I know there are resources out there regarding this, but perhaps you could at least reference the difference between the "aptitude" and "apt-get" commands.  I am just starting (on my second week of Linux) and it was a bit confusing in the forums seeing some people use one command and others, in the same threads, using the other.

---

### Post by Mad_Dawg on 2008-01-24
Installing any program not in a depository.  Especially tar.bz files.  And I still can't get my printer going even though Kubuntu 'sees' it.  :(

---

### Post by PeterJS on 2008-01-24
> **Mad_Dawg said:**
> Installing any program not in a depository.  Especially tar.bz files.  And I still can't get my printer going even though Kubuntu 'sees' it.  :(

Tar.gz is just an archive format, like a zip file. So just having the extension doesn't tell much about the contents of the file, we can make some reasonably safe statistical assumptions, but ultimately they're just assumptions. The most common thing to find in a tarball is program source code and the scripts to build and install the program, but they only way to know for sure is to unpack it and read the README or INSTALL file. Assuming you have the build tools installed (the package name is [build-essential](apt:/build-essential)) the process of building from source goes like this:
1)unpack the tarball
2)cd in to the new directory
3) run ./configure
4) step 3 is pretty much guaranteed to fail the first time, it's going to pitch a fit about missing -dev packages, install the needed packages and re-run step 3 until it it completes sucessfully
5)run make
6)get some coffee make takes any where from 30 seconds to 8 hours depending on what you're making
7)run sudo checkinstall

---

### Post by Paul820 on 2008-01-24
> **TJCIB said:**
> I know there are resources out there regarding this, but perhaps you could at least reference the difference between the "aptitude" and "apt-get" commands.  I am just starting (on my second week of Linux) and it was a bit confusing in the forums seeing some people use one command and others, in the same threads, using the other.

They are more or less the same, **apt-get** just gets the packages, **aptitude** cleans out all the crap left behind by other uninstalls like unused dependencies as well as getting the package you want.

---

### Post by minutest on 2008-01-24
I am with Mad_Dawg. I downloaded a tar file and was unsure what to do with it.

Unsure how basic you are looking to go but my main trouble was with getting my NVIDIA drivers working.

Took a lot of reading to find out how to stop and stop Xserver.Still not 100% sure I know the correct command.

Also it seams like some commands change a little with each distro.

---

### Post by nick_h on 2008-01-24
Just read this forum to get an idea what problems new users encounter.  Some examples that come to mind are:

Installation
Grub
Lost password
Program installation
Hardware (Printers and WiFi)
Command line

---

### Post by Lord Illidan on 2008-01-24
Well, it was quite a long time ago, but I didn't know how to use vi, nor start the terminal.

Also, installing apps not in repositories is another problem, true

---

### Post by Arwen on 2008-01-24
> Well, it was quite a long time ago, but I didn't know how to use vi
That was one of the things I was really familiar when first booted in ubuntu,cause I've used vi before in solaris 10:-P.But the most common problems I've been asked for help  are lost GRUB and XP and graphic cards' and modems' drivers and utilities to manage mobile phones.Apart from the 'How Do I....?' questions..(you know,where's the music/movie player,where's sth like MS Word..)

---

### Post by oldos2er on 2008-01-24
I had  problems with multimedia setup. If you read through these forums you find it's a very common problem with new users.

---

### Post by Lord Illidan on 2008-01-24
Vi was horrifying though for a fresh linux guy. What the hell do I press!

---

### Post by PeterJS on 2008-01-24
> **Lord Illidan said:**
> Vi was horrifying though for a fresh linux guy. What the hell do I press!

Vi is frightening to everybody. I've been using linux for over 6 years and that thing still frightens me.

---

### Post by murmel on 2008-01-24
Hehe, thank you so much boys n' girls! I really appreciate it! One thing I'll use is how to use tar and how to install a program from source. =)

Keep em' coming!

- Simon

---

### Post by newbeeman on 2008-01-24
> **murmel said:**
> Hehe, thank you so much boys n' girls! I really appreciate it! One thing I'll use is how to use tar and how to install a program from source. =)

Keep em' coming!
- Simon

One big problem I have is out of date Tutorials. Just finding a tutorial is bad enough, then to get part way through using it to install something, only to find the files have a different name or are missing. 
One case in particular. Try installing the HP printer to Linux files. Man what a mess!:(

---

### Post by bodhi.zazen on 2008-01-24
Moved to the Cafe as this is not a direct request for support.

The command line is intimidating to most, I suggest you teach your friend how to user the man pages. "teach a man to fish" kind of thing.

NOT introducing [size=4]**tab completion**[/size] is also cruel and unusual punishment.

Helpful links to get started :

[http://doc.gwos.org/newdoc/doku.php/clibeginner](http://doc.gwos.org/newdoc/doku.php/clibeginner)

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)


[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
	[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)
	[http://www.reallylinux.com/docs/guru.shtml](http://www.reallylinux.com/docs/guru.shtml)
	

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Racecarandy on 2008-01-24
> **PeterJS said:**
> Tar.gz is just an archive format, like a zip file. So just having the extension doesn't tell much about the contents of the file, we can make some reasonably safe statistical assumptions, but ultimately they're just assumptions. The most common thing to find in a tarball is program source code and the scripts to build and install the program, but they only way to know for sure is to unpack it and read the README or INSTALL file. Assuming you have the build tools installed (the package name is [build-essential](apt:/build-essential)) the process of building from source goes like this:
1)unpack the tarball
2)cd in to the new directory
3) run ./configure
4) step 3 is pretty much guaranteed to fail the first time, it's going to pitch a fit about missing -dev packages, install the needed packages and re-run step 3 until it it completes sucessfully
5)run make
6)get some coffee make takes any where from 30 seconds to 8 hours depending on what you're making
7)run sudo checkinstall

step 1 tells me to unpack the tarball...how do i do that?  step 2 says to CD in to the new directory...how do i do that?  i am amazingly lost and wish i could spend all day on the forums.  nice topic!

---

### Post by Mateo on 2008-01-24
for me, i still can't wrap my head around how to use | with commands.  i don't get it.

---

### Post by p_quarles on 2008-01-24
> **Mateo said:**
> for me, i still can't wrap my head around how to use | with commands.  i don't get it.
Piping isn't simple, but it's one of my favorite elements of the Bash CLI. Basically, it takes the output of the command before the "|" and uses the second command to process that output. A really simple example: say you have a directory with a large number of files. If you type "ls -la", you'll need to do a lot of scrolling to see everything. But if you were to pipe that output through the "less" pager, it becomes much more manageable:
```
ls -la | less
```
Give it a try.

---

### Post by Lord Illidan on 2008-01-24
> **Mateo said:**
> for me, i still can't wrap my head around how to use | with commands.  i don't get it.

The | or "pipe" simply pipes the output of one command to another command.

A simple example. Try running ls in a large directory. Notice how you need to scroll to see the entire input.

To get rid of it, you can type ls | less

Another example is ps aux and grep
ps aux | grep firefox will give you all the processes that match firefox.

---

### Post by Mateo on 2008-01-24
^^ thanks both of you.  i think my problem is that it's usually run with a program that you never use by itself.  for example, i often see "grep" used on the right side of |, but when do you *ever* use grep as a standalone program?  so i think my problem is that the programs used on the right side of the | are programs that i'm completely and totally unfamiliar with.

---

### Post by Mateo on 2008-01-24
See, this is another reason why I don't get it.  I just tried this:

```
cd Music | ls
```

and it didn't work.  Instead of showing what's in my Music directory, it showed what's in my home directory.

---

### Post by Lord Illidan on 2008-01-24
Grep works on any input, so it can be used to search for patterns in a file, too.

For example, let's put the output of ps aux into a file
```
ps aux > test
```
We can use grep to search for firefox in that file :
```
grep firefox test
```

---

### Post by bodhi.zazen on 2008-01-24
Oh no, grep is quite useful as a stand alone.

Lets say you want to search a config file for a specific option (you just want to check your config)

grep root /etc/ssh/sshd_config

will post any lines with root, so you can check the status of root log ins w/o opening an editor.

Search a text file for a person's phone number, email, tons of use.

You can also colorize grep, which I like at least.

---

### Post by Lord Illidan on 2008-01-24
> **Mateo said:**
> See, this is another reason why I don't get it.  I just tried this:

```
cd Music | ls
```and it didn't work.  Instead of showing what's in my Music directory, it showed what's in my home directory.

But cd Music does not return any output. All it does is change your current directory.

What you could do is ls ~/Music

---

### Post by p_quarles on 2008-01-24
The "grep" command finds lines in text output that have at least one occurrence of the search term. So, yeah, you could easily use it by itself, as long as you gave it a target text file. Random example from my home directory:
```
me@me:~$ grep wallpaper theme-details_1-15-08 
```
returns:
```
wallpaper: Carbon plain weave by BIGBC at deviantart
```The entire target file is about 10 lines long (so I wouldn't do this except as an example), but grep returns only lines that match the search term. This would definitely be useful with any large text file.

---

### Post by bodhi.zazen on 2008-01-24
grep "command line geeks" "Ubuntu Forums"

---

### Post by p_quarles on 2008-01-24
> **bodhi.zazen said:**
> grep "command line geeks" "Ubuntu Forums"
I'm pretty sure that would crash my system. :D

---

### Post by Mateo on 2008-01-24
i didn't say that all of the programs to the right of | are unuseable standalone, i said that they aren't commonly used standalone (specifically by me), so i'm almost completely familiar with using them.  so think that's why i'm not good at understanding the | symbol.

---

### Post by murmel on 2008-01-24
I've always used 
```
cat /etc/fstab | grep nfs
```
but
```
grep nfs /etc/fstab
```
does the same and is... a little shorter. :D
Everything is about how lazy one can be.. :)

Thanks everybody for replying! I'm some good stuff here and I've been working with the questions and it's getting gooood .. I think...

If someone got time, could you explain how the ./configure , make , make install with details about what they do when executing them and maybe show an example? (Haven't found a program yet to install. All programs comes with ubuntu, darn it! ;)

Keep the posts rolling!

- Simon

---

### Post by murmel on 2008-01-24
```
ls -al /usr/bin | grep add | less
```
First I list everything (-a) in /usr/bin with "long listing" (-l), then I pipe it to grep, and greps everything that has the word add in it. At last I use less to make it easy (if it would be alot of stuff there with add in it) to scroll with the up/down arrows.
That's one easy command.
Another is if you would like to get the md5sum of "hello";
```
echo -n hello | md5sum | cut -d ' ' -f 1
```
echo hello without a new line added , pipes it to md5sum and cuts out the ugly "-" that usually comes with it.
I'm not that good with piping, maybe others could show even longer and more awsome pipings. :popcorn:

---

### Post by nick_h on 2008-01-24
> If someone got time, could you explain how the ./configure , make , make install with details about what they do

Have a look at the [How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/) web page.  It gives a good guide to all types of installation.

---

### Post by kevdog on 2008-01-24
If you think grep is hard, try reading about sed -- the ultimate stream editor.  Its very useful, but difficult to master.

---

### Post by Bruce M. on 2008-01-24
> **Lord Illidan said:**
> Vi was horrifying though for a fresh linux guy. What the hell do I press!

> **PeterJS said:**
> Vi is frightening to everybody. I've been using linux for over 6 years and that thing still frightens me.

I'm not frightened nor horrified by it because I have no idea what it is.   :lolflag:

```

bruloo@The-Team:~$ man vi
No manual entry for vi
bruloo@The-Team:~$ 

```

And still don't.  :confused:

So obviously the question is:  What's **vi**

---

### Post by p_quarles on 2008-01-24
> **Bruce M. said:**
> So obviously the question is:  What's **vi**
It's an old UNIX text editor. The contemporary version, and the one that's included with Ubuntu, is called Vim (Vi iMproved). It can be intimidating at first, but once you get the hang of it, it becomes a very efficient editor.

---

### Post by Bruce M. on 2008-01-24
> **p_quarles said:**
> It's an old UNIX text editor. The contemporary version, and the one that's included with Ubuntu, is called Vim (Vi iMproved). It can be intimidating at first, but once you get the hang of it, it becomes a very efficient editor.

:popcorn: :lolflag: :)  OH! VIM is Vi, I know VIM.

I was *frightened* **and** *horrified* by it and just as quick deleted it.

Maybe someday, just not now.

---

### Post by nick_h on 2008-01-25
I just had a few thoughts about the CLI for beginners.

1. Unix is case sensitive.
2. To navigate to directories with spaces use quotes or the escape character.
3. Shell commands do not have an "are you sure?" enabled by default and can be very powerful (and destructive).

Take the rm command example:
```
rm *mp3
```
including an extra space by mistake would be unfortunate.
```
rm * mp3
```
especially with the -r option !

---

