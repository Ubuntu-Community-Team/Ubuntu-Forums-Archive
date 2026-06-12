---
title: "What do you think of the new FatELF?"
date: 2009-10-26
forum: The Cafe
---

### Post by handy on 2009-10-26
Ryan Gordon, (Icculus), coder extraordinair has come up with a universal binary system that could streamline the distribution of packages for different architectures, to the point of affecting how distros are packaged:

[I]**Overview:**

FatELF is a file format that embeds multiple ELF binaries for different architectures into one file. This is the Linux equivalent of what Mac OS X calls "Universal Binaries."

The format is very simple: it adds some accounting info at the start of the file, and then appends all the ELF binaries after it, adding padding for alignment. The end of the file isn't touched, so you can still do things like self-extracting .zip files for multiple architectures with FatELF.

FatELF lets you pack binaries into one file, seperated by OS ABI, OS ABI version, byte order and word size, and most importantly, CPU architecture.

Work is focused on GNU/Linux, but this could be applied to most modern Unix systems: the BSDs, Solaris, etc.[/I]

[http://icculus.org/fatelf/](http://icculus.org/fatelf/)
_________________


*(**P.S.** There is another thread here in the forums that incorrectly presents FatELF as being a method of running Mac OS X software on Linux!  & has a horribly incorrect thread title. So I started this thread in an effort to prevent this important (imho) topic from being lost due to this unfortunate misrepresentation.)*

---

### Post by Xbehave on 2009-10-26
pretty pointless:
[LIST]
[*]Apps would have to abandon package management systems to use it (a fatpkg would be useful, but wouldn't need this)*
[*]It's only real use is legacy binaries (apart from different arches it also supports packaging compiles against multiple APIs (e.g 2.6.1 and 2.6.31)
[*]AFAIK you still need to compile it for every arch & API seperatly this is just a way to stick them together (Why not just use a compressed file containing mutliple binaries and a smart installer script (gets the same effect but without needing a modified kernel,glib,etc)*
[/LIST]
I mean it does have some potential uses (a distro CD that boots on any arch) but for your average user/distro this isn't anything to get excited about.

*have opera opensourced their linux build system because it not only compiles against multiple APIs but also packages the binaries up with the relevant dependencies (as in dependency resolution not just static), the end result is that when its combined with useragent sniffing they give users a link to the correct managed package, which is much more useful than this.

---

### Post by hoppipolla on 2009-10-26
Interesting, but yeah would it be well integrated enough with current package systems? A good move though, smooths out one of the current problems with Linux a bit :)

---

### Post by ad_267 on 2009-10-26
I think that distros won't move away from the current packaging methods, but it's better suited to distributing closed source applications. In this situation FatELF could provide a much easier way for companies to distribute closed source software and for users to install it. They don't require separate downloads for different architectures, and the installation will be a lot simpler.

---

### Post by koshatnik on 2009-10-26
And there was me thinking this was a thread about Ronnie James Dio.

---

### Post by Regenweald on 2009-10-26
I don't like the idea of downloading larger packages if this impacts on size. Linux distros are already so dependent on connectivity, I prefer to support better compression technology and more efficient package transfer.

This would be an advantage if we followed the 'scour the internet and find your software model' in which case rpm, deb, bsd users could download a singilar package and not worry about it, but considering that all distros package specifically, it seems like unnecessary effort. If all FOSS distros pointed to a singular global repo, this could be of use, but again for those with thin bandwith, this format could be a pain.

---

### Post by MaxIBoy on 2009-10-26
Won't work for distros, but it's great for vendors and the like. I hope this succeeds.

---

### Post by gnomeuser on 2009-10-26
It would fix an important bug, namely "which architecture to download", we could do one DVD that supports everything... in theory at least.

Is it worth the cost, I don't know. Binary sized would increase proportionally with the number of archs the distro supports. This means more IO which is a major bottleneck, it also mean larger storage requirements.

Perhaps one could do the LiveDVD like this then have a stripper to remove unneeded arch from the binaries after install..

I am intriqued by the idea, I think it would make testing Linux much simpler for new users by removing the instant worry of picking the right download.

---

### Post by handy on 2009-10-26
Apparently a simple command will strip what is not desired.

Also, the ability to make a portable LiveCD/CF that will run on anything will appeal to some.

---

