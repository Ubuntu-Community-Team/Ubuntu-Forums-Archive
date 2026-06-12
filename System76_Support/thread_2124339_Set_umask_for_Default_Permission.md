---
title: "Set umask for Default Permission"
date: 2013-03-10
forum: System76 Support
---

### Post by Cliff Bentley on 2013-03-10
Rookie Linux-user here, bought this System76 in Jan. I'm looking to set Default Permissions. My research found umask. My question is this: **According to "Best Ubuntu Practices" where should I set umask for my personal login?**

I intend to set umask to 007 for my login, and leave it at 022 for everyone else (i.e. Guests). This presumes the expectation that I will always be the only member of the group that bears my user name, otherwise I'd go with 027. My box is singleuser today, but I would like to allow for separate settings for future "Guest" users. That's why I'm **not** setting umask in **/etc/profile**. Setting umask in **~./bashrc** would have the disadvantage of not affecting the Default Permission for Nautilus (per my current understanding). I invoke Nautilus from the Launcher, so that's out. The comments I read in **/etc/profile** say this:
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.
I vaguely recall reading somewhere that **pam_umask** is a good place to do this, but my find cmd does not find that file (possible I erred with find). Editing the **/etc/login.defs** file as sudo seems to be one option. Creating pam_umask somewhere does not seem to make sense, unless I just need to go find it instead. So my main question remains:
**According to "Best Ubuntu Practices" where should I set umask for my personal login?**

Please advise.

---

### Post by isantop on 2013-03-11
What is your end-goal? What specific permissions are you setting, and where are you trying to set them? Ubuntu includes a very secure file-permissions system which may accomplish your task.

---

### Post by schragge on 2013-03-11
[pam_umask]("http://manpages.ubuntu.com/manpages/precise/en/man8/pam_umask.8.html") is not a configuration file, it's a [PAM]("http://manpages.ubuntu.com/manpages/precise/en/man7/pam.7.html") module that gets executed by [login]("http://manpages.ubuntu.com/manpages/precise/en/man1/login.1.html"), [uwiki]LightDM[/uwiki], [sshd]("http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html") and so on, when a user logs in on the system. It gets its defaults from */etc/login.defs* as documentation states. For GUI applications that create files like Nautilus, I guess you can put umask either in *~/.xsessionrc* or in some script that gets autorun from /etc/lightdm/lightdm.conf.

The place for setting umask for all logins of all users how ever they occur is UMASK in  */etc/login.defs*. You also may put umask into the [GECOS field]("http://en.wikipedia.org/wiki/Gecos_field") in */etc/passwd* for each user individually as described in [pam_umask man page]("http://manpages.ubuntu.com/manpages/precise/en/man8/pam_umask.8.html"). This also should be respected by logins of any kind.  I guess the following command will accomplish this
```
sudo chfn -o umask=007 [COLOR=blue]username[/COLOR]
```

Note however, that users are able to override your choice by specifying umask in their *~/.bashrc* and/or *~/.xsessionrc*. Obviously, umask only applies to new files in the directories where users are permitted to create them, i.e. on a sanely configured system mainly anything under * /tmp*, */var/tmp*, and respective user's home directory.

BTW, IIRC [the default umask on recent Ubuntu releases is 002]("https://blueprints.launchpad.net/ubuntu/+spec/umask-to-0002"), not 022, thus giving the full access to group members.

---

### Post by Cliff Bentley on 2013-03-12
Thanks for the help. I set umask in ~/.bashrc and it worked well for my bash CLI. That was a good start. It's also the bulk of my need.

I did not find a place to set umask for Nautilus. The file, [COLOR=#800000]~/.xsessonrc[/COLOR] does not exist in my system. To try that, would I just create a file by that name in my home dir that contains nothing but the umask setting? Is that how that is done?

My purpose is simple isantop. Whenever I create a file I'd like its default permission to be 660, and whenever I create a dir I'd like the permission to be 770. The group I'm part of will always contain only me, so I don't see a need to differentiate the owner and group. The only foreseeable other user will be "Guest". I want Guest to have zero visibility to my stuff unless I specificallly allow it.

---

### Post by schragge on 2013-03-13
> **Cliff Bentley said:**
> The file, [COLOR=#800000]~/.xsess[color=red]i[/color]onrc[/COLOR] does not exist in my system. To try that, would I just create a file by that name in my home dir that contains nothing but the umask setting? Is that how that is done?Yep. Or your can keep the initialization tasks common to CLI and GUI in some separate file, and source it from both *~/.bashrc* and *~/.xsessionrc*. This is how I do it on my system.
From my *~/.xsessionrc*:
```

# source common environment
test -s ~/.shenv && . ~/.shenv

```

---

### Post by Cliff Bentley on 2013-03-14
Thanks again, schragge. It worked fine, plus I learned a couple of things. I will take your suggestion about a common file the next time I need to add a setting that functions the same in both places. Learning Ubuntu is fun. Now on to my next step.

---

### Post by schragge on 2013-03-15
Glad it worked. Note however, that *~/.xsessionrc* gets executed only for your default X session. If you have installed say Unity, KDE, GNOME3 shell, and XFCE, and your default DE is Unity then this will work only when you're logging in into Unity, and won't work when you're choosing another X session from the LightDM login screen.

---

