---
title: "BIG BIG boo boo"
date: 2007-07-16
forum: The Cafe
---

### Post by retroP on 2007-07-16
Ok well I was trying to edit a read only text document and I tried to make my user account the exact same as root, so I unchecked everything thinking it'd be the same as root since thats what it seemed root was like.... and well now I can't edit anything, access anything nothing, I've tried to fix this problem on my own but to no avail. I tried using sudo commands but it says this user has no sudo privleges and this incident will be reported.....

 Can anyone please help me out? Is there a type of system restore or some loop hole through all this.... I tried logging in as root but in reading some old posts learned you can't for security reasons... so yeah please some one help me out,I am sooo mad at myself...

---

### Post by sloggerkhan on 2007-07-16
you have to log in as root from a recovery console and change your user permissions.

If you wanted to make your user acount have root level access (probably a bad idea) or at least more access, you probably should have checked boxes, not unchecked them.

You have the option when starting to go to a recovery console.

---

### Post by retroP on 2007-07-16
oh ok, so when it says "press esc"at the bottom when booting up I should press esc then it should be self explainitory from there? or do I access this recovery console some other way?

---

### Post by sloggerkhan on 2007-07-16
You should press escape or whatever key it says, there should be a recovery console option which logs you in as root on a command line. If you want to do stuff via gui, type 
startx
I don't know specifically what you need to change to fix your user, but possible you could do it by starting x and working through the users & groups control panel.

Also, since you have a general problem, the community cafe might not be the best place to post.

---

### Post by retroP on 2007-07-16
> **sloggerkhan said:**
> You should press escape or whatever key it says, there should be a recovery console option which logs you in as root on a command line. If you want to do stuff via gui, type 
startx
I don't know specifically what you need to change to fix your user, but possible you could do it by starting x and working through the users & groups control panel.

Also, since you have a general problem, the community cafe might not be the best place to post.

ok thanks alot I'll try it all out

---

