---
title: "Read .lit files?"
date: 2009-10-23
forum: The Cafe
---

### Post by tetrisalphabet on 2009-10-23
I'm trying to find a way to open .lit files, or convert them to something else. I found [this](http://ubuntuforums.org/showthread.php?t=159331) thread and tried following the instructions, except that the folder I have is called clit18. Once I finished, I tried typing "clit [file path and name]", but only received "bash: clit: command not found" in response.

---

### Post by cariboo on 2009-10-24
Have a look at calibre, it is in the repositories. I haven't found an ebook it won't display. I haven't tried the conversion utility yet, but if it is like the reast of the application it should work quite well.

Thanks to Technoviking for mentioning it in his Kindle 2 review.

---

### Post by Sporkman on 2009-10-24
> **tetrisalphabet said:**
> I'm trying to find a way to open .lit files, or convert them to something else. I found [this](http://ubuntuforums.org/showthread.php?t=159331) thread and tried following the instructions, except that the folder I have is called clit18. Once I finished, I tried typing "clit [file path and name]", but only received "bash: clit: command not found" in response.

This actually has comedic potential...

---

### Post by CharmyBee on 2009-10-24
Do you have it installed? Does documentation appear when you type 'man clit'? Have you tried executing it locally like **./**clit?

---

### Post by fenian on 2009-10-24
You also have to put a location for the saved file...

> clit /pathto/file.lit /pathto/saveloation

or you could just use a period to save to the same directory...

> clit /pathto/file.lit .

That being said Calibre does an excellent job and IMO is a better option.

---

### Post by Nerd King on 2009-10-24
Also MS reader works fine on my wine setup with the usual extras added via winetricks (msxml, vcrun, vbrun, etc)

---

### Post by dragos240 on 2009-10-24
> **Sporkman said:**
> This actually has comedic potential.. 

Agreed.

---

### Post by JillSwift on 2009-10-24
> **tetrisalphabet said:**
> I'm trying to find a way to open .lit files, or convert them to something else. I found [this]("http://ubuntuforums.org/showthread.php?t=159331") thread and tried following the instructions, except that the folder I have is called clit18. Once I finished, I tried typing "clit [file path and name]", but only received "bash: clit: command not found" in response.
Unless you out it in one of the directories in your path, you have to type:

/path/to/clit /path/to/input /path/to/output

---

### Post by tetrisalphabet on 2009-10-24
I tried including the saveto path as well, and am still told that there's no such command as clit. There's no man entry for it either.

I tried to download Calibre also, but it doesn't show up in Synaptic so I had to go to ubuntu.com, and neither the AMD64 nor the I386 versions would install. I386 gives me an error that says "Error: Dependency is not satisfiable: libqtcore4" and AMD64 says "Error: Wrong architecture: amd64".

---

### Post by Islington on 2009-10-24
> **tetrisalphabet said:**
> I tried including the saveto path as well, and am still told that there's no such command as clit. There's no man entry for it either.

I tried to download Calibre also, but it doesn't show up in Synaptic so I had to go to ubuntu.com, and neither the AMD64 nor the I386 versions would install. I386 gives me an error that says "Error: Dependency is not satisfiable: libqtcore4" and AMD64 says "Error: Wrong architecture: amd64".

hold on .. what? go to synaptic make sure universe is enabled.

---

### Post by JillSwift on 2009-10-24
> **tetrisalphabet said:**
> I tried including the saveto path as well, and am still told that there's no such command as clit. There's no man entry for it either.
It's the bit where you type in the path to clit that counts here. When you compile it there's no installation - it's in the folder "clit18" in whatever folder you put the source files.

So it would look something like:

```
~/clit18src/clit18/clit /path/to/lit /path/to/converted_files
```

(You have compiled it, right?)

---

### Post by tetrisalphabet on 2009-10-24
> **JillSwift said:**
> It's the bit where you type in the path to clit that counts here. When you compile it there's no installation - it's in the folder "clit18" in whatever folder you put the source files.

So it would look something like:

```
~/clit18src/clit18/clit /path/to/lit /path/to/converted_files
```(You have compiled it, right?)

That worked! I was doing it wrong before. Sorry for my newbishness, and thanks for all the help.

---

