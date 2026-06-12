---
title: "[SOLVED] Need help with login banner"
date: 2008-07-22
forum: Server Platforms
---

### Post by silverglade00 on 2008-07-22
Hi everyone!

I am installing a few Ubuntu computers in a student lab at a State University as a test to see if a full lab based on Ubuntu might be something that our students would want. Right now, I have everything configured and working... student logins, admins with sudo access, etc. The only thing that is holding me back is the need to have a warning banner displayed to each user as they log in.

This is a state-mandated banner and could kill the whole project if I cannot get it going. If you have ever been on a Windows computer and pressed CTRL-ALT-DEL to log in and had a huge legal text file with an OK button shoved in your face before you can enter your username, you know what I am talking about. I have the banner in /etc/issue and /etc/issue.net already and it works fine when I ssh in. I need gdm to display one now and I have been unsuccessful. 

If any of you have been successful in implementing this, I would be very grateful for your help. You would be helping spread the Ubuntu joy and helping me add Linux admin skills to my resume :)

Thanks in advance!

---

### Post by Dr Small on 2008-07-22
So basically, you need /etc/issue to display after they login at GDM?

---

### Post by silverglade00 on 2008-07-22
That would work fine with me. As long as they have to click OK to get past it and do their work. Simply flashing it won't work, they have to actively accept it and have a chance to read it. Extra points if there is a "Cancel" or "Not OK" that logs them out immediately.

Though at this point, I am willing to resort to modifying the background picture and locking them out from changing it somehow, but I am hoping for something a little more elegant.

---

### Post by beniwtv on 2008-07-23
I think you could do something with the .xsession file in each user's home dir. If this file exists, it will be executed after the user has logged in.

You could write a bash script that displays the dialog, and an OK and cancel button. If the user clicks on OK, launch gnome (perhaps you can just execute the default Xsession file), and if he clicks on cancel, return "exit 0" to terminate the session.

Cheers,

---

### Post by ad_267 on 2008-07-23
I know this is possible because my university has something similar to this with Ubuntu. When users get to the login screen there is a popup with a message. There isn't a "cancel" button that logs users out though and I'm not sure how it works.

---

### Post by ad_267 on 2008-07-23
Edit: Ignore, read next post.

---

### Post by ad_267 on 2008-07-23
Aha, haven't tried this but in /etc/gdm/gdm.conf at line 509 there's this:

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

Edit: Tried it and it works. Users have to click OK before they can log in. Just change
```
#InfoMsgFile=
```
to
```
InfoMsgFile=/etc/issue
```

---

### Post by silverglade00 on 2008-07-23
Thanks to everyone who has responded so far. I have tried the InfoMsgFile setting with no success. I have tried to set /etc/gdm/PostLogin (and the others)/Default with a zenity --info --info-text="blah blah blah" with no success. Could this have anything to do with Compiz? I am really reaching here. I just do not understand why it will not work for me when it should.

---

### Post by silverglade00 on 2008-07-23
Not what I had in mind, but this works great. System -> Administration -> Login Window and paste the whole banner into Custom Welcome. It's ugly, but they cannot login without seeing it. Thanks for everyone's help!!

---

### Post by ad_267 on 2008-07-23
You need to restart after setting the InfoMsgFile, it works for me.

---

### Post by silverglade00 on 2008-07-23
I also needed to do a system update after enabling the proposed updates. Thanks, it works now!

---

### Post by sapg on 2011-06-05
Anyone know how I do this in Lucid and later, it doesn't seem to be the same.

---

