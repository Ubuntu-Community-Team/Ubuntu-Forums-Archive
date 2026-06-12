---
title: "How can I disable the keyring?"
date: 2009-07-08
forum: Security
---

### Post by Fzang on 2009-07-08
Every time I log in I'm asked to enter a password to connect to the internet, however, this has become quite annoying over time and now I just want to disable it.

How do I do?

---

### Post by lovinglinux on 2009-07-08
> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

[keyring password](http://www.google.com/search?q=keyring password+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) [ubuntuforums.org]  

> [color=#CC0000]**Note:**[/color] when you see [ubuntuforums.org] after a link on my posts it means that I am using Google site search feature. This feature allow us to get search results only from a specific site, in this case Ubuntu Forums, by adding the string *site:ubuntuforums.org* after the keywords. This method is much better than the forum search feature, since it gives you more precise results. I usually add this to my posts when a subject is very common and already answered several times.

---

### Post by B34N on 2009-07-08
> **lovinglinux said:**
> [keyring password](http://www.google.com/search?q=keyring password+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) [ubuntuforums.org]

I used the search first and see you've answered this question a number of times.  Unfortunately I don't have a "Password Keyrings" tab.  I only have the "Key Servers" and "Key Sharing" tabs.  I tried logging on as both users and the tab does not exist for either user.  Is it possible that I didnt' set a unique password for the keyring and the system used the user's password for the keyring?  If so, how do I create a keyring that I can set the password to nothing?

Thank you!

---

### Post by Maheriano on 2009-07-08
Marked for later.

---

### Post by B34N on 2009-07-08
> **st8ofmi9d said:**
> Unfortunately I don't have a "Password Keyrings" tab.  I only have the "Key Servers" and "Key Sharing" tabs. 

I played around a bit more and I went to the "Passwords" tab on the main "Passwords and Encryptions" screen.  I changed the password for "login" to blank.  Is that effectively doing the same thing or have I also made the users login password blank as well?  While I don't care if anyone has access to his keyring, I don't want them to be able to do administrative tasks without having to type in a password.

---

### Post by lovinglinux on 2009-07-08
> **Maheriano said:**
> Marked for later.

You don't need to post to subscribe a thread. Click the **Thread Tools** menu in the top of the thread and select subscribe.

---

### Post by lovinglinux on 2009-07-08
> **st8ofmi9d said:**
> I used the search first and see you've answered this question a number of times. 

Yes, I did :)

> **st8ofmi9d said:**
> Unfortunately I don't have a "Password Keyrings" tab.  I only have the "Key Servers" and "Key Sharing" tabs.  I tried logging on as both users and the tab does not exist for either user.  Is it possible that I didnt' set a unique password for the keyring and the system used the user's password for the keyring?  If so, how do I create a keyring that I can set the password to nothing?

Thank you!

> **st8ofmi9d said:**
> I played around a bit more and I went to the "Passwords" tab on the main "Passwords and Encryptions" screen.  I changed the password for "login" to blank.  Is that effectively doing the same thing or have I also made the users login password blank as well?  While I don't care if anyone has access to his keyring, I don't want them to be able to do administrative tasks without having to type in a password.

They changed the application in Jaunty, that's why you couldn't find the tab. I love when they do that :)

Here is the answer:

> **vanshark said:**
> 
The keyring password can be changed (or removed) in Applications/Accessories/Passwords and Encryption Keys. ON the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password".

This shouldn't change your administrative password, just the login keyring. Anyways, you can test it using a sudo command. For example, try to run the command below on a terminal [see footnote].

```
sudo iptables -L
```

When it asks for a password, try just hitting enter. It should ask the password again, so enter your real password, then the command should run. If it runs without asking a password, then you might have a problem. Please keep in mind that once you enter your password on a terminal you won't need to enter it again for next 5 minutes.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.:

---

