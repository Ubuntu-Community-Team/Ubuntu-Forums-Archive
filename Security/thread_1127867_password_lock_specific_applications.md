---
title: "password lock specific applications?"
date: 2009-04-16
forum: Security
---

### Post by AFarris01 on 2009-04-16
Is this possible? I was seeking to password lock the launch of particular applications (Evolution in my case) without using sudo/gksudo in the launch so that without the user entering their login password, the application would not launch.

This question came up when setting up Evolution for my father, who is used to programs, such as AOL and Lotus Notes, that required a password when launching the program, and was somewhat disgruntled when he found that Evolution did not do likewise... so i wanted to see if there was some way to accomplish this sort of operation.

He's already got seperate passwords for everything, and none of them are being automatically remembered, so its not THAT big of an issue, but i was just wondering if this was possible somehow

Thanks!

Andrew

---

### Post by alfplayer on 2009-04-18
So you want to disallow Evolution for every user except you? without a password dialog?

---

### Post by Carl Hamlin on 2009-04-18
Unless you've disabled password-protected login, he's already proved his identity by logging into the machine itself. If he's not keen on logging out every time he get up, then he can certainly lock the screen, as well. You can even set it up so that a screensaver activates after a certain amount of idle time, and locks the screen *for* him.

No need to specifically password protect individual applications, under the circumstances.

---

### Post by alfplayer on 2009-04-18
Maybe he just wants to lock Evolution. Locking the screen means locking the system, this way only the current user can unlock it, which is a limitation. If he logs out and decides to use the computer again he will have to log in again, which is also a limitation because applications have to be reopened and it takes some time.

However, if he wants to disallow other users to open Evolution he can do it with file permissions.

---

### Post by bodhi.zazen on 2009-04-18
I suggest you simply write a simple wrapper script that asks for a password and then calls Evolution.

But I agree with Carl Hamlin

The more practical solution, IMO, is to encrypt your father's home directory.

See : [http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by AFarris01 on 2009-04-19
Thanks for all the replies everybody!

I was actually considering writing a small script that would ask for his password, then launch evolution, but i got to thinking that doing so would, in the end, only 'look' secure, without actually being so.*

Also, the original intention wasn't to lock out access to evolution completely to all users... which, in hindsight, is how i asked it in the original post, and was wrong. Upon more reflection, I think this is more of a 'feature wish' for Evolution, rather than an issue trying to password lock a particular executable.

finally...
@bodhi.zazen: Thanks very much for the link! I'll be reading up on that, and i'll present my dad with that information and see what he thinks.

Thanks everybody!

---

### Post by HermanAB on 2009-04-20
The Ubuntu way is to control this kind of stuff in /etc/sudoers file.  So read 'man sudoers'.

---

