---
title: "Audio input not registering in Ardour"
date: 2011-07-20
forum: Ubuntu Studio
---

### Post by CaseyCaseyCasey on 2011-07-20
I have connected an edirol FA-66 to my computer and have run Ardour.  I plugged my guitar into Balanced Input2 and created two tracks: an Audio track and a Bus track.  But the track meter doesn't seem to register any input.  What have I neglected to do?

---

### Post by jejeman on 2011-07-21
Did you setup jack corectly? Did you connect capture2 with adrour audio track?

---

### Post by sgx on 2011-07-21
> **CaseyCaseyCasey said:**
> I have connected an edirol FA-66 to my computer and have run Ardour.  I plugged my guitar into Balanced Input2 and created two tracks: an Audio track and a Bus track.  But the track meter doesn't seem to register any input.  What have I neglected to do?
The tracks in ardour needs to be armed, and the play button pressed after the record button to begin recording. There may also be a monitoring option to choose. Do the connections appear in qjackctl?
I would install timemachine, and attempt recording, since there is only
one button to begin and stop the recording. Thus knowing if the Fa-66
is getting connected right.

Cheers

---

