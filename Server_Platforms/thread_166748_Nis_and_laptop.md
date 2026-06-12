---
title: "Nis and laptop"
date: 2006-04-27
forum: Server Platforms
---

### Post by Koybe on 2006-04-27
Hello,

I don't know if the better solution was to post here or on the general ubuntu forum. Anyway here's my question :

What can I do with laptop on a network using NIS? If the Laptot is on the network, everything should go right with authentication and home directory mounting. But what if the laptop is out? How can I authenticate and how can I sync the datas?

Any help would be great! Thanx!

---

### Post by Koybe on 2006-04-27
I've got another NIS related question.
How to give a NIS user admin rights on the local machine?
Can we use a NIS admin group?

Thank you.

---

### Post by BrianK on 2006-05-01
[QUOTE=Koybe]Hello,

I don't know if the better solution was to post here or on the general ubuntu forum. Anyway here's my question :

What can I do with laptop on a network using NIS? If the Laptot is on the network, everything should go right with authentication and home directory mounting. But what if the laptop is out? How can I authenticate and how can I sync the datas?

Any help would be great! Thanx![/QUOTE]
Well, what are you trying to achieve?  Do you want to be able to logon as a particular NIS user when you're not on the network?  If that's the case, there's no real way to do it.  You can, however, create a user on your local machine with the same username, group, UID, and GID as the NIS user and set /etc/nsswitch to look at file and nis for passwd, group, and user.

If your homedir is mounted on a server via NFS (or some orther network file protocol), and you want to access your files when off the network... you may want to create some local account, then rsync the local account's omedir with your homedir prior to pulling the laptop off the network.

The short answer is that NIS and laptops don't play well togetteher, AFAIK.

---

### Post by mbeierl on 2007-09-17
This was exactly what I was contemplating - putting an nis infrastructure in place - until I realized that the laptops would be cut off at the knees.

So, what is anyone's thought of making the laptop an NIS slave and having the user authenticate against the laptop itself?

---

