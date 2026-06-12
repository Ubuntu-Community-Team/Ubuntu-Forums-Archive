---
title: "Advice for a FOSS project"
date: 2009-03-24
forum: The Cafe
---

### Post by talsemgeest on 2009-03-24
Ok, for my I.T. class this year, I have to choose a project. For this project, I have chosen to create a simple GUI frontend to Mencoder and ffmpeg, for use in converting/re-encoding video files. Since I already have a little experience in writing simple python programs, I decided to use that, in conjunction with PyGTK and glade. And of course, being the open source advocate that I am, I will be releasing it under an open source license for free on the net.
 
So, does anyone have any advice while I am still in the early stages of planning this software?

---

### Post by MaxIBoy on 2009-03-24
Make it easy to add new features. For your project, try abstracting the way the program interfaces with the codecs, such that... well, it's easier to explain in a picture.

This may seem like overkill, but you never know what new encoder programs you'll have to add support for in the future, and this makes your program useful in a greater variety of situations. Python is a great language for a modular design like this, too.


Also, check this out:
[http://catb.org/esr/writings/taoup/html/](http://catb.org/esr/writings/taoup/html/)

---

### Post by DeadSuperHero on 2009-03-24
Although I don't know how to give the best advice, it's always nice to have native support for converting a file from a proprietary format (mp3, M4a, AAC, WMV, WMA, MP4) into a Free Software format. (Ogg Vorbis, Ogg Theora, Dirac)
 
Remember, GStreamer is your friend!
 
So is, Xine, though, if you're not fond of GStreamer.

---

### Post by dragos240 on 2009-03-24
so is vlc, i use that 


:)

---

### Post by bsharp on 2009-03-24
I don't know of many GUI frontends for ffmpeg/mencoder, but the one I DO know of and use is WinFF. Works fine, but the limited options annoys me.

Have support for most/all options PLEASE. WinFF only supports converting to a limited range of formats and only uses a tiny fraction of what ffmpeg's potential.

---

### Post by talsemgeest on 2009-03-24
> **MaxIBoy said:**
> Make it easy to add new features. For your project, try abstracting the way the program interfaces with the codecs, such that... well, it's easier to explain in a picture.

This may seem like overkill, but you never know what new encoder programs you'll have to add support for in the future, and this makes your program useful in a greater variety of situations. Python is a great language for a modular design like this, too.


Also, check this out:
[http://catb.org/esr/writings/taoup/html/](http://catb.org/esr/writings/taoup/html/)

Thanks, that is very good advice. I still haven't decided how I will implement the choice between ffmpeg and mencoder, other than that it will prefer ffmpeg. So, just to make sure, what you are saying is that I should leave room for other converter backends, other than ffmpeg and mencoder, if a good one should come along?

> **Mr. Psychopath said:**
> Although I don't know how to give the best advice, it's always nice to have native support for converting a file from a proprietary format (mp3, M4a, AAC, WMV, WMA, MP4) into a Free Software format. (Ogg Vorbis, Ogg Theora, Dirac)
 
Remember, GStreamer is your friend!
 
So is, Xine, though, if you're not fond of GStreamer.

This program should have support for everything that ffmpeg or mencoder supports.

> **dragos240 said:**
> so is vlc, i use that 


:)

VLC is all well and good, but it was designed as a video player, with converting as a bit of an afterthought. (Also, I have never been able to get it to work... ;))

Yep, this should have support for most of the options of ffmpeg and mencoder. I must say, I like to have a bit of control over video files that I convert. :)

---

### Post by MaxIBoy on 2009-03-24
> **talsemgeest said:**
> Thanks, that is very good advice. I still haven't decided how I will implement the choice between ffmpeg and mencoder, other than that it will prefer ffmpeg. So, just to make sure, what you are saying is that I should leave room for other converter backends, other than ffmpeg and mencoder, if a good one should come along?Your main program should be an entirely different piece of software from the programs that interface with the backends. These programs should be easy for power users to write. Want the software to use xine? Write a plugin python script to interface with xine, stick it in the right folder, and the software will automatically recognize the plugin and use it.

The Gimp has this capability, and this has made it much more useful.

---

### Post by talsemgeest on 2009-03-25
> **MaxIBoy said:**
> Your main program should be an entirely different piece of software from the programs that interface with the backends. These programs should be easy for power users to write. Want the software to use xine? Write a plugin python script to interface with xine, stick it in the right folder, and the software will automatically recognize the plugin and use it.

The Gimp has this capability, and this has made it much more useful.
Ok, I will look into it and see what I can do. Thanks again for the advice :)

---

### Post by MaxIBoy on 2009-03-25
A pretty easy way to do it is this:


```
#all plugins must have this function defined! 
def convert( inputCodec, outputCodec, filename ): 
    errorHasOccurred = False
    errors = ""
    if inputCodec not in knownInputCodecs:
        errorHasOccurred = True
        errors += "inputCodec;"
    if outputCodec not in knownOutputCodecs:
        errorHasOccurred = True
        errors += "outputCodec;"

    #more error checking. 
    #Remember that all plugins should use the same names for their errors!

    if errorHasOccurred:
        return errors



    #perform the actual action. 
    #The details of this part are left up to the writer of the plugin.
    #Extra functions can be defined as necessary. "Convert" is the only one that is 
    #externally called from outside the plugin.

    return "success;"
    
```Pretty simple spec, but you get the idea.

---

### Post by FakeOutdoorsman on 2009-03-25
Will you keep up with FFmpeg SVN or will you just stay with the new schedule of releases such as the recent FFmpeg 0.5?  Personally I use SVN since development is active, but the releases would probably be easier to keep up with and most GUI users probably won't care.  I recommend sticking with one or the other to prevent confusion like I sometimes see with the WinFF presets.

---

### Post by talsemgeest on 2009-03-25
> **MaxIBoy said:**
> A pretty easy way to do it is this:


```
#all plugins must have this function defined! 
def convert( inputCodec, outputCodec, filename ): 
    errorHasOccurred = False
    errors = ""
    if inputCodec not in knownInputCodecs:
        errorHasOccurred = True
        errors += "inputCodec;"
    if outputCodec not in knownOutputCodecs:
        errorHasOccurred = True
        errors += "outputCodec;"

    #more error checking. 
    #Remember that all plugins should use the same names for their errors!

    if errorHasOccurred:
        return errors



    #perform the actual action. 
    #The details of this part are left up to the writer of the plugin.
    #Extra functions can be defined as necessary. "Convert" is the only one that is 
    #externally called from outside the plugin.

    return "success;"
    
```Pretty simple spec, but you get the idea.

Ok, thanks for that, I get what you mean now.

> **FakeOutdoorsman said:**
> Will you keep up with FFmpeg SVN or will you just stay with the new schedule of releases such as the recent FFmpeg 0.5? Personally I use SVN since development is active, but the releases would probably be easier to keep up with and most GUI users probably won't care. I recommend sticking with one or the other to prevent confusion like I sometimes see with the WinFF presets.

Are there differences in the commands between versions? Since choosing a version of ffmpeg doesn't have to be done until I go to package (probably around august-september), I will probably leave it until then to decide which is the best for my software. Still, it shouldn't really matter what is happening behind the scenes to the average user, they care more about the output video file than the backend software that does the hard work. ;)

---

### Post by paul.gevers on 2009-03-25
> **bsharp said:**
> Have support for most/all options PLEASE. WinFF only supports converting to a limited range of formats and only uses a tiny fraction of what ffmpeg's potential.

What options are you missing in WinFF? And which formats? You can write your own presets using ALL potential of ffmpeg ([Howto make your own presets.]("http://code.google.com/p/winff/wiki/HowToMakePresets")) and if you are using predefined presets you can add additional options in the "Addition options" field.

If you are feeling that WinFF misses features, please file a wishlist bug in the [bug tracker]("http://code.google.com/p/winff/issues/list").

---

### Post by paul.gevers on 2009-03-25
> **talsemgeest said:**
> Are there differences in the commands between versions? Since choosing a version of ffmpeg doesn't have to be done until I go to package (probably around august-september), I will probably leave it until then to decide which is the best for my software. Still, it shouldn't really matter what is happening behind the scenes to the average user, they care more about the output video file than the backend software that does the hard work. ;)

As I understand it, if you are going to make a proper gui for ffmpeg, you should make a frontend for the library (libavcodec) instead of passing commands to ffmpeg (like Winff does). Commands change when the soname of the libraries are raised (which is done exactly to make sure you know the ABI is changed and you can still use your program.

---

### Post by talsemgeest on 2009-03-25
> **paul.gevers said:**
> As I understand it, if you are going to make a proper gui for ffmpeg, you should make a frontend for the library (libavcodec) instead of passing commands to ffmpeg (like Winff does). Commands change when the soname of the libraries are raised (which is done exactly to make sure you know the ABI is changed and you can still use your program.

Ah, Ok, I see what you mean. So is libavcodec the only library I would have to interface with for this to work, or does ffmpeg use multiple libraries? But anyway, I'm sure I could learn how to pass the commands to libavcodec, provided it is not too complicated.

Thanks for the input Paul :)

---

### Post by talsemgeest on 2009-07-30
Ok, Im getting close to the stage of actually writing my software, but I need to check if there are any major options that are requested. Take a look at the screenshots and tell me if there is anything major missing.

[IMG]http://talsemgeest.doesntexist.com/myencoder/Screenshot-MyEncoder-Fileopts.png[/IMG]
[IMG]http://talsemgeest.doesntexist.com/myencoder/Screenshot-MyEncoder-videoopts.png[/IMG]
[IMG]http://talsemgeest.doesntexist.com/myencoder/Screenshot-MyEncoder-audioopts.png[/IMG]

---

### Post by paul.gevers on 2009-07-30
> **talsemgeest said:**
> Take a look at the screenshots and tell me if there is anything major missing.

Not major, but ffmpeg allows for A LOT of (and IMPORTANT) tweaking of HOW a codec is supposed to encode the video. I don't see that possibility in your screenshots (yet). The problem with those additional parameters is that they usually (naming and such) depend on exactly which codec you are using. Also not all aspect ratios/resolutions are allowed in every codec. 

Also the name "resolution" for the audio part, I find confusing, but that is just naming.

---

### Post by talsemgeest on 2009-07-30
> **paul.gevers said:**
> Not major, but ffmpeg allows for A LOT of (and IMPORTANT) tweaking of HOW a codec is supposed to encode the video. I don't see that possibility in your screenshots (yet). The problem with those additional parameters is that they usually (naming and such) depend on exactly which codec you are using. Also not all aspect ratios/resolutions are allowed in every codec. 

Also the name "resolution" for the audio part, I find confusing, but that is just naming.
Ok thanks Paul, I appreciate the help :)

---

