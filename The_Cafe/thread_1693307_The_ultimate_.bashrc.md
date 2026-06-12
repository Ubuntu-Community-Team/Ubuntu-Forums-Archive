---
title: "The ultimate .bashrc"
date: 2011-02-22
forum: The Cafe
---

### Post by Quadunit404 on 2011-02-22
[Mentlegen, BEHOLD!]("http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746") The mother of all .bashrcs!

What this does is add a TON of useful aliases and functions to the terminal, which includes:

- Currency conversion via Google
- "Down for everyone or just me?" functionality
- Translation via Google
- DVD/CD ripping
- Video conversion
- .deb extraction/repackaging
- Media metadata info
- Various computer info
- Copy/paste from the command line
- Bookmarking directories
- sudo for an entire line
- Ripping audio from video
- Backing up your packages and repositories to a .deb
- And much more!

The best part is you don't have to use the whole 330-something kilo file; if you want to you can just rip whatever functions and aliases you want out of the .bashrc and put it in your own! And that is probably a good thing because with a filesize THAT huge it's gonna take a while to load the terminal.

Sorry if this has been presented to the community here before but I don't feel like searching right now.

---

### Post by inameiname on 2011-05-18
Thanks for the mention of my Ultimate Bashrc. I am glad there are others who enjoy it as much as I do.

On a personal note, I actually use the entire bashrc, as well as several custom commands, and do not find it slow at all. So while you are welcome to cut and paste your favorites from it, it is possible to keep the whole thing. Really it all depends on how well it runs on your computer.

FYI, I finally updated it after a few months, with several more handy little aliases and functions: [http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746&PHPSESSID=c94a476ffdf073a070c8c6df3a872364](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746&PHPSESSID=c94a476ffdf073a070c8c6df3a872364).

---

### Post by Toz on 2011-05-18
niiiiiiiiice :cool:

---

### Post by Quadunit404 on 2011-05-18
> **inameiname said:**
> Thanks for the mention of my Ultimate Bashrc. I am glad there are others who enjoy it as much as I do.

You're welcome :)

> **inameiname said:**
> On a personal note, I actually use the entire bashrc, as well as several custom commands, and do not find it slow at all. So while you are welcome to cut and paste your favorites from it, it is possible to keep the whole thing. Really it all depends on how well it runs on your computer.

When I first found out about this .bashrc I was on a rather low-end PC (Acer Aspire 4530-6823) and by then it was pretty much falling apart despite being only a year old It could barely handle running a 90kb file in the Terminal so I ended up having to rip parts from the .bashrc and merge them into my own. Fortunately I don't use that PC anymore and have a more powerful PC... but when I migrated everything from my old one to this new one I didn't update my own .bashrc to use all the extra functions and aliases.

> **inameiname said:**
> FYI, I finally updated it after a few months, with several more handy little aliases and functions: [http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746&PHPSESSID=c94a476ffdf073a070c8c6df3a872364](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746&PHPSESSID=c94a476ffdf073a070c8c6df3a872364).

Thanks, I'll be sure to check that out.

---

### Post by Simian Man on 2011-05-18
But a real command-line fan should be using zsh anyway :).

---

### Post by ilovelinux33467 on 2011-05-19
> **simian man said:**
> but a real command-line fan should be using zsh anyway :).

+1

---

### Post by Quadunit404 on 2011-05-19
> **Simian Man said:**
> But a real command-line fan should be using zsh anyway :).

I haven't used zsh before. I guess I'll try it out on my testing VM after reinstalling Ubuntu on it since I hosed it last night :lolflag:

---

### Post by nothingspecial on 2011-05-19
> **Simian Man said:**
> But a real command-line fan should be using zsh anyway :).

Bet you use vi.......

I run a couple of boxes cli only and use nano and ........ bash.......

oh yeah, I use alpine not mutt as well..........

......... so sue me .... or don't be such a snob :)

---

### Post by Telengard C64 on 2011-05-19
> **Simian Man said:**
> But a real command-line fan should be using zsh anyway :).

At first I wasn't very impressed. "It's just Bash with [spell checking](http://zsh.sourceforge.net/Guide/zshguide06.html#l162)", I thought. Then I noticed these features:

[list]
[*][recursive globbing](http://zsh.sourceforge.net/Guide/zshguide03.html#l59)
[*][associative arrays](http://zsh.sourceforge.net/Guide/zshguide05.html#l122)
[*][floating point](http://zsh.sourceforge.net/Guide/zshguide05.html#l130) and [scientific notation](http://zsh.sourceforge.net/Guide/zshguide03.html)
[/list]

Could be interesting  :)

---

### Post by Simian Man on 2011-05-20
> **nothingspecial said:**
> Bet you use vi.......

I run a couple of boxes cli only and use nano and ........ bash.......

oh yeah, I use alpine not mutt as well..........

......... so sue me .... or don't be such a snob :)

I'm not a snob.  If someone wnats to use a screwdriver instead of a drill, I won't say anything.  However, if that person shows others how to improve the screwdriver by duct-taping it onto a motor, then I will just point out that a drill might be better :).

---

### Post by inameiname on 2011-05-21
To Quadunit404:

Geez. One year old and your Acer Aspire was already falling apart? I would complain about that. Hehe. Anyway, yeah, some older end ones probably need a smaller file. Although, I currently run this bashrc on three computers, a few year old laptop (my main), a custom-built desktop from about 8 years ago, and a really old one in a room that was designed for Windows 98, without issues. 

To Simian Man:

Thanks for the input about Zsh. There was a WebUp8 article about my bashrc and Zsh was also mentioned there. I will be honest and say I do not really know much about it. Its just I started this a few years back when I first discovered the marvels of Linux, and have just kept it up every since. 

I definitely use the command line for nearly everything, so I should look into it. I have only ever used the gnome-terminal that was built into my Linux distro. Do you know off hand if much of the stuff in bash in this bashrc would work and/or run the same using Zsh?


Anyway, I love being educated. The more learned, the more shared. :)


UPDATE:

I found a couple little threads about zsh vs bash and the basics between the two:

[https://bbs.archlinux.org/viewtopic.php?id=68121](https://bbs.archlinux.org/viewtopic.php?id=68121)
[http://serverfault.com/questions/4993/unique-features-of-bash-compared-to-zsh](http://serverfault.com/questions/4993/unique-features-of-bash-compared-to-zsh)

What's funny with the first article is it mentioned completions as being the big worthwhile thing zsh has over bash. I say its funny because if you go to: /etc/bash_completion, you will find tons of built-in ones for bash. I have never had issues with completions in a bash shell. Maybe this is a new thing added since this thread. 

Regardless, it sounds like bash has most of the features that zsh. It might have not in the past, but bash has been growing. And while zsh might have more, most aren't necessary for most users. Just my two cents, of course.

---

### Post by Simian Man on 2011-05-22
> **inameiname said:**
> I definitely use the command line for nearly everything, so I should look into it. I have only ever used the gnome-terminal that was built into my Linux distro. Do you know off hand if much of the stuff in bash in this bashrc would work and/or run the same using Zsh?
Some of the stuff like prompt strings would have to be changed, but most of the functions should work in both.  In fact most of them should just be moved to shell scripts in ~/bin.  That would ensure they work in any shell the user wants, and prevent them from having to be parsed every time you open a terminal.

> **inameiname said:**
> Regardless, it sounds like bash has most of the features that zsh. It might have not in the past, but bash has been growing. And while zsh might have more, most aren't necessary for most users. Just my two cents, of course.
While bash has added some completion features, they aren't on by default, don't support as many programs out of the box, and doesn't work nearly as well.  Zsh lets you navigate through options when more than one matches, and gives nice descriptions of what options do etc.  Zsh frequently surprises me with how smart it is.  It recognizes exuberant ctags files, so I can type "vi -t f[TAB]" and get a list of all functions I have.  It reads source control metadata so I can type "hg add [TAB]" and it will give me a list of files not yet added to my Mercurial repository.  It just does SO MUCH for you that bash doesn't.  It also has some nice features, and fewer gotchas than bash when doing scripting.  Bash has closed the gap somewhat since I started using zsh, but it's still not even close IMHO.

Give it a try for a week and see if you still think bash is just as good :).

---

### Post by nothingspecial on 2011-05-22
> **Simian Man said:**
> 

Give it a try for a week and see if you still think bash is just as good :).

I did. I prefer bash. That may be a limitation on my part, but I prefer a screwdriver :P

---

### Post by Quadunit404 on 2011-05-22
> **inameiname said:**
> To Quadunit404:

Geez. One year old and your Acer Aspire was already falling apart? I would complain about that. Hehe. Anyway, yeah, some older end ones probably need a smaller file. Although, I currently run this bashrc on three computers, a few year old laptop (my main), a custom-built desktop from about 8 years ago, and a really old one in a room that was designed for Windows 98, without issues.

Yes, sad isn't it? Let's just say I abused it a lot :P (fortunately this new laptop I have is capable of handling FAR more punishment than my last one. I remember trying to crash Windows on it by detonating 30 nukes in Garry's Mod at once, but all what I got was "hl2.exe has stopped responding" instead. If I tried that on the Acer I would have seen "A problem has been detected on your computer and Windows has been shut down to prevent damage" or something like that. Hell, one of the USB ports on it doesn't work anymore :lol:) I don't think it would have liked the whole bashrc either, considering how long it took to load the Terminal with a 30KB .bashrc :lolflag:

And wow. You must have been incredibly lucky choosing PCs if those old things handle the whole thing perfectly. This laptop I'm using right now is the most responsive PC I've had since Windows 95 tbh.

---

### Post by toupeiro on 2011-05-22
> **Simian Man said:**
> 
Give it a try for a week and see if you still think bash is just as good :).
I've tried zsh.  Its ok, but certainly not the end-all of shells.  

tcsh with vi integration is what I always go back to.  It can interpret direct and variants of bsh and csh shells, can do foreground/background control, and my tcshrc fills some of the other little things I did like in zsh just fine.

---

### Post by inameiname on 2011-05-22
[Simian Man]("http://ubuntuforums.org/member.php?u=481510"):

Thanks again for all the info about Zsh. I will definitely inquire further about it. It is definitely one of the many things I would love to learn more about regarding Linux. I have only been involved with Linux for about two years, so I still have lots to learn. Not just that, but it can be fun.

Quadunit404:

Apparently so. My job is actually working with computers, and I have created my own remastered Ubuntu distro and put it on tons of computers over the past couple of years, all with the same bits and pieces, including this Bashrc, and none have given me trouble about it. Perhaps my ease with it relates to the particular packages I install/uninstall.

---

### Post by COKEDUDE on 2012-06-01
Thx for sharing this.

---

### Post by KiwiNZ on 2012-06-01
Back to sleep

---

