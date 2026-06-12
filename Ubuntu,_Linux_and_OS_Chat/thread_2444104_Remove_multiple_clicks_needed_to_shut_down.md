---
title: "Remove multiple clicks needed to shut down"
date: 2020-05-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Andrew F in Australia on 2020-05-24
Hi All,

Just a suggestion for Groovy Gorilla - it's too late now for 20.04

I know things are always done for a reason, but the below may have been overlooked.

To shut down now, it's just as long to click as it is to command line shutdown.

Need to click the drop down arrow.
Then move the mouse to Power Off/Logout(click)
Then move to Power Off (click)
Then move to the middle of the screen to click Power Off (click)

Why a four-click shutdown?   (worse than Windows.)

Been working with computers since DOS command line (1981 - pre windows) and prefer to use linux/unix.

It's easier to now open a terminal and type in the shutdown -P now command than it is to use a mouse.

Any chance of a Shutdown Now as a separate option to bypass the rigmarole in an upcoming release? 

Just an opinion and feedback.

A

---

### Post by grahammechanical on 2020-05-24
I agree with you. Power off; Log out & Suspend should all be available from the first drop down menu. If I remember correctly it used to be that way when we used Unity 7. Now, we have Gnome 3 shell we have to put up with the opinions of the Gnome developers.

Regards

---

### Post by zika on 2020-05-25
Not a solution for Your proper complaint but just a nifty shortcut to making a shortcut for the thing You need: [https://linuxonfire.wordpress.com/2012/10/19/what-are-init-0-init-1-init-2-init-3-init-4-init-5-init-6-2/](https://linuxonfire.wordpress.com/2012/10/19/what-are-init-0-init-1-init-2-init-3-init-4-init-5-init-6-2/) ...
I do use init all the time just in a execute-comand-line shortcut in any UI I encounter...

---

### Post by slickymaster on 2020-05-25
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by TheFu on 2020-05-25
Just setup an accel key that does reboot/shutdown/whatever you prefer.  Best not to make shutdown too easy for normal users.  Make it too easy and they'll be unhappy because they were just looking through menus and the system got shutdown.

Can't make everyone happy all the time.

---

### Post by kurt18947 on 2020-05-27
> **Andrew F in Australia said:**
> Hi All,

Just a suggestion for Groovy Gorilla - it's too late now for 20.04

I know things are always done for a reason, but the below may have been overlooked.

To shut down now, it's just as long to click as it is to command line shutdown.

Need to click the drop down arrow.
Then move the mouse to Power Off/Logout(click)
Then move to Power Off (click)
Then move to the middle of the screen to click Power Off (click)

Why a four-click shutdown?   (worse than Windows.)

Been working with computers since DOS command line (1981 - pre windows) and prefer to use linux/unix.

It's easier to now open a terminal and type in the shutdown -P now command than it is to use a mouse.

Any chance of a Shutdown Now as a separate option to bypass the rigmarole in an upcoming release? 

Just an opinion and feedback.

A
There may be an extension that will do what you want - "Bring Out Submenu of Power Off/Logout Button". I have a keyboard  shortcut on my desktop using the 'pause' key. Couple the pause key to this command:

```
systemctl suspend
```

I don't see why you couldn't use shutdown -P in place of suspend though I haven't tried it.

---

### Post by monkeybrain20122 on 2020-05-27
That's why I don't use gnome, every little task is frustrating and it is clunky and sluggish. Happily using unity (with nemo as file manager) on 20.04.

---

### Post by mastablasta on 2020-05-28
i am counting 3 click on KDE. not sure what will happen if i let the timer run out, but i think it just returns to the desktop.

so it's 
1. click K
2. click&select - logout, reboot, shutdown , suspend...
3. click - confirm action, select another action or let the timer run out.

this is annoying only on laptop, while desktop is always (at least during the day).

---

