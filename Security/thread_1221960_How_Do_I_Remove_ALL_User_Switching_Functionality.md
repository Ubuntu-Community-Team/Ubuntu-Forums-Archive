---
title: "How Do I Remove ALL User Switching Functionality?"
date: 2009-07-24
forum: Security
---

### Post by oreodoh on 2009-07-24
Ubuntu has become a security nightmare for me ever since 7.10 was released. It continues in 9.04. The fast-user-switch-applet was annoying enough. I finally figured out the very simple method of removing it (apt-get remove fast-user-switch-applet).  Now I have another problem - the Logout dialog.

Let's say my username is "abuser". When I click "System --> Log Out abuser...", I am presented with two options:

1. Log Out
2. Switch User

What I want is to remove option #2, as I don't want more than one person running a local gdm session at a time. Please help me to find the answer to this problem. I would like for the "Switch User" button to be removed altogether. Failing that, breaking the button is fine, too (e.g. when a user clicks on it, they just get logged out, or they get an error message but can still log out).

Thanks for any help!

---

### Post by dk06 on 2009-07-24
> **oreodoh said:**
> Ubuntu has become a security nightmare for me ever since 7.10 was released. It continues in 9.04. The fast-user-switch-applet was annoying enough. I finally figured out the very simple method of removing it (apt-get remove fast-user-switch-applet).  Now I have another problem - the Logout dialog.

Let's say my username is "abuser". When I click "System --> Log Out abuser...", I am presented with two options:

1. Log Out
2. Switch User

What I want is to remove option #2, as I don't want more than one person running a local gdm session at a time. Please help me to find the answer to this problem. I would like for the "Switch User" button to be removed altogether. Failing that, breaking the button is fine, too (e.g. when a user clicks on it, they just get logged out, or they get an error message but can still log out).

Thanks for any help!
[http://ubuntuforums.org/showthread.php?t=284871](http://ubuntuforums.org/showthread.php?t=284871)
[http://ubuntuforums.org/archive/index.php/t-700675.html](http://ubuntuforums.org/archive/index.php/t-700675.html)

---

### Post by oreodoh on 2009-07-27
> **dk06 said:**
> [http://ubuntuforums.org/showthread.php?t=284871](http://ubuntuforums.org/showthread.php?t=284871)
[http://ubuntuforums.org/archive/index.php/t-700675.html](http://ubuntuforums.org/archive/index.php/t-700675.html)

"Switch User" is still an available option in 9.04 after all those changes. The problem with the "System --> Logout" button persists.

I'm going to try adding the following setting to /etc/gdm/gdm.conf-custom.

[server]
flexible=false

We did this for 7.04 and it didn't remove the switch user option, but it did make it ineffective. The following error pops up when trying to click "Switch User":

"The allowed limit of flexible X servers reached."

But this is an error I want, so I'm okay with it. :)

---

### Post by oreodoh on 2009-07-31
> **oreodoh said:**
> 
I'm going to try adding the following setting to /etc/gdm/gdm.conf-custom.

[server]
flexible=false



My proposed solution didn't pan out. That Switch User option is persistent!!! :evil:

What happened to OPTIONS, Canonical??? Is there some mandate that says the Switch User "feature" must be included or the whole system blows up? I can't believe how difficult it is to limit the GUI to a SINGLE local user session. ](*,)

I miss 7.04... :(

---

### Post by bodhi.zazen on 2009-07-31
How is switch user a security risk ?

I suggest you either do not run GDM or log out when you are finished.

And this is a feature of gnome (gdm) not Ubuntu. You certainly can install Ubuntu without X or gnome and you will not have a switch user option, so if you have concerns or can identify a security hole probably best to direct it upstream (ie @ gnome) and not Ubuntu.

---

### Post by oreodoh on 2009-08-04
Thanks for replying! I appreciate the feedback.

> **bodhi.zazen said:**
> How is switch user a security risk ?


It's a risk due to having a requirement for the last person leaving the lab to verify all systems are locked or logged out. Many of these users are NOT Linux-savvy, so they would not think to check the other virtual terminals for additional GUI logins. All they know is Ctrl-Alt-Del. It's too much to ask them to remember Ctrl-Alt-F1,F2,F3,F4, etc. Some of these folks don't even use the computers in the labs, so it's even worse for them.

Yes, I realize now that Gnome is primarily at fault, but Canonical uses Gnome as the primary display manager for Ubuntu. It's just inconvenient because all the users are finally getting used to Ubuntu and now I might have to switch to Kubuntu just because of this one "feature".

Anyway, we just renewed our support contract with Canonical, so I will send my question up the chain and hopefully get a resolution there. Ousting Gnome may very well be the final solution.

---

### Post by danl on 2009-08-30
I'm trying to do this too under 9.04. I'm trying to get rid of the switch user option on the logout dialog under a live CD distribution (where there is only one user). I want to get rid of it, because it's confusing in this situation - the only user that you can switch to is "ubuntu", so you aren't actually switching do a different user.

I've tried everything I can find in this forum:
-removed fast-user-switch-applet using apt-get remove
-added settings for apps/panel/global/disabled_applets and desktop/gnome/lockdown/disable_user_switching in gconf.xml.mandatory as noted in other posts.

Still, the switch user option is in the logout dialog prompt. Has anyone been successful removing this in 9.04?

---

### Post by mightyiam on 2009-10-13
Please [see]("http://ubuntuforums.org/showpost.php?p=8098191&postcount=7").

---

### Post by __p1n__ on 2009-10-13
1. Use the kde gui instead of the gnome gui
2. Configure the locked-down behavior directly or use the old kiosktool to assist in this.

---

