---
title: "Password Problems"
date: 2010-08-03
forum: Security
---

### Post by carrickfergus on 2010-08-03
Hey All,

Tried searching for this and I don't seem to be finding my particular problem here.

Apparently when I installed Ubuntu 10.04, I set a password. Then I changed it because I like the other one better. I did this through the Terminal using

```
sudo passwd
```I was still getting the feel for my new desktop OS and had to restart a couple of times for packages I had installed, etc. When I logged in to my user with the password that I changed, it worked fine but then I was prompted to enter the password that I entered when I installed the OS.

So... I have two questions:

1. What is this password called at the second prompt I get (i.e. user password, root password, etc.)?

2. How do I change it (re-installing Ubuntu 10.04 is not an option at this point)?

If you can answer the first question I'm sure I can figure out the second, but if you can answer the second too then it would sure help a lot. Thanks Ubuntu community! :D

---

### Post by lisati on 2010-08-03
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
If you still have questions, feel free to ask.

---

### Post by carrickfergus on 2010-08-03
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
If you still have questions, feel free to ask.
Is the original installation password called the root then? I was under the impression that the root was something different. I just put it in the examples because I don't know what the original password is called that I used.

---

### Post by carrickfergus on 2010-08-03
Here's what I'm referring to:
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs141.ash2/40384_10150243614665347_786230346_14156356_2599343_n.jpg[/IMG]

---

### Post by FuturePilot on 2010-08-03
That is the gnome-keyring password. If you don't want to see that your login password should be the same as the keyring password. Also, for future reference to change your password use System > Preferences > About Me or 
```
passwd
```
Doing it any other way (forcibly), as you have seen, tends to break things.

Delete ~/.gnome2/keyrings. The next time something tries to access the keyring it will ask you to create a new password. Make sure it is the same as your login password or else you will continue to see that prompt after logging in. (note you will lose any passwords you had stored in the keyring by doing this)

---

### Post by carrickfergus on 2010-08-03
Thank you, this seemed to work, FP.

To clarify for future users who are having the same problem here is what I did step by step.

1. Accessed the Home Folder
2. Home>"Your Username"
3. "ctrl" + "h" (you should now see all of your hidden files and folders)
4. Home>.gnome2
5. Delete the folder "keyrings"
6. Log out
7. Log back on

---

### Post by Baldrick_NZ on 2010-09-02
You can also go Applications>Passwords and Encryption Keys, under the 'Passwords' tab, right click 'Passwords: login' then choose 'Change Password'. 
Type in your old password (the one you originally logged on with), but leave the new password and the confirm box blank. Click OK. You'll be asked if you want to use unsafe storage, click yes. 

I would only do this if you are using a stand-alone PC, or maybe one that is locked down over a network.

Hope this helps..

---

