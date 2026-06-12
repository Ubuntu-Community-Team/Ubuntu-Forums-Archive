---
title: "Steam Install probem"
date: 2016-12-10
forum: Ubuntu Studio
---

### Post by sterlinglee38 on 2016-12-10
I am trying to install Steam and it needs to add additional software or libraries, and a dialog box comes up and asls for my password, but I am unable to type anything. I it enter/return and then after a split second it say sorry, try again. Any ideas? I included a link to a screen shot.

[http://i628.photobucket.com/albums/uu5/sterlinglee38/steaminstall_zpsetseazmn.png](http://i628.photobucket.com/albums/uu5/sterlinglee38/steaminstall_zpsetseazmn.png)

Thanks in advance!
Lee

---

### Post by sterlinglee38 on 2016-12-10
For future reference, if anyone has this problem the solution is just type your password and hit enter, it just doesn't show you are typing, but it is registering your key strokes.

---

### Post by ajgreeny on 2016-12-10
Your password will never show when it's typed into a terminal window, which is what is shown in your screenshot, not even as asterisks.

This is a security property to avoid watchers even knowing how many characters there are in your password.

---

### Post by oldos2er on 2016-12-10
You can have asterisks appear in terminal when entering your password if you add *pwfeedback* to your sudoers file. I don't know why more distros don't ship with this option, since this is one of the most FAQ in Linux.

[https://help.ubuntu.com/community/Sudoers#Enabling_Visual_Feedback_when_Typing_Passwords](https://help.ubuntu.com/community/Sudoers#Enabling_Visual_Feedback_when_Typing_Passwords)

---

