---
title: "ia32-libs or lib32stdc++ is required to be installed."
date: 2014-03-04
forum: Ubuntu Development Version
---

### Post by SuperFreak on 2014-03-04
I am trying to install my Brother MFC 5490CN priner on 14.04. The printer is recognized immediately but the printer doesn't get installed I just have a window that says searching for printer drivers that does not seem to resolve itself. The alternative to allowing Ubuntu to install automatically is to use Brother's instructions [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html"). Unfortunately to use these instructions I have to install ia32-libs or lib32stdc++ and if I am not mistaken this can't be done in Ubuntu past 13.04. Seems a little drastic to have to buy a new printer.
Anyway right now I am testing 14.04 on a USB stick install not on the SSD (12.04 is installed there) so I have a little time to sort this out

---

### Post by mc4man on 2014-03-04
does this not work?
```
sudo apt-get  install lib32stdc++6
```
There *could* be an issue on live sessions where only the current arch packages  are available...

---

### Post by Mateusz Stachowski on 2014-03-04
Brother has a very nice installer script.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

[http://ubuntuforums.org/showthread.php?t=1850454](http://ubuntuforums.org/showthread.php?t=1850454)

---

### Post by grahammechanical on 2014-03-04
On my Trusty Tahr synaptic shows lib32stdc++6 available for installation but then, I have all the repositories enabled. I do not think that a live session has Universe and Multiverse enabled by default.

> [COLOR=#333333][FONT=Ubuntu]The Ubuntu [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Install[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] CDs contain software from the "Main" and "Restricted" components of the repositories. [/FONT][/COLOR]

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Regards.

---

### Post by SuperFreak on 2014-03-04
> **Mateusz Stachowski said:**
> Brother has a very nice installer script.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

[http://ubuntuforums.org/showthread.php?t=1850454](http://ubuntuforums.org/showthread.php?t=1850454)

Thanks I will give that a try.

> There *could* be an issue on live sessions where only the current arch packages are available... 
This is not a live USB rather I did a full install on the USB stick (Nor is it a persisitent Live install)

---

### Post by SuperFreak on 2014-03-05
>  Quote Originally Posted by Mateusz Stachowski View Post
Brother has a very nice installer script.

[http://welcome.solutions.brother.com...rn.html#f00104](http://welcome.solutions.brother.com...rn.html#f00104)

[http://ubuntuforums.org/showthread.php?t=1850454](http://ubuntuforums.org/showthread.php?t=1850454)

Tried installer and it installed wrong printer drivers. Looked promising.

lib32stdc++6 was installed and the next try I managed to get right printer installed with the instructions on Brothers web site. I also got the scanner function to work.

Thanks everyone for your help

---

### Post by Mateusz Stachowski on 2014-03-05
Please mark the thread as SOLVED. You should find the option for it in Thread Tools.

---

