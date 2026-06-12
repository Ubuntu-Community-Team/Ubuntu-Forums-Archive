---
title: "KDE Neon &quot;change user&quot; just breaks my session and ends up to the same user"
date: 2020-01-20
forum: Ubuntu/Debian BASED
---

### Post by p5music on 2020-01-20
I am using KDE Neon (last release) that is based upon Ubuntu 18.04, on a Lenovo G50 (8Gb Ram).
When the computer is idle, like when listening to some music, after a certain amount of time (that does not resemble what I decided in the settings) the login screen appears, and it asks for the password.
I see also the "change user" option. If I select such option the system creates a new session for the same user, so it does not lead to the login screen.
I have en encrypted partition so I decided not to be asked for the password, being that I am asked at startup and when coming back after the screen block.

So my question is about three point:
1- If I do not set the password to be asked when logging in does it allow anyone to break my session clicking on "change user"? Are the things related?
2- Is that a bug when "change user" just leads to a new fresh session with the same user without asking me for the password?
3- Where is the lost session?

I think this information could be useful for other people too.
Thanks in advance

---

### Post by jimmyrus on 2020-01-20
> **p5music said:**
> I am using KDE Neon (last release) that is based upon Ubuntu 18.04, on a Lenovo G50 (8Gb Ram).
When the computer is idle, like when listening to some music, after a certain amount of time (that does not resemble what I decided in the settings) the login screen appears, and it asks for the password.
I see also the "change user" option. If I select such option the system creates a new session for the same user, so it does not lead to the login screen.
I have en encrypted partition so I decided not to be asked for the password, being that I am asked at startup and when coming back after the screen block.

So my question is about three point:
1- If I do not set the password to be asked when logging in does it allow anyone to break my session clicking on "change user"? Are the things related?
2- Is that a bug when "change user" just leads to a new fresh session with the same user without asking me for the password?
3- Where is the lost session?

I think this information could be useful for other people too.
Thanks in advance
Did you think about what you wrote above? Your screen locker came on because of inactivity so if you dont want it change the setting. And your questions
1- Clicking change user doesnt "break" your session it starts another one
2- No because again its creating a NEW session for a NEW user with a NEW password. Has nothing to do with your original sesion.
3- Running in the background and not lost at all. If the other user logs off you can log back in easily.

you do know that you can have multiple users logged in at the same time right?

---

### Post by coffeecat on 2020-01-20
KDE Neon is not an official Ubuntu flavour. *Thread moved to **Ubuntu/Debian Based** sub-forum.*


> **p5music said:**
> When the computer is idle, like when listening to some music, after a certain amount of time (that does not resemble what I decided in the settings) the login screen appears, and it asks for the password.

That sounds as though it could be a lock screen rather than a login screen.

---

### Post by p5music on 2020-01-20
@[**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=129087")
Doesn't the lock screen (but the time was not right for it to appear) have to ask for login too?
And why does the "change user" button reset the session for the same user (without asking for the password)?

---

### Post by jimmyrus on 2020-01-20
> **p5music said:**
> @[**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=129087")
Doesn't the lock screen (but the time was not right for it to appear) have to ask for login too?
did you set it to ask?
> And why does the "change user" button reset the session for the same user (without asking for the password)?
BECAUSE YOU ARE ALREADY LOGGED IN

---

### Post by jimmyrus on 2020-01-20
> **p5music said:**
> @[**[COLOR=#000000]jimmyrus[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133269")
Sorry but in my understanding "change user" does not mean "clear the current user session, and start a new clean session for the same user".
I cannot help you answering my questions.
Furthermore I never saw this in the past with other DEs, or Kubuntu itself.
"change user" means just that: start a new user session (that means, CHANGE USER). You are logged in as usera and clicking "change user" will let you log in as userb. Or usera a 2nd 3rd or whatever time. Simple.

Doesnt matter if you've seen it in the past or not, its here now. Can't explain it more simply and if you don't understand it I can't make you.

---

