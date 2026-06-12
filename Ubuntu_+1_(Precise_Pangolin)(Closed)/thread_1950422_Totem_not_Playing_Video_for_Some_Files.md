---
title: "Totem not Playing Video for Some Files"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Confused Computer User on 2012-03-31
hi all,

It's been a while since I've posted on the forum. Since Ubuntu switched to unitity to be precise. That aside I think that Precise has actually irroned out most of the kinks in the GUI and I'm pretty happy with the results so far.

That beeing said I have an issue with totem player. It plays some videos but for others it plays the audio only. Further more for those where only the audio is played, Nautilus displays a standard movie thumbnail instaed of the expected snapshot from the clip.

Prior to Ubuntu I had Fedora 16 which played the same files in totem without fail.

Also the files play without issues in VLC.

Here is the output of totem in the terminal:

> $ totem "Video 1.mp4"

(totem:30004): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'

and

> $ totem "Video 2.flv"

(totem:30279): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


Can some one tell me what is going on?

---

### Post by dcstar on 2012-03-31
> **Confused Computer User said:**
> hi all,

It's been a while since I've posted on the forum. Since Ubuntu switched to unitity to be precise. That aside I think that Precise has actually irroned out most of the kinks in the GUI and I'm pretty happy with the results so far.
.......

Is this just happening after the latest updates?

---

### Post by Confused Computer User on 2012-03-31
> **dcstar said:**
> Is this just happening after the latest updates?

I installe Precise 64-bit (beta 2) yesterday. I hadn't tried it previously nor can I say if it is due to recent updates.

---

### Post by mc4man on 2012-03-31
It may be worthwhile to idenify the encoding of the problem video's, totem (gstreamer) has shown issue with some avc1 Baseline@L2.1 or Baseline@L1.1 files

mediainfo is now available in repo, maybe install and open your vid(s) in
(mediainfo-gui is probably what you'll want

---

### Post by Confused Computer User on 2012-03-31
> **mc4man said:**
> It may be worthwhile to idenify the encoding of the problem video's, totem (gstreamer) has shown issue with some avc1 Baseline@L2.1 or Baseline@L1.1 files

mediainfo is now available in repo, maybe install and open your vid(s) in
(mediainfo-gui is probably what you'll want

Thanks, the two videos both have Baseline@L2.1.

What are my options?

Wait for update or is there some fix?

It's not a major problem just annoying.

---

### Post by mc4man on 2012-03-31
You could re-encode or if not too long (or you have the time) use vlc to record the video's

I'm pretty sure the repo vlc can do this - open vlc > View > Advanced Controls
Then start your vid & quickly click the 'record' button. It's a real time recording, the file will be saved in Videos or Home folder & will play in totem (will be recorded/saved as a .mp4

---

### Post by Confused Computer User on 2012-03-31
> **mc4man said:**
> You could re-encode or if not too long (or you have the time) use vlc to record the video's

I'm pretty sure the repo vlc can do this - open vlc > View > Advanced Controls
Then start your vid & quickly click the 'record' button. It's a real time recording, the file will be saved in Videos or Home folder & will play in totem (will be recorded/saved as a .mp4

Not too excited about the re-encoding. There is ususally some loss of quality from one format to the next.

Guess it should be done at one point.

I could use winFF to do the conversion faster since it can handle multiple videos at a time rather than opening one at a time and recording them.

Going off on a tangent now, do you know what is a general codec (video and adio) that can be played on Windows and on Mac.

P.S.
Thanks for the help so far. I really appreciate your perservirence.

---

### Post by Baldrick_NZ on 2012-03-31
I'm not sure whether this will be of any help, but it might.

[https://answers.launchpad.net/openshot/+faq/1040](https://answers.launchpad.net/openshot/+faq/1040)

It refers to the openshot video editor that was having probs with regarding not having the right codecs.

Follow the instructions, and report back. 

Hope it helps.

---

### Post by mc4man on 2012-03-31
> **Confused Computer User said:**
> Not too excited about the re-encoding. There is ususally some loss of quality from one format to the next.

Using vlc to record does not re-encode, just puts in an different container w/ headers that are good for totem
Edit: at least that was my impression..

---

### Post by Confused Computer User on 2012-03-31
> **mc4man said:**
> Using vlc to record does not re-encode, just puts in an different container w/ headers that are good for totem
Edit: at least that was my impression..

It is possible you are right...But doesn't the record option produce a second file? If that happens then that would mean it's encoding.
By the way I'm a semi noob. So if i say something silly feel free to correct me.

> **Baldrick_NZ said:**
> I'm not sure whether this will be of any help, but it might.

[https://answers.launchpad.net/openshot/+faq/1040](https://answers.launchpad.net/openshot/+faq/1040)

It refers to the openshot video editor that was having probs with regarding not having the right codecs.

Follow the instructions, and report back. 

Hope it helps.

well the problem videos opne in openshot whithout fail and without the need to apply the modifications sugested in your link. So i'm a bit stuck on this.

Thank you for the sugestion... worth a shot.

---

### Post by mc4man on 2012-03-31
I'm not exactly sure what vlc does when recording but it really doesn't look like it's doing a sout with trancoding. If it was then cpu use would have to rise & it doesn't
I think it's just doing a sout to a new file, ect.

---

### Post by cariboo on 2012-03-31
@Confused Computer User, do you install the ubuntu-restricted-extras meta package as part of the install process? I'm not sure exactly what it installs, as I've never had a problem viewing any video's, so I haven't bothered to look what is included in the meta-package.

---

### Post by Confused Computer User on 2012-03-31
> **cariboo907 said:**
> @Confused Computer User, do you install the ubuntu-restricted-extras meta package as part of the install process? I'm not sure exactly what it installs, as I've never had a problem viewing any video's, so I haven't bothered to look what is included in the meta-package.

Yes... I have to if I want to watch dvds. the issue is that VLC and Openshot both run the videos but totem fails to open the video. Audio works great otherwise.

> **mc4man said:**
> I'm not exactly sure what vlc does when recording but it really doesn't look like it's doing a sout with trancoding. If it was then cpu use would have to rise & it doesn't
I think it's just doing a sout to a new file, ect.

makes sense based on your observations. thanks for shedding a light on my question.

---

### Post by mc4man on 2012-03-31
I've never filed a bug on this for a couple of reasons, the least of which is providing a sample file or link to a small sample without any 'legal' questions.

Did file a round-about bug on minitube requesting allowing the vlc backend instead of only the gstreamer one. Minitube users are definitely going to be affected, quite a number of youtube vids will only play sound & no video, most are the above mentioned encodes though not just limited to.

[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

(if you run vlc from cli with vlc -vv & do a record should show what;s up..

---

### Post by Confused Computer User on 2012-04-01
> **mc4man said:**
> I've never filed a bug on this for a couple of reasons, the least of which is providing a sample file or link to a small sample without any 'legal' questions.

Did file a round-about bug on minitube requesting allowing the vlc backend instead of only the gstreamer one. Minitube users are definitely going to be affected, quite a number of youtube vids will only play sound & no video, most are the above mentioned encodes though not just limited to.

[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

(if you run vlc from cli with vlc -vv & do a record should show what;s up..

Understood. In that case there isn't much to be done in that case except to wait for some sort of update or continue to use VLC. Or as you sugested do the VLC trick.

Now can someone tell me if there is any similarity between the totem player in Fedora and the one in Ubuntu. Because this is why I'm lost. Fedora did not have issues opening these in totem.

Then again fedora was 32-bit while Ubuntu is 64-bit. Can factor in into what's available in terms of video codecs?

Thank you again for the support.

---

### Post by mc4man on 2012-04-03
Decided to cut a small sample file & report bug on, we'll see..
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

---

### Post by Confused Computer User on 2012-04-03
> **mc4man said:**
> Decided to cut a small sample file & report bug on, we'll see..
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

fingers crossed:-o

Thank you for the continued support.

---

