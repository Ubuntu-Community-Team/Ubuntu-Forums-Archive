---
title: "Ubuntu one does not open"
date: 2010-05-19
forum: Ubuntu One (CLOSED)
---

### Post by ssdt on 2010-05-19
When i go to preference>> ubuntu one and click on it, it does not open even through it's installed. Can anyone tell me what type of problem it is? 

Thank you

---

### Post by koolblue3 on 2010-05-20
Hi,

If you just added your computer to your Ubuntu One, you have probably already tried this but, open it a second time, if this fails reboot and try again. If it still does not open try reinstalling Ubuntu One. I had the same issue after adding my computer to my Ubuntu One account and opening it a second time fixed the issue.

---

### Post by ssdt on 2010-05-20
Well, i had done reinstalling and opening it after turing it off. Still the problem goes on, no solution yet.

---

### Post by duanedesign on 2010-05-20
Could you please try running the following command in a Terminal and let me know if this gets your Ubuntu One Preferences to start. There is a gnome keyring bug going around that has these symptoms

```
gnome-keyring-daemon; ubuntuone-preferences
```

if that does not work could you look in the following file to see if it contains anything:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

if you post anthing from your log please use the CODE tags. You can make the open and close brackets automagically with the # button in the post editor.

Also try launching the preferences from the terminal to see if any errors get printed. The command
```
ubuntuone-preferences
```
Post any errors that appear in the Terminal.
-
-

---

### Post by ssdt on 2010-06-30
After an update, the problem seems to have been gone. Thank you.

---

