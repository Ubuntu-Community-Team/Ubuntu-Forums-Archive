---
title: "Dell Studio 1555 on ElementaryOS can't connect to password protected wifi"
date: 2014-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by oberyn2 on 2014-05-02
So, I'm a networking and Ubuntu noob.  I'm not entirely sure this is the appropriate place for ElementaryOS problems, but here it is.  I'm running ElementaryOS on my Dell Studio 1555.  I attempt to connect to my home WiFi.  I'm prompted for a password or encryption key.  The button to "Connect" is disabled unless the input password/key is 5 or 13 characters in length.  I don't understand the reasoning for this.  My password is greater than 14 characters.  In editing the connection, I have the option to enter the key/passphrase, as seen below:
[IMG]http://i.imgur.com/Ta81NPY.png[/IMG]

So, I logged into my router and got to this area:
[IMG]http://i.imgur.com/ckIhBNO.png[/IMG]
I enter an arbitrary passphrase just to generate some keys.  I then paste a key into the connection editor.  It cycles and cycles, trying to connect but never does.  What am I missing here?  I'd be happy to return the results of any command in the terminal if that would help.

---

### Post by varunendra on 2014-05-04
Welcome to Ubuntu Forums oberyn2 !

The only familiarity I have with Elementary OS is that I have heard its name, and now have also seen a screenshot of its connection manager (above one) :p, so not sure if I'm going to be able to help with it. What do these commands tell us -
```
lspci -nnk | grep -iA2 net
sudo iwlist scan
```
(replace 'sudo' with whatever equivalent you have in Elem.OS to run a command as root)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by howefield on 2014-05-04
Thread moved to the "*Other OS/Distro Support*" forum.

---

