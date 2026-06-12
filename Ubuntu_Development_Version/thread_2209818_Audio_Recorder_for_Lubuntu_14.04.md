---
title: "Audio Recorder for Lubuntu 14.04"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by wjbmd48 on 2014-03-07
Hi:

I'm running the Trusty Tahr daily build, and I'm looking for a decent audio recorder, similar to Total Recorder for Win (doesn't run in Wine).

Gnome audio recorder simply doesn't work--the record button is dead.

Sourceforge has streamripstar as a .jar. I can decompress this, but have no idea at all how to install it from all the folders that result.

I'm looking for something that will record as 44.1/128k/stereo mp3 as a GUI, a tall order, I know.  Does anyone know how to do this with an easy install?  I don't think this problem is related to the TT daily build, since I had the same problem with 12.04.

Thanks!

Bill

---

### Post by grahammechanical on 2014-03-07
Gnome Recorded has not worked for me for more than a year. Then I found Audio-Recorder.

[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

It does not yet have a PPA for Trusty but right now I am recording a BBC radio audio stream on Trusty Tahr. After adding the PPA change the link from trusty to saucy and update the sources list. Then it will install. Change

> [http://ppa.launchpad.net](http://ppa.launchpad.net) /osmoma/audio-recorder/ubuntu trusty main

to 

> [http://ppa.launchpad.net](http://ppa.launchpad.net) /osmoma/audio-recorder/ubuntu saucy main

I do not know if the excellent utility meets your requirements but I recommend it. It will put an app indicator icon in the unity top panel which easily controls recording. Once you have run Update or Check for Updates audio-recorder should appear in the Software Centre. I have it there. After installation disable the PPAs for audio-recorder and you will not get errors with your daily updates of Trusty Tahr.

Regards.

---

### Post by wjbmd48 on 2014-03-07
Hi:

Sorry to be such a doofus newbie, but I can't find 


 	 		 			 			 				[http://ppa.launchpad.net](http://ppa.launchpad.net) /osmoma/audio-recorder/ubuntu saucy main   			 		(or trusty . . )

 	
 

anywhere on that page

I *can* download the audio recorder tar.gz, but when i unzip it I get the usual salad of folders that I can't interpret how to use.

And when I try this,

sudo apt-add-repository ppa:osmoma/audio-recorder
 sudo apt-get update
sudo apt-get install audio-recorder

It hangs on the last step, telling me it can't locate audio recorder.

You're extremely kind and helpful; could I impose on you to unpack your instructions a bit more?  (Also, I have no idea what a "PPA" is. The instructions on another webpage tell me I'll have to disable one of its settings so the program doesn't wipe out with updates?

Also, apparently, once the program is installed, to record as .mp3 I have to:


You will also need to install one or more of these packages to add support for various audio-formats.
gstreamer1.0-plugins-base  (OGG format)
gstreamer1.0-plugins-good (WAV and Flac formats)
 gstreamer1.0-plugins-ugly  (MP3 format)
 gstreamer1.0-plugins-bad (AAC, m4a format)
 Notice: The recorder now requires Gstreamer 1.0.
 Notice also:
Fluendo's gstreamer0.10-fluendo-mp3 package provides MP3-playback, but it has no recording capabilities. Playback only.

I have no idea how to enter the appropriate terminal command.

Thanks!

Bill

---

### Post by Frogs Hair on 2014-03-07
***Moved to Ubuntu + 1***

---

### Post by grahammechanical on 2014-03-07
Ok, here we go.

PPA = Personal Package Archive. It is a way for developers to provide applications which are not available through the usual Ubuntu archives/repositories.

Running this command

```
sudo apt-add-repository ppa:osmoma/audio-recorder
```

will create the reference to the archive/PPA in our list of sources/repositories. But the Update Manager is smart enough to know that we are running Trusty Tahr, so it puts the line

> [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu) trusty main

In our sources list. Go to System Settings>Software and Updates>Other Software tab and you will see it there and also a line for the source code. But the developer has not yet created a personal repository for audio-recorder in Trusty and that is why you cannot install it. So we need to edit the reference. Select the line

> [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu) trusty main

Click Edit and change the line to

> [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu) saucy main

When you click edit you will get a dialog that will list the Distribution as trusty. Change it to saucy and click OK. That is it done. Now you can run

```
sudo apt-get update
sudo apt-get install audio-recorder
```

In fact when you try to close Software and Updates you will be prompted to Reload. Do so and then Open the Software Centre and search for audio-recorder. You should be now able to install it from there.

But there is a warning. Because we are running Trusty and one of our repositories is listed as saucy then Update Manager (apt-get update) will throw up an error. So, after installing go back into Software and Updates>Other Software tab and untick both references to the audio-recorder PPA.

Give it ago.

---

### Post by wjbmd48 on 2014-03-07
I cannot thank you enough. You have not only taught me how to fish, but hopefully have presented me with a tuna.

Hopefully, I won't have to bug you further about this!

Best,

Bill

---

### Post by grahammechanical on 2014-03-07
As regards those gstreamer libraries you might find that they are already installed. Especially if you have installed Ubuntu Restricted Extras. I have all of them and gstreamer0.10-fluendo-mp3 and a later one - gstreamer1.0-fluendo-mp3. I also have the proposed repository enabled and I am getting stuff through that.

I find it useful to have Synaptic Package Manager installed. Then I can look for specific libraries to see if they are installed or available. The Audio-recorder developer has done a lot of work since I first installed it more than six months ago. Back then I had to compile the source code. That was the first time that I tried doing that. Now, we get it through a PPA and those instructions are not always necessary.

Regards.

---

### Post by stephenson-carl on 2014-03-07
If you're up for a little terminal action, check out this link: [http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ/#index34h3](http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ/#index34h3)
It's not hard to write a short script to record the output of your sound card (only one line, in fact)

---

### Post by wjbmd48 on 2014-03-07
Home run! Now recording mp3 flawlessly.  I do see the gstreamer in  synaptic, downloading the other 3 libraries, should be fun, will look at  the terminal commands above.

You guys are the best!

Bill

---

### Post by andrew125 on 2014-06-14
Search led me here and I am pleased with the advice. Am now recording streaming. Thanks .

---

