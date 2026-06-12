---
title: "no microphone"
date: 2007-05-18
forum: System76 Support
---

### Post by perce on 2007-05-18
Hi,

I'm still fighting with my new Darter, more and more depressed: the microphone doesn't  work with skype. Do you have any idea how to solve the problem?

---

### Post by icechen1 on 2007-05-18
> **perce said:**
> Hi,

I'm still fighting with my new Darter, more and more depressed: the microphone doesn't  work with skype. Do you have any idea how to solve the problem?


Search the forum,there are some solutions that might work for you.
I have the same problem too,it can be considered as a bug because lots of user have this problem.
Do you have a HDA Intel card?If yes you might got the bug.

---

### Post by thomasaaron on 2007-05-18
Hey, guys. I don't think it's a bug.
The Darter can be a little tricky to properly configure.

I've requested that a customer who just got Skype up and running post screenshots of his settings here. My Darter is a little different than yours, and screenshots of my settings have not been very helpful to others. But his Darter is the same as yours.  Standby...

(My screenshots are on the other forum (..system76[dot]com/forums) in the hardware section...

Best,
Tom

---

### Post by perce on 2007-05-18
I looked at those screenshots, and I've tried to "translate" for my computer, which had different menus, but with no luck. I'll wait for the new screenshots, and pray.

---

### Post by perce on 2007-05-20
The problem is almost solved!

After some search in the Ubuntu forums and wiki, (the page [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) was particularly helpful) and some random tries, I came up with this solution: 

1) I added the line options snd-hda-intel model=ref to the file /etc/modprobe.d/alsa-base
2) in alsamixer I changed the column <input so> from mic to <front mic>, and I put at maximum volume all the columns in the capture section.

Now I have micorphone in skype, and also in ekiga, however the quality if the sound is poor: it has a background noise in skype, and it looks like the demon possessed voice of an horror movie in ekiga. If you have a suggestion on how to improve the sound quality you're welcome.

EDIT: after a while skype loses the microphone again. If I close skype and reopen it, the microphone comes back to life. All this is very strange.

---

### Post by klato on 2007-05-20
I have a problem with my mic, but the issue is that I can't record anything using sound recorder.  I hit Record, say something, hit Play, and nothing plays back (even though the mic volume is maxed and I can hear myself talking)...haven't tried Skype yet.  Gazelle Performance/Feisty

---

### Post by perce on 2007-05-20
> **klato said:**
> I have a problem with my mic, but the issue is that I can't record anything using sound recorder.  I hit Record, say something, hit Play, and nothing plays back (even though the mic volume is maxed and I can hear myself talking)...haven't tried Skype yet.  Gazelle Performance/Feisty

I've tried, and it's the same for me. In another forum Tom said that one should use gnusound to record, and set it to OSS (at least for the Darter, I don't know about he gazelle.

---

### Post by riseringseeker on 2007-05-21
> **thomasaaron said:**
> Hey, guys. I don't think it's a bug.
The Darter can be a little tricky to properly configure.

I've requested that a customer who just got Skype up and running post screenshots of his settings here. My Darter is a little different than yours, and screenshots of my settings have not been very helpful to others. But his Darter is the same as yours.  Standby...


I think Tom is talking about me.  Sorry I hadn't replied earlier, I've been traveling even more than usual these past few days.

I was tearing my hair out getting skype to work for me, or rather the mike to work with skype.  Honestly, though he did his best, and I admire his tenacity when it comes to try to solving any problems system76 customers have, Tom's settings were really of little use when it came to doing this.  Skype is **very** important to me, since I am out of the country as much as I am.  It makes staying in touch with family and friends **so** much easier - unless I am in the UAE.  (Sometime I will have to post and asked how to spoof an IP address to get around that!)

I am using alsamixer, and I guess the easiest thing is to just show the screen shots of what I have, that work just fine with skype.  I have noticed, depending on the phase of the moon, or if it's St Bastille day, skype sometimes needs to be closed, and then reopened before it'll work, or work on a second call.  Rarely, you may even need to restart alsa.

```
 sudo /etc/init.d/alsa-utils restart
```

Please let me know if this works for you.  Given how much time Tom spent chasing down what I considered a minor problem, I feel I owe him, and hey, I have always been amazed at the helpfulness and friendlness of the Linux community, so whenever I get the chance to give back, I take it!

---

### Post by perce on 2007-05-21
Strange, quite different from what made my microphone work: I had to chose front mic over mic.

---

### Post by riseringseeker on 2007-05-21
> **perce said:**
> Strange, quite different from what made my microphone work: I had to chose front mic over mic.

But it **does** work for you now?

On mine (and as far as I know, they should be the same), the front mic is the built-in one down by the Ubuntu sticker.  I got that one to work as well, but not too well, given the feedback level.  It also seems to give a more muffled "talking with your head in a trash can" type sound quality.

I did notice that the headset I have is a little touchy when plugging in - but I got it in Hong Kong for $2, I really did not expect as much sound quality as it has, but I figured for $2 how could I loose?  Bottom line is I have to take extra effort when plugging it in.  I think it's the cheap headset, but might be the brand new jack on the darter - who knows.

---

### Post by perce on 2007-05-21
> **riseringseeker said:**
> 

But it **does** work for you now?



With my setting it does work, with yours, I haven't tried yet.

> 

On mine (and as far as I know, they should be the same), the front mic is the built-in one down by the Ubuntu sticker.  I got that one to work as well, but not too well, given the feedback level.  It also seems to give a more muffled "talking with your head in a trash can" type sound quality.



For me it's the opposite: I got a better sound with the bilt-in microphone than with an external one.

---

### Post by seekers on 2007-05-28
The problem is almost solved!

After some search in the Ubuntu forums and wiki, (the page [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) was particularly helpful) and some random tries, I came up with this solution:

1) I added the line options snd-hda-intel model=ref to the file /etc/modprobe.d/alsa-base
2) in alsamixer I changed the column <input so> from mic to <front mic>, and I put at maximum volume all the columns in the capture section.

Now I have micorphone in skype, and also in ekiga, however the quality if the sound is poor: it has a background noise in skype, and it looks like the demon possessed voice of an horror movie in ekiga. If you have a suggestion on how to improve the sound quality you're welcome.

EDIT: after a while skype loses the microphone again. If I close skype and reopen it, the microphone comes back to life. All this is very strange.

Perce you are a life saver.  This worked for my intel sound card.   The recording is not too bad.  I also am using Skype and this worked.   Good work!

---

### Post by riseringseeker on 2007-06-20
This justs getting weirder and weirder.  I got a notice of an upgrade available for skype (I had skype repository enabled).  When I updated, I had 1.4x **BETA**.  Skype is too important to me to rely on a beta version. The beta did not work at all for me anyway, and it lacked many features, such as contact groupings, the tabs across the top, any menus choices at all.  It took some doing to downgrade again, but I did. 

I tried the downgraded version with the settings I showed above in this thread and it worked fine.  Then, this morning I tried to call home.  I heard my wife, but she could not hear me at all.  I tried and tried tweaking the settings and was getting more than a little tired of the "Welcome to skype call testing center" voice, when I tried to change the options  in the volume control to Front Mic, as opposed to Mic.

It worked, but the voice quality was bad, lots of humming/buzzing in the background and when I got hold of my wife, she said it sounded also as if I had my head in a barrel.  I needed to go to breakfast, she was getting ready for bed, so the call did not last long.

Just because I am perverse, I opened volume control again and tried switching back to Mic from Front Mic, call skype test call and it worked great!  Good voice quality, no hum or buzz.

I cannot understand what happened here, but thought I would pass it on.

---

### Post by perce on 2007-06-20
Just about wierdness: I had to reinstall a couple of weeks ago because of a bad crash. With the clean install microphone works without the line options snd-hda-intel model=ref I needed before in the file /etc/modprobe.d/alsa-base. Both the options mic and front mic in Alsamixer now work, and they actually switch the input between the external and the built-in microphone.

---

### Post by jaycee15* on 2007-06-23
My Skype works fine, sound is excellent now.  I too had microphone problems before I made the following changes:
1.  Go to Volume control screen in Ubuntu and change device to Realtek OSS Mixer
2. In Skype, go to Tools/options/sound devices and change Audio System to Use from Alsa to OSS.
 I use Feisty Fawn on a S76 Pangolin laptop.

---

### Post by cleardays on 2007-07-30
> **perce said:**
> The problem is almost solved!

After some search in the Ubuntu forums and wiki, (the page [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) was particularly helpful) and some random tries, I came up with this solution: 

1) I added the line options snd-hda-intel model=ref to the file /etc/modprobe.d/alsa-base
2) in alsamixer I changed the column <input so> from mic to <front mic>, and I put at maximum volume all the columns in the capture section.

Now I have micorphone in skype, and also in ekiga, however the quality if the sound is poor: it has a background noise in skype, and it looks like the demon possessed voice of an horror movie in ekiga. If you have a suggestion on how to improve the sound quality you're welcome.

EDIT: after a while skype loses the microphone again. If I close skype and reopen it, the microphone comes back to life. All this is very strange.

Hi, thanks! I follow you, it works!

---

### Post by vbarzov on 2007-09-01
Hi, I read all the posts and I tried everything and my stupid microphone just refuses to work. No, it is not broken. I cannot record any sound with the sound recorder, even though everything is unmuted and to the max (the only complication being that I have "capture", "capture mux", and "digital" fields in the alsamixer, all of which are unmuted and set to max). Anybody any idea?

Thanks,

Vladimir

---

### Post by perce on 2007-09-01
What is your model?

---

### Post by vbarzov on 2007-09-01
I am running Ubuntu 7.04 Feisty Fawn. The microphone is a street brand, but is new. It does work. I tried Alsamixer and OSS, but the sound recorder does not produce anyhting but an empty file with "invalid parameters". The ultimate goal is to run Skype.

---

### Post by perce on 2007-09-01
> **vbarzov said:**
> I am running Ubuntu 7.04 Feisty Fawn. The microphone is a street brand, but is new. It does work. I tried Alsamixer and OSS, but the sound recorder does not produce anyhting but an empty file with "invalid parameters". The ultimate goal is to run Skype.

I mean the model of your computer.

---

### Post by vbarzov on 2007-09-01
Model is Dell Inspiron, but it finally worked -- it had simply needed a restart. Must be due to either the line that you advised adding in one of your previous postings or the fact that I installed the newest alsamixer utils. Now my volume settings menue looks like a Christmas tree for that matter.

Thanks a lot!

Vladimir

---

### Post by raananschwartz on 2007-09-03
wierd indeed.


_______________
[http://iplobster.com]("http://iplobster.com")

---

### Post by victimSurvivor on 2008-06-23
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 
Running the first command here ie the installing the required tools and kernel headers did it for me... None of alsa settings worked for me. Thanks for the person who provided this link and this is so active a forum for new people like us.

---

