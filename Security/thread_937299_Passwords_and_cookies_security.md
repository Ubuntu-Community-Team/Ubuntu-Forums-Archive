---
title: "Passwords and cookies security"
date: 2008-10-03
forum: Security
---

### Post by lovinglinux on 2008-10-03
I have been struggling to find a good password manager that provides a good balance between security and usability. I was a KeePass user before using Linux and I tried KeePassX, but it doesn't offer a good web browser integration.

I'm currently using Revelation Password Manager, mainly because of the panel applet, which makes my daily Internet browsing easier due to quick access to the password database, without opening the application itself. I have configured the applet pop up window to stay on top, so it is relatively simple to copy and paste the user name and password while I surf the web. 

Nevertheless, it's kind of annoying to copy and paste the login data every time I visit a web site, so I have allowed Firefox to remember passwords and enabled cookies on favorite sites with expiration determined by the cookie.

Another thing that is annoying is the Firefox Master Password prompts, but I'm currently using it.

So what I want to know is the security risks (remote and local) of:

1 - Using Firefox password manager
2 - Not using Firefox Master Password
3 - Allowing cookies on a per site basis, but not setting the cookie expiration to whenever I close the browser or only for the session.

I guess if I allow cookies to not expire after restarting Firefox, I could get rid of Firefox password manager and use only the Revelation applet. In the other hand, if I set the cookies to expire after the current session, would be annoying to enter the login every time using only the Revelation applet.

Which would be the most secure approach and how my data could be compromised locally and remotely?

---

### Post by Trebaruna on 2008-10-03
Remotely there should be no risks. I.e. nobody should be able to read anything--including the passwords, obviously--on your box. If they can, you're in big trouble. Firefox will not expose your passwords to the internet.

Locally, if you do not use a master password then the passwords must obviously be readable without your intervention; they can thus be retrieved by firefox or anyone else. I am not entirely certain, but I'd imagine firefox encrypts the file containing your passwords when you set a master pass and unlocks it in memory when you enter that pass. Close the browser and the pass is removed from memory.

---

### Post by lovinglinux on 2008-10-03
> **Trebaruna said:**
> Remotely there should be no risks. I.e. nobody should be able to read anything--including the passwords, obviously--on your box. If they can, you're in big trouble. Firefox will not expose your passwords to the internet.

Locally, if you do not use a master password then the passwords must obviously be readable without your intervention; they can thus be retrieved by firefox or anyone else. I am not entirely certain, but I'd imagine firefox encrypts the file containing your passwords when you set a master pass and unlocks it in memory when you enter that pass. Close the browser and the pass is removed from memory.

Thanks. About using cookies with no expiration?

---

