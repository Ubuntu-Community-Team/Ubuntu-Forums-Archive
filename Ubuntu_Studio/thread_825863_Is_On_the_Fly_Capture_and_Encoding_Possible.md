---
title: "Is On the Fly Capture and Encoding Possible?"
date: 2008-06-11
forum: Ubuntu Studio
---

### Post by SyCo123 on 2008-06-11
A windows loving friend (read in zealot) is actually sniffing around Linux, but he has a question. This is a Linux noob I'm talking about but a skilled windows guy.

His question was, can you hook up a DV camcorder with a firewire connection and capture and encode direct to DivX in Linux, in one step. The aim being to hook up the camcorder, 'set and forget', return after a while and have the DivX file ready to view.

Is there any software that will do that. He's tech savy but has no desire to delve deep in config files. The command line wont intimidate him too much though, if it's not too complex.

---

### Post by eye208 on 2008-06-12
> **SyCo123 said:**
> His question was, can you hook up a DV camcorder with a firewire connection and capture and encode direct to DivX in Linux, in one step.
Yes, you can pipe the output of dvgrab into ffmpeg or mencoder.

---

### Post by Unterseeboot_234 on 2008-06-12
Using DVgrab you can pipe. Consider

```
dvgrab –format -raw - | ffmpeg -f dv -i -vcodec mpeg4 -vtag XVID -deinterlace -b 2000 -acodec mp3 -ab 128 -trell -m4v OUTPUT_FILE.avi
```

You have to study the man pages.

---

### Post by SyCo123 on 2008-07-22
Thanks for your replies but I don't think the command line is going to win over a windows user. 

I've learnt something cool though so thanks!

---

### Post by rlameiro on 2008-07-22
Well I think that the command line is not so bad as the people think, I came from dos to windows and to linux (dos was like half year, only to launch shinobi :) ). 
But the command that Unterseeboot_234 showed seem to be self explanatory and easy run :) also if you have the command copied to a text document you can always copy and paste to the command line and just replace the name of the output file, anyway  drop the idea just because there is no Graphic tool that does exactly what he want seem a litle bit extreme.

---

### Post by SyCo123 on 2008-07-22
The guy I was investigating this about is a network admin and Windows guru so the command line is no problem for him. I ca hear him scoffing at the concept of it right now, even though he uses a DOS prompt all the time.

I know, I know... You don't need to say it.. really :)

---

