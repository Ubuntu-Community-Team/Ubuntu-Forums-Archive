---
title: "simple app for testing recording from builtin camera and microphone?"
date: 2009-09-21
forum: System76 Support
---

### Post by tlroche on 2009-09-21
During the [System 76 30-Day Limited Money Back Guarantee]("https://system76.authsecure.com/article_info.php?articles_id=15"), I'd like to smoketest as much of my new [PanP]("https://system76.authsecure.com/product_info.php?cPath=28&products_id=86")'s functionality as possible without undue effort. ([Checklist here]("http://ubuntuforums.org/showpost.php?p=7958828&postcount=1").) Among those functions are the builtin camera and microphone. For a quick'n'dirty smoketest I just wanna

[LIST=1]
[*]enable each device
[*]record myself speaking
[*]replay the recording to verify the hardware basically works
[/LIST]

So I'm wondering, can anyone recommend one or more simple (preferably default or preloaded) applications allowing one to quickly test these devices?

---

### Post by gila_monster on 2009-09-21
> **tlroche said:**
> So I'm wondering, can anyone recommend one or more simple (preferably default or preloaded) applications allowing one to quickly test these devices?

I've done something like that with 'cheese.' Took me a bit to figure out the microphone settings and such, but it worked. I'm sure there are other programs as well, but as I don't mess with the webcam much, I haven't tried them.

---

### Post by jdb on 2009-09-21
> **tlroche said:**
> During the [System 76 30-Day Limited Money Back Guarantee]("https://system76.authsecure.com/article_info.php?articles_id=15"), I'd like to smoketest as much of my new [PanP]("https://system76.authsecure.com/product_info.php?cPath=28&products_id=86")'s functionality as possible without undue effort. ([Checklist here]("http://ubuntuforums.org/showpost.php?p=7958828&postcount=1").) Among those functions are the builtin camera and microphone. For a quick'n'dirty smoketest I just wanna

[LIST=1]
[*]enable each device
[*]record myself speaking
[*]replay the recording to verify the hardware basically works
[/LIST]

So I'm wondering, can anyone recommend one or more simple (preferably default or preloaded) applications allowing one to quickly test these devices?

Audacity isn't very complex if you're not interested on all the bells & whistles.

You may have to edit 'file > preferences' to select your recording & playback devices,
but if the defaults are not cortrect you would probably have to do that with any application.

1 open audacity

2 click on the round red record button

3 after done recording click on the square stop button

4 click on 'file > export'

5 a box will come up to enter title, artist, etc .. just click OK

6 choose mp3 for the file type, give the file a name & save it

7 when you exit it will ask if you want to save changes, just say no

jdb

---

### Post by ajgreeny on 2009-09-21
Use cheese to check that the webcam works, and sound-recorder (or audacity, if you want more bells and whistles) to check the microphone.  remember that yopu may well need to play with the mixer controls (from the volume icon on the panel) to ensure that "capture" is set to the correct level.

---

### Post by thomasaaron on 2009-09-21
You could also use Skype to test both the mic and the cam.

---

### Post by macabrem on 2009-10-04
I did post this as a separate question, but since I saw it mentioned here, do you have specific instructions or tips for getting Cheese's audio to work?  I've played around with this for over 2 hours and still can't get it working...:confused:

I am able to record with sound recorder with no problems.

---

### Post by thomasaaron on 2009-10-05
Just answered your other post pertaining to cheese.

---

### Post by MattMiller on 2013-03-12
I just wanted to mention that I have a System76 Gazelle version and had trouble myself trying to discover an easy way to enable/disable the microphone. I soon realized that I could by going through the sound menu, and eventually assigned my [Pause] key to mute/unmute via amixer. Also found that Fn+F10 toggles the webcam. 

I recently decided to attempt to write a basic unity application indicator for both and had some success. There is no gaurantee that this will work on anyone elses system and requires some setup but it works great for me. 

For anyone interested here is the link. [https://github.com/mgmtech/sys76_unity_webmic](https://github.com/mgmtech/sys76_unity_webmic)

Eventually I would like to improve the icon (to provide visual status) and package this into a unity application. 

-- Matt

---

### Post by MattMiller on 2013-03-13
aparently I did NOT write an applicatin indicator but rather a nice way to break the sound system on my machine.. -or- its just a coincidence, either way use the above with caution.

---

