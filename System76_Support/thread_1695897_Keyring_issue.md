---
title: "Keyring issue"
date: 2011-02-26
forum: System76 Support
---

### Post by smarmytime on 2011-02-26
Something odd has been happening the last few times I've logged on to my laptop (Panp7). Usually the way it would go would be I'd start the laptop up, select myself as user, swipe my fingerprint, and I'd be logged in, but I'd still have to manually enter the password for the keyring. The last few times I've logged in, though, maybe the last 8-10 times, I've entered my keyring password, hit enter...then a couple seconds later it prompts me to do it again. Since it started happening, I always have to enter the keyring password twice. 

Any ideas? The one thing I can think of is I installed prey (kind of a lojack system for laptops - preyproject.com), and it recommended allowing guest accounts.

---

### Post by Tank Jr on 2011-02-26
I can confirm this. I have a Pan P7, Maverick 64 bit.

---

### Post by smarmytime on 2011-02-26
You're having the same problem, Tank? The thing that's weird for me is it just started doing it one day, and it never had before.

---

### Post by Tank Jr on 2011-02-28
Yes, I am having the same issue. I did not think about it until I saw your post, and now it seems to me that initially I too did not have this issue. And in case you are curious, I did not install the software that you mentioned.

---

### Post by isantop on 2011-03-01
This is a known issue, caused by the fact that GDM did not get your password when you logged in, and thus can't send it to the keyring to unlock it. You can solve this by changing the keyring to use a blank password, but that is less secure.

---

### Post by smarmytime on 2011-03-01
I don't have a problem with entering in the keyring password - it's that I have to do it twice; it just seems a little odd. Just to be clear, you're saying that having to enter it in twice is the known issue? If so, I just won't worry about it, since it's only a question of a few keystrokes.

---

### Post by isantop on 2011-03-02
That is quite odd. I'd try removing then re-adding the keyring (System > Preferences > Passwords and Encryption Keys in 10.10 and later).

---

### Post by smarmytime on 2011-03-03
Ok, just looked there, and under Passwords, it shows

Passwords: login
Ubuntu One
Network Secret for blah blah
Desktop Couch user authentication
Desktop Couch user authentication
Gwibber Preference: blah blah
Gwibber Preference: blah blah
Network Secret for Auto Sprint MIFIblah blah

So would I be looking to delete one or both of the Desktop Couch auths? There are two other tabs - My Personal Keys, and Other Keys, and there is nothing listed under either.

---

### Post by isantop on 2011-03-03
Actually, just delete the entire Passwords: login item. Then, reconnect to your wireless network. This will ask you to re-enter your WiFi password, then create a new keyring password. You'll want to make the keyring password identical to your login password.

---

