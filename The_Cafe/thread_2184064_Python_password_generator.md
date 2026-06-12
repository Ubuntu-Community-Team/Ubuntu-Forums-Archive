---
title: "Python password generator"
date: 2013-10-27
forum: The Cafe
---

### Post by wille.sync on 2013-10-27
Hey fellow Linux users!

I thought that I should share my password generator with you guys.
It produces a password of at least 8 characters (random letters, numbers and special characters(if specified)).
Also, there will be no repeated characters.

The code can be downloaded from my github: [https://github.com/wille-dev/genpw](https://github.com/wille-dev/genpw)

Usage: ./genpw.py [OPTIONS] [LENGTH]



Please let me know what you think :)

---

### Post by lykwydchykyn on 2013-10-27
Not bad; here's a few pointers:

- Python's random module is not recommended for security purposes; it's recommened to use os.urandom() or SystemRandom instead (see the note here: [http://docs.python.org/2/library/random.html](http://docs.python.org/2/library/random.html))

- You might want to look into the built-in "optparse" module to process command line arguments.  It's much cleaner and more flexible.

Keep up the coding!

---

### Post by wille.sync on 2013-10-28
Thanks for the tips mate :)
Never seen optparse before, I'll have a look at that.
Regarding the random module, as the purpose is to grab a random item from a list and later checks for duplicates I see no reason in using another function though :/ Unless it somehow produces a tru word...

Anyway, thanks again :)

---

### Post by lykwydchykyn on 2013-10-28
I'm not a cryptology expert, but two points here:

- If you want to make a secure password generator, you need to use a cryptographically secure random source.  Otherwise your results will be more easily guessed by brute force attacks.  You may not envision this as a possible issue, but the whole point of a password generator is make a more secure (and harder to guess) password than what a user could come up with.

- I'm not sure that avoiding duplicates necessarily makes a more secure password.  Seems offhand like it would reduce the overall entropy of the password.

---

