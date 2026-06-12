---
title: "Can't change my Password"
date: 2010-01-04
forum: Security
---

### Post by Hariharan_the_great on 2010-01-04
Hi guys, :lolflag:

Im new to ubuntu. Now iam using Karmic Koala. I want to change my password. So i used, 

system->Administration->users and groups to change my password :P. As i entered my new password and clicked on 'Change Password', It is saying, 'password changed'. But when I click the close button in the main users and groups window, it is asking for my password, and I am forced to enter my old password only.  

After the window is closed, i logout to check whether my password is changed. But it is not. I have to enter my old password to login :confused:

Can any one help me?????????

---

### Post by kiranmurari on 2010-01-04
[SIZE=2]You can change your password from System -> Preferences -> About Me.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]System -> Administration -> Users and Groups is for the system administrator to manage the system user accounts.[/SIZE]
   	[SIZE=2]
[/SIZE]
[SIZE=2]Regards,
Kiran[/SIZE]
[SIZE=2]

[/SIZE]

---

### Post by shane77777 on 2010-01-19
That's a bit confusing for new people - Users and Groups seems like a logical place to change your own password too

---

### Post by temporos on 2010-01-26
> **kiranmurari said:**
> [SIZE=2]You can change your password from System -> Preferences -> About Me.[/SIZE]
[FONT=Verdana][SIZE=2]I'm also a complete newbie to Ubuntu.  I used (Slackware) Linux briefly while I was an undergrad several years ago, but I just used a few programmes in X-Windows, and I didn't get deep into the system itself.

I tried the above suggestion, and I couldn't get it to change the password.  I'm also running 9.10 (the netbook edition), and when I use the "About Me" panel to change my password, it hangs until I close the window.  First, it asks me to enter my current password.  Then it asks for the new password and the confirmation.  When I do that and click "Change Password," I see the spinning ball icon that says the machine is working on it, but it just sits there spinning until I cancel the process by closing the window.  I've let it chew at it for a half-hour once before closing it, just to make sure.  Any idea why I can't change my password?[/SIZE][/FONT]

---

### Post by rogue_0111 on 2010-01-26
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by adam814 on 2010-01-27
If you can still log in you could just run "passwd" in a terminal anyway.

---

### Post by temporos on 2010-01-28
I was able to change my password by using the *passwd* command from a terminal window.  This raises a new question, however.  Why does the GUI password change utility malfunction?  Is this a bug that the Ubuntu developers know about?

---

### Post by cariboo on 2010-01-28
The password change doesn't take place right away, you have to log out, then back in again, the same with adding or removing groups.

**Edit**: I just added a new user using Users & Groups, logged out, logged in as the new user, changed the password in About Me, logged out, then logged back in again with the new password.

---

### Post by temporos on 2010-01-28
> **cariboo907 said:**
> The password change doesn't take place right away, you have to log out, then back in again, the same with adding or removing groups.
No, it doesn't change at all.  Attempting to change the password using the "About Me" panel causes the panel to hang until the process is cancelled.  The only way I was able to change it was via terminal window.

---

### Post by 1915flyer on 2010-02-28
> **temporos said:**
> No, it doesn't change at all.  Attempting to change the password using the "About Me" panel causes the panel to hang until the process is cancelled.  The only way I was able to change it was via terminal window.
I have the same problem. 

Should this be reported as a bug? How do I do that?

---

### Post by cariboo on 2010-02-28
I you're sure that you're problem lies with About Me, you can report the bug using the bug reporting utility. To do this, press Alt-F2 and type:

```
ubuntu-bug gnome-about-me
```

You have to have a [Launchpad]("http://launchpad.net") account if you want to add any extra details to the bug.

---

### Post by uqcodonn on 2010-03-26
> **kiranmurari said:**
> [SIZE=2]You can change your password from System -> Preferences -> About Me.[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]System -> Administration -> Users and Groups is for the system administrator to manage the system user accounts.[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]Regards,
Kiran[/SIZE]
[SIZE=2]

[/SIZE]
Thanks Kiran - I was having the same problem as that posted above and couldn't figure out why I couldn't get my password to change properly. Tried System->Preferences->AboutMe as you suggested and that worked perfectly.

Cheers,
Chris

---

### Post by Hariharan_the_great on 2010-04-02
Hey guys :D:D

     I didn't think that i would get help from all of u...  So I want to thankyou all for replying in my thread...:o

Regards,

Hariharan:KS

---

### Post by bobmage on 2010-04-04
> **rogue_0111 said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Rogue-0111.  Thanks for the url.  The recovery procedure worked perfectly.

---

### Post by squall1156 on 2011-01-05
> **temporos said:**
> No, it doesn't change at all.  Attempting to change the password using the "About Me" panel causes the panel to hang until the process is cancelled.  The only way I was able to change it was via terminal window.

For anyone else that stumbles upon this thread, the hanging issue is a result of the GUI not providing the specific reason that the password can't be changed.

When this happened to me, it was because I was using something that was too similar.  For example, the current password was "password1" and the new one was "password2" - this minor difference doesn't satisfy Linux's embedded change requirements, so it would hang as described but not inform me as to why.

So, I instead went from "password1" to "whatever" (which allowed the GUI to work and not hang), then from "whatever" to "password2".

Hope that helps.

---

