---
title: "running video (media) player from command line on E4.5"
date: 2016-02-29
forum: Ubuntu Phone and Tablet
---

### Post by ales-horak on 2016-02-29
Hi,

is there a way how to start playing a video file from the command line (terminal) in Ubuntu Phone (BQ E4.5)?

---

### Post by QDR06VV9 on 2016-02-29
>          This is something that a lot of people want - the ability to play music and video on their phones, in a smooth,         seamless way. When it comes to copying stuff onto the phone, it's a breeze. When it comes to playing content,         not quite so. I encountered tons of problems.       
                Video wise, the default player, and at the moment, the only player, is broken. It will not play anything.         Instead, it will tell you to activate the Video scope, and then, you can search through your local collection         there, and hopefully get to play some of the stuff.       



The syntax to open any file in its default application is

xdg-open <file_name>

If you mean play the video in the terminal video, install mplayer (install mplayer) and run

mplayer -vo caca <movie_file>

It doesn't run directly in the terminal window, but it does display in ASCII characters.
Or have a look here: [http://ubuntuforums.org/showthread.php?t=1866520](http://ubuntuforums.org/showthread.php?t=1866520)

---

### Post by handaxe on 2016-03-01
This is a useful resource : [https://www.gitbook.com/book/gurucubano/bq-aquaris-e-4-5-ubuntu-phone/details](https://www.gitbook.com/book/gurucubano/bq-aquaris-e-4-5-ubuntu-phone/details)

See chapter 12

---

### Post by ales-horak on 2016-03-01
to [[COLOR=#000000]runrickus[/COLOR]]("http://ubuntuforums.org/member.php?u=27449"):

I may be mistaken, but it seems that you are answering something else than my question:
```
phablet@ubuntu-phablet:~$ xdg-open file.avi
bash: xdg-open: command not found
```

caca ascii video output is interesting, but more like a joke.

And I don't see a connection between my question and a thread about installing miniDLNA on a Ubuntu server :-(


to          handaxe:

that's **perfect!** thanks a lot!
why is not such a book distributed with the phone by default?

---

