---
title: "jeos/server: How to display stuff above the first login prompt?"
date: 2008-02-09
forum: Server Platforms
---

### Post by mark_k on 2008-02-09
Hi all.

When I use vmware to start up an ubuntu-JeOS instance, it goes through the normal bootup process, and then you´re left with the login  prompt, like so


> Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 7.10 jeos tty1

jeos login:



So the question - What magic runs to print the ´Ubuntu 7.10 jeos tty1´ text? Is there any way I can run some command and display more stuff, or other regular old text?

I´m after a way to display the ip address on the screen, so a user can start up the appliance, see the ip, and login to it. Even better would be some way to figure out the ip address and wrap it in a message that shows the webmin url, something like this, with the message before the login prompt




> To manage this appliance, visit [https://1.2.3.4:10000](https://1.2.3.4:10000) and login with an administrator account.

jeos login:



Thanks in advance.
- Mark

---

### Post by jrib on 2008-02-09
/etc/issue is the file you want to edit (see 'man issue').  'man getty' lists the escapes you can use in the file.  See if one of those does what you want.  Feel free to ask again if that's not enough!

---

### Post by mark_k on 2008-02-16
That was immensely helpful!

I created a simple /etc/init.d/ script, scheduled to run after /etc/rcS.d/S40networking, and borrowed heavily from [http://suseforums.net/lofiversion/index.php/t23000.html]("http://suseforums.net/lofiversion/index.php/t23000.html")
to pluck out the ip address.

I seem to having timing issues on fast machines (this is a virtual instance) where the networking is started but doesn't come up all the way before the issue-modifying script runs, but other than that it works great.

Thanks for the pointer!
- mark

---

### Post by nickmuldoon on 2008-02-27
Hi Mark,

I'm getting the same issue with the image booting too fast and the IP being out of date (old /etc/issues) or not displaying at all. 

Do you have any suggestions for how to prevent this? How were you able to schedule that particular script to run after the networking?

Thanks Mark,
Nick

---

### Post by jason_Xtreme on 2008-03-12
can you upload you script please i created on a long time ago by editing the motd file and addin a script that ran after login but i can find the file

---

