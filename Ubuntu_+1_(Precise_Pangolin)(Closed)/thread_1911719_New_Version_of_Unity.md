---
title: "New Version of Unity"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jdogzz on 2012-01-19
A week or two ago I was updating my system and after a reboot, one of the updates apparently upgraded Unity to a vastly improved version. It made the bar appear slightly darker than usual, it had what looked like the makings of a resize button in the bottom right of the menu, and it had smooth-scrolling in the app menus. Overall it had a much nicer feel to it. However, after a subsequent update it was removed. Did anyone else see this, and if so do you know where it went? I feel disappointed to see it released then taken away immediately after.

---

### Post by zika on 2012-01-19
> **Jdogzz said:**
> A week or two ago I was updating my system and after a reboot, one of the updates apparently upgraded Unity to a vastly improved version. It made the bar appear slightly darker than usual, it had what looked like the makings of a resize button in the bottom right of the menu, and it had smooth-scrolling in the app menus. Overall it had a much nicer feel to it. However, after a subsequent update it was removed. Did anyone else see this, and if so do you know where it went? I feel disappointed to see it released then taken away immediately after.

[http://ubuntuforums.org/showthread.php?t=1905631](http://ubuntuforums.org/showthread.php?t=1905631)

---

### Post by Jdogzz on 2012-01-19
Thank you!:) I will add those repositories and install the packages right now:)

---

### Post by Jdogzz on 2012-01-19
Not quite there I'm afraid:( I installed the package from the link you provided and it's still not what I saw. Is there a Unity 6.0 in the works by any chance? The one I saw was way more developed than this one.

---

### Post by cariboo on 2012-01-19
To keep up on Unity development, have a look [here]("https://launchpad.net/unity").

---

### Post by xyzzyman on 2012-01-19
Were you actually in unity 2d?

---

### Post by effenberg0x0 on 2012-01-19
@OP
At some point, there was an idea for a resizable dash. See if what you remember using looked like the **video** in [this link]("http://www.omgubuntu.co.uk/2011/03/latest-unity-update-adds-animated-dash-drag-and-drop-more/"). Back then, I *think* someone had this merge proposal in a PPA. But honestly, we have tested so many things, I'm not 100% sure it it was really in a PPA or if I had compiled it.  But if it really was in a PPA, maybe you had added it to give it a try.

And, to be completely sure, you could tell us what PPAs you have there.
Or, to make it easier, you can copy the code below, paste it in a terminal, and copy/paste the output back here.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep "deb http" | sed -e 's|deb [http://||]("http://%7c%7c/")'  | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e  's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e  's|main||' | tee -a /$HOME/ppa-sources.list; done 
```

---

### Post by mc4man on 2012-01-19
> **xyzzyman said:**
> Were you actually in unity 2d?
That sounds like the most likely explanation.

(though not sure about the resize button in Dash, at least here it's gone but I'm using a ppa unity-2d

---

### Post by Jdogzz on 2012-01-19
@cariboo907 Bookmarked it and I'll keep checking back every day:)

@xyzzyman I was in the normal version of Unity, not 2d, unless an update temporarily changed that for some unknown reason.

@effenberg0x0 That looks extremely similar to what I saw. I'm guessing that was tested briefly in the development release but then removed?
And here is the output of the command you posted:

> ppa:chromium-daily/ppa  
dl.google.com/linux/chrome/deb/ stable 
dl.google.com/linux/chrome/deb/ stable 
dl.google.com/linux/talkplugin/deb/ stable 
ppa:myunity/ppa  
ppa:tualatrix/ppa  
ppa:ubuntu-mozilla-daily/ppa precise 
ppa:ubuntu-mozilla-daily/ppa precise

---

### Post by effenberg0x0 on 2012-01-20
> **Jdogzz said:**
> @effenberg0x0 That looks extremely similar to what I saw. 

When you mentioned the resize control in the dash bottom/right and a smoother scroll of icons, I immediately remembered this test...  
> **Jdogzz said:**
> I'm guessing that was tested briefly in the development release but then removed? And here is the output of the command you posted:
I don't think so, it shouldn't work like this. A code change/feature implementation is generally proposed first. People receive a notification and compile the code proposal (locally, not published yet) to review it. Then if it's non-UI (i.e. code improvement), the reviewers opinions and votes count and the proposal is merged if it's right. But if the proposal is UI related, the process is a lot more complicated and most merge proposals are denied. 

Best shot would be if you had added some PPA that had this merge proposal, which is not the case according to the PPAs you posted. So I can't explain how you had that installed if you didn't build Unity and the Merge Proposal yourself. Does anyone else uses your PC?

---

### Post by Jdogzz on 2012-01-20
Nope, I'm the only one who uses it. I thought it was strange too that it was so sudden. Maybe it was accidentally uploaded?

---

### Post by 1roxtar on 2012-01-20
> **Jdogzz said:**
> A week or two ago I was updating my system and after a reboot, one of the updates apparently upgraded Unity to a vastly improved version. It made the bar appear slightly darker than usual, it had what looked like the makings of a resize button in the bottom right of the menu, and it had smooth-scrolling in the app menus. Overall it had a much nicer feel to it. However, after a subsequent update it was removed. Did anyone else see this, and if so do you know where it went? I feel disappointed to see it released then taken away immediately after.

Do you think that perhaps initially your computer did boot into Unity 2D, then after subsequent updates, your video drivers were updated and you later booted into regular Unity 3D?  I'm just saying because this has happened to me.  The Unity 2D dash is slightly darker with a resize button on it's lower right-handed corner.  I get this especially with computers with ATI graphics.

---

### Post by Jdogzz on 2012-01-20
That must have been what happened, because Unity 2D looks like exactly what I saw, except I don't see a resize button. But nevertheless, it looks like Unity 2D was the interface I used that day, and I must say for the most part it surpasses Unity 3D in every way. Why can't we see these features in Unity 3D?

Also, it seems that Unity 3D has been mysteriously removed from my computer, so I'll be in 2D exclusively until that gets fixed.

---

### Post by 1roxtar on 2012-01-22
> **Jdogzz said:**
> That must have been what happened, because Unity 2D looks like exactly what I saw, except I don't see a resize button. But nevertheless, it looks like Unity 2D was the interface I used that day, and I must say for the most part it surpasses Unity 3D in every way. Why can't we see these features in Unity 3D?

Also, it seems that Unity 3D has been mysteriously removed from my computer, so I'll be in 2D exclusively until that gets fixed.

I love Unity 2D.  It is much faster and I like the darker dash look compared to Unity 3D's version.  If I could resize the side bar Launcher and get the accordian stack on 2D, I would use it full time.

---

