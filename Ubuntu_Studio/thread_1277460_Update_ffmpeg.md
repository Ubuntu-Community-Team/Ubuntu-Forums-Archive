---
title: "Update ffmpeg"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by arnab_das on 2009-09-28
How can i update ffmpeg to the latest version?

i already have it installed.

---

### Post by FakeOutdoorsman on 2009-09-28
Try this:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by arnab_das on 2009-09-28
> **FakeOutdoorsman said:**
> Try this:

[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")


thank u so very much for writing such an awesome article. but can i delete the ffmpeg and x264 folders (under home directory) which have been created? they're consuming around 300mb.

also when i try to use winff the converter, then i get an error message saying i need to install ffplay. why is that? i thought i had installed all ffmpeg packs.

---

### Post by andrew.46 on 2009-09-29
Hi arnab,

> **arnab_das said:**
> thank u so very much for writing such an awesome article. but can i delete the ffmpeg and x264 folders (under home directory) which have been created? they're consuming around 300mb.

I can answer at least part of your question :). It is an excellent idea to keep these 2 folders so that both can be updated easily. Have a look at this section of FakeOutdoorsman's guide:

> **Updating Your Installation**
You may eventually want to update to the newest revisions of FFmpeg and x264 if there are any major developments or changes:


which details this procedure. Personally I update x264, FFmpeg and MPlayer every week and it is well worthwhile doing for the extra functionality gained.

Andrew

---

### Post by paul.gevers on 2009-09-29
> **arnab_das said:**
> also when i try to use winff the converter, then i get an error message saying i need to install ffplay. why is that? i thought i had installed all ffmpeg packs.
If you compiled your own ffmpeg (and ffplay) the path to it might be different than the default. In the options -> Settings -> Linux menu you can specify the path to it.

---

### Post by arnab_das on 2009-09-29
> **paul.gevers said:**
> If you compiled your own ffmpeg (and ffplay) the path to it might be different than the default. In the options -> Settings -> Linux menu you can specify the path to it.

that i believe is exactly the case. apparently my ffmpeg and ffplay is now in /home/user

so i changed the paths of ffmpeg executable and ffplay. (without changing the terminal pathway) its working properly now. but since i did it manually, i still am in doubt if i did the right thing.

---

### Post by ArtInvent on 2009-09-29
I've had the same problem - compiled ffmpeg as per the excellent HowTo. So much better, but WinFF says it 'could not find ffplay'. 

My ffplay and ffmpeg ended up in /usr/local/bin/ which I determined running the command 'locate ffplay'.

I also have WinFF 1.1 which is the latest but gotten from the WinFF project private repo as per their instructions at the project web page. To change the pat to ffmpeg and ffplay, you go to Edit | Preferences | Linux, which is different from the above mention procedure. 

Now it seems to work again. Thanks.

---

### Post by paul.gevers on 2009-09-30
> **ArtInvent said:**
> To change the pat to ffmpeg and ffplay, you go to Edit | Preferences | Linux, which is different from the above mention procedure.

This is indeed the procedure that I meant. Sorry, the first one was from the top of my head and clearly I got it wrong.

---

