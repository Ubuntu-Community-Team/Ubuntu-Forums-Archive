---
title: "Auto Authentication for software install?"
date: 2012-06-22
forum: Security
---

### Post by youknowme on 2012-06-22
I am fed up of having to keep typing in a password every time i want to install software using the software centre. How can I set it up so in any session I am only asked once and then it remembers my password?

It is more a security threat to have to enter a password over and over instead of once.

---

### Post by Ms. Daisy on 2012-06-22
Honestly how much software are you installing in any given session?  I suppose if you really don't care about security at all you could run as root. But that's not supported in this forum so you'll have to google for that yourself.  Maybe if you understood what the password was doing for you, you would reconsider:  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by |{urse on 2012-06-22
There are ways to do this but really really really not a good idea to automate sudo.

To log in as root, it's sudo su, but you don't want to install packages that way. If your laptop has a biometric fingerprint scanner you could set up fprint along with libpam to only require a fingerprint scan instead of a typed password (I have this on my main laptop, works beautifully).

---

### Post by youknowme on 2012-06-24
> **Ms. Daisy said:**
> Honestly how much software are you installing in any given session?  I suppose if you really don't care about security at all you could run as root. But that's not supported in this forum so you'll have to google for that yourself.  Maybe if you understood what the password was doing for you, you would reconsider:  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Are you serious?

---

### Post by cariboo on 2012-06-24
> **youknowme said:**
> Are you serious?

Linux was designed from the ground up to be a multi-user system, and as such the need to separate user permissions is a part of the core system, which makes it totally different from any other operating systems you've used.

If you are constantly installing packages due to re-installs, it may be an idea to script the process, so all you have to do is run a couple of commands in a terminal, to restore your system to the point where it was at before the re-install.

Once you have the system setup to your satisfaction, open a terminal and run the following command:

```
dpkg --get-selections > installed-software
```

The above command creates a list of installed packages in a file called **installed-software**, make sure you include this file when you do your backup, before doing a re-install. Once you have done your new installation, and are ready to re-install all the extra packages, run the following command:

```
dpkg --set-selections < installed-software
```

Followed by:

```
dselect
```

**Note:** dselect isn't installed by default, so you probably get a notice to install it.

---

### Post by zombifier25 on 2012-06-24
You can edit PolicyKit. No need to do anything as root, since the aptd daemon will automatically grant you privilige. BUT, like what others have said, consider the dangers before going with this. I would strongly, strongly recommend against doing so. Besides, normally you provide your password once and you can use it for about 15 minutes.

Open /usr/share/polkit-1/actions/org.debian.apt.policy as root, find this section:

```

  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

```
Change it to:
```

  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

```
Now you can install whatever you want from Software Center freely.

The forum does not allow instructing people to run as root permanently. I'm pretty sure this is not, this is simply giving an admin more priviliges - install a package from Ubuntu's repo. With this, the administrator still have to provide a password in order to add an external PPA and installing from it.


Of course, this is still a security risk. Consider it before you do anything.

---

### Post by youknowme on 2012-06-25
Now this is the real dope man!
Thanks

---

### Post by youknowme on 2012-06-25
> **zombifier25 said:**
> You can edit PolicyKit. No need to do anything as root, since the aptd daemon will automatically grant you privilige. BUT, like what others have said, consider the dangers before going with this. I would strongly, strongly recommend against doing so. Besides, normally you provide your password once and you can use it for about 15 minutes.

Open /usr/share/polkit-1/actions/org.debian.apt.policy as root, find this section:

```

  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

```Change it to:
```

  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

```Now you can install whatever you want from Software Center freely.

The forum does not allow instructing people to run as root permanently. I'm pretty sure this is not, this is simply giving an admin more priviliges - install a package from Ubuntu's repo. With this, the administrator still have to provide a password in order to add an external PPA and installing from it.


Of course, this is still a security risk. Consider it before you do anything.

Now this is the  REAL DOPE man - thanks!

---

