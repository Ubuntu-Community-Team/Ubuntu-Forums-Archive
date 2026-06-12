---
title: "Possible Security risk with sudo involed with ssh and bash scripts ?"
date: 2009-02-12
forum: Security
---

### Post by Dave_Connor on 2009-02-12
I was trying out an update bash script I wrote of the commands I use to save time and when I used "ssh sever" "location of script" it required sudo and when I enter the password it is in plain text and can be seen. Isn't usally there is a guard against the password being shown on screen to prevent someone who has physical access to the computer to look at the person who is on to prevent them writing the password ?

---

### Post by hyper_ch on 2009-02-12
I have no clue what you have done or what you have tried. Please explain in more detail.

---

### Post by argie on 2009-02-12
I will explain since I'm able to replicate this:
1. Create a script on ssh server with these contents and call it file.sh:
```

#!/bin/bash

sudo aptitude update

```
2. Make it executable.
3. Run the script remotely by logging in (I use keys to login)
```

ssh remotehost ./file.sh

```
4. You are prompted for password.
5. Password is visible as you type it.

Pretty neat find, Dave_Connor.

---

### Post by hyper_ch on 2009-02-12
hmmmm, interesting...

---

### Post by Neural oD on 2009-02-12
looks like we need a patch ;)

---

### Post by sanemanmad on 2009-02-12
Yup, Just confirmed on 8.04 Hardy and 8.10 Ibex (Server).

---

### Post by cdenley on 2009-02-12
Try this:
```

ssh -t remotehost ./file.sh

```

---

### Post by argie on 2009-02-12
Neat! Works great.

---

### Post by Dave_Connor on 2009-02-13
So will the "-t" setting in ssh be patched or be fixed in some manor ?

---

### Post by cdenley on 2009-02-14
> **Dave_Connor said:**
> So will the "-t" setting in ssh be patched or be fixed in some manor ?

If you think ssh should force pseudo-tty allocation by default when executing a single command given as an argument, then perhaps you should file a bug report (if one doesn't exist already).

---

### Post by sanemanmad on 2009-02-15
> **cdenley said:**
> If you think ssh should force pseudo-tty allocation by default when executing a single command given as an argument, then perhaps you should file a bug report (if one doesn't exist already).

Kinda strange... but maybe it's that way for a good reason?

---

### Post by Dave_Connor on 2009-02-16
Sorry to disagree and not trying to sound mean. But isn't issues like this can be a security concern and should be looked at ? I'll file a bug report but just saying.

---

### Post by bodhi.zazen on 2009-02-16
> **Dave_Connor said:**
> Sorry to disagree and not trying to sound mean. But isn't issues like this can be a security concern and should be looked at ? I'll file a bug report but just saying.

The proper action, with any application on any distro, is to file a bug report. Bug reports are how things like this get fixed, not posting on the forums.

One of the joys of finding a bug and filing a bug report is you get to subscribe to the bug report and see what happens to it.

The behavior you have identified is IMO a minor problem as it requires physical access (to see the password in the terminal).

If someone has physical access you are in a whole lot of hurt anyways ...

---

