---
title: "Password to delete all data"
date: 2012-04-30
forum: Security
---

### Post by Tenginec on 2012-04-30
Hi Folk.
Who has seen a solution for the complete removal of data with the introduction of a specific password?
 Or how to authenticate a user in two different passwords?
 Thank you.

---

### Post by HermanAB on 2012-04-30
Encrypt the data and forget the password when you want to delete it.

Hit yourself upside the head with a brick when required...

---

### Post by nutpants on 2012-05-01
add a user where when it first logs in a script runs that wipes the encrypted home of the user you want to protect.

should be doable.
even better if you don't have a user list at login. could even have a user auto login if you don't stop it that wipes partition table.

just don't snoose at login

redneck tech but should work.

---

### Post by HermanAB on 2012-05-01
You don't need to erase encrypted data.  If the encryption is any good, it is already 'random noise'.  So all you need to do is forget the password.

---

### Post by Tenginec on 2012-05-01
Encryption is the protection from his wife or friends in the office.
Forgotten your password to any of you remember using a soldering iron will help.
And if the data have already been destroyed? Forced to remember the password does not make sense.

---

### Post by nutpants on 2012-05-01
> **HermanAB said:**
> You don't need to erase encrypted data.  If the encryption is any good, it is already 'random noise'.  So all you need to do is forget the password.

forgetting your password only works in countries that feel your freedom and well being is more important than their security.

and that is very few countries indeed.

encrypting your girlfriends phone number so your wife can never see it
is a whole other topic. one where forgetting works fine. 
but where the fact that something is encrypted is far more damning than what is really being encrypted.

but this is not a topic about the necessity of encrypting personal information in case it is lost,stolen or just being peeked at by your wife.

---

### Post by beboylips on 2012-05-04
Add a start up script to delete the data you want (use shred, not rm). Set a timer on the script (maybe 30 seconds) and unless you kill the process, it will delete the files.

On login, open terminal, type in "killall <name of the process>, and done, files safe. 

What do you think?

-Beboy

---

### Post by duncan12 on 2012-05-04
> **beboylips said:**
> Add a start up script to delete the data you want (use shred, not rm). Set a timer on the script (maybe 30 seconds) and unless you kill the process, it will delete the files.

On login, open terminal, type in "killall <name of the process>, and done, files safe. 

What do you think?

-Beboy

You wouldn't want to, for example, walk away at login for some reason, and come back to have all your files deleted.

The script should be opt-in when you do need to delete the files, not "opt out - quickly!" at every login. ;)

I tend to agree with @nutpants. Make a new user that you wouldn't normally use. Then you could use your idea, for extra security against accidental deletion. But not with the same user as you'd be using day to day.

---

