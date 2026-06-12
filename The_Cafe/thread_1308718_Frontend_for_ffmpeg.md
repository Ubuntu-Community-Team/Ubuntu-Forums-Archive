---
title: "Frontend for ffmpeg"
date: 2009-10-31
forum: The Cafe
---

### Post by talsemgeest on 2009-10-31
Hey all, I have been writing a frontend for the command line video encoder FFmpeg. To pass the course for school I need feedback from the wider community stakeholders which, in this case, is the Ubuntu community. :) 

It is functional, but it is certainly not ready to be released. It is still a very simple program, and I will continue to work on it after I have completed the school-related part of it.

So, if anyone is brave enough to try it, has ffmpeg installed, I would appreciate any feedback on whether or not it is "fit for the purpose", which is to be a Beginner-friendly frontend for ffmpeg. If you want to try, the download is [here.]("http://talsemgeest.doesntexist.com/myencoder/files/myencoder-0.01.tar.gz")

If you dont have ffmpeg installed, you can get it with ```
sudo apt-get install ffmpeg
```

Thanks,

talsemgeest.

---

### Post by Simey on 2009-10-31
Hey,
I had a little play, and it works, but I don't know if I'd let a beginner loose on it; there is no open file dialogue where I can just click the input file. That leaves typing the full path or dragging the file in to the box then adjusting the path name to make it work.
Same with output.

It has potential, though.
Good luck.

---

### Post by dragos240 on 2009-11-01
It works fine here! Pretty usefull! Adding to the AUR.

---

### Post by talsemgeest on 2009-11-01
> **Simey said:**
> Hey,
I had a little play, and it works, but I don't know if I'd let a beginner loose on it; there is no open file dialogue where I can just click the input file. That leaves typing the full path or dragging the file in to the box then adjusting the path name to make it work.
Same with output.

It has potential, though.
Good luck.

Yes, I actually put a file-chooser into the gui, but I couldnt figure out how to make it work with python. That is first on the list of things I will have to put in though. Thanks for the feedback :)

> **dragos240 said:**
> It works fine here! Pretty usefull! Adding to the AUR.

Excellent, good to know it works. Thanks for the feedback :)

---

### Post by Frak on 2009-11-01
Works nicely, I like it.

---

### Post by dragos240 on 2009-11-01
It'd also be usefull to add that you need python.

And gtk2

---

### Post by talsemgeest on 2009-11-01
> **Frak said:**
> Works nicely, I like it.

I am glad you like it, thank you for the feedback :)

> **dragos240 said:**
> It'd also be usefull to add that you need python.

And gtk2

Ah, thanks for mentioning that, I will have to add that to the docs somewhere.

---

### Post by dragos240 on 2009-11-01
By the way. Does that server of yours stay up 24/7?

---

### Post by sloggerkhan on 2009-11-01
I think you should lose the tabs and put all the options in one window.

---

### Post by talsemgeest on 2009-11-01
> **dragos240 said:**
> By the way. Does that server of yours stay up 24/7?

Yes, its up 24 hours a day, and should be getting a bandwidth increase in the next couple of days.

> **sloggerkhan said:**
> I think you should lose the tabs and put all the options in one window.
Really? I think the tabs simplify the interface a bit. However, I will make a single-window version for you to try out, it shouldn't be too difficult.

---

### Post by dragos240 on 2009-11-01
> **talsemgeest said:**
> Yes, its up 24 hours a day, and should be getting a bandwidth increase in the next couple of days.


Really? I think the tabs simplify the interface a bit. However, I will make a single-window version for you to try out, it shouldn't be too difficult.

Thanks!

I have just uploaded the myencoder package to the AUR.

Tips:

[LIST=1]
[*]I had no success with installing myencoder via yaourt, do it manually.
[*]Launch myencoder from your home directory.
[/LIST]
Myencoder can be launched with: myencoder
in the teminal.

Enjoy!

---

### Post by talsemgeest on 2009-11-01
> **dragos240 said:**
> Thanks!

I have just uploaded the myencoder package to the AUR.

Tips:

[LIST=1]
[*]I had no success with installing myencoder via yaourt, do it manually.
[*]Launch myencoder from your home directory.
[/LIST]
Myencoder can be launched with: myencoder
in the teminal.

Enjoy!
Oh, brilliant! :)

Although, I have never heard of AUR. From a little bit of googleing I am guessing its the Arch User Repository?

---

### Post by dragos240 on 2009-11-01
> **talsemgeest said:**
> Oh, brilliant! :)

Although, I have never heard of AUR. From a little bit of googleing I am guessing its the Arch User Repository?

Yup. Many users here use arch (including myself), and the AUR is a very usefull little tool for getting packages! This is my first package. I think it works good!

---

### Post by spupy on 2009-11-01
* Could you add "copy" as options for vcodec and acodec? It specifies that the codec of the input file is to be used. It is handy for resizing videos.
* It would be nice to have some predefined resolutions. For the resolution you could use the entry combo box (is that the name?) - the same kind of widget you use for framerate, for example. It can have predefined values that you can select from the drop-down list, or you can enter your own resolution (and parse the text).

Nice job! :D

EDIT: If you allow me, some tips on the code:
* For the endless if-then-else cases where you select the codecs, use a dict instead. (a hashmap) It will make your life easier.
* The "commands" module for python can also execute commands. It has the advantage that you can read the exit code of the subprocess. This way you can determine if the process exited with an error (exit_code!=0)
* The filename input can't handle names with spaces in them.

---

### Post by talsemgeest on 2009-11-01
> **spupy said:**
> * Could you add "copy" as options for vcodec and acodec? It specifies that the codec of the input file is to be used. It is handy for resizing videos.
* It would be nice to have some predefined resolutions. For the resolution you could use the entry combo box (is that the name?) - the same kind of widget you use for framerate, for example. It can have predefined values that you can select from the drop-down list, or you can enter your own resolution (and parse the text).

Nice job! :D

EDIT: If you allow me, some tips on the code:
* For the endless if-then-else cases where you select the codecs, use a dict instead. (a hashmap) It will make your life easier.
* The "commands" module for python can also execute commands. It has the advantage that you can read the exit code of the subprocess. This way you can determine if the process exited with an error (exit_code!=0)
* The filename input can't handle names with spaces in them.
Thank you very much for the advice, I will add in copy for the vcodec and acodec, and will change the spin-boxes to entry combo boxes. Can you give me a list of resolutions you would like on there? I will also look into using the dictionary for the codec lists (I actually wrote another python script to generate that code for me ;) ). And, I will also look into the commands module, and see about fixing the problem with the spaces.

Thank you very much for the advice :)

---

### Post by spupy on 2009-11-01
> **talsemgeest said:**
> Can you give me a list of resolutions you would like on there?

I don't know. It's a bit of work, but you can make a list of the resolutions of common devices. Even put their names in the drop down list. But this work is for later down the road.

---

### Post by talsemgeest on 2009-11-01
> **spupy said:**
> I don't know. It's a bit of work, but you can make a list of the resolutions of common devices. Even put their names in the drop down list. But this work is for later down the road.
Ok, well I will certainly add it to the list :)

---

### Post by FakeOutdoorsman on 2009-11-01
One little thing: your archive file, *myencoder-0.01.tar.gz*, is a [tarbomb](http://en.wikipedia.org/wiki/Tarbomb#Tarbomb).

---

### Post by talsemgeest on 2009-11-01
Good point, I will fix it when I get home.

---

### Post by talsemgeest on 2009-11-01
Fixed and uploaded to the server. :)

---

