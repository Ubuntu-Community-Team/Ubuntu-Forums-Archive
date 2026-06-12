---
title: "I'm logged in twice"
date: 2010-07-05
forum: Security
---

### Post by halfpower on 2010-07-05
When I issue the command "users" or "finger," I can see myself logged in twice.  That is, at least if I'm using a desktop environment.  It doesn't matter who I'm logged in as.  If I log in as root, I see two instances of the user root.  I just noticed this today.  It did not happen in the past.  Is there just happening because I'm using a newer version of *nix?

---

### Post by squaregoldfish on 2010-07-05
Every time you start a new terminal window, you get a new login session. This is entirely normal and nothing to worry about.

The command 'w' will show that you have one user for the X login (tty7), while your other logins are from pseudo terminals (pts/x), which are set up to handle the terminal window environment. As soon as you close the terminal, the pseudo-terminal disappears.

Steve.

---

### Post by halfpower on 2010-07-07
This is not standard behavior though.  I've used more than a half dozen *nix distros, and I've never seen this before.  I have Konsole open right now, and there is no double login.  In fact, I can open up two instances of Konsole, and there is still no double login.

---

### Post by kemra on 2010-07-07
I believe Steve is correct the standard behaviour is that when a new shell is opened a new user session is spawned for that shell. I have experience with other *NIX's and in my experiance they have also tended to adhere to this rule.

---

