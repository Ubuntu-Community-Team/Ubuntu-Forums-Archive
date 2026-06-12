---
title: "Hydrogen synced to Jack transport"
date: 2013-09-15
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2013-09-15
I posted this at Hydrogen's Forums as well, but it looked a bit deserted, so I though I would post here as well:

We've been using Hydrogen in our studio for a little while now and I really like it's simplicity and features, along with the features of Jack. 

 

However, I've run across an issue that is not discussed much on the internet, but it is a key issue and is a "show stopper/Deal breaker." ~in my opinion

 

When I have Hydrogen synced to Jack and Ardour synced to Jack, the only way it syncs right is if you play from the very beginning of a song.

 

Now imagine, you've finished working on the first verse of your song, you're working on the first chorus of your song, and you've got a Snare that's off time.  You now have to start from the very beginning and wait until that pattern comes up to listen for the drum and edit it.  Then you have to start from the beginning again to listen and see if your edit was correct.  This turns a 4 hour drum session into an 8 hour nightmare, where you're ready to trash the song, because you've heard it WAY more than you need to.

 

I had a vocal session yesterday and I had to tell the vocalist to ignore the drums, because he would be singing the first verse while hydrogen was playing some random drum section of the song.  This becomes especially frustrating when your doing multiple tracks of vocals, or anything for that matter.

 

I should be able to click anywhere in Ardour's timeline, hit play, and Hydrogen sync to the correct time code of the song.  Instead, it syncs at a random point in the Hydrogen playlist.  Same thing happens when the transport is used in Hydrogen rather than Ardour. 

 

Either way, it ONLY syncs correctly if played from the very beginning.  Even then, it sometimes doesn't reset to zero and you have to open Hydrogen and spam the rewind button until the playhead reaches zero.

 

Again, I don't want to seem ungrateful for a peice of software that I really like a lot, except for this big elephant in the room that's giving me a brain tumor.

So...

Is there some work around?

 

Some kind of easier way to edit the drums?

 

How do you guys manage it?

Edit:  I downloaded the Hydrogen Git source and built version "0.9.6-fb5a9d1."  It's doing better after I fiddled with the Jacksync master button.  It's really finnicky though.

---

### Post by jejeman on 2013-09-15
Why not use Ardour's MIDI track to play Hydrogen?

---

### Post by pepsifx357 on 2013-09-15
I can't play drum on a keyboard.  Otherwise I'd be doing just that.  I got used to using things like FL Studio and manually adding in patterns on the matrix with a mouse.

---

### Post by jejeman on 2013-09-15
I know what you mean, I used to do that. Making patterns on a drum machine. But now, I just loop between two points and add notes with mouse. Then, copy MIDI parts etc. to make drum MIDI track.

---

### Post by pepsifx357 on 2013-09-15
I can see that in FL Studio or Logic where the piano roll is very nice looking and easy to manipulate.  I don't think there's any other software than those two that makes MIDI editing a pleasure to perform.  I've used Reason, Nuendo/Cubase, Pro Tools, Cakwalk, ect.  I even tried Rosegarden and Muse, but they're all the same.  Very quirky and cumbersome to edit with.  I'm hoping that the Ardour team will really come through with their MIDI editing features.  Right now, It's about the same as any other DAW, which is actually pretty damn impressive, considering Ardour didn't have MIDI not too long ago.  :)

---

### Post by jejeman on 2013-09-16
I've never used FL or Logic that much, so I don't remember how that looks. Actually, FL was always disgusting to me. I have used Reason, Cubase and MIDI editing was just fine.
I know that Ardour is still not good for work with MIDI, and would never recommended it (I said it here because you mention that you record in Ardour). 
I use MusE, and MIDI editing is 0 trouble. For drums you can make your own drum maps, loop the section, and just put in the beat. You can define your own MIDI instruments, so you can have banks, controllers, you can just choose what you need.

---

### Post by christoph-froehner on 2014-09-04
Even if this thread is now one year old. I'm having the same issue as described above by pepsifx357 and would really like to use ardour and hydrogen. I'm using ardour3 (Ardour 3.5.308~dfsg-1) which i installed from the repository and the latest version of hydrogen (0.9.6). Has anyone found a solution to the problem?

---

### Post by christoph-froehner on 2014-09-04
Ok ... Right after posting i started looking into ardour's preferences. After i deactivated ardour as time master (under 'session' -> 'properties') it worked just fine.

Solved it at least for me.

---

