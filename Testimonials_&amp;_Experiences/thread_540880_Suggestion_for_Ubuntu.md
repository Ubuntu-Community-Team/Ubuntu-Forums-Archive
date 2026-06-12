---
title: "Suggestion for Ubuntu"
date: 2007-09-02
forum: Testimonials &amp; Experiences
---

### Post by amitroy5 on 2007-09-02
I love Ubuntu, but I have one issue that gripes me. My suggestion is for Ubuntu to give an option in the packet manager to automatically remove all traces of a program and packages that are no longer needed, including all configuration files. Sometimes, I break a file and I need to reinstall it, and it is hard when I find that the configuration files are the same. Thus, it makes re-installation and fixing very difficult. Thanks.

---

### Post by wolfen69 on 2007-09-02
suggestion: you learn how to use ubuntu.

---

### Post by amitroy5 on 2007-09-02
I am trying to learn, that is why I am posting on these boards. I know that there is the option of apt-get autoremove --purge [[packet]] option, but it often misses some things. Wofen69, how can I deal with this issue then if its possible? Obviously, Ubuntu still can be improved. Otherwise, there would be no more releases. :)

---

### Post by por100pre1 on 2007-09-02
You can do some autoremove, purge, and even clean using Synaptic too. Keep in mind that most programs are very likely to leave configuration files in your user folder, that behavior is typical in OSS. That way is not likely to lose the settings of your favorite programs if you ever need to uninstall and reinstall some software. You can manually search your user folder and remove those files if you wish. :)

---

### Post by -SpaZ on 2007-09-03
> **wolfen69 said:**
> suggestion: you learn how to use ubuntu.

No need to get nasty.  He just wants help, and help is what this forum is all about.

---

### Post by Vadi on 2007-09-03
> **amitroy5 said:**
> I love Ubuntu, but I have one issue that gripes me. My suggestion is for Ubuntu to give an option in the packet manager to automatically remove all traces of a program and packages that are no longer needed, including all configuration files. Sometimes, I break a file and I need to reinstall it, and it is hard when I find that the configuration files are the same. Thus, it makes re-installation and fixing very difficult. Thanks.

Newbie here just as you, but I think checking the "mark for complete removal" in synaptic removes the config files too. Might be wrong.

It would be nice if that option was in add/remove though. (time to go find where to submit that feature request :D)

---

### Post by 3rdalbum on 2007-09-04
Mark For Complete Removal does remove the config files. If you have already done an ordinary removal, you can go into Synaptic and click the Status button, then choose the "Not Installed (Residual Config)" filter from the list.

Most of the time you don't need to uninstall and then reinstall the program. If the program starts misbehaving, you can delete its preferences. For instance, if Skype was misbehaving, you could delete the .skype folder from your home directory (in Nautilus, you press Control-H to show hidden files).

---

