---
title: "Negative UX for Volume Control in Xubuntu (for VoIP)"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-06
While running Skype under Xubuntu 12.04 Beta2 (i386) I discover the new Volume Control window is more difficult to work with, particularly for voice conferencing.  This is compared to previously using Ubuntu 10.10.

1.  Cannot see both input and output at the same time.  I must tab between them to go back and forth.  Previously all volume controls were on one view.  This slows down by ability to respond to loud noises, or unmute my mic when someone asks me a question.

2.  The mute button does not work if you have already pressed it before, unless you move the mouse OFF the button and then back ON.  Previously I could keep the mouse in the same position over the button all the time.  This causes an even slower response to questions in a conference.

3.  The input volume control adjusts itself (upward) and defeats my ability to reduce background noise from my room getting into conversations.  When I am unmuted, and start to speak, or if there are other noises, it starts to move the control levels up automatically, which increases the background noise to a level that disrupts the conference.

I don't know if this is because of a change to Xubuntu or a change to 12.04.  But I give a definite "minus minus" to Volume Control now.  Skype is the exact same .deb file as previously used on Ubuntu 10.10.

```
0df02583896d01a78817426008cd1d9c  skype-ubuntu_2.2.0.35-1_amd64.deb
cf392f3d627654ff1ba37605969d14c7  skype-ubuntu_2.2.0.35-1_i386.deb  <-- I installed this one
```Maybe the developer is thinking only in terms of music?  Even if so, I think he didn't consider classical music.

I guess I do need to learn how to do GUI programming some day (already have 30 years experience with C but zero with GUI APIs).  I have seen a general trend of UX regression in a number of apps over the past few years.  If I were to do this app, I would also add keyboard buttons to work the levels and mutes during VoIP conversation (when keyboard focus is on the Volume Control, with a user option to lock that focus like in a modal window with an easy escape).  And I would have controls locked by default.  The option to do dynamic ranging can have its uses in some cases, but I do not think it should be the default.

---

### Post by Skaperen on 2012-04-10
A colleague found that Skype has an option to control Pulse's audio setting.  That might solve #3.  But #1 and #2 remain UX issues.

---

