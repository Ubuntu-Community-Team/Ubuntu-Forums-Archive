---
title: "Root Password? There is indeed..."
date: 2005-02-14
forum: Server Platforms
---

### Post by gajeghst on 2005-02-14
HELP!!! It's 6AM and I need to find out what the root password is.
I've all those posts about there not being one, and yadda yadda, but I have one and I did not put it there.
So please, What can I do?
Thank you
John

---

### Post by josue on 2005-02-14
[QUOTE=gajeghst]HELP!!! It's 6AM and I need to find out what the root password is.
I've all those posts about there not being one, and yadda yadda, but I have one and I did not put it there.
So please, What can I do?
Thank you
John[/QUOTE]
 Hi John,

it's not that you have one and you never created it. It's just that root is disabled per default.

Just type this in a terminal, to create a password for root (you must have pass for su):

sudo passwd root

---

### Post by gajeghst on 2005-02-14
Thank you so much, um...where do I find a Pass for Su?
I did exactly what you said,  
The screen read: password: (I entered my users PW)
Then it read: enter new Unix Password (I did)
Then It read: PW change succesful (so I thought yeah, done)
The I went to Login new user and tried it...nothing I cannot sign in as root.
What am I doing wrong?

John

---

### Post by Buffalo Soldier on 2005-02-14
Go to  Computer -> System Configuration -> Login Screen Setup -> Security -> Allow root to login with GDM

---

### Post by gajeghst on 2005-02-14
YESSS!!
That did it.
Buffalo S. You are the hero of the hour.
Thank you
John

---

### Post by rufius on 2005-02-14
[QUOTE=gajeghst]HELP!!! It's 6AM and I need to find out what the root password is.
I've all those posts about there not being one, and yadda yadda, but I have one and I did not put it there.
So please, What can I do?
Thank you
John[/QUOTE]
 Considering this is the security forum, why would you login to gnome as root? Thats just asking for a huge load of trouble, and one of the number one rules of *nix to never break.  Thats only going to give more chances to others to exploit you and considering you seem to not be an expert user its highly suggested you avoid use of X as root. 

A wise man once said: "He who plays in root eventually kill tree."

---

### Post by gajeghst on 2005-02-15
Thanks, and no I am not an expert. ( nice of you to point that out, FLOG)
Anyway, where else was I going to put ask it.
I got the answer and no one even knows what the PW is.
And I do know enough to not run in root.
So thanks again.

---

### Post by rufius on 2005-02-15
[QUOTE=gajeghst]Thanks, and no I am not an expert. ( nice of you to point that out, FLOG)
Anyway, where else was I going to put ask it.
I got the answer and no one even knows what the PW is.
And I do know enough to not run in root.
So thanks again.[/QUOTE]
 Thats because no root password is ever set. You have to manually set it considering Ubuntu was designed to keep users from making the mistake of playing in root. Hence why most everything is done via sudo.

---

### Post by Jolly on 2005-02-16
[QUOTE=josue]Hi John,

it's not that you have one and you never created it. It's just that root is disabled per default.

Just type this in a terminal, to create a password for root (you must have pass for su):

sudo passwd root[/QUOTE]


Thank you that worked a treat ...

---

