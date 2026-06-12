---
title: "[IDEA] libnotify on steriods"
date: 2007-10-31
forum: Ubuntu Brainstorm
---

### Post by booljayj on 2007-10-31
libnotify is a great and simple way for applications to display messages to the user, but it occurred to me that in this day and age a slightly more in-depth approach would be beneficial. I've heard about the mumbles project for a while now, and it does look like an excellent way to extend the functionality of libnotify. However, more could be done.

Notifications should be not only themed, but customized on a per-application, per-message basis. Display time, position, sound, and color should all be customizable from within the notifier framework. Initially, this may not be a complicated program. When a dbus call is received, the program searches through a small config file to see if the notification matches any criteria, and displays it using special or default criteria. Let's say I want my e-mail notifications to be persistent in the upper left corner of my screen, and I want them to be blue and make a 'ping' sound when created. I would just specify that notifications coming from evolution pertaining to e-mail should do that, and let it go. A plugin framework would of course be beneficial to this sort of program, since not every user has the need for every notification feature of every program.

I love GNOME, but it has it's shortcomings. I would love to one day see Ubuntu and OS X battle head-to-head, but in order for that to happen added functionality like this would need to be added. And hey, how big would this program be? A few kilobytes, depending on python bindings for things like cairo and dbus? Maybe Mumbles could become this one day, and I'd love to see that.

---

