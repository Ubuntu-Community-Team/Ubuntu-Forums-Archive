---
title: "Password required in Ubuntu 10.04"
date: 2012-01-05
forum: Security
---

### Post by asharpham on 2012-01-05
Since upgrading to Ubuntu 11.04, I find that my password is required whenever I open Evolution and also when my user name and password are automatically entered in certain websites. How can I turn this off?

---

### Post by bluexrider on 2012-01-05
If your password is automatically entered in the websites its because your browser is set in that manner. Check the preferences settings of your browser and empty the cache. As far as evolution... I use Thunderbird, sorry

---

### Post by OpSecShellshock on 2012-01-05
This usually happens when either initial login is set to not use a password or it uses a password different than what is in the keyring. By default the first user account you set up will use the same password for both. If you change your user password by any means other than the About Me utility then it will no longer match. If you set your desktop login to not use a password then the keyring will still be locked when you open applications that store credentials in it. So either of those things will lead you to the situation you're in now.

To solve it, you'll need to either use a password for logging into a desktop session or make sure that your user password is the same as the keyring password.

---

### Post by asharpham on 2012-01-08
My initial login does use a password. Also I'm pretty sure my keyring password is the same as my evolution and website passwords. It only occurs with websites where I have chosen to automatically enter the login details.

---

