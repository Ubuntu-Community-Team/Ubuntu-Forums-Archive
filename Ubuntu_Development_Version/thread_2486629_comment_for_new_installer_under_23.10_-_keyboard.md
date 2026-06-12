---
title: "comment for new installer under 23.10 - keyboard"
date: 2023-05-06
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-05-06
Hello,

the new installation process of ubuntu is not new under Mantic Minotaur. It had already started from Lunar Lobster where it had some (serious) issues that in the process were getting better and better. Now that a new version is under way, I fired it up and I noticed the following:
1) the installation doesn't hung and the display of the first image of the installation process has improved a lot, time-wise
2) it is still slow overall though, without showing any progress 
3) there is no meaning of choosing a non-english keyboard

and the last one is my comment: during installation one has the option to choose one's keyboard. I can do so by typing only a couple of characters. I follow the slideshow with the available options until the credentials of the new installation are required. Typing any name as my name, using different keyboards (I tried two different ones) is working fine. The problem arises when the computer name is required: it doesn't pick up non-english characters. Maybe in general non-latin ones (haven't checked it). 

So my question is: what is the meaning of detecting one's keyboard if one cannot change it to english during installation. I have the option to change it via settings, which not only makes the installation even harder for it to finish, but also is irrelevant to the installation process.

Since english/latin characters are required during installation, I suppose that it might be a nice idea for the availability of switching keyboards during installation, when a non latin keyboard is chosen. I do know that this  concerns a minor number of installations, yet this might be something that could be implemented in the future.

Regards!

---

### Post by corradoventu on 2023-05-07
non-english or non-latin keyboard? I had no problem installing in English with an Italian keyboard.

---

### Post by Claus7 on 2023-05-07
Hello,

> **corradoventu said:**
> non-english or non-latin keyboard? I had no problem installing in English with an Italian keyboard.

thank you for your answer once again. From what I get is that using an Italian keyboard you didn't have any problem during installation of mantic: you could use it in order to fill in any information that was required during installation. So the answer to your question goes towards non-latin keyboards. I haven't checked other keyboards. Navigating back and forth wasn't an easy task at the time, at least using a fresh mantic development iso under virtualbox. The process wasn't smooth, unless the procedure was followed as intended. 
Using Hellenic (Greek) keyboard, it didn't allow me to proceed the installation process. The only acceptable part was entering my name. The border around the other names (e.g. computer name) was becoming red and underneath with e.g. the message: The computer name is invalid. 

So during installation either non-latin characters should be accepted or availability to latin character keyboard for those inputs that demand such kind of characters should be at hand. That was my comment in the first place. I have to admit that I didn't remember what was happening in the past, yet I had the impression that I wasn't facing issues, so I decided to pick up a 10.10 64 bit iso and tried to install it under virtualbox. I picked up the Hellenic option at hand, which automatically switched the environment to that language. When name of computer e.t.c. was required I was able to switch to english when needed without having to open settings e.t.c. just by tapping Alt+Shift. It happened out of the box. Only the name of the computer and username required latin characters. On the other hand during installation of mantic I couldn't switch to latin/english keyboard either by pressing Alt+Shift or Super+space.

The good news is that during installation the virtualbox screen is not so tiny as it used to be.

Regards!

---

### Post by sudodus on 2023-05-08
@ Claus7,

I suggest that you **create a bug report at Launchpad** about this language/keyboard problem. That is the best way to reach the Ubuntu developers.

---

### Post by Claus7 on 2023-05-08
Hello,

> **sudodus said:**
> @ Claus7,

I suggest that you **create a bug report at Launchpad** about this language/keyboard problem. That is the best way to reach the Ubuntu developers.

thank you *sudodus* for your suggestion. This is the link: [https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943](https://bugs.launchpad.net/ubuntu/+source/subiquity/+bug/2018943)

Regards!

---

### Post by sudodus on 2023-05-08
@ Claus7,

That's a good start :KS

I suggest that you provide more details in the bug report. You could copy and paste from your first post here to the bug report (and edit it if you wish).

You should also be prepared to help, when a developer starts looking at the problem in order to debug the installer.

I hope we can find another user here who uses some non-latin keyboard and knows how it used to work to install Ubuntu because it is good to get the bug confirmed by at least one more user to get the developers interested.

I think I understand the problem, but I cannot really manage the non-latin keyboard. Anyway, after trying a for a while with Greek letters, I failed too, and can confirm the bug.

Edit: This bug affects both **23.04** and **mantic**.

---

### Post by Claus7 on 2023-05-09
Hello,

> **sudodus said:**
> @ Claus7,

That's a good start :KS

I suggest that you provide more details in the bug report. You could copy and paste from your first post here to the bug report (and edit it if you wish).

You should also be prepared to help, when a developer starts looking at the problem in order to debug the installer.

I hope we can find another user here who uses some non-latin keyboard and knows how it used to work to install Ubuntu because it is good to get the bug confirmed by at least one more user to get the developers interested.

I think I understand the problem, but I cannot really manage the non-latin keyboard. Anyway, after trying a for a while with Greek letters, I failed too, and can confirm the bug.

Edit: This bug affects both **23.04** and **mantic**.

*sudodus* thank you so much for your contribution and time! I edited the bug report. Hope is not so lengthy now, yet it is much more detailed I guess than before.
I think that using an unknown keyboard is a hard task. I remember choosing a wrong language in android phone and it was hard to bring it back to normal. Set aside following guidelines for the installation! At least the steps are not so many and in general are familiar.

I could provide help and testing if required from the developers. It could be nice for this to get fixed as working before. I have high hopes for the ability to change keyboard while renaming files under nautilus too.

Regards!

---

### Post by Claus7 on 2024-02-17
Hello,

I noticed that these days changes are taking place concerning the desktop installer. So I tried it myself and this is what happened: still choosing hellenic keyboard doesn't allow the installation to take place, since it is not recognized. Yet, now, going back and selecting the english one, the process doesn't freeze and is smooth. In the meantime I can type my name in greek, and go back and select the english keyboard. Doing so, a bug appeared that was reported here: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/2054193](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/2054193)

Installation went fine without hiccups. The only thing I can report is that allowing info to be sent to Canonical didn't work, because it was not possible to be sent at that time.

Regards!

---

### Post by corradoventu on 2024-02-17
under 23.10? or 24.04 Noble Numbat?
bug/2054193 can not be displayed because is private? please set it to public by clicking the small yellow pencil top right
starting from the ISO of February 14 or 15 ubuntu-desktop-installer has been replaced by ubuntu-desktop-bootstrap so many things are changed

---

### Post by Claus7 on 2024-02-17
Hello,

thank you for your response:
> **corradoventu said:**
> under 23.10? or 24.04 Noble Numbat?
now 24.04 noble numbat
> **corradoventu said:**
> 
bug/2054193 can not be displayed because is private? please set it to public by clicking the small yellow pencil top right
thank you, done. It was like that by default.
> **corradoventu said:**
> 
starting from the ISO of February 14 or 15 ubuntu-desktop-installer has been replaced by ubuntu-desktop-bootstrap so many things are changed
That's why I tried to test it anew.

Regards!

---

