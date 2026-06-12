---
title: "As long as it works, I'm happy but..."
date: 2014-12-24
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-12-24
I just did a fresh install of Vivid Xubuntu on my netbook. When I closed the lid, Xubuntu would go to sleep, but when waking it up, all I got was a black screen with no cursor. Using Google to find a solution, I found a link on a facebook to a solution, open the setting menu and go to lightlocker, turning it off then back off again solved the problem, but now when the system comes back up again, the Display properties window is open. This happens every time I open the lid and log on. Has anyone else seen this, and is there a work-around for it?

---

### Post by Elfy on 2014-12-25
This issue is mostly driving us up the wall - as soon as one thing is fixed something else breaks - but it appears at times to be a bit hardware specific too.

Nothing I've tried to confirm the issue with has it.

---

### Post by sudodus on 2014-12-25
See also this thread: [Suspend problem when running LiveUSB from USB 3.0 port]("http://ubuntuforums.org/showthread.php?t=2256743")

---

### Post by ventrical on 2014-12-25
I am testing this in live USB mode. I close the lid, it suspends but then opens into  logon screen prompting for user name and pswrd. What are these user name and pswrds?

Thanks 

Regards..

---

### Post by ventrical on 2014-12-25
Could be a bug with lightdm. I Ctrl+Alt+F1 and then:

```

sudo service lightdm restart

```

and get the below. Also Ctrl+Alt+F1 and lightdm restart will break network connection.

edit:Network fixed by installing drivers.

---

### Post by ventrical on 2014-12-25
> **cariboo907 said:**
> I just did a fresh install of Vivid Xubuntu on my netbook. When I closed the lid, Xubuntu would go to sleep, but when waking it up, all I got was a black screen with no cursor. Using Google to find a solution, I found a link on a facebook to a solution, open the setting menu and go to lightlocker, turning it off then back off again solved the problem, but now when the system comes back up again, the Display properties window is open. This happens every time I open the lid and log on. Has anyone else seen this, and is there a work-around for it?

Just did fresh install with daily-live. What I get is similar black screen. The, touch mouse pad and logon screen comes up. Enter logon and screen goes back to black.

---

### Post by ventrical on 2014-12-25
This works but I get a whole new theme when it wakes from suspend.

---

### Post by ventrical on 2014-12-25
Open from suspend with Lightlocker off vid clip (too small for youtube).

edit: Not too small :)

[https://www.youtube.com/watch?v=Iwx1Q8gxrTk&feature=youtu.be](https://www.youtube.com/watch?v=Iwx1Q8gxrTk&feature=youtu.be)

---

