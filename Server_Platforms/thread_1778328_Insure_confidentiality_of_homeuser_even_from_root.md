---
title: "Insure confidentiality of /home/user even from root"
date: 2011-06-08
forum: Server Platforms
---

### Post by dudumomo on 2011-06-08
Hi there,

I got a tricky question (Well, it seems to be).
I am the admin of a small serveur with 3 users. I'd like to insure them a complete confidentiality of their data, but not using virtualisation.

What I want to do is to restrict my access for not being possible to acces to their /home/user folder for example.

Any solution?

By encrypting the folder ? But it has to be always accessible to the user.
If it is possible, I guess I'll still have the right to modify the password and then, access to their data. But this is fine as they will rapidly know that I've changed their password.

Thank you for your help !!

---

### Post by ruffEdgz on 2011-06-08
Well the best thing to do in this situation would be to make sure:
[LIST=1]
[*]No user is a part of another users group
[*]Make sure to change the mode is recursively changed for each users home directory (*/home/user*) to 750
[*]Have each user add the command 'umask 027' to their ~/.bashrc file (*default dir = 750, default file = 640*)
[*]No one can access root from sudo (*sudo su -*)
[*]No one know the root password (*randomize it*)
[/LIST]
Lets take into note that I just wanted to show you the options you can do if you wish to try and place your server in 'complete confidentiality'. These changes can place risks in the future when it comes to administering the box (problem arises but no one can go into root without rebooting the machine). I don't advise in using all of them on your box but using some of these to help complete you goal shouldn't hurt.

The administrator of a server will always have complete access to that box and if anyone is worried about 'confidentiality', I would write up a Service Level Agreement which will talk about the purpose of the server, what your role is on the server, what you will do in case of an emergency, etc...

Hope this helps.

---

### Post by dudumomo on 2011-06-13
Thank you for your answer.
It is indeed difficult to hide stuff to the admin...quite normal behavour anyway.

I'll implement the umash setting tho. Very useful !
Thank you !

---

### Post by BkkBonanza on 2011-06-13
You can just migrate users onto encrypted homes. This is fairly easy and once done not even root can see the contents of their home folders. Even if they get physical access. The solution given above doesn't help at all since someone with physical access can undo everything.

See, [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

This can also be chosen as an option when installing first time. Users use their home as normal. I've been using this for a couple years now without any problem mostly because I don't want someone who steals my notebook while travelling to see my content. Each user login unlocks the home for them with their normal password. You can also easily support two-factor authentication if need be.

---

