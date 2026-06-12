---
title: "Gnome Nanny"
date: 2011-01-02
forum: Security
---

### Post by toolmania1 on 2011-01-02
I installed Gnome Nanny.  I can choose the times when the computer can be used and limit the internet.  However, these times are not being enforced.  Is there some other settings that are used to enforce these settings?

---

### Post by cariboo on 2011-01-03
If you are using a router, you can limit connection times, block sites and set keywords.

---

### Post by toolmania1 on 2011-01-03
That is a good idea.  However, I need it to be per user as I will still use the computer at hours when I do not want other users using it.

---

### Post by bodhi.zazen on 2011-01-03
The best way to enforce such things, IMO, is with iptables or if you prefer install squid as a transparent proxy.

With iptables you can restrict outbound traffic per user based on many factors including time of day and destination (ip address , port, etc).

If you need anything beyond those, next would be to use something such as dansguardian. Dansguardian needs some attention as it is impossible to ship with a set of defaults that will satisfy everyone.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by toolmania1 on 2011-01-03
I'll check out the iptables.
 
 
Can you set this per user?
 
 
Also, how do you get Firefox settings to be the same accross all users?  I have to install each add-on for every new user right now.  ( WOT, BetterPrivacy, NoScript )
 ( I can start a new thread if this is too far off topic.  The only reason I posted here is if I am to do the iptables per user, I will create another user in Firefox for my children to use.  But, then I have to set all the settings again and install the add-ons as far as I know.  That isn't that hard, but if I can inherit my current Firefox settings from the one user, that would be great )

 
 
> **bodhi.zazen said:**
> The best way to enforce such things, IMO, is with iptables or if you prefer install squid as a transparent proxy.
 
With iptables you can restrict outbound traffic per user based on many factors including time of day and destination (ip address , port, etc).
 
If you need anything beyond those, next would be to use something such as dansguardian. Dansguardian needs some attention as it is impossible to ship with a set of defaults that will satisfy everyone.
 
[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by toolmania1 on 2011-01-06
[FONT=Calibri]I set up dansguardian using the instructions you proveded.  Howdo I configure what it blocks and does not block now along with any other configuration settings?[/FONT]

---

### Post by bodhi.zazen on 2011-01-06
> **toolmania1 said:**
> [FONT=Calibri]I set up dansguardian using the instructions you proveded.  Howdo I configure what it blocks and does not block now along with any other configuration settings?[/FONT]

What are you wanting to configure ? Dansguardian / web content ?

For that you could configure either dansguardian or privoxy, either will work. Privoxy uses filtering and regular expressions.

[http://www.privoxy.org/user-manual/quickstart.html](http://www.privoxy.org/user-manual/quickstart.html)

[http://dansguardian.org/?page=documentation](http://dansguardian.org/?page=documentation)

If you want to limit all access, by user, by time either use squid or easier use iptables.

[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)

Note: I find iptables works best by user by time for the OUTPUT chain.

Other then that, you may need to be more specific with your questions. What are you trying to configure and where did you get stuck ?

---

### Post by toolmania1 on 2011-01-06
I did not start yet.  I went to that dans guardian page, but was not sure what to configure since I many of those posts are for other set ups like squid.


I am going to do some of the iptables this weekend, or at least try...lol


The links you provided are helpful.  I will look at the privoxy later also.  That seems like that will be a good idea.


Can you limit the amount of time a user is allowed to use the coimputer using either: dansguardian, privoxy, iptables?


I also installed gnome nanny and that has options for limiting time.  But, I could not get it to work yet.  I set it up, but the computer and internet are still usable.


> **bodhi.zazen said:**
> What are you wanting to configure ? Dansguardian / web content ?
 
For that you could configure either dansguardian or privoxy, either will work. Privoxy uses filtering and regular expressions.
 
[http://www.privoxy.org/user-manual/quickstart.html](http://www.privoxy.org/user-manual/quickstart.html)
 
[http://dansguardian.org/?page=documentation](http://dansguardian.org/?page=documentation)
 
If you want to limit all access, by user, by time either use squid or easier use iptables.
 
[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)
 
Note: I find iptables works best by user by time for the OUTPUT chain.
 
Other then that, you may need to be more specific with your questions. What are you trying to configure and where did you get stuck ?

---

### Post by toolmania1 on 2011-01-06
So, I set up the iptables that you had listed on the other post you had for your blog.  Then, on one user pointing to port 8118, I can access the privoxy site listed below.  On the limited user, pointing to port 8080, I cannot access the privoxy site listed below since dansguardian blocked it.  I am also not sure why it was blocked because it seems to be a legimate site.  

So, on to the next item.  I cannot even find where I can configure anything for dansgaurdian.  I don't have anything for it under "Parental Control" under Administration.  I looked on that documentation page for dansguardian, but they are all different set ups.  Is there a file I look at, or a menu item under System -. Administration or something like that?

Thanks for the help so far.  This is pretty fun!

:popcorn:
> **bodhi.zazen said:**
> What are you wanting to configure ? Dansguardian / web content ?

For that you could configure either dansguardian or privoxy, either will work. Privoxy uses filtering and regular expressions.

[http://www.privoxy.org/user-manual/quickstart.html](http://www.privoxy.org/user-manual/quickstart.html)

[http://dansguardian.org/?page=documentation](http://dansguardian.org/?page=documentation)

If you want to limit all access, by user, by time either use squid or easier use iptables.

[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)

Note: I find iptables works best by user by time for the OUTPUT chain.

Other then that, you may need to be more specific with your questions. What are you trying to configure and where did you get stuck ?

---

### Post by bodhi.zazen on 2011-01-06
It takes a little time and reading to learn these tools, no doubt about it.

I can not always follow from your posting style what you are trying to configure (web content, access by time of day, etc) and what tool you want help with (iptables, privoxy, or dansguardian).

Basically read the config files, they are well commented.

See also:

[http://linsec.ca/bin/view/Main/DansGuardian](http://linsec.ca/bin/view/Main/DansGuardian)

---

### Post by toolmania1 on 2011-01-07
Ya, I like it.  Coming over from Windows, I have learned a lot.

Any tips on how I can post better?  Always trying to improve communication skills.

:guitar:

---

### Post by Jallu59 on 2011-12-06
> **toolmania1 said:**
> Ya, I like it.  Coming over from Windows, I have learned a lot.

Any tips on how I can post better?  Always trying to improve communication skills.

:guitar:

I think you're posting clearly. BodhiZ was just not aware of the misbehavior of Nanny, which also I have suffered since update to 10.10. That's why he didn't fully understand your question.

How did you solve the problem ? I was unable to find the answer from these posts.

EDIT. Am I blind ? You used dansguardian instead. Misbehavior of Nanny remains unsolved-

Yours

Jallu59

---

### Post by Guido Tabbernuk on 2012-01-20
> **toolmania1 said:**
> I installed Gnome Nanny.  I can choose the times when the computer can be used and limit the internet.  However, these times are not being enforced.  Is there some other settings that are used to enforce these settings?

... and ...

> **Jallu59 said:**
> Am I blind ? You used dansguardian instead. Misbehavior of Nanny remains unsolved-

I can confirm you that I got Nanny to work on Oneiric pretty well and posted my remarks about it in [https://bugs.launchpad.net/nanny/+bug/877318](https://bugs.launchpad.net/nanny/+bug/877318)

Basically, you can use the Ubuntu repositories version (2.31.1) and easily fix the minor stuff, and at least enforcing the times will work. It may be not perfect, though. (I had some issues with autostart applications starting after Nanny blocked the desktop and which appeared above the blocker.)

That's why I took a newer development version from Nanny's GIT repository which has updated desktop blocker and this seems to work even better after some patching. I did quite a many fixes for the code myself and implemented even a system of rewarding computer use time for accepting chores from predefined list (each of them rewards different amount of time).

I plan to publish my code any time soon, but if somebody would like to help testing it first, I can send the package. I attached some images, too.

---

### Post by bodhi.zazen on 2012-01-20
> **Guido Tabbernuk said:**
> I plan to publish my code any time soon, but if somebody would like to help testing it first, I can send the package. I attached some images, too.

If you are not familiar with it, I suggest you use a ppa.

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Canonical also offers assistance for packaging

[http://developer.ubuntu.com/publish/my-apps-packages/](http://developer.ubuntu.com/publish/my-apps-packages/)

---

### Post by Guido Tabbernuk on 2012-01-22
> **bodhi.zazen said:**
> If you are not familiar with it, I suggest you use a ppa.
You can install some of my test builds from: [https://launchpad.net/~boamaod/+archive/nanny-test](https://launchpad.net/~boamaod/+archive/nanny-test)

---

### Post by torturedutopian on 2012-01-30
Oh ! Thanks for providing us with a PPA ! I've been looking for a way to get Nanny to work for months... Well, even years if I recall correctly ! Desperately needed it. (not really willing to spend hours to configure other pieces of software. Well, I could, but that's not satisfying)

Thanks ! I really hope it will be fixed upstream and will work out of the box in 12.04 !

---

### Post by torturedutopian on 2012-01-30
Just made a couple of tests. It seems to work, although I have the following issues : 

- I cannot get the systray indicator to work (so I don't know how much time I have left).

In the terminal, I get : (I tried under Cinnamon as well, to check if it was due to the lack of systray)

```
ERROR:dbus.proxies:Introspect error on :1.13:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.152" (uid=1001 pid=3919 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1141 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")
Reconnecting to new nanny server instance
ERROR:dbus.proxies:Introspect error on :1.13:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.152" (uid=1001 pid=3919 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1141 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")

```

- After a while (I'll have to double check and see if it's reproducable) I couldn't start the Nanny GUI either with some kind of dbus-related error. Rebooted and it worked again - a log out wasn't enough.

Cheers & thanks a lot !!

---

### Post by Guido Tabbernuk on 2012-01-31
> **torturedutopian said:**
> Just made a couple of tests. It seems to work, although I have the following issues : 

- I cannot get the systray indicator to work (so I don't know how much time I have left).

In the terminal, I get : (I tried under Cinnamon as well, to check if it was due to the lack of systray)

```
ERROR:dbus.proxies:Introspect error on :1.13:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.152" (uid=1001 pid=3919 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1141 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")
Reconnecting to new nanny server instance
ERROR:dbus.proxies:Introspect error on :1.13:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.152" (uid=1001 pid=3919 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1141 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")

```

- After a while (I'll have to double check and see if it's reproducable) I couldn't start the Nanny GUI either with some kind of dbus-related error. Rebooted and it worked again - a log out wasn't enough.

Cheers & thanks a lot !!
I think rebooting starts the daemon properly. Maybe it can be enhanced, I'm not sure.

Yes, I didn't take time to try to fix the SysTray application because I don't really need/use it and it probably also needs to be converted to appinidicator system. I described my changes in changelog (at [https://launchpadlibrarian.net/90786646/nanny_2.31.2~boamaod6~precise_source.changes](https://launchpadlibrarian.net/90786646/nanny_2.31.2~boamaod6~precise_source.changes)). I also considered creating a Screenlet to display used time etc, but haven't had time to do it.

Also, I don't know what to do with blocking individual applications. Anybody seen it in action? How does it work exactly? I wonder if this has worked in any point of time at all, because I don't see any code that does it. Maybe this needs some design decisions.

---

### Post by Guido Tabbernuk on 2012-02-24
I have done some work on Nanny again. This time I have fixed:

  * DBus daemon settings for normal users (before worked only as admin)
  * Timeout button label (on second run)
  * Unity delay hack (was broken in Unity 2D)
  * Support for Unity 2D, GNOME, GNOME Classic, Lubuntu, LXDE

The packages are at: ppa:boamaod/nanny-test

---

### Post by torturedutopian on 2012-02-24
Thanks for your work Guido ! Oops, too bad I cannot test it right now (switched to KDE) !

---

### Post by foxy123 on 2012-05-27
Does it work in 12.04?

---

### Post by Guido Tabbernuk on 2012-05-27
> **foxy123 said:**
> Does it work in 12.04?
Yes. I haven't actually used it in 12.04, but I tested it in beta and everything seemed to work (except known bug with "Force logoff", which should not be turned on by now, I hope to apply the patch any time soon).

---

### Post by foxy123 on 2012-05-27
> **Guido Tabbernuk said:**
> Yes. I haven't actually used it in 12.04, but I tested it in beta and everything seemed to work (except known bug with "Force logoff", which should not be turned on by now, I hope to apply the patch any time soon).

Thanks a lot for the response. I have installed it from the PPA but when I start the programme it's locked and I cannot unlock it. When I click on the unlock button and enter my password nothing happens and it always says YOu don't have admin privileges (although I have) and clicking on the unlock button does not have any effect.

---

### Post by foxy123 on 2012-05-27
it actually crashes with the following error:

```
TypeError in get_chore_settings():list indices must be integers, not str
```

if it helps

---

### Post by foxy123 on 2012-06-02
OK, I have purged nanny and installed it again and it seems to work. Thanks a lot, Guido. So it's not possible to have a systray icon? I'd like to have a notification like 5 min before it should end the session to make sure that my daughter can save anything she was doing. Is it possible to have?

---

### Post by Guido Tabbernuk on 2012-06-04
> **foxy123 said:**
> OK, I have purged nanny and installed it again and it seems to work. Thanks a lot, Guido. So it's not possible to have a systray icon? I'd like to have a notification like 5 min before it should end the session to make sure that my daughter can save anything she was doing. Is it possible to have?

Actually there is a notification service, when you run nanny-systray (you can put it into autostart programs list). If there is actual systray in the system (i.e. LXDE or GNOME 2 or similar) it will be used too. Otherwise (i.e. in Unity) it only displays notification if certain amounts of time is remaining (like 30 min, 15 min, 5 min and 3 min, 2 min, 1 min).

I think you have to reboot in order to make nanny work properly after first install. I'm not sure why.

---

### Post by AEblefisk on 2012-09-23
> **foxy123 said:**
> OK, I have purged nanny and installed it again and it seems to work. Thanks a lot, Guido. So it's not possible to have a systray icon? I'd like to have a notification like 5 min before it should end the session to make sure that my daughter can save anything she was doing. Is it possible to have?
How did you purge it? I uninstalled using synaptic (complete removal) but some configuration file still remains and I can't get rid of the "get_chore_settings" error.

---

### Post by foxy123 on 2012-09-30
> **AEblefisk said:**
> How did you purge it? I uninstalled using synaptic (complete removal) but some configuration file still remains and I can't get rid of the "get_chore_settings" error.

```
[CODE]sudo apt-get purge nanny
```[/CODE]

---

### Post by foxy123 on 2013-01-28
Is there a version for 12.10 available? I know that the project is essentially dead and there is no alternatives (I guess developers’ kids have grown up and they do not need it any more :-)).

---

### Post by bodhi.zazen on 2013-01-28
> **foxy123 said:**
> Is there a version for 12.10 available? I know that the project is essentially dead and there is no alternatives (I guess developers’ kids have grown up and they do not need it any more :-)).

Most people use a service such as opendns rather then maintain black lists personally.

The problem with all these services is that nothing replaces parenting.

No two people can agree 100 % on what should or should not be blocked.

In additions new servers pop up faster then black lists can be updated, etc.

Good luck to you.

---

### Post by foxy123 on 2013-01-28
> **bodhi.zazen said:**
> Most people use a service such as opendns rather then maintain black lists personally.

The problem with all these services is that nothing replaces parenting.

No two people can agree 100 % on what should or should not be blocked.

In additions new servers pop up faster then black lists can be updated, etc.

Good luck to you.

I actually use Gnome Nanny mainly for limiting usage rather than blocking contents and for that I cannot find any alternative.

---

### Post by bodhi.zazen on 2013-01-28
> **foxy123 said:**
> I actually use Gnome Nanny mainly for limiting usage rather than blocking contents and for that I cannot find any alternative.

iptables can limit use, depends on what and how you want to limit, but it can easily limit by user, by time of day, etc.

---

### Post by foxy123 on 2013-02-01
> **bodhi.zazen said:**
> iptables can limit use, depends on what and how you want to limit, but it can easily limit by user, by time of day, etc.

Yes, but if you need to grant an extra hour occasionally or change the schedule during school holidays, it's quite difficult to do quickly. Also there is no notification with iptables. I quite liked Timekpr and Gnome Nanny because it was easy to manage access to laptops with them.

---

### Post by bodhi.zazen on 2013-02-02
I understand, you could probably script it, but it gets complicated.

---

### Post by foxy123 on 2013-02-04
> **bodhi.zazen said:**
> I understand, you could probably script it, but it gets complicated.

I hope that soem of developers with kids will get concerned about this problem and will come up with some new tool or re-write the existing ones.

---

