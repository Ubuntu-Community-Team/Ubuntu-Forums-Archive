---
title: "Gsettings for unity-greeter is broken?"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jokerdino on 2012-04-13
Can anyone confirm that the gsettings for unity-greeter is broken? If I change the options here, they don't actually get reflected on the unity-greeter. But if I test it with the command ```
unity-greeter --test-mode
```, they work as expected. I wonder if it is just me or someone else already has this problem.

[IMG]https://lh3.googleusercontent.com/-qwKurfDivY4/T4jM2vlIvRI/AAAAAAAAAas/kuxSdW2nMLc/w497-h373/Screenshot%2Bfrom%2B2012-04-14%2B09%253A02%253A29.png[/IMG]

And, if someone has stumbled across any relevant bug reports, please link me to them. Thanks!

(I can't tell if [this thread]("http://ubuntuforums.org/showthread.php?p=11840170") is relevant to my thread.)

---

### Post by NHclimber on 2012-04-13
You have to change the gsettings as the lightdm user (not as your login because of course you haven't logged in ;)

Do my instructions in the last post on that thread not work for you?

---

### Post by jokerdino on 2012-04-13
Right. Thanks. [It works.]("http://ubuntuforums.org/showpost.php?p=11840170&postcount=25") I didn't try it last time.

---

### Post by mc4man on 2012-04-13
You were & could, at least for some of those options, supposed to be able to set as a user, clearest example would be the grid on or off.
That broke at some point & hasn't been fixed (or maybe not even reported

Bug that caused the grid setting (per user) to exist

[https://bugs.launchpad.net/unity-greeter/+bug/883908](https://bugs.launchpad.net/unity-greeter/+bug/883908)

---

### Post by NHclimber on 2012-04-13
> **mc4man said:**
> You were & could, at least for some of those options, supposed to be able to set as a user, clearest example would be the grid on or off.
That broke at some point & hasn't been fixed (or maybe not even reported

Bug that caused the grid setting (per user) to exist

[https://bugs.launchpad.net/unity-greeter/+bug/883908](https://bugs.launchpad.net/unity-greeter/+bug/883908)

That would be bad, being able to access gsettings of a user without authenticating. So I could have just patched the key name in the binary and read other values from a user's dconf backend??

Glad that security hole got closed.

---

### Post by mc4man on 2012-04-13
> **NHclimber said:**
> That would be bad, being able to access gsettings of a user without authenticating. So I could have just patched the key name in the binary and read other values from a user's dconf backend??

Glad that security hole got closed.

What is so bad about a user deciding if they want the grid displayed on the their greeter screen or not?

---

### Post by NHclimber on 2012-04-13
> **mc4man said:**
> What is so bad about a user deciding if they want the grid displayed on the their greeter screen or not?
That's not what I mean.

If a program can access user-specific information without ever authenticating, then it can be subverted to access different, maybe more valuable information *without having to authenticate*.

At the time unity-greeter is running, you haven't logged in. So unity-greeter being able to read your user-specific information is bad.  What if unity-greeter is subverted so that it reads other, more valuable information *as you* than whether you want the grid on or not?

---

### Post by mc4man on 2012-04-14
Okay - I thought this thread was about the user settings for the greeter & whether they could be edited in gsettings (per user), & if so was that broken.
From what I' see you should be able to & currently can't.
(what some of them do I'm not too sure & honestly don't really care

---

### Post by mc4man on 2012-04-22
> **NHclimber said:**
> That's not what I mean.

If a program can access user-specific information without ever authenticating, then it can be subverted to access different, maybe more valuable information *without having to authenticate*.

At the time unity-greeter is running, you haven't logged in. So unity-greeter being able to read your user-specific information is bad.  What if unity-greeter is subverted so that it reads other, more valuable information *as you* than whether you want the grid on or not?

That seems to be correct - earlier in 12.04 dev you could edit greeter settings thru gsettings, now you obviously can't.

So to mention - an alternate to the cli switching to lightdm user, ect would be to create an override file & compile. 
Ex. with 3 of the settings though don't see much purpose to the color one

```
sudo  gedit /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override


```
```
[com.canonical.unity-greeter]
play-ready-sound = false
background-color = "#000000"
draw-grid = false

```

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

