---
title: "Ubuntu one asking for keyring"
date: 2009-11-17
forum: Ubuntu One (CLOSED)
---

### Post by gabe17 on 2009-11-17
Hi, I am using Ubuntu One (ehm, I am just starting), and everytime I log in to Ubuntu, it shows me a window like on the screenshot included...it wants from me a keyring. Why does it wan't? And what can I do that this window not to be shown everytime I log in to the system? Sorry for noob question and thanks for help.

---

### Post by pootan on 2009-11-18
I had a similar issue with Ubuntu One asking for access whenever I sent or received emails. It's very annoying that Ubuntu One/Couch Desktop/CouchDB tries to integrate itself into everything without first asking if I want it to. 

I found the best solution for me was to remove Ubuntu One, Couch Desktop and Couchdb and the 4 or 5 dependencies that show up with it(one of which is python related) until they can come up with an unobtrusive Cloud computing solution.

---

### Post by pixelmuerto on 2009-11-19
I have same problem, 
how I can add a application to the keyring ? 

many thanks.

---

### Post by pixelmuerto on 2009-11-19
pootan, 
  don't remove ubuntuOne of system, only remove of list of applitation in begin system.

System > preferences > "application in begin"

---

### Post by gabe17 on 2009-11-23
I've removed it from application in begin. Thanks for your advice.

---

### Post by joshuahoover on 2009-11-24
> **gabe17 said:**
> Hi, I am using Ubuntu One (ehm, I am just starting), and everytime I log in to Ubuntu, it shows me a window like on the screenshot included...it wants from me a keyring. Why does it wan't? And what can I do that this window not to be shown everytime I log in to the system? Sorry for noob question and thanks for help.

This will occur when using Ubuntu One in one of two scenarios:

1) You are setup with auto-login
2) Your keyring password is different than your login password

For #1, I suggest users setup a login and then you'll only have to login once. All applications requesting access to the keyring will have access as long as the keyring password and login password are the same.

For #2 you can open Applications->Accessories->Passwords And Encryption Keys, right-click on the "Passwords" folder and select "Change password". Change the password to match your login password.

Thank you,

Joshua

---

### Post by artm on 2009-12-08
That defies the whole purpose of the auto-login option. If I configure my user to auto-login, it means I don't want to type in passwords period. May be this is the computer inside my secret underground lair, if the enemy managed to get to it, it's too late to protect ubuntu one from them: I'm most probably already dead anyway.

---

### Post by joshuahoover on 2009-12-15
> **artm said:**
> That defies the whole purpose of the auto-login option. If I configure my user to auto-login, it means I don't want to type in passwords period. May be this is the computer inside my secret underground lair, if the enemy managed to get to it, it's too late to protect ubuntu one from them: I'm most probably already dead anyway.

True, but this isn't just Ubuntu One. This is going to happen with any application that uses the keyring.

---

### Post by nimrodmilo on 2009-12-19
I didn't really understood the process advised for the first scenario, should I login only once with my regular login ? or should I just disable the autologin for good ?

---

### Post by sofasurfer on 2009-12-19
I don't know what is meant by "Ubuntu One".
I have Ubuntu 8.10. I disabled login but I still have to enter my password for keyring in order for wireless network to connect.
How can I eliminate this password request?
Like the other guy said, the Soviets have already entered my National Security computer. Its just a matter of time before they crack the password for internet access. Lets just eliminate that security layer. 
How?

---

