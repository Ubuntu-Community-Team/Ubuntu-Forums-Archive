---
title: "Ubuntu 10 Lucid Login"
date: 2011-02-17
forum: Security
---

### Post by kakashi_12 on 2011-02-17
How do I disable showing Usernames? I want to be prompted for BOTH un and pw. If it is necessary I could just change it so that it boots into a fullscreen terminal so that you would have to input "startx" and then username and password. Or I could just change it through gui or 3rd party software.

anyone?

---

### Post by JOHNNYG713 on 2011-02-17
What are you trying to accomplish ? Security? More info would be helpful, so as to anchor your needs! ;)

---

### Post by cariboo on 2011-02-17
You can remove the names from the user list by opening gconf-editor. Press Alt-F2 and type:

```
gconf-editor
```

then navigate to apps->gdm->simple-greeter->disable_user_ list, and make sure it is checked.

---

### Post by JOHNNYG713 on 2011-02-17
Is that what he said ! I must have misread, I thought he wanted to login at terminal per user and NOT GDM< **I** must be gettn old ! :p

---

### Post by kitsuneclem on 2011-02-17
actually Me thinks OP wants to disable the username process In general

---

### Post by Dave_L on 2011-02-17
> **cariboo907 said:**
> You can remove the names from the user list by opening gconf-editor. Press Alt-F2 and type:

```
gconf-editor
```

then navigate to apps->gdm->simple-greeter->disable_user_ list, and make sure it is checked.

[10.04 / Netbook edition / Gnome]

I added that setting a while ago, but it didn't make any difference. The list of users is still present when I log in.

---

### Post by cariboo on 2011-02-17
You can also use [Ubuntu-Tweak]("http://ubuntu-tweak.com/"), to remove the list of names.

---

### Post by kakashi_12 on 2011-02-17
> **cariboo907 said:**
> You can also use [Ubuntu-Tweak]("http://ubuntu-tweak.com/"), to remove the list of names.

THANK YOU! You just made me life so much more easy and fun :)

---

