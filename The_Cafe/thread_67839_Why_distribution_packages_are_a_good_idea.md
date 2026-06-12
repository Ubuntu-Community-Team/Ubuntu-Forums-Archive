---
title: "Why distribution packages are a good idea"
date: 2005-09-21
forum: The Cafe
---

### Post by Wolki on 2005-09-21
Take a look here: [http://www.viruslist.com/en/weblog?calendar=2005-09](http://www.viruslist.com/en/weblog?calendar=2005-09)

There's some inaccuracies in the article, but it's still clear that you should not trust everything on the net, even if it seems to come from a source you would trust. With linux becoming more popular, it'll be even more important to have trustworthy distributions; everything else is a security risk.

---

### Post by papangul on 2005-09-21
> Yet another example of why you should have an up to date antivirus solution, and scan EVERYTHING you download, without exception.  
i had an impression that only linux mail servers need to have anti-virus solutions. Do I need to install anti-virus programs for Ubuntu also ??!!

---

### Post by Wolki on 2005-09-21
[QUOTE=papangul]i had an impression that only linux mail servers need to have anti-virus solutions. Do I need to install anti-virus programs for Ubuntu also ??!![/QUOTE]

Do you install software from outside the ubuntu repositories? If so, it could be a good idea, but probably not necessary. There is a very, very small number of linux viruses, and they are rare. Making software "easier" to install (all the distribution-independent package things) will of course make installing (and thus distribution of) malware easier. Being aware of security issues is important and will become more important as   linux becomes popular.

---

### Post by Kvark on 2005-09-21
Thats a mirror that was infected. Always check the download against an MD5 checksum on the official site or in worst case on another mirror.

An Ubuntu or backport mirror could be infected just as well as a Mozilla mirror. Then a lot of people would download the new infected version quickly thanks to the update notifier. But synaptic seems to automatically check against MD5 sums. If thats the case then both the download mirror and the server with the checksums would need to be compromised.

I think there will eventually be a need for download programs that have a list of checksum servers that it checks each download against to see if it is on any blacklists or whitelists. Ubuntu, Mepis and the other distros as well as secuirty companies could probably have checksum servers with huge black/white lists. That way it wouldn't be enough to infect a mirror. There'd a whole load of independant servers to infect before you could get anyone to download the virus or troyan.

---

### Post by papangul on 2005-09-21
[QUOTE=Wolki]Do you install software from outside the ubuntu repositories? [/QUOTE]
I followed instructions in ubuntuguide.org to add many repositories in my sources.list file, most probably some of them are not official ubuntu repositories. Frankly, I am pissed off by this repository stuff.

---

### Post by Wolki on 2005-09-21
[QUOTE=papangul]I followed instructions in ubuntuguide.org to add many repositories in my sources.list file, most probably some of them are not official ubuntu repositories. Frankly, I am pissed off by this repository stuff.[/QUOTE]

Ubuntuguide recommends only official + backports repos.  You can consider them safe (especially now that backports is becoming official). The problem are random .debs or source code found on the internet.

Repositories mean that ubuntu guarantees the content is relatively safe (may  contain bugs of course ^^;; and a corrupted mirror like Kvark said could still be possible). Without repositories you lose that safety.

---

### Post by poofyhairguy on 2005-09-21
[QUOTE=papangul] Frankly, I am pissed off by this repository stuff.[/QUOTE]

Don't hold back. Tell us your true feelings!

---

### Post by az on 2005-09-21
[QUOTE=papangul]I followed instructions in ubuntuguide.org to add many repositories in my sources.list file, most probably some of them are not official ubuntu repositories. Frankly, I am pissed off by this repository stuff.[/QUOTE]


So what do you want?  To go to a homepage for an application and install it from there?  You can do that.  You will just have to compile it yourself, using your system's own libraries.  You see, since thre is so much choice around, there are many ways to do things.  The person who wrote the application cannot possibly know what your computer runs or what it is going to run.  And frankly, she shouldn't.  

It is far easier for developers to interface at the souce code level than at the binary level.  In other operating systems, there is only one way to do things, so one one kind of binary packages is needed.

Now, this is an oversimplification of the issue, but it boils down to you getting *more* choice at the end of the day.

---

### Post by poofyhairguy on 2005-09-21
[QUOTE=azz]So what do you want?  To go to a homepage for an application and install it from there?  You can do that.  You will just have to compile it yourself, using your system's own libraries.  [/QUOTE]

The universal installer for Linux is a tar file.

---

### Post by papangul on 2005-09-21
There was a misunderstanding here as I didn't elaborate, I meant I was pissed off (due to fear of malware being installed from "**unofficial** repository") when I added additional repositories following ubuntuguide.org. Ideally I shouldn't need to mess with the sources.list file except before dist-upgrading.

---

### Post by zenwhen on 2005-09-22
[QUOTE=papangul]There was a misunderstanding here as I didn't elaborate, I meant I was pissed off (due to fear of malware being installed from "**unofficial** repository") when I added additional repositories following ubuntuguide.org. Ideally I shouldn't need to mess with the sources.list file except before dist-upgrading.[/QUOTE]


Ideally, there wouldn't be any restrictive licenses in this world that keep the software in those repos out of our main distribution.

---

### Post by stimpack on 2005-09-22
Hopefully finer grained security such as SElinux will help the silly situation we are in at the moment with the archaic system of only installing from trusted sources, sounds exactly like Windows to me.

Any program I install should NOT be able to affect anything apart from itself, let alone require root that is just crazy. And even with user level access trashing my home dir is not acceptable either, much much finer control needed me thinks.

---

### Post by papangul on 2005-09-22
[QUOTE=stimpack]Hopefully finer grained security such as SElinux will help the silly situation we are in at the moment with the archaic system of only installing from trusted sources, sounds exactly like Windows to me.

Any program I install should NOT be able to affect anything apart from itself, let alone require root that is just crazy. And even with user level access trashing my home dir is not acceptable either, much much finer control needed me thinks.[/QUOTE]
 That sounds great!

---

### Post by Wolki on 2005-09-22
[QUOTE=stimpack]Hopefully finer grained security such as SElinux will help the silly situation we are in at the moment with the archaic system of only installing from trusted sources, sounds exactly like Windows to me.

Any program I install should NOT be able to affect anything apart from itself, let alone require root that is just crazy. And even with user level access trashing my home dir is not acceptable either, much much finer control needed me thinks.[/QUOTE]

I thought about this yesterday, too. You can already run programs as a different user,  and that user can have the rights to write nowhere. 
But it's still not a perfect solution. Giving out text editors that cannot edit files will not go over well. Or take music players; people will complain if a player doesn't support tag editing. You could have an additional system dialog asking for confirmation each time you edit a file, which will seem very tedious to users; or give it write acess to your entire music library, at which point it can delete them all.
The problem is that the only easy way to manage security risks would be a tcpa-like solution, and we certainly don't want that. But we can't force users to micromanage file access rights; they'd just run as root the whole time because it'll be more "user-freindly".  :?

---

