---
title: "Crontab"
date: 2010-11-02
forum: Server Platforms
---

### Post by Strega on 2010-11-02
Hello,

I'm trying to set up a crontab. I type
```
crontab -e
```...and the only thing showing up is```
29
```When I enter the crontab I would like to execute and press enter I get this```
29
* 3 * * * /srcds/public.sh restart
?

```I don't know what that ? means and I also don't know how to save this file.
Any solutions?

Regards,
Strega

---

### Post by Ryan Dwyer on 2010-11-02
I just edit the /etc/crontab file manually. Never had any problems.

---

### Post by Strega on 2010-11-02
> **Ryan Dwyer said:**
> I just edit the /etc/crontab file manually. Never had any problems.Well, I've done that too but there was no result. Also, I've heard the crontab file is ran by root and since it's a process it can be unsafe.

---

### Post by mdojka on 2010-11-02
Assuming you're running bash.  Try this:

# export EDITOR=vi
# crontab -e

---

### Post by Boondoklife on 2010-11-02
> **Strega said:**
> Well, I've done that too but there was no result. Also, I've heard the crontab file is ran by root and since it's a process it can be unsafe.

Anything ran by root has a possibility of causing an issue. It is up to you to make sure that does not happen by only putting trusted programs/scripts into crontab.

---

### Post by Strega on 2010-11-02
> **mdojka said:**
> Assuming you're running bash.  Try this:

# export EDITOR=vi
# crontab -e

Fantastic :D It worked!
Thank you

Regards,
Strega

---

