---
title: "bouncing KDE ball"
date: 2010-08-02
forum: The Cafe
---

### Post by sandyd on 2010-08-02
I added the bouncy ball widget to KDE, and now I can't remove it.

I set it to autobounce, so the ball won't stop long enough for me to close it......

help lol.....

---

### Post by _h_ on 2010-08-02
Poke it with a sharp needle or pin!

---

### Post by WorfSOM on 2010-08-03
I did the exact same thing the other day!:p

Just lock the widgets and it will freeze in place for you.

---

### Post by Zorgoth on 2010-08-03
I think the only way to improve KDE would be to make the cursor a ball and have a combination desktop/Kollision.

---

### Post by sandyd on 2010-08-03
> **WorfSOM said:**
> I did the exact same thing the other day!:p

Just lock the widgets and it will freeze in place for you.

oh hai, thanks!

---

### Post by WorfSOM on 2010-08-03
> **carlee said:**
> oh hai, thanks!

No problem, just glad to help. I know exactly how frustrating that particular problem is!:p

---

### Post by wieman01 on 2010-10-16
Thank you, guys. I had the exact same problem, stupid. I locked my widgets and changed the settings of bouncy ball. I had a good laugh. :-)

---

### Post by ibuclaw on 2010-10-16
> **wieman01 said:**
> Thank you, guys. I had the exact same problem, stupid. I locked my widgets and changed the settings of bouncy ball. I had a good laugh. :-)

Ahh... I love the bouncy ball! Once spent 5 minutes playing with it, when one of my friends walked in gave a strange look.

"And I thought Linux was an OS for boring developers who use nothing but a command prompt."

I turned to him and just smiled; then put it away...

---

### Post by wieman01 on 2010-10-16
> **ibuclaw said:**
> Ahh... I love the bouncy ball! Once spent 5 minutes playing with it, when one of my friends walked in gave a strange look.

"And I thought Linux was an OS for boring developers who use nothing but a command prompt."

I turned to him and just smiled; then put it away...
Lol... Linux can take people by surprise, indeed. :-)

---

### Post by inobe on 2010-10-16
older version of kde the ball bounced off the screen, it was a buggy ball at the time, could never find it after that.

---

### Post by NightwishFan on 2010-10-16
It never worked at all for me until Maverick. :D

---

### Post by kio_http on 2010-10-16
Can't help laughing at the consequences of the ball bouncing every where! Maybe someone should make a dog plasmoid to fetch it.
:lol::lol::lol::lol:

---

### Post by wieman01 on 2010-10-17
> **kio_http said:**
> Can't help laughing at the consequences of the ball bouncing every where! Maybe someone should make a dog plasmoid to fetch it.
:lol::lol::lol::lol:
Hey,that would be hilarious!

It's still a little buggy though, you'd see artifacts from while to while which disappear when the screen refreshes. Could be my computer which is kind of slow.

---

### Post by Giant Speck on 2010-10-17
> **NightwishFan said:**
> It never worked at all for me until Maverick. :D
I haven't used KDE since Karmic, and even then it never worked.  It'd bounce a couple times and then Plasma would crash completely.  That was one destructive little bugger.

---

### Post by TurtleKing on 2011-05-01
lol locking widget won´t stop mine for some reason. I feel the lock is looking at me saying, ¨why would you put the bounce bar all the way to the middle!":P Any other solutions? Does it stop on login?

---

### Post by CraigPaleo on 2011-05-01
Oh no! I just had to get that thing started! 

You just have to be really quick. If you can click on it, it'll stop. I haven't tried loging out and back in. It might work.

---

### Post by tkelito on 2011-05-04
In 11.04 it won't stop.  It was funny for the first few minutes, but I have bigger issues to tackle.  For a second I thought a ball on my screen I could drag around would be a stress reliever... I was wrong.

Just be quick with the right click to catch it and get into settings.  Might need an abort mission escape key.

---

### Post by el_koraco on 2011-05-04
lol, maybe you can find it in running processes and kill it?

---

### Post by ilovelinux33467 on 2011-05-04
lol, I have had that happen to me before but locking the widgets worked. Must have been an older version of KDE. I haven't tried the bouncing ball since that :)

---

### Post by nuras on 2011-07-10
Hi,

I have the same problem but cant kill it. I tried locking widgets it but it just would not stop. I tried to run "ps -ef" in konsole but y system freezes and i have had to hard reboot in both my tries. Any help would be highly appreciated.

I thought the situation was a classic lol issue but its started to get annoying now.

---

### Post by Alex89 on 2011-10-04
Hi,

I had the same problem. You can get the ball when you put your mouse on the left or right boarder of your desktop. Sometimes the ball only jumps up and down at the boarder and than you can get it. It takes a few minutes but it works.

So good luck

---

### Post by Linuxratty on 2011-10-06
> **inobe said:**
> older version of kde the ball bounced off the screen, it was a buggy ball at the time, could never find it after that.

LOL! I never had this happen, but would like to see it.

---

### Post by jnorichards on 2011-12-02
> **Linuxratty said:**
> LOL! I never had this happen, but would like to see it.

Yeah, let me tell you, it gets old *real fast*  ](*,)

I stupidly clicked on autobounce to see what happened. Kids, do not try this at home.  The ball flies around the desktop (btw it does not seem to bounce off the borders with any sort of physical reality) and you can't catch it without difficulty, then if you do, you have to "let go" to click on the 'remove' control, and off it goes again... :evil:

This solution worked for me. [I'm on kubuntu 11.04, KDE v4.6]
The plasma widgets are controlled by a configuration file in 
~/.kde/share/config/plasma-desktop-appletsrc

Open this file in your text editor of choice (nano, kate, or vi, or whatever), and find the stanza (i.e. segment of the file) with the name BbalL in it (that's a lowercase el followed by an uppercase one. Why the stupid leet naming, huh?).

One line of that stanza will have the line 'autobounce=true'. Change it to 'autobounce=false', and save the file.

Log off from your KDE session, and log back in again.  The infernal ball will now be static on your desktop, and you can (with widgets unlocked) click on its remove control and banish it forever.

Hope that helps.

Jonathan

---

### Post by kio_http on 2011-12-02
I do this for fun sometimes. I set autobounce and try to catch it!

---

### Post by jnorichards on 2011-12-02
> **kio_http said:**
> I do this for fun sometimes. I set autobounce and try to catch it!
Hmm. Have you considered chewing on a hedgehog?  Should be equally fun, I'm guessing!
:popcorn: <- and equally poor spectator sport :)

---

### Post by Eliah Jasper on 2012-03-01
Yes I thanks alot.!....this is my second day on linux.....i thought i go crazy....it worked but after rebootin kubuntu all my widgets were gone...
respect

---

### Post by osirisgothra on 2013-02-04
i almost comitted suicide over trying to catch that stupid thing from bouncing all over the place...... kids screaming.... dog barking at me... cats on top of the monitor swatting at it... arrrgghhh!!! i'm getting my knife kupo!!

Version 12.10 of ubuntu... ver 9.4.2 kde and STILL NO FEATURE to get rid of that ball any easy way!! who made it??? where does he/she live??? if you know, then can you sell me a gun too??????? I'll have some driving to do.... :)

BTW FUTURE READERS:
Do what was suggested above, but if you dont want to reboot (my server takes FOREVER to do post and stuff) do it by 'logging off' of your kde session (or "Leave").. when you arrive back at your greeter/login screen, then ALT+SHIFT+F1 to get to a TTY terminal and log in (i did it as root just to make sure i didnt run into permission problems), then edit that file "~/.kde/share/config/plasma-desktop-appletsrc" as said above (i also set the gravity to 0), then save it under the same name (i use pico (nano), so you can just hit CTRL+O, then CTRL+X) and exit and then logout, press CTRL+F7(usually, sometimes its CTRL+F8 or CTRL+F9, depending on how many TTYS are setup)
and then proceed normally. The ball will still be there but at least not bouncing (thanks jnorichards saved me from going bald and grey and becoming a murderer)..

---

### Post by Jakin on 2013-02-04
Ah the bouncing ball.. i put it on one my other deskspaces to have some fun with when im super bored, mine always eventually calms and stops though..

---

### Post by montag dp on 2013-02-04
This thread should have a warning with it!  I read the first post just thoroughly enough to get curious, which means I didn't read about the autobounce part ... which means I ended up in the exact same predicament as the OP.    :lolflag:

I was eventually able to catch it.

---

