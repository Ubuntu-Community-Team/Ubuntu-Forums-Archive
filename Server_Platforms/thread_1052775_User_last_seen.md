---
title: "User last seen"
date: 2009-01-28
forum: Server Platforms
---

### Post by SeaborneClink on 2009-01-28
Hey I've been googling for a fair few minutes, and dropped by IRC to ask.

What I'm looking for is some type of command or a flag on a command that will allow me to see when the user last logged in.

ex.
```
fred  2009-01-24 17:56:45
george  2008-3-15 12:15:23
```

Is there anything that exists like this for the server command line?

---

### Post by x33a on 2009-01-28
open terminal

type: last

---

### Post by HermanAB on 2009-01-28
or type:
$ sudo tail -f /var/log/secure

for a running commentary.

Cheers,

Herman

---

### Post by SeaborneClink on 2009-01-31
Thanks so much guys :)

---

### Post by tubezninja on 2009-01-31
If you want just the last seen on a specific user, install finger.

```
sudo apt-get update && sudo apt-get install finger
```

then

```
finger <username>
```

Will show when they last logged on, and last read mail (if your server or workstation has mail).

---

### Post by electrogeist on 2009-01-31
People used to finger each other all the time!

---

### Post by linux_tech on 2009-01-31
You can also check the last number of times a user has logged on by using command 
```
  last -n [username] 
```

---

