---
title: "Changing icon of app in messaging menu (python)"
date: 2011-05-03
forum: Ubuntu Dev Link Forum
---

### Post by unboogyman on 2011-05-03
Hi, I'm using Gmail Notifier on Ubuntu 11.04.  Its a python script and easy to modify.  I want to have it use my own icon in the messaging menu instead of the default mail icon it currently uses.

I think the code needed would be here somewhere:
```
lass Message(indicate.Indicator):
    def __init__(self, title, sender, time, link, callback=None):
        indicate.Indicator.__init__(self)
        self.title = title
        self.sender = sender
        self.link = link
        self.time = time
        self.show()
        if(callback == None):
            self.connect("user-display", self.clicked)
            self.alert()
        else:
            self.connect("user-display", callback)
        self.set_property("subtype", "mail")
        if(len(title) > 30):
            tmp = title[:30] + "..."
        else:
            tmp = title
        self.set_property("name", "%s - %s" % (tmp, sender))
        self.set_property_time("time", self.time)
        self.last = 0
```

Thanks for any help.

---

### Post by miesogeno on 2011-05-04
I want to change this too.

I already managed to change the icon that shows on the bubble when you receive an email. somewhere in that python code you'll find something called "notification-message-email", change it to "gmail".

I'm still trying to fix the other icon. let me know if you can do it.

---

### Post by unboogyman on 2011-05-04
Thanks!  That worked for 1/2 of what I wanted.  I still can't figure out how to change the small mail icon.  I think this code has something to do with it ```
self.set_property("subtype", "mail")
```
but don't know how to change it.

I tried changing the shortcut icon and it did change the messaging menu icon, but it changed it to an error icon, not the one i set.

I am clueless at this point.

---

### Post by miesogeno on 2011-05-09
yep, me too. have you found an answer yet?

EDIT:

I got it!

this is just a work around, but if gmail is your only email application in that menu, you can change the icon called applications-email-panel.svg to a gmail icon (I've been assuming you're trying to change it to gmail...)

I'm using elementary theme with dark panels, so I tried to change it in /usr/share/icons/elementary-mono-dark/panel/22 and it didn't work... so I found it and changed it in /home/"my name"/.icons/elementary-mono-dark/panel/22 and it did work! I just had to restart gmail-notifier. but if it doesn't work either, you can try to change the icon theme to any other, and then back into the one you want to use.

don't ask me why its using the icon theme installed in my home folder instead the one in /usr/share. maybe its just elementary.

remember, if you ever use another application for email, like evolution or thunderbird, it will use that icon you just got in there, you'll probably want to change it by then.




another thing. does your notifier open your gmail when you click the icon?
mine doesn't since I installed natty. it simply opens another firefox instance in my homepage. any ideas? thanks

---

