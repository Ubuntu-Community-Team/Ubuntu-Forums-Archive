---
title: "how to create your own sound schemes"
date: 2010-11-04
forum: The Cafe
---

### Post by brandenmikal on 2010-11-04
recently i posted a blog on 3 wonderful sound schemes for ubuntu users. now i'm posting a blog on how to create your own and instantly have your own sound schemes. 

things you'll need: 

-gedit (text editor) 
-audacity (audio editor) 

step 1 - open "audacity" and take your .wav or .mp3 files and import them into the program. once imported; export in the .ogg vorbis format. .ogg vorbis is the ONLY format accept by ubuntu because it is the free format and it's open source. 

step 2 - create a folder with the name of your sound scheme. then create a folder inside that folder called "stereo" and a file named "index.theme" 

step 3 - rename all of your sounds to fit with the actions you want them to sound on. look at usr/share/sounds/ubuntu for help on this matter. then import your newly named sounds into the "stereo" folder inside your new sound scheme folder. 

step 4 - write the "index.theme" file in gedit (text editor) 

copy and paste the following and put your sound scheme name in the "name=" area. 


[Sound Theme] 
Name= 
Directories=stereo 

[stereo] 
OutputProfile=stereo 


now save the newly written file and make sure it is inside the sound scheme folder beside the "stereo" folder.  then after logging into ROOT; import the sound scheme folder into the file system directory; "usr/share/sounds" 

now you can simply click on the speaker icon on the top panel and select "sound preferences" then select from the dropdown menu in the effects tab.

---

### Post by bjnueva8623 on 2010-11-23
Can you link me to your blog about the 3 sounds schemes? Thanks in advance.

---

### Post by brandenmikal on 2010-11-24
> **bjnueva8623 said:**
> Can you link me to your blog about the 3 sounds schemes? Thanks in advance.

sure :]

here they are:

[http://bmikal.limewebs.com/blog#nabble-td1839513](http://bmikal.limewebs.com/blog#nabble-td1839513)
[http://bmikal.limewebs.com/blog#nabble-td1832590](http://bmikal.limewebs.com/blog#nabble-td1832590)
[http://bmikal.limewebs.com/blog#nabble-td1832660](http://bmikal.limewebs.com/blog#nabble-td1832660)

enjoy!

---

