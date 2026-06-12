---
title: "Indication to user of 2D or 3D running?"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-03-16
So far in beta 1 I cannot see anything which is a positive indication showing which session is running, 3D or 2D.
It comes to mind because the test machine I used initially seems to have graphics which probably runs only in 2D, (in the alpha and beta, anyway). I actually had no idea it was falling back to 2D  even though I seemed to be getting some 'problems' with what I saw, or did not see, on the display. It was only when I installed beta1 on another machine did I realise that the second machine ran in 3D and did not fall back to 2D and that the original apparent anomalies in display behaviour  I had seen were probably because the first test machine was silently falling back to 2D. If I log out and then log in again, the session is not indicated as (previously) 2D.

1) is there an indication of state of running in 2D?
2) is the lack of indication of previous session 2D or 3D at login session list - a bug?

tia

---

### Post by mraandtux on 2012-03-16
You have to figure it out by Unity panels.

---

### Post by x-shaney-x on 2012-03-16
In an ideal world, the two would be as indistinguishable as possible so those with older/weaker hardware have as close as possible the same experience as the rest.

Suppose the easiest and most obvious way is to look at the menu bar:
By default, 3D has a drop shadow whereas 2D doesn't.

Or hover your pointer over the menu bar when using a non-maximized app:
On 3D the window title fades at the edge where the menu starts.
On 2D it is a much sharper line and the window title is simply cut off.

---

### Post by mc4man on 2012-03-16
```
echo $DESKTOP_SESSION
```
if it returns ubuntu you're on unity 3d, if it returns unity-2d ..

---

### Post by Splooshie123 on 2012-03-16
I don't know if it still applies but in Lucid at the login screen there is a bar at the bottom which lets you select a desktop environment (GNOME, xterm, fail-safe GNOME). Maybe if it still exists in Pangolin and would show Unity 2D and Unity 3D.

---

### Post by candtalan on 2012-03-16
> **mc4man said:**
> ```
echo $DESKTOP_SESSION
```
if it returns ubuntu you're on unity 3d, if it returns unity-2d ..

bingo! thanks. That answers my main problem. The machine is only running in 2D.

But I recall that ubuntu 11.04 and 11.10 indicate in the login screen sessions options, a persistence of the previous session. 
12.04 beta1 updated does not (yet), so in principle the lack of indicated session - at login  - it is a bug I guess?

---

### Post by jerrylamos on 2012-03-16
I just look at the bottom edge of the top border.

If it's fuzzy and indistinct, it's Unity-3D.  Compiz is king of fuzzy, foggy, and indistinct.

If it's sharp and clear, it's Unity-2D.  No Compiz overhead.

I run mostly -2D on faster pc's, and also lubuntu on this handy older laptop next to the breakfast table.

Actually, I run full screen applications mostly like Firefox so I don't see the desktop anyway.  Even on my 1440x900 and 1280x1024 screens.  On this 2005 Thinkpad T40 1024x768 14" diagonal screen I've got a clear comfortable 36 lines.

Enjoy.

Jerry

---

### Post by jbicha on 2012-03-16
Also, the new Alt-tab only works on Unity 3D. If you can come up with a good, simple-to-explain way to distinguish the two, it would make a great addition to [https://help.ubuntu.com/11.10/ubuntu-help/fallback-mode.html](https://help.ubuntu.com/11.10/ubuntu-help/fallback-mode.html)

---

### Post by grahammechanical on 2012-03-16
In 12.04 you click the small Ubuntu icon that is on the login panel where you put your password. You should see Ubuntu, Ubuntu 2D and whatever other user interface/shell you have installed.

It is there. I have it on two installs of 12.04. One install dates back to November when all the labelling was 11.10 and the other install which is a default 12.04 Beta 1.

Don't forget that Ubuntu does not install any proprietary software unless we ask it to. This includes proprietary video drivers which are often necessary to get Ubuntu 3D. So, a new install will always default to Ubuntu 2D. Then we run Additional Drivers and we get the Ubuntu option which is Unity 3D.

Regards.

---

### Post by jbicha on 2012-03-16
graham, that's wrong on two accounts. Many computers support Unity 3D without needing proprietary drivers (Intel's open source drivers are great, nouveau works on my wife's computer, etc.)

Also, since even selecting Unity 3D will actually run Unity 2D if the drivers aren't sufficient, we're looking for an easy way to tell which you're actually running.

---

### Post by mc4man on 2012-03-16
Well unity-3d has a panel menu on Desktop focus, unity-2d doesn't. Also launcher icons can be pulled out of the launcher in 3d, not in 2d.
Still think the most obvious is just the command

---

### Post by grahammechanical on 2012-03-16
So this is not true?

> Don't forget that Ubuntu does not install any proprietary software unless we ask it to. This includes proprietary video drivers which are often necessary to get Ubuntu 3D.

When I disable my Nvidia driver the system defaults to Nouveau which in turn dumps me into 2D mode. I knew straight away that I was no longer running 3D because of the change in icon size. Also any compiz special effects stop working.

This is the comment I was referring to

> If I log out and then log in again, the session is not indicated as (previously) 2D.

Well, on my system LightDM does give this information.

This is still true, is it not?

> In 12.04 you click the small Ubuntu icon that is on the login panel where you put your password. You should see Ubuntu, Ubuntu 2D and whatever other user interface/shell you have installed.

If this is not happening on the OP's system is it a bug in 12.04 or an issue particular to his set up?

Regards.

---

### Post by mc4man on 2012-03-16
> If I log out and then log in again, the session is not indicated as (previously) 2D. 

At least here the previously used session is always auto reused but if in the login screen  you expose the menu it doesn't indicate which one that was.
The 'highlight' always goes to the 1st. listed

---

### Post by kaldor on 2012-03-16
This might be somewhere else in this thread, so excuse me if this has already been said.

GNOME has the ability to tell the user what "Experience" they have in their Details > Graphics section. GNOME Shell shows "Standard", while fallback shows "Fallback". In Unity, no such details exist. Maybe this should be considered a papercut?

Ideally, it shouldn't matter, indeed. However, the user should still be able to visually find out the DE that they are currently using. They don't want to log out and check the Greeter or type commands.

---

### Post by mc4man on 2012-03-16
> **kaldor said:**
> This might be somewhere else in this thread, so excuse me if this has already been said.

GNOME has the ability to tell the user what "Experience" they have in their Details > Graphics section. GNOME Shell shows "Standard", while fallback shows "Fallback". In Unity, no such details exist. Maybe this should be considered a papercut?

Ideally, it shouldn't matter, indeed. However, the user should still be able to visually find out the DE that they are currently using. They don't want to log out and check the Greeter or type commands.
How does this work out? (simple source edit to what shows on Desktop focus
It also could be Ubuntu-2d Desktop, whatever suits

[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/957215](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/957215)

---

