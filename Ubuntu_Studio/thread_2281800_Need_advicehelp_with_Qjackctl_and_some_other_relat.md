---
title: "Need advice/help with Qjackctl and some other related programs it supports"
date: 2015-06-09
forum: Ubuntu Studio
---

### Post by stevecook on 2015-06-09
Hello Folks. Steve Cook here:

I am currently running Ubuntu Studio and need some help with adjusting a midi/audio setup that involves the use of QJackCTL, Qsynth, VMPK and Rosegarden.

My current setup is as follows:

[[IMG]http://i958.photobucket.com/albums/ae67/stevecook172001/current-rosegarden-setup_zpswhmrjbx5.jpg[/IMG]]("http://s958.photobucket.com/user/stevecook172001/media/current-rosegarden-setup_zpswhmrjbx5.jpg.html")

All of the above components are connected together using QJackCTL. The way they work is: a midi tune is loaded into rosegarden and played. The midi signals are first sent to VMPK, which displays which notes are being pressed as the tune progresses. However, VMPK also passes these midi signals through to Qsynth, Which, in turn, passes them to the system speakers. Thus, the tune is heard throuigh the system speakers in correct time with the keys that are being depressed in VMPk. Meanwhile, I also have my real world external midi keyboard controller attached to VMPK via Qjackctl. This allows me to press the keys on my controller and have these key depressions appear on VMPK as well as have them also passed onto Qsynth and then onto the system speakers. This means I can simply follow what I am seeing on VMPK, in terms of input from Rosegarden, on my midi controller. If I press the same keys on my midi controller as are initially being pumped to VMPK from Rosegarden, the midi song will sound in tune. If I do not, then it will sound out of tune and I will be able to immediately auditorily (as well as visually) recognize that. In short, then, this system allows me to learn a tune by seeing and copying instead of having to read music.

I have made a video of the above setup on You-Tube for a fellow user on another forum. So, it might help to more easily understand my setup by viewing it:

[https://www.youtube.com/watch?v=vRpDbe5hQJE](https://www.youtube.com/watch?v=vRpDbe5hQJE)

Okay, having explained all of the above, I now need to explain what am trying to do with it in terms of extending it's functionality. My proposed setup is:

[[IMG]http://i958.photobucket.com/albums/ae67/stevecook172001/propposed-rosegarden-setup_zpsco8rvbpf.jpg[/IMG]]("http://s958.photobucket.com/user/stevecook172001/media/propposed-rosegarden-setup_zpsco8rvbpf.jpg.html")

I know, diagrammatically, how to setup the proposed arrangement, above. What I don&#8217;t know is how to tell Rosegarden this is where I want the two different tracks to go. Tthat is to say, the two different instruments in the midi file are represented as two separate tracks in Rosegarden. At the moment (with my existing setup), if I send the signal out from Rosegarden to a single instance of VMPK, VMPK only picks up the first track and ignores all others. I currently get round that by merging all tracks in Rosegarden into a single track and then sending that to a single instance of VMPK and this works fine. However, what I want to do is to keep the tracks separate and send them to two separate VMPK keyboards simultaneously, as per my second diagram. Is that possible with Rosegarden? I should say, the reason I want to send the two tracks out to separate VMPK's is twofold. Firstly, my two real world midi controllers are 61 keys each and not full 88 keyboard controllers. Thus, some tunes span a sufficient range of keys as to require me to play with my left hand on one keyboard and my right hand on the other. That is to say, I set my left hand controller to start three octaves lower than the right one. Thus, they overlap by two octaves. Between them, though, I get a full 88 key span. The second reason I want to send different tracks to each of the keyboards is because some of the midi tunes I am wanting to learn are for duets between two instruments. And so, my proposed setup would allow me to effectively playback the two instruments simultaneously from Rosegarden to two instances of VMPK.

Rosegarden appears to allow the sending of the midi signal from each track to separate outputs. But I cant get them to work. so I am obviously doing something wrong. I should make it clear, finally, that I do not have a problem with the external midi controllers themselves in that it is perfectly possible for me to connect them both up to two instances of VMPK and have *them* both play with two separate voices at the same time (in other words, my second diagram, minus Roasegarden). The problem is between Rosegarden and VMPK. 

Please help, if you can.

---

### Post by jejeman on 2015-06-10
Never used Rosegarden, just an idea:
Each MIDI track set to be on different MIDI channel. Set VMPK(s) to listen to different MIDI channels on the same MIDI port.

---

### Post by stevecook on 2015-06-12
Yes, that's what I guessed it might involve. I just cant figure out how to do it, assuming that it is possible,

---

### Post by stevecook on 2015-06-18
In the absence of any help here or anywhere else, I figured out solution myself. Don't have to assign tracks to different channels. Do have to add extra item in playback devices dialogue box and also have to rename both devices. At which point, different tracks can be sent to different devices.

Posted video here:

[https://www.youtube.com/watch?v=FXSyvIfGV-k](https://www.youtube.com/watch?v=FXSyvIfGV-k)

---

