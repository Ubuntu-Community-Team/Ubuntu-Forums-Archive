---
title: "Teaching people the basics of linux"
date: 2011-09-29
forum: The Cafe
---

### Post by nikhilbhardwaj on 2011-09-29
I'm pursuing a masters course at my university in computer science, we don't have any linux/unix machines in our university. It's all Windows, some of my classmates have asked me to introduce them to linux,
How would you suggest that I approach this?

I don't need to teach people how to use the GUI, that they can figure out themselves. Is their some online reference that I can stick to so as to teach them the basics of the shell and then shell scripting.

Feel free to post suggestions and ideas.

---

### Post by haqking on 2011-09-29
> **nikhilbhardwaj said:**
> I'm pursuing a masters course at my university in computer science, we don't have any linux/unix machines in our university. It's all Windows, some of my classmates have asked me to introduce them to linux,
How would you suggest that I approach this?

I don't need to teach people how to use the GUI, that they can figure out themselves. Is their some online reference that I can stick to so as to teach them the basics of the shell and then shell scripting.

Feel free to post suggestions and ideas.

[www.linuxcommand.org](www.linuxcommand.org)

---

### Post by nikhilbhardwaj on 2011-09-29
+1
I've learnt a lot from there,
more similar sites??

---

### Post by haqking on 2011-09-29
> **nikhilbhardwaj said:**
> +1
I've learnt a lot from there,
more similar sites??

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.shell-fu.org/](http://www.shell-fu.org/)
[http://www.commandlinefu.com/commands/browse](http://www.commandlinefu.com/commands/browse)
[http://www.freesoftwaremagazine.com/articles/command_line_intro#](http://www.freesoftwaremagazine.com/articles/command_line_intro#)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://babbloo.com/index/index.php/edusiteoperating-system-/461-materials-science%20](http://babbloo.com/index/index.php/edusiteoperating-system-/461-materials-science%20)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://linux.die.net/Linux-CLI/](http://linux.die.net/Linux-CLI/)
[http://www.howtoforge.com/useful_linux_command](http://www.howtoforge.com/useful_linux_command)

ad nauseum ad infinitum

the best place is the shell itself along with man, info, apropos and help.

enjoy

---

### Post by Lars Noodén on 2011-09-29
I would recommend anything that gets them hands on with Ubuntu.  Actually I would not recommend plain Ubuntu, but instead users find Kubuntu or Xubuntu much nicer.  When I had students pick their distros, they settled on Xubuntu.

---

### Post by HermanAB on 2011-09-29
Hold an 'Install Fest'.

Tell people to bring any old computer and help them install Linux on it.

---

### Post by rjbl on 2011-09-29
> **nikhilbhardwaj said:**
> I'm pursuing a masters course at my university in computer science, we don't have any linux/unix machines in our university. It's all Windows, some of my classmates have asked me to introduce them to linux,
How would you suggest that I approach this?

I don't need to teach people how to use the GUI, that they can figure out themselves. Is their some online reference that I can stick to so as to teach them the basics of the shell and then shell scripting.

Feel free to post suggestions and ideas.

I would guess that all of your classmates must have studied UNIX as part of the their first year studies for B.Sc - Computer Science. 'NIX is, after all, *the* definitive multi-process, multi-user computer OS and, in all its flavours including GNU/Linux, it is by far the most widely deployed computer operating system - current estimates are that about 80 - 90% of all the global Internet's resources are served up by 'NIX, and today this usually means GNU/Linux or FreeBSD because all the big proprietary UNIX vendors gave up work on their brands by about 2005. Your classmates should be, no doubt are, pretty familiar with UNIX and GNU/Linux is not significantly different.

It could be that you would best help your classmates along by introducing them to the GNU/Linux world's most innovatory concept: the 'Linux Distribution' - the idea of a complete, supported, configured and integrated functional computing package. A good and thought-provoking presentation could, I guess, be based upon comparing and constrasting, say, Fedora (long the epitome of the very complete software engineers environment); Ubuntu (an extra-ordinarily successful 'everyman's personal computing system') and, say, SUse (which has a very distinguished history as a business / corporate desk top environment). You might wish to examine how each system is developed, managed and distributed into its target user-groups.

Just a few thoughts - hope they are relevant and, perhaps, useful.

Cheers
rjbl

---

### Post by drawkcab on 2011-09-29
Besides focusing on basics, make sure that you address the issue of why anyone should concern themselves with gnu/linux in the first place?  

Also, years ago, I think I would have benefited from having someone walk me through an overview of the major distros, desktop environments in an attempt to explain that, although confusing at first, gnu/linux offers a lot of choice in terms of selecting/customizing an OS for a particular purpose or for specific hardware.

---

### Post by Lars Noodén on 2011-09-29
> **HermanAB said:**
> Hold an 'Install Fest'.

Tell people to bring any old computer and help them install Linux on it.

+1

*Any activity* at all that gets them hands-on experience with Linux is the best.  Most of the time I find that people only need a nudge to dispel the FUD about it being hard to use or lacking apps.  Once they can use it themselves, they see how easy to use it is and how many awesome apps there are.  Also, the desktop environment is something we take for granted but blows away Windows.

---

### Post by BBQdave on 2011-09-29
+1

And Debian would be another distro, to show the function of a GNU/Linux community.

---

### Post by ninjaaron on 2011-09-29
If they are CS majors, be sure to introduce them to shell scripts.  There are few things that make my computer more useful than the ability to script things that I find myself doing more than once, such as scripts to automate media encoding, scripts to add all my tweaks to a fresh install, scripts for time-triggered events (such as morning alarms or system maintanence), scripts to automatically generate html image galleries from an image folder for easy browsing, scripts for creating thumbnails for images,  scripts to scan websites and download the correct content, scripts for custom actions on keybindings, scripts for making new directory structures based on file info...  scripts for everything.  I basically redesigned the UI for my netvertible using existing elements with scripts.

I'm continually amazed at how much I can get done with a very basic knowledge of bash and a text editor.

---

### Post by nikhilbhardwaj on 2011-10-04
Someone has a list of simple shell scripts that I can teach one by one,
each one implementing a new concept.

---

### Post by Lars Noodén on 2011-10-04
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)

[http://www.faqs.org/docs/air/tsshell.html](http://www.faqs.org/docs/air/tsshell.html)

---

### Post by speedwell68 on 2011-10-04
If they are computer science students I would suggest to them a current mainstream distro, then have the install fest and then let them get on with it helping them out when they get stuck.

I studied computer science in the early 90s and had some experience with a Unix Zilog Mini, so when I picked up Linux about a decade layer I had a little bit of a clue.  But I taught myself.

---

### Post by Claus7 on 2011-10-04
Hello,

I would like to say, that before teaching people the basics of linux, it is nice to inform them that there are other options. From my humble experience there are two things that are putting off users of other OS to follow linux:

1) they do not trust something free and not well known (for them)
2) they think it is for geeks

Since (I learned it from posts here in the forums) some laptop manufacturers say that the warranty won't be valid if you install another OS, you can understand that this does not help to teach something, if you do not provide even the basic tools! 

About 1&2 in order to overcome them we have to point out that there is much more security, no defragment or antivirus updates, free of charge, less time for booting (for some is important) less resources taken while ONLY the OS in use, ability to browse the internet as in every other OS, new and improving and stable environment, no need for formatting the disk every now and then and last but not least: there is compatibility with most of other OS's applications with layers such as wine, which are working (most of them) really nice, without eating a lot of ram and cpu.

Linux requires time and for some might not be ideal. For simple things is doing the job pretty nicely. If they want to invest some time to learn something new, this time might prove rewarding. Yet, teaching: starts from the very basics I think, and shows to other people what we are talking about, and how we can make other people understand, taking into account their prior knowledge on the subject. Also terminal is part of linux and we should not hide its powers.

Regards!

---

### Post by JDShu on 2011-10-04
I've been quite amazed that there are CS students who can't use shell clients. It's pretty much a required skill for any serious job. The most important skill is to navigate around the system. Then make sure they can use a text editor like nano or pico.

---

### Post by alphacrucis2 on 2011-10-04
The first thing is to explain how the Linux file system works. OMG where's my C drive gone!

---

### Post by Dragonbite on 2011-10-05
When I started with Linux one of the things that confused me was the difference in terminology (~ or /home rather than "My Documents", having to "mount" a drive before using it) as well as equivalent applications ("how do I do xyz in Linux?")

---

### Post by tulipán on 2011-11-03
+1 for basic unix skills. i arrived here through a thorough unix training a looooong time ago: i don't remember the commands, but i remember the philosophy. also using OOO and firefox and all things free will charm them in the end :)

---

