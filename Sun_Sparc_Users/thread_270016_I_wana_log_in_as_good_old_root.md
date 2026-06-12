---
title: "I wana log in as good old root"
date: 2006-10-02
forum: Sun Sparc Users
---

### Post by hortimech on 2006-10-02
I have read quite a few of the posts about howto log in as root, they all seem to say the same thing, it's bad to log into an X session as root, but what about the server version, it does not have X unless you choose to load it and I haven't. I need to have root ( with a password ) so what was done in the background to stop root working properly?
Before you start saying "use sudo", Have you ever tried to do that from windows across the network?:confused: :confused:

---

### Post by malathia on 2006-10-02
I have always been under the impression that the only reason to not want to be logged in as root at any given moment in whatever environment (terminal CLI or X GUI) was due to security reasons. I haven't ever experienced some sort of maleffect while employing root in any other way, aside from possibly screwing myself over with a config file or some such (but sudo allows the same sort of idiocy/learning curve). Perhaps I am incorrect? I'm as open to enlightenment as anyone. Lets see how the responses go.

---

### Post by christhemonkey on 2006-10-02
If you login as root, then important files can be unreadable by normal users, causing them to not be able to log in.
As well as lots of added security risks and the possiblities of accidentally deleting something important ('rm -rf /' anyone?)


There are ways of logging into the CLI straight away as root, although i cant remember any right now.

---

### Post by Karlos on 2006-10-02
do this in a terminal

sudo passwd root

type a root password - twice

thats it you've set your good old root password

now you can type su and become root

it can also be done without setting a root password by typing this

sudo -s -H

hope that helps

./karlos

---

### Post by hortimech on 2006-10-02
perhaps I was misunderstood, I do not want to use sudo, if required I am very willing to remove sudo from my system. I am trying to set up my server as a samba pdc, this is working but windows will not copy the profile across because I need to do it as an administrator. Administrator = root, root does not excist except as sudo, therefor I can not copy the profile across.
Now we have settled that, will some one tell me what ubuntu did that is different from every other linux distro.
I am not asking how to run root on X but on a command based server that is only connected to from windows boxes to netlogon, profiles and homes, nowhere else, no locally loging users, it is illogical to have to type sudo before every command on a server!!!!

---

### Post by mitch.c on 2006-10-02
> **hortimech said:**
> perhaps I was misunderstood, I do not want to use sudo, if required I am very willing to remove sudo from my system. I am trying to set up my server as a samba pdc, this is working but windows will not copy the profile across because I need to do it as an administrator. Administrator = root, root does not excist except as sudo, therefor I can not copy the profile across.
Now we have settled that, will some one tell me what ubuntu did that is different from every other linux distro.
I am not asking how to run root on X but on a command based server that is only connected to from windows boxes to netlogon, profiles and homes, nowhere else, no locally loging users, it is illogical to have to type sudo before every command on a server!!!!
Karlos told you how to enable root ^^. It's also documented here: [https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c](https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c)

---

### Post by hortimech on 2006-10-03
thanks for all the help, but after some more browsing I found the real answer is to reload ubuntu server but this time be an expert:D

---

