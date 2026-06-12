---
title: "shared desktop launcher"
date: 2018-06-20
forum: Server Platforms
---

### Post by N-t-F on 2018-06-20
Hello everyone,

I have found how to create shared menu entries (by placing [FONT=Courier New].desktop[/FONT] files in [FONT=Courier New]/usr/share/applications/[/FONT], with the possible additional tweaking of [FONT=Courier New]/usr/share/icons/[/FONT] and [FONT=Courier New]/usr/share/desktop-directories/[/FONT]).

Now I'm stuck when trying to put them not only in main menu, but also on desktop. Is it even possible without excessive hassle? I mean I could probably use scripts to put them on all users desktops, since I am root on the fileserver. First problem: ugly practice, really. Second problem: launchers would be there even when they log on systems where the corresponding application is not installed.

Thanks!

PS: Xubuntu 18.04, regular amd64 desktop version, but a solution spanning various flavors or even distributions would obviously be best.

---

### Post by ajgreeny on 2018-06-20
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit as you appear to be dealing with a server system.

I think you may also need to explain a little more clearly exactly what you're trying to do as it is not totally obvious to me, perhaps because I am not a server administrator.

---

### Post by kerry_s on 2018-06-20
sounds like you need a script to me.

first you need to check for the app:
```
which app-name
``` -> if not installed, install it, which is going to require root

second you need to get it there:
```
cp /path/to/*.desktop /home/*/Desktop

```
then you need to make it trusted & launch-able:
```
gio set "$@" "metadata::trusted" yes && chmod +x "$@"

```

pretty basic, should be easy to whip up a script.

---

### Post by N-t-F on 2018-06-21
@ajgreeny

Hello, and thanks for your interest.

Apparently I really wasn't clear at all indeed: the problem *is* on clients.
What I meant is that I could devise somewhat of a fix server-side because I luckily have admin rights on it, but I would much rather configure desktop clients instead.

I have about 180 pc on which users can log using LDAP accounts, automounting home directories from a file server.
So I would like the client's system to display launchers of locally available applications straight on user's desktop.

Sorry for the mess, I honestly hadn't realized how confusing it could be.

---

### Post by N-t-F on 2018-06-21
@kerry_s

Thanks for the tips.

This is exactly the kind of solution I was thinking about and would like to avoid. Launchers wouldn't adapt to locally available or unavailable applications, for instance. Plus I'm not keen on meddling with user's files.

That said, I didn't know about the "metadata::trusted" part, good to know!

---

### Post by kerry_s on 2018-06-21
it's the > locally available or unavailable applications that would be the issue, your talking about different launchers for 180?

cause i was think since your already automounting home, just create a "Desktop" folder with the launchers & soft link it in home. hmmm, not sure if i'm saying that right. :)

---

### Post by N-t-F on 2018-06-21
> **kerry_s said:**
> it's the  that would be the issue, your talking about different launchers for 180?

Indeed, different either in space (ie. some computers being better geared toward math processing, or having a good GPU, or simply having access to specific software licenses), or in time with the change of OS version, use of new software or termination of others.

> **kerry_s said:**
> cause i was think since your already automounting home, just create a "Desktop" folder with the launchers & soft link it in home. hmmm, not sure if i'm saying that right. :)

Yes, I get your point. What I'm doing so far is packing launchers in a folder distributed through nfs and have a soft link to it in the template used to create new accounts. Not the sexiest thing for users, but acceptable. Doesn't cover the differences between computers though, only the changes over time.

---

