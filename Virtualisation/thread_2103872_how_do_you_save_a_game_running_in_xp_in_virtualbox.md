---
title: "how do you save a game running in xp in virtualbox?"
date: 2013-01-11
forum: Virtualisation
---

### Post by soulresonence on 2013-01-11
Hi all,
I'm running a  windows XP machine  in virtual box. Had no problems setting up and running. Is there any way to make a game save and not get lost after shutdown?
At the moment I've been saving the machine state.
any help appreciated

---

### Post by Nathanael Culver on 2013-01-11
> **soulresonence said:**
> Is there any way to make a game save and not get lost after shutdown? At the moment I've been saving the machine state.

What's the game? Does it have built-in save functionality that's somehow not working in VB? More details on exactly what you're trying to accomplish would be helpful.

Why not use snapshots? They allow you to permanently save a machine state and return to it whenever you'd like. And you can save as many snapshots as you'd like. Of course, if you're just looking for a temporary "pause", saving the machine state will do just fine.

There are good intros to snapshots >[here]("http://ryantrotz.com/2011/12/virtualbox-snapshots-and-vmis/")< and >[here]("http://www.virtualbox.org/manual/ch01.html#snapshots")<.

---

### Post by CharlesA on 2013-01-11
Snapshots can eat disk space like crazy.

@OP: What game are you trying to save in?

---

