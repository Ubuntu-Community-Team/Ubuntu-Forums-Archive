---
title: "saving streaming flash video"
date: 2009-09-13
forum: The Cafe
---

### Post by stuart.reinke on 2009-09-13
Hi all, I'm trying to save streaming flash video to my hard drive.

I've read a couple tutorials on how to do this. They both say to copy the streaming file from the /tmp directory to the desktop and rename it. Sound simple enough.

I can't find any temporary flash files (Flashxxxxxx) in my /tmp directory while the video is streaming.

I tried a movie from Hulu and the only temporary files that show up are the commercials. The movie has nothing.

I also tried a tv show from CBS.com and got no file at all. (even using ls -a)

What am I doing wrong?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-13
I use a firefox addon. videodownloader

---

### Post by stuart.reinke on 2009-09-13
> **&#1057 said:**
> I use a firefox addon. videodownloader

i'll give that a try.

---

### Post by SuperSonic4 on 2009-09-13
I use video downloadhelper for firefox

---

### Post by NESFreak on 2009-09-13
open adblocks blockable objects list (ctrl-shift-v) filter for any flv files, copy its url and do whit that url whatever you want (download, open in external mediaplayer, whatever)

---

### Post by binbash on 2009-09-13
Use a firefox addon. NESFreak's way also works.

---

### Post by etnlIcarus on 2009-09-13
- The flashgot addon for Firefox will put download links in your statusbar for a number of streaming sites (youtube, pornhub, etc).

- In the case of Youtube, I use "YousableTubeFix", from userscripts.org. Besides adding download links in a number of formats in the video description column, it also makes youtube a lot less infuriating.

- sudo aptitude install youtube-dl. Read it's manpage; it's very straight-forward.

---

### Post by hoppipolla on 2009-09-13
> **SuperSonic4 said:**
> I use video downloadhelper for firefox

2nded :)

---

### Post by hoppipolla on 2009-09-13
> **etnlIcarus said:**
> - The flashgot addon for Firefox will put download links in your statusbar for a number of streaming sites (youtube, pornhub, etc).

- In the case of Youtube, I use "YousableTubeFix", from userscripts.org. Besides adding download links in a number of formats in the video description column, it also makes youtube a lot less infuriating.

- sudo aptitude install youtube-dl. Read it's manpage; it's very straight-forward.

What's wrong with Youtube?  As long as you have the official adobe plugin it should run smooth as anything :)

---

### Post by etnlIcarus on 2009-09-13
> **hoppipolla said:**
> What's wrong with Youtube?  As long as you have the official adobe plugin it should run smooth as anything :)

Videos automatically start; they only offer two size options: small and full-screen; the site doesn't honour your quality settings, often starting videos in, "HQ"; comments are visible, creating the temptation to flame idiots; other, extraneous information is displayed, that I don't want.

Also, Adobe haven't enabled video acceleration for people using R300 graphic chipsets, so it's hardly, "smooth".

---

### Post by RabbitWho on 2009-09-13
I'm using video downloadhelper.. what program can i use to convert the downloaded videos into .ogg (I just want the audio)?

---

### Post by ecmatter on 2009-09-13
> **RabbitWho said:**
> I'm using video downloadhelper.. what program can i use to convert the downloaded videos into .ogg (I just want the audio)?

The following command converts to mp3:

```

ffmpeg -i full/path/to/file.flv -vn new_file.mp3

```

*I've never used it to convert to ogg, but I think you would use the same command (replacing '.mp3' with '.ogg', of course).

---

### Post by RabbitWho on 2009-09-13
> **ecmatter said:**
> The following command converts to mp3:

```

ffmpeg -i full/path/to/file.flv -vn new_file.mp3

```*I've never used it to convert to ogg, but I think you would use the same command (replacing '.mp3' with '.ogg', of course).

Tried it with mp3 to start, cd to the folder with the videos in it and then pasted in what you wrote, everything stayed the same, what else do I have to do?

---

### Post by ecmatter on 2009-09-13
> **RabbitWho said:**
> Tried it with mp3 to start, cd to the folder with the videos in it and then pasted in what you wrote, everything stayed the same, what else do I have to do?

When you pasted in what I wrote, you changed 'full/path/to/file.flv' to reflect an actual file on your computer?

Do you have the restricted-extras package installed?

---

### Post by SuperSonic4 on 2009-09-13
> **RabbitWho said:**
> I'm using video downloadhelper.. what program can i use to convert the downloaded videos into .ogg (I just want the audio)?

Use ffmpeg 

```
ffmpeg -i input.flv -vn -acodec libvorbis -ac 2 -ab 128k output.ogg
```

---

### Post by RabbitWho on 2009-09-13
> **ecmatter said:**
> When you pasted in what I wrote, you changed 'full/path/to/file.flv' to reflect an actual file on your computer?



wey-hey it worked! stupidly I thought if I was in the right directory I wouldn't have to put in the full path! 

Sorry about that, thanks!

I don't suppose there's a nice way to get that to apply to all files in a folder?

Next question:

Is there a way to record streaming music files from things like myspace and deezer?

---

### Post by NESFreak on 2009-09-15
> **RabbitWho said:**
> 
I don't suppose there's a nice way to get that to apply to all files in a folder?

the following command should do that for you:
first go to the directory which contains the files you'd like to convert*
next enter the following command:
```
for i in *.flv; do ffmpeg -i $i -vn -acodec libvorbis -ac 2 -ab 128k ${i%flv}ogg; done
```


*(tip: a small utility called nautilus-open-terminal, which allows you to open the directory you're viewing by just richtclicking on some empty space, and select open in terminal. It's really neat, and available in synaptic, after installing nautilus requires a restart though, 'killall nautilus; nautilus)

---

