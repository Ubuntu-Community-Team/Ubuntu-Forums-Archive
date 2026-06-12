---
title: "Non-Sudoer for Safer Browsing?"
date: 2015-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by johny why on 2015-08-19
hi

since the default xubuntu user is a sudoer, is it therefor not a bad idea to create a non-sudoer login account for safer web-browsing and daily use?

thx

---

### Post by grahammechanical on 2015-08-19
I do not use Xubuntu but it is my understanding that the same principle applies to all flavours of Ubuntu.

The user that we set up when we install is the administrator and therefore it would be in the sudoer's list, but, once we login we work as a standard user. It is only when we carry out an action that requires administrator or root privileges that we work as an administrator. And for that action we authenticate by putting in our password. If we are running the command through the terminal we prefix the command with the word sudo and then we are asked to authenticate by putting in our password. On Ubuntu certain commands will not run unless we prefix them with "sudo" and authenticate with our password.

Once the action has ended or after a certain period of time our access as an administrator lapses and we revert to being a standard user again.

So, unless you are loading a web browser from the terminal and using the sudo command then I think that you will find that the web browser is not running as an administrator/root/sudoer but as a standard user. And the same applies to usual actions on the desktop.

This is the big difference between Ubuntu and some other Linux distributions. In Ubuntu the root account is disabled by default. In other distributions the user has to create a root/administrator account and a standard user account. On those distributions if we login as root/administrator and run a web browser then we would certainly be increasing the risk of a security failure.

Regards.

---

### Post by Bucky Ball on 2015-08-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Unless you open Firefox as root you will not create the situation you speak of. :)

As in last post, you are in the sudo-ers group, but you have no 'sudo-ed' to launch Firefox, and if you have, you shouldn't.

---

