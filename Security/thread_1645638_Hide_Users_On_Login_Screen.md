---
title: "Hide Users On Login Screen"
date: 2010-12-14
forum: Security
---

### Post by dev.null on 2010-12-14
How can you configure the login screen to not show any accounts in the login-list?

It used to have a form you had to type in the user name and the password.

Displaying a user name is a pretty big security hole (half the login is now given away).

---

### Post by FuturePilot on 2010-12-14
> Displaying a user name is a pretty big security hole (half the login is now given away).
This thinking is flawed. If you can see what is on the monitor then you most likely have physical access. If you have physical access it doesn't mater if you know usernames or not. Someone could easily just boot up a live CD and have access to everything (if it's not encrypted). If there are measures in place to prevent booting from other media, then they'll probably just rip the hard drive out. Hiding usernames on the login screen is a false sense of security.

---

### Post by movieman on 2010-12-15
While that's true, there is a list of users to exclude from the gdm login screen: it appears to be in /etc/gdm/gdm.schemas as far as I can see.

There may be an option there to disable the list altogether.

---

### Post by Megaptera on 2010-12-15
There's an option in Ubuntu-Tweak _not_ to display names at log in. Simple to implement via GUI.

Hope this helps?

---

### Post by karthick87 on 2010-12-15
You can modify the user's level to below 1000 so they don't show in the list,  ```
sudo usermod -u 999 <username>
```  The only other way I know is to hide the list completely,
  ```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```

---

