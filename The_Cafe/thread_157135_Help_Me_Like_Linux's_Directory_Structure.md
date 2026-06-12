---
title: "Help Me Like Linux's Directory Structure"
date: 2006-04-08
forum: The Cafe
---

### Post by Lord2k on 2006-04-08
Hi. 

I seem to have a problem that I want to try to get off my back. Well, I've been WANTING to switch to Linux for good for a long time. I've installed Ubuntu several times in the last years. The thing is, I can't stand the directory structure. (/bin, /dev, etc) Why do I hate it? I really want to move away from Windows. But, that's the only thing that is holding me back. What can I do to alleviate this problem?

Thank you,

- Steve

---

### Post by helpme on 2006-04-08
[QUOTE=Lord2k]Hi. 

I seem to have a problem that I want to try to get off my back. Well, I've been WANTING to switch to Linux for good for a long time. I've installed Ubuntu several times in the last years. The thing is, I can't stand the directory structure. (/bin, /dev, etc) Why do I hate it? I really want to move away from Windows. But, that's the only thing that is holding me back. What can I do to alleviate this problem?

Thank you,

- Steve[/QUOTE]
Please tell me you aren't serious.
Please tell me you just tried to make a joke.

Thank you.

---

### Post by Lord2k on 2006-04-08
Why would I be joking about it? I like Linux in all other aspects but the structure is just bothering me. :\

---

### Post by PatrickMay16 on 2006-04-08
What exactly bothers you about the directory structure? How is it causing you problems?

---

### Post by dabear on 2006-04-08
Yeah, I agree that typing /media/hda1/ and things like that is somewahat longer etc. than d:\. I solved this by opening two nautilus windows, one on /media/ and one in my home dir, then both-buttons-click-dragging hda1 from /media to my home dir and selecting «make link here». You could then rename the link to d: , and you'll be able to to acces /media/hda1 through alt+f2 and typing in "d:".

Offcourse, you could do the same from the command line:
```

ln -s to_path from_path

```

---

### Post by John.Michael.Kane on 2006-04-08
From the looks of it you can't change it. so you have to love it or leave it. sorry.
[http://www.lowfatlinux.com/linux-directories.html](http://www.lowfatlinux.com/linux-directories.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by helpme on 2006-04-08
[QUOTE=Lord2k]Why would I be joking about it? [/QUOTE]
Because the filesystem layout is for all intends and purposes totally and absolutely irrelevant as you never interact with it?

Really, if I wasn't such a nice guy, I'd say you are simply trolling, but as I'm such a nice guy I'll give you the benefit of the doubt and wait if you'll be able to deliver something resembling a coherent argument.

---

### Post by briancurtin on 2006-04-08
i dont think linux is for you if the directory structure is that big of a problem.

---

### Post by Lord2k on 2006-04-08
> What exactly bothers you about the directory structure? How is it causing you problems?

It just feels overwhelming. I don't know.. maybe I'm not giving it enough time to sink in.

---

### Post by helpme on 2006-04-08
[QUOTE=Lord2k]It just feels overwhelming. I don't know.. maybe I'm not giving it enough time to sink in.[/QUOTE]
Again, as you don't interact with it, why should it bother you?

---

### Post by briancurtin on 2006-04-08
for me there was no transition or sink in time to understanding linux directory sturcture. one day i decided to completely drop windows and adopt linux. on day one i understood it and its all ive dealt with for about a year.

---

### Post by Lord2k on 2006-04-08
> Because the filesystem layout is for all intends and purposes totally and absolutely irrelevant as you never interact with it?

Really, if I wasn't such a nice guy, I'd say you are simply trolling, but as I'm such a nice guy I'll give you the benefit of the doubt and wait if you'll be able to deliver something resembling a coherent argument.

I didn't ask this with intent on trolling. It's just something that has been bothering me. I know it may sound like I am.. but I'm not.

---

### Post by helpme on 2006-04-08
[QUOTE=Lord2k]I didn't ask this with intent on trolling. It's just something that has been bothering me. I know it may sound like I am.. but I'm not.[/QUOTE]
Ok, I apologize then.

However, I'd still be interested to know why it bothers you. You really never interact with it.

And I'd also like to know if you think the filesystem layouts of other systems are better and if so, why.

---

### Post by Lord2k on 2006-04-08
Well, the main reason it bothers me is because it's not like Windows. I'm used to the way Windows file structure is handled. (/Windows for OS / system related files, /Program Files for applications, etc.)

Also, SD-Plissken, those links are helpful. They explain some things.

---

### Post by John.Michael.Kane on 2006-04-08
@Lord2k you have to give it time. moving from windows to any other OS is going to take time, and they all for the most part have some kind of learning curve. no one here i think would want you to feel overwhelmed. just take your time. the community is here to help as much as it can. don't be put off gnu/linux/ubuntu because of the file structure.

---

### Post by Lord2k on 2006-04-08
Thank you, Plissken. And, thank you all. I'm going to give it another shot. And, hopefully, It'll work better this time.

---

### Post by poofyhairguy on 2006-04-08
[QUOTE=Lord2k] What can I do to alleviate this problem?
[/QUOTE]

Look at it differently than Windows.

In Windows, I knew what almost every directory did and what it was. A large part of this is because I did not trust Windows and its programs (as often they would put important files in odd places).

But in Ubuntu I am more relaxed. I don't need to know it all, as I trust the system more. The only directories I care about are:

/home

/usr/bin/

/media


And I leave the rest alone. Unlike in Windows, I'm not punished for not knowing where everything is- it lets me put all the important stuff in my home folder.

---

### Post by MenZa on 2006-04-08
[QUOTE=Lord2k]It just feels overwhelming. I don't know.. maybe I'm not giving it enough time to sink in.[/QUOTE]

It felt weird for me the first month or two, but quickly got used to it. One day, in a few months, you'll look back and think "WTF? D:\?!".

..either that, or you're suffering from obsessive thoughts ;)

---

### Post by Kvark on 2006-04-08
[QUOTE=Lord2k]Well, the main reason it bothers me is because it's not like Windows. I'm used to the way Windows file structure is handled. (/Windows for OS / system related files, /Program Files for applications, etc.)

Also, SD-Plissken, those links are helpful. They explain some things.[/QUOTE]
If you want it to be like Windows then it is Windows you want. The whole point of switching from one thing to something else is to get something different.

Everything you need to know about the Linux directory structure during normal use is:
/home/yourname/ <-- All your files and settings are here.
Everywhere else <-- Stuff that there is no point in careing about.



For example most executables are in /usr/bin but you don't make a shortcut to "/usr/bin/gedit", you make a shortcut to "gedit" and thats also what you type in the command line to start Gedit. So it doesn't matter where the executables are because you never use their full path anyway.

Another example is that the manual page for Gedit is in the file "/usr/share/man/man1/gedit.1.gz" but you don't dig up that file, you type "man gedit" in the command line. So it doesn't matter where the manual pages are because you never use their full path either.

There are exceptions of course such as when you edit a system wide config file or mount hard disk partitions. But it's usually a one time job to configure partitions to auto mount on startup and configure other system settings. So the times you need to go outside of your home are so rare that you can just look up which path you need when you need it and forget it again when you're done.

---

### Post by jc87 on 2006-04-08
[The file structure](https://wiki.ubuntu.com//UbuntuHowCome#head-4c8305d50cb1f72924493a4938d8b6a6184e7b14)

---

### Post by Omnios on 2006-04-08
This may help abit, All the goodies that windows have problems with are root protected so Linux will never have the problems windows have.

---

### Post by mrgnash on 2006-04-08
[QUOTE=Lord2k]Well, the main reason it bothers me is because it's not like Windows. I'm used to the way Windows file structure is handled. (/Windows for OS / system related files, /Program Files for applications, etc.)

Also, SD-Plissken, those links are helpful. They explain some things.[/QUOTE]

**[Linux is Not Windows](http://linux.oneandoneis2.org/LNW.htm)**

If you're not prepared to embrace that, then don't bother with Linux.

---

### Post by picpak on 2006-04-08
You could try this:

[HOWTO: Hide Unix File Structure](http://ubuntuforums.org/showthread.php?t=76521&highlight=.hidden)

---

### Post by Stormy Eyes on 2006-04-08
[QUOTE=Lord2k]But, that's the only thing that is holding me back. What can I do to alleviate this problem?[/QUOTE]

Wait, and be patient. Really, unless you're doing admin stuff, you should be keeping all of your stuff in /home/$userid. You don't need to dick around with the other stuff under normal circumstances.

---

### Post by htinn on 2006-04-08
*This* is the part that's like a different language, and just like learning a different lanuage your brain plays tricks on you at first.

---

