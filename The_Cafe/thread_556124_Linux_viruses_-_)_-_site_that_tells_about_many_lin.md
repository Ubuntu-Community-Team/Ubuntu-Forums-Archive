---
title: "Linux viruses - :) - site that tells about many linux viruses"
date: 2007-09-20
forum: The Cafe
---

### Post by nowshining on 2007-09-20
[http://www.viruslist.com/en/viruslistfind.html?findWhere=011&findTxt=linux](http://www.viruslist.com/en/viruslistfind.html?findWhere=011&findTxt=linux)


Phrase to find: "linux"
Found: 1269

:)

---

### Post by Gremlinzzz on 2007-09-20
Virus Protection With AVG Antivirus On Ubuntu Feisty Fawn

Version 1.0
Author: Falko Timme <ft [at] falkotimme [dot] com>
Last edited 09/07/2007

This tutorial shows how you can install and use AVG Antivirus on an Ubuntu Feisty Fawn desktop. Although there aren't many Linux viruses out there, this can be useful if you often exchange files with Windows users - it can help you to not pass on any Windows viruses (that don't do any harm to Linux systems) to Windows users. AVG Antivirus for Linux is free for private and non-commercial use. 
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)

---

### Post by misfitpierce on 2007-09-20
None of these are widespread around the net. They are network shared locally. I have never seen any of these and noone has any reason to spread any of these lol

---

### Post by ~LoKe on 2007-09-20
You probably have to install them manually using sudo. =/

---

### Post by reyfer on 2007-09-20
All those are not necessarily linux viruses, but viruses with "linux" on their names. And did you noticed that almost all of them say "No description available"?

---

### Post by energiya on 2007-09-21
> **~LoKe said:**
> You probably have to install them manually using sudo. =/

One of the reasons I like linux.

---

### Post by the_darkside_986 on 2007-09-21
I did a search with the option of finding only those that have descriptions, and I got 31 results. 

I wouldn't waste my CPU time on antivirus software anyway and I try to keep up with all the latest updates with the Ubuntu update notification program. 

The only concern would be the proftpd I set up so I could put files on my machine remotely (using a diff. ftp user account in /var/ftp, of course). But I set the permission level to 775 so that anyone who gets my guest account username and password won't be able to set the permissions to be executable. Also, the shell for that user is set to /dev/null. I guess I'm safe enough.

---

### Post by niceguy123 on 2007-09-21
Does running a windows application under wine endanger my system? 

The only one I'm running is Internet Explorer running using IEs4Linux that I use for web developing and browsing a few sites that don't run properly on Firefox or Opera.

One of these sites (on IE) has been causing a pop up notice calling on installing Java Virtual machine in order to work right. Should I (and if so how) go about installing that?

BTW - is  IEs4Linux really  Internet Explorer or is it something that looks and works like it?

---

### Post by NIT006.5 on 2007-09-21
I also personally don't see too much of a point in worrying about antivirus on Linux... although trying to explain this to our IT auditors (who know nothing but Windoze) is another story...

I wouldn't think there's any real danger in running programs through wine. Even if viruses could execute themselves through wine too, what would they be able to do? I'm no expert though...

---

### Post by the_darkside_986 on 2007-09-21
It would probably mess up your wine installation in a worst case scenario by tearing up some wine dlls, but most likely the virus would fail to execute. A lot of the viruses depend on obscure API calls that the Wine team might have overlooked and didn't implement.

What kind of website is this that wants Java? If you can browse the site without any difficulties without Java then there is no reason to install it. I've seen some idiot webpage designers use Java applets simply for the purpose of a simple button that changes colors when clicking it. Not javascript, but literally Java. I can only imagine how easy it might be exploit Java with malicious bytecodes that overflow the Java software stack and make their way into the code.

---

### Post by Bothered on 2007-09-21
> **niceguy123 said:**
> Does running a windows application under wine endanger my system? 

Potentially, yes. I've heard (largely rumour) of people having their home directories damaged by a virus in wine.

---

### Post by the_darkside_986 on 2007-09-21
Well, yeah, if your Wine variables are set in such a way that your /home/folder =My Documents then there could be trouble. So it would probably be better to set your My Documents folder to something in ~/.wine/ just to be safe. The viruses would probably only damage the files in such a way that they would exploit Windows using Win32 code, but you don't want corrupt files either way.

---

### Post by nowshining on 2007-09-21
it's not the viruses u should be concerned about it's rootkits - :( the most dangerous is at the kernel level however unlike windows just visiting a page will not or should not give you a rootkit nor a virus.

---

