---
title: "Allow limited users to change IP address"
date: 2009-03-24
forum: Security
---

### Post by Skaught11 on 2009-03-24
I have a few dozen netbooks that are used by Internet installation techs.  It is a locked down desktop to prevent wierd apps from being installed and used.

The techs do not have root access of any sort.

They do however need to change their static ip.  How do I grant the user permission to change the ip address?

The nm-connection-editor app will run and I can enter a static ip and it accepts it, however an ipconfig shows that my setting is being ignored.

---

### Post by bodhi.zazen on 2009-03-24
IMO Network manager does not do such a good job setting a manual ip address.

You can take a look at wicd (it does wired as well as wireless and allows profiles for different networks).

Or you can give your techs permission to edit the files and limited root access to do so via sudo.

---

### Post by Skaught11 on 2009-03-24
sudo would not be an option, I think.

the users are intentionally limited and not sudoers.

---

### Post by bodhi.zazen on 2009-03-24
> **Skaught11 said:**
> sudo would not be an option, I think.

the users are intentionally limited and not sudoers.

Well that is the beauty of sudo, you can absolutely use sudo and configure limitied root powers for various users. su is all or none, sudo allows some users to run some commands as root.

See : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Look at the "Examples" section at the bottom.

---

