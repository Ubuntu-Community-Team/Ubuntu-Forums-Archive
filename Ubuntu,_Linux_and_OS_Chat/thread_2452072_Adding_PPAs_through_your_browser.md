---
title: "Adding PPAs through your browser"
date: 2020-10-16
forum: Ubuntu, Linux and OS Chat
---

### Post by metacell on 2020-10-16
What if you could add a PPA with a simple click in your browser?

Eg, I want to install Lutris. I go to lutris.net and click the big download button, which is a PPA link. The browser sends the link to [FONT=courier new]add-apt-repository-gui[/FONT], which asks me to confirm and then sets up the PPA. Lutris is now automatically installed and updated.

Would this be a good thing?

---

### Post by TheFu on 2020-10-16
> **metacell said:**
> Would this be a good thing?

No.  It would be bad for security.  Browsers are being moved into containers to prevent malicious code from running with full reign over a system. Plus, inside a business, there's often a 1:100 ratio of admins to users, so users would be frustrated when they couldn't install anything.

I bet gdebi could be setup as a browser addon for specific mime-types.  Seems like a bad idea to me to have any browser allowed to launch a program that needs sudo.  What if sudo access was unlocked outside 60 seconds ago so the command from the browser completes without asking?  Just seems like a terrible idea for security.

---

### Post by grahammechanical on 2020-10-16
Most of what you suggest can all ready be done. A browser takes us to a web site which in turn offers to set up a PPA as a repository. Is this not what happens with Wine and the Google Chrome browser? But the software is not installed automatically. We need to update our sources list and run an install command which requires our sudo password.

> A *PPA* is a Personal Package Archive, and is a method of  distributing software to users, without requiring developers to undergo  the full process of distribution in the main ubuntu repositories.
PPAs have not undergone the same process of validation as regular ubuntu packages.
Subsequently, installing a PPA should be considered to be a low-security alternative as compared to the main repository,


[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

It would be our decision to trust the developer. I certainly think that running a script from a web site and giving it administrator rights to install whatever may be listed in the script is down right dangerous.

Regards

---

### Post by metacell on 2020-10-17
> **grahammechanical said:**
> Most of what you suggest can all ready be done. A browser takes us to a web site which in turn offers to set up a PPA as a repository. Is this not what happens with Wine and the Google Chrome browser?

I think I've missed that. Can you click a link in Chrome and it sets up a PPA?

---

### Post by Frogs Hair on 2020-10-17
The browser would have to have elevated permissions to install anything if it were possible. This would be a major security issue for me.

---

### Post by Tadaen_Sylvermane on 2020-10-18
Real life example. You live in a neighborhood where theft is common. Do you leave your door unlocked while you're gone all day so you can save 10 seconds unlocking it when you get home?

---

### Post by metacell on 2020-10-20
> **Frogs Hair said:**
> The browser would have to have elevated permissions to install anything if it were possible. This would be a major security issue for me.
I was thinking the browser sends the link to another app, and that app asks the user for permissions to install a PPA.

Like when you click a magnet: link, and the browser sends the link to your BitTorrent application.

So the browser itself wouldn't need elevated permissions, would it?

---

### Post by Frogs Hair on 2020-10-20
> **metacell said:**
> I was thinking the browser sends the link to another app, and that app asks the user for permissions to install a PPA.

Like when you click a magnet: link, and the browser sends the link to your BitTorrent application.

So the browser itself wouldn't need elevated permissions, would it?

Having the browser as part of the installation chain would be a security issue for me though it may not for other users. Check out the pling store app image as an example of a browser with installation capabilities.    [https://www.pling.com/p/1175480/](https://www.pling.com/p/1175480/)

---

