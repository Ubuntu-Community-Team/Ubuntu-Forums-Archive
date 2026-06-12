---
title: "gksu and sudo timeout = bad"
date: 2010-03-07
forum: Security
---

### Post by fermulator on 2010-03-07
Has anyone every discussed (I'm sure they have) this potential security problem with gksu and sudo timeouts?

Consider:

Every time a user has to input their "sudo" credentials, these actually last for many seconds (I've never timed it .. but it might even be on the order of minutes).

i.e.

 A) Action: Ubuntu Updates.  This requires the root password, and is prompted via gksu password prompt.
 B) now, for xx mins, if we try to do other gksu actions, the user IS NOT prompted again!  It would be very easy for virus/spyware/etc. (if they existed) to sneak in under the radar without the user knowing.

The same applies to sudo commands in the terminal.

i.e.

 A) Action: sudo ls /
 B) now, for xx mins, if we try to do another sudo action, the user is NOT prompted for their password until some timeout period.  Again, seems like a vulnerability.

Is this being addressed?  Considering Linux's reputation for security, I'm very interested to know how we can fix it, or if it's already in the works.

---

### Post by FuturePilot on 2010-03-07
```
sudo visudo
```

Add this to the Defaults line

```
timestamp_timeout=X
```
Where X is the number of minutes. Be sure to separate it from existing "Defaults" options with a "," No spaces. Ctrl+X to save and quit.

---

### Post by fermulator on 2010-03-07
If I specify 0, is that actually zero, or infinite?

---

### Post by FuturePilot on 2010-03-07
> **fermulator said:**
> If I specify 0, is that actually zero, or infinite?

It should be zero. -1 is infinite for the session.

---

### Post by cariboo on 2010-03-07
Remember if you set the timeout to 0, you will have to enter your password every time you use sudo. gksudo and gksu.

---

### Post by aysiu on 2010-03-07
> **fermulator said:**
> Has anyone every discussed (I'm sure they have) this potential security problem with gksu and sudo timeouts? Yes, it's been discussed plenty of times:
[sudo timeout: security risk?](http://ubuntuforums.org/showthread.php?t=1236036)
[Security issues with sudo](http://ubuntuforums.org/showthread.php?t=1215058)
[What do you think about the 5 minute sudo window?](http://ubuntuforums.org/showthread.php?t=1056529)
[sudo privilege escalation flaw?](http://ubuntuforums.org/showthread.php?t=1051348)
[can programs run sudo ... without password within sudo's 15 minutes?](http://ubuntuforums.org/showthread.php?t=1045209)
[Gksudo and Ubuntu's security model](http://ubuntuforums.org/showthread.php?t=910201)
[How much of a security risk could the sudo timeout become?](http://ubuntuforums.org/showthread.php?t=709580)
[Sudo=Bad Security!](http://ubuntuforums.org/showthread.php?t=26115)

Obviously it's more secure to have no timeout, but we already get enough people complaining about too many password prompts even *with* the timeout. If Ubuntu devs changed the timeout to 0 by default, it would induce the convenience-over-security users to just log in as root all the time or disable the prompt altogether. If you make it difficult for people to put on a seat belt, they will just drive without it. The default 15-minute timeout is a compromise between usability and security.

My guess is that as Ubuntu becomes more popular and more and more security threats appear, there will be more pressure on the Ubuntu devs to shorten that timeout.

---

### Post by fermulator on 2010-03-08
Linux has a pretty good security model.

I don't see a problem with setting a default value of 0s for this sudo/gksu timeout.

We don't want to leave regular users vulnerable.  Especially since we have a steadily growing number of newcomers switching to Linux, it's dangerous to have such a long timeout.  "Linux Newbies" don't know what's "normal" and what's an "attack".  Sure a timeout = 0 comes close to the Vista fiasco w/ UAC, but it's secure.  Not everything requires root access anyways.  A lot can be done without root password, and if it requires elevated privileges, the user should be prompted for authorization to modify system level stuff.

For power and expert users, if they want to increase the timeout, easy peasy.  They're power users, and they'll either already know how to change the default, or they'll know how to learn about it.  (even better, this setting is easily configurable in system configuration...)

Anyways, just my two cents.  In summary, I think the default should be 0s.

---

