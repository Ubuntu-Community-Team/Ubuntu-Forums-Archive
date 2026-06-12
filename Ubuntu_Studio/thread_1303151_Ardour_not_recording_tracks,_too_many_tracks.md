---
title: "Ardour not recording tracks, too many tracks???"
date: 2009-10-27
forum: Ubuntu Studio
---

### Post by homerj742 on 2009-10-27
I have an ardour project, currently there are 11 tracks (I separated the drums kit coming in from hydrogen). 

I'm recording a third guitar part, and no matter what, the track just will not record! I made sure all the connections were correct, even opened up an older project (with less tracks) and was able to record. 

Any ideas as to where I should begin troubleshooting this?

---

### Post by trulan on 2009-10-27
11 tracks is certainly not too many for Ardour.

How are you setting you connections?
I am assuming you have successfully added a blank track for your guitar part, but you can't get any audio into it.  Does the level meter for the track move when you arm the track to record?

Are you setting your connections with Ardour's mixer?  With Jack Control?  With Patchage?  Patchage is my favorite as it lets you see everything that is going on with the connections.

---

### Post by Stochastic on 2009-10-28
Can you import audio into that track and play it?  Is the mute button on in the mixer?

How far do you get during the recording process?  Does the track appear to record an empty track, does the track not arm for recording, does the record button not advance the playhead, etc...?

If you start Ardour from a terminal then open that project are there any error messages on attempted recording?

Oh, and what hardware are you running this on (CPU, RAM, and HD space)?  Is this project on a partition that's full?

---

### Post by homerj742 on 2009-10-28
Thanks for responses guys. It was something dumb! I had punch markers set towards the end of the project. Although they were disabled (via the buttons on the top) Ardour seemed to not want to record outside of them until I removed them completely. 

Then BANG, recording lol

---

