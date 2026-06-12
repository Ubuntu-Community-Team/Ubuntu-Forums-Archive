---
title: "Niggles with Linux/Ubuntu"
date: 2006-06-05
forum: The Cafe
---

### Post by evolvedlight on 2006-06-05
1) Installation of programmes outside of the repositories.
Its brilliant **if** an application is inside of a reposity, but:
**How is someone supposed to magically know that you need to ./configure, make, install, whatever?**
Would it be possible for ubuntu to recognise the structure that allows you to make, configure, etc and ask you if you do want to make/ cogure automagically? It could then resolve dependancies and then in general solve alot of headaches. Perhaps, even make a .deb file?

2) Permissions. 
Take, for example, changing the permissions of /var/www/ so that you can write into it. I know now, that you need to do chmod 777 /var/www/.

But how does X user magically know that? Could you have an option somewhere to "change permissions". One could then allow write access, then it asks you for the admin password. 

:-) I do like Dapper+XGL - very nice :grin:

---

### Post by Kindred on 2006-06-05
You don't need to magically know.. you look it up, that's how you learn.  I'm assuming you looked it up, others can too.

---

### Post by evolvedlight on 2006-06-05
What if you did not have internet access? I know many people do not. I am not saying it is "HUGE PROBLEM", but that doing many, many things in Ubuntu would get easier. I know that 99% of users on these forums will be technologically very knowledgable... but over a wider group, as in the real world, the percentage of people that will even just be able to accuratly google their problem is much lower. 

My point is that Ubuntu, while accessible for those who know computers well and are prepared to learn, is not as accessible for those who don't. Lets take a parent

Downloading from sourceforge as an example
Windows: Browse to it, find the exe, download it, run it, it crashes.

Linux: Browse to it: find the .tar.gz, download it, double click it, it opens a list of files. Looks in README. It does'nt say how to do it. Looks up on internet. 5 mins later, thinks that he knows how to do it, finds the terminal, goes back on the internet to find out how to change directory, changes directory, runs ./configure, it needs some more files, goes to synaptic to get them, gets them, back and ./configures it again. And I can't go on any further. Because I have never got this far. And because your getting bored

How about this as my alternative:
Linux: Goes to it, downloads .tar.gz, Ubuntu says "Do you want to install that?" Installs it automagically. Puts shortcuts where shortcuts go.

Its not a problem, per say, but it could be improved

---

### Post by Hanj on 2006-06-05
1) 90% of all source packages come with an INSTALL file which tells the user to do *compile && make && sudo make install*. A user who downloads source code packages is probably competent enough to find out how to install them. If you can't even do that you're better off using only Synaptic.

2) Right click on the file in Nautilus, select "Properties" and click on Permissions.

---

### Post by evolvedlight on 2006-06-05
1) If it comes with them, can't we make Ubuntu see that file and ask you if you want ubuntu to do the magic? 

2) "You are not the owner, so you cannot change these permissions"

---

### Post by xtacocorex on 2006-06-05
There are programs in the repos that will take a source package and compile them for you, I just forgot their names. 

I did download one yesterday, even though I prefer the CLI method.

---

### Post by Hanj on 2006-06-06
There's [Kompile]("http://www.kde-apps.org/content/show.php?content=30223") for KDE. Don't know if any Gnome equivalent exists.

---

### Post by frodon on 2006-06-06
If you want something automated look for .deb files and not sources, the install of .deb files is easy and it's made for that (.deb are precompiled packages for debian distributions). It would be difficult to automate the install from source because there a lot of compilation options and dependencies to solve before performing a compilation from source therefore this process would really often fail.

As for internet connections, like each OS it's always harder to have a functionnal computer without internet connection because there're always new codecs versions, new software versions and it's difficult to be up to date without internet connection.

However some people are working on an ubuntu addon CD which includes a lot of packages you may need, so in your case it seems to be what you need, have a look here for more informations : 
[http://ubuntuforums.org/showthread.php?t=183933](http://ubuntuforums.org/showthread.php?t=183933)

---

### Post by givré on 2006-06-06
[QUOTE=evolvedlight]
2) "You are not the owner, so you cannot change these permissions"[/QUOTE]gksu nautilus

but i think it's not that hard to pass 10 minute reading documentation to know how linux is working (because it is simply that), and after you will know it forever.

I guess that the first time you use windows you understand nothing, but you learned.
Because linux is not like windows (and i hope it will never be) you will have to learn things an other time.

---

### Post by givré on 2006-06-06
[QUOTE=evolvedlight]
2) Permissions. 
Take, for example, changing the permissions of /var/www/ so that you can write into it. I know now, that you need to do chmod 777 /var/www/.[/QUOTE]
Why would you like to do that, if you want to write in a file own by root, just run it as root```
sudo gedit /var/www/the_file_you want
```it is not that hard

---

### Post by evolvedlight on 2006-06-06
That looks usefullish - but this is not about what **I need**. This is about what someone just being introduced to linux and wanting an application outside of the repositories needs. Oh well. Silly argument really.

---

### Post by givré on 2006-06-06
[QUOTE=evolvedlight]
How about this as my alternative:
Linux: Goes to it, downloads .tar.gz, Ubuntu says "Do you want to install that?" Installs it automagically. Puts shortcuts where shortcuts go.
[/QUOTE]
That's not an installation that's a compilation. That's definitly different. You can't expected to a compilation to go as well as an installation, that's why it is useful to do it via a terminal.
You can install program (binary already compile for your system, not source, like the .exe if you want), that's what we call .deb, or .rpm for some other distribuation. More and more project diffuse source but also package already compile for various distribution.

EDIT: To be really clear, a .deb or a .rpm is equivalent to a setup.exe, but there is no equivalent to a .tar.gz in windows (you never compile stuff)

---

### Post by egon spengler on 2006-06-06
[QUOTE=evolvedlight]What if you did not have internet access? I know many people do not. [/QUOTE]

If you don't have internet access how would you obtain this package you need to install? If a friend gives it to you then they could explain how to use it, if you get it off a magazine then they would normally include instructions.

---

