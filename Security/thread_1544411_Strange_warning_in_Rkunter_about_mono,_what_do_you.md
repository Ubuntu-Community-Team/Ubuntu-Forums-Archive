---
title: "Strange warning in Rkunter about mono, what do you think."
date: 2010-08-02
forum: Security
---

### Post by MechaMechanism on 2010-08-02
I got a warning from Rkhunter that I had never seen before.  I have the Silverlight plugin.  Do you think this is from the Silverlight plugin.  It seems to me that this is because of Silverlight, but I wanted to be sure since I'm not familiar with mono.  I don't use any other mono apps that I'm aware of, such as F-Spot or Tomboy.


/dev/shm/mono-shared-1000-shared_fileshare-universal-mechanism-Linux-x86_64-40-12-0: data
/dev/shm/mono-shared-1000-shared_data-universal-mechanism-Linux-x86_64-328-12-0: data
/dev/shm/mono.9756: data

---

### Post by cariboo on 2010-08-02
Have you run

```
rkhunter -update
```

 since you installed the silverlight plugin? If not, run it and then run rkhunter again to see if you get the same results.

Mono is installed by default, even if you don't use any apps using it.

---

### Post by MechaMechanism on 2010-08-02
> **cariboo907 said:**
> Have you run

```
rkhunter -update
``` since you installed the silverlight plugin? If not, run it and then run rkhunter again to see if you get the same results.

Mono is installed by default, even if you don't use any apps using it.
No update is available for Rkhunter.  But I think it has to do with mono.  So I'll just keep an eye on it for now.  Thanks anyway.

---

### Post by cariboo on 2010-08-02
Rkhunter is really not a very good tool, as it comes up with false positives, and it doesn't find most rootkits. The last two I played with weren't detected by either rkhunter or chkrootkit.

---

### Post by FuturePilot on 2010-08-02
This is normal. Nothing wrong.

---

### Post by MechaMechanism on 2010-08-05
> **cariboo907 said:**
> Rkhunter is really not a very good tool, as it comes up with false positives, and it doesn't find most rootkits. The last two I played with weren't detected by either rkhunter or chkrootkit.
I hear ya and agree.  I engage in various voodoo practices with my computer ;), why, beats me.  I used to use Windows years ago, so maybe voodoo habits die hard.

---

### Post by cariboo on 2010-08-05
If you are running the utilites, without knowing why, it makes it harder to interpret the results.

There are plenty of post/threads here that advise you on how to track down unusual activity, without having to resort to rkhunter/chkrootkit.

---

### Post by MechaMechanism on 2010-08-05
> **cariboo907 said:**
> If you are running the utilites, without knowing why, it makes it harder to interpret the results.

There are plenty of post/threads here that advise you on how to track down unusual activity, without having to resort to rkhunter/chkrootkit.
I'm well aware of the capabilities of rkhunter and chkrootkit.  I use a wide variety of tools.  And I do not rely on them to do all the work.  Thats why I was here on the forums to ask about mono and my research into it put me at ease.  The voodoo was only to the fact that security tools are really only effective against known attacks although they can be somewhat effective as a brick wall but not for very long.  Hence the biggest part of security is about proper damage control.  By far the greatest amount of effort that I expend is into damage control, so I am not down for the count very long.

You are right about what you said though as it applies to anybody who relies on tools alone to do all the work for them.

---

### Post by unspawn on 2010-08-06
> **cariboo907 said:**
> and it doesn't find most rootkits. The last two I played with weren't detected by either rkhunter or chkrootkit.
You're most welcome to help improve them.

---

### Post by OpSecShellshock on 2010-08-06
> **unspawn said:**
> You're most welcome to help improve them.

Not much point. An application that tries to find rootkits still ultimately suffers from the self-reporting problem if a machine actually is compromised (can't trust what it says about itself). There's nothing stopping a rootkit (or whatever user/process it's trying to hide) from altering the expectations and configurations of the detection software, and then hiding the fact that it's done so.

But of course, the risk of such things is very low barring an intruder having physical access to the machine, or an approximation of physical access by fooling the legitimate user or impersonating a legitimate user via remote connections. A rootkit is just there to hide the activities that follow a successful compromise from the target computer and its users. It's a tool whose job is maintaining the persistence of some other thing that's already happened. Most likely it would be specifically designed by the intruder for the target system.

---

