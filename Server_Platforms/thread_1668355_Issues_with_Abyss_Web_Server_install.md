---
title: "Issues with Abyss Web Server install"
date: 2011-01-16
forum: Server Platforms
---

### Post by TouchuvGrey on 2011-01-16
Attempting to install Abyss Web Server on my 64 bit laptop. i have done mkdir ABYSS to create the ABYSS directoty to install the server to.

    Command cd ABYSS then "tar xzfm Abyss Web Server installation package" as per instructions. Result
tar (child) Abyss cannot open; No such file or directory
tar: (child) Error is not recoverable: exiting now
tar Child returned status 2
tar: Error is not recoverable: exiting now

   likely i am missing something obvious. is someone can show me my error i'd appreciate it.

     i'm not married to Abyss, i'm open to other servers if their are any suggestions. i need something that will work with DadaMail Pro though.

---

### Post by Calimo on 2011-01-16
Hi!

> **TouchuvGrey said:**
> Command cd ABYSS then "tar xzfm Abyss Web Server installation package"
You have to replace the "Abyss Web Server installation package" in this command with the name of the file you downloaded. If there are
spaces in the file name, you have to surround it with quotes.

I highly recommand you to read an introduction to the command line so you understand what you're doing. You can find [one on the community documentation]("https://help.ubuntu.com/community/UsingTheTerminal") for example, but you'll find many others on the web!

Good luck :)

---

### Post by TouchuvGrey on 2011-01-16
Thank you Calimo:

       i replaced "Abyss Web Server installation package"
with "abwsx1.tgz" as per your instructions. same result.
TRied "abyssws" same result,

    i read the introduction you suggested. It brought back
much i had forgotten as i have not used linux much in the past few years,

      i will keep on trying, i suspect it is something
very simple that i'm not seeing right now.

---

### Post by cariboo on 2011-01-16
Instead of typing the package name and maybe making a typo, why not copy and paste it using your mouse. Highlight the file name, the type:

```
tar xzfm
```

with a space at the end, then click you mouse wheel, or both mouse buttons at once

---

### Post by TouchuvGrey on 2011-01-16
Hello Cariboo:

        i have tried that also with the same result.
i also used mkdir ./ABYSS to insure that the directory was actually being created.

     As i said, i'm more than willing to go with another server as long as it supports CGI at a minimum as i intend to be running DadaMail Pro on it.

    Though having put this much effort into getting Abyss running i want to get it running.

---

### Post by TouchuvGrey on 2011-01-16
Additional information that may be relevant.

    i had forgotten that i am running 11.04 Natty Narwhal
on my computer. Obviously an Alpha ( or possibly Beta)
release.

     i looked for information on how to revert to 10.10 in hopes that doing so might fix this issue but could not find anything relevant.

---

