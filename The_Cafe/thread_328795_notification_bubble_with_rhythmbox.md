---
title: "notification bubble with rhythmbox"
date: 2006-12-31
forum: The Cafe
---

### Post by Choad on 2006-12-31
ok i use xubuntu edgy at the moment, just recently rhythm box has started telling me what song is playing by bringing up a notification bubble. im not sure if this is a rhythmbox feature, or if its a generic notification daemon, and only rhythmbox uses it at the moment for me, but regardless it looks hideous

[img]http://img177.imageshack.us/img177/8845/screenshot19qq9.png[/img] [img]http://img291.imageshack.us/img291/4135/notifysa9.png[/img]

so i am just wondering.... is this a general purpose notification bubble, does it look this bad for you, and why cant it look like my improved version underneath?

is this a bug that should be reported? is it like this in feisty? etc. etc.

---

### Post by red_Marvin on 2006-12-31
I'm on dapper and gnome atm so it might not work for you, but I can right-click on the note to get a dropdown menu where I can choose if I want to see notifications or not (Which makes it a rythmbox feature)...

EDIT: sorry I misread, I thought you wanted to remove it altogether...

---

### Post by PriceChild on 2006-12-31
> **Choad said:**
> why cant it look like my improved version underneath?What improved version?

---

### Post by happy-and-lost on 2006-12-31
Banshee has the same problem. I think it's th generic notification daemon's issue

---

### Post by Choad on 2006-12-31
> **PriceChild said:**
> What improved version?
there are 2 notification bubbles in my screenshot. the top is the one that i am presented, the bottom is what it *should* look like

edit: i added a bigger pic ;)

---

### Post by Choad on 2006-12-31
> **red_Marvin said:**
> I'm on dapper and gnome atm so it might not work for you, but I can right-click on the note to get a dropdown menu where I can choose if I want to see notifications or not (Which makes it a rythmbox feature)...
ah yes! i must have accidentally clicked it. still, it is an issue that should be addressed

---

### Post by PriceChild on 2006-12-31
Ah yeah I see it now lol... sharp eyes...

Same problem as the forums have at the top, where the graphic with the ubuntu logo doesn't quite meld into the right of the page perfectly on the bottom.

Report it as a bug

---

### Post by Choad on 2006-12-31
how do i report it? never done this before :)

---

### Post by Choad on 2006-12-31
okey i registered with launchpad, but there is a very similar bug already reported

[https://launchpad.net/distros/ubuntu/+source/notification-daemon/+bug/35696](https://launchpad.net/distros/ubuntu/+source/notification-daemon/+bug/35696)

similar but not the same. you can see clearly from his picture that the line drawing method of the notification box certainly leaves alot to be desired. its like they were trying to achieve an anti-aliased effect but completely missed the point.

should i report my bug too?

---

### Post by banjobacon on 2006-12-31
It's a different bug.

---

### Post by Khaine on 2007-01-01
My understanding is that it uses libnotify [http://www.galago-project.org/news/index.php](http://www.galago-project.org/news/index.php) and I agree it looks but ugly in ubuntu, does anyone else know how you can change the appearance ?

[Edit]
Apparently this is how you can change the appearance, although I haven't tested it:

There is a quite easy way to change appearance of notifications. Method checked on Ubuntu.

1. List contents of folder /usr/lib/notification-daemon-1.0/engines to see what you have to choose from. I have such files:
libbubble.a   libbubble.so   libstandard.la  libubuntu.a   libubuntu.so libbubble.la  libstandard.a  libstandard.so  libubuntu.la
Which means I have 3 themes to choose from: bubble, ubuntu and standard.
2. Launch gconf-editor. Find node /apps/notification-daemon and edit key "theme". I changed the default value "ubuntu" to "standard".
[/edit]

---

