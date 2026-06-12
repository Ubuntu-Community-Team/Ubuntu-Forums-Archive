---
title: "Best Way to Record a Google Talk Phone Session via Ardour &amp; Jack"
date: 2015-06-22
forum: Ubuntu Studio
---

### Post by Joshua_Crockett on 2015-06-22
Would anyone have any advice on how to do this effectively? I'm currently patching my phone into our mixer when we place phone calls, but it would be way more efficient if I had the ability to use google voice while Jack is running.

I have VLC and Ardour, both of which are "Jack aware" and work while the audio server is running, but I find that since things like Firefox don't interface with Jack, I can't really use Google Voice as my method of making phone calls. 

Does anyone have any advice on how to possibly get Firefox to become "Jack aware" or how I might otherwise be able to use Google Voice while my Jack server is running? Any advice is appreciated! Thank you!

PS: Skype is also an option if this works with Jack, and I certainly can give that a try if that's an option.

---

### Post by TheFu on 2015-06-22
I've never heard of "jack" - always record audio using audacity. If I need video with the audio, then using OBS to record both stream works or if it is a screen session, simplescreenrecorder works. SSR works for HTML5 and flash content, I'm positive.  Never tried it with g-voice - use phones for that.

Doesn't g-voice have a way record the conversation?  Yep.
> Once you've enabled it you can turn it on during a call by pressing 4 at any time to record your incoming calls. You can do it when you first accept a call, or any time after it's started. To stop the recording, press 4 again or hang up.

It's not currently possible to record outbound calls made through your Google number at this time.

Doubt any of this will help you. Sorry.

---

### Post by dawiba2 on 2015-06-23
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio)

Hope this helps.

---

### Post by SonnyE on 2015-06-28
+dawiba2  I was wondering about why Jack interferes with playing any videos for me (YouTube or Totem video player) where I have to kill jackd to get them to play. Thanks for the info.

---

