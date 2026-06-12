---
title: "A new project: JapelServer.  Streaming for the iPhone..."
date: 2009-12-12
forum: The Cafe
---

### Post by patrickballeux on 2009-12-12
Hi,

I've been doing some reseach on the internet in the last month on playing movies on the iPhone 3GS.  What I wanted to do it being able to stream any movie files to my iPhone from my PC.  And finally, I found the solution using the GStreamer framework.  By combining some code from WebcamStudio for GNU/Linux, I created a new software called JapelServer.

JapelServer is open-sourced and can be found at :  [http://sourceforge.net/projects/japelserver/]("http://sourceforge.net/projects/japelserver/")

It's a command line app that will scan a folder for any movies and make them available to your iPhone thru the Safari browser.  In your iPhone, you click on the movie link and it starts playing right away!  No transcoding, no jailbreaking!

Features:

    * Fully configurable thru a configuration file
    * All movie formats are supported
    * Can support multiple profiles (hi/low speed stream, Ogg streaming, etc...)
    * Can stream any live feed (Webcam, Internet feed, etc...)
    * Custom html page
    * Direct access to files
    * Can include images, multiple webpages


For now JapelServer only works in Linux but as soon as the GStreamer framework will be updated for Windows, it should also work on the Microsoft operating systems.

How to use:

    * Unzip the archive in a folder
    * Edit the japel.properties configuration file for your own settings
    * From the console, in that folder, launch: java -jar JapelServer japel.properties
    * Open the Safari browser in your iPhone to [http://YOUR_PC_IP:8888](http://YOUR_PC_IP:8888)
    * Watch movies or any streams configured


Enjoy!

Patrick

---

### Post by patrickballeux on 2009-12-14
Just released the version Alpha 2 of the project.  Go try it!

---

### Post by patrickballeux on 2009-12-17
JapelServer Alpha 3 has just been released...  Go get it!

---

### Post by patrickballeux on 2009-12-17
The offical website for JapelServer is now at : [http://japelserver.ws4gl.org]("http://japelserver.ws4gl.org")

Enjoy!

---

### Post by pwnst*r on 2009-12-17
interesting, i'll have to check this out. thanks patrick!

---

### Post by patrickballeux on 2009-12-17
Make sure that you read the docs on the website.  This is a configuration/console based apps, so no GUI to configure your stuff...

---

### Post by Frak on 2009-12-17
subscribed

---

### Post by HappinessNow on 2009-12-17
> **patrickballeux said:**
> JapelServer Alpha 3 has just been released...  Go get it!
Have you released an Android app yet?

---

### Post by patrickballeux on 2009-12-19
JapelServer should work also with Android base cell phone.

It's just a matter of configuring the transcoding configuration in the profile if the default does not work with it.

Actually, JapelServer can be compatible with anything that can read movie streams over a network.  By default, the streams are configured for Mp4 (h264 & AAC) format.  But I've been successful at streaming OGG format also so computers can read the streams.

Patrick

---

### Post by EvilGenius007 on 2010-01-10
Subscribed! I need to check this out when I get home. Any chance you could be motivated towards exapnding the functionality of this software? I obviously need to get it running to see what it's capable of now, but from what you mentioned in another thread it seems like it could do much more...

---

### Post by patrickballeux on 2010-01-11
Hi,

By default, it was made for the iPhone, but by adding your own gstreamer pipeline in the configuration file, and playing around with the index.html file, it can do a lot more.  

There is a new release also, Alpha 4.


> **EvilGenius007 said:**
> Subscribed! I need to check this out when I get home. Any chance you could be motivated towards exapnding the functionality of this software? I obviously need to get it running to see what it's capable of now, but from what you mentioned in another thread it seems like it could do much more...

---

### Post by patrickballeux on 2010-01-11
If your iPhone is jailbroken, and you are using the plugin for Safari to download the movies, then using JapelServer, you can transcode/download the movie in a single step.

Have fun!

---

### Post by sadanro100 on 2010-02-05
I've been looking for something like this for ages, tried several different alternatives available for windows but none of them worked under wine.
I wasnt expecting to find something that would also allow me to stream my webcam apart from video files, which i managed to do with openstreamer(cydia) + vlc, but wasnt a very elegant/stable option.
Obviously the web interface could be easily improved, not that it matters, just looking at what it does i can already consider it magic!!!
i love this open source community because things tend to take a long time to come, but once they do i feel happier than ever!
thank you ever so much!

---

### Post by holmesy999 on 2010-02-06
I'll admit - I am a gump at installing things / understanding, but I am an excellent cut and paster - if I am being honest, if I can get this thing to work, then anyone can.

when I follow the instructions on the japelserver homepage, I get an error - 
step 1 - sudo apt-get install gstreamer etc etc - works

step 2 - sudo apt-get install openjdk - fail. I get the following error in my terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openjdk

little help?

---

### Post by Dayofswords on 2010-02-06
if i had an iphone, i'd probably find this pretty cool

but i dont have one, or a cell phone for that matter

if i get an iphone, i'll check it out

---

### Post by Frak on 2010-02-06
> **holmesy999 said:**
> I'll admit - I am a gump at installing things / understanding, but I am an excellent cut and paster - if I am being honest, if I can get this thing to work, then anyone can.

when I follow the instructions on the japelserver homepage, I get an error - 
step 1 - sudo apt-get install gstreamer etc etc - works

step 2 - sudo apt-get install openjdk - fail. I get the following error in my terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openjdk

little help?
```
sudo apt-get install openjdk-6-jre
```

---

### Post by holmesy999 on 2010-02-06
> **Frak said:**
> ```
sudo apt-get install openjdk-6-jre
```

thankyou! that's it. perhaps instructions need to be updated on japelserver website?

---

### Post by sadanro100 on 2010-02-09
Hello, Im well pleased with the software, its running smoothly (when my network cooperates), thank you very much.
Ive only got one question though, am I missing something or its actually not supposed to work with mwv files?
Cheers

---

