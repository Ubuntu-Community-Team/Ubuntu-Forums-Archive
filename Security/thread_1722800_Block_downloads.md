---
title: "Block downloads"
date: 2011-04-06
forum: Security
---

### Post by Menneskefernis on 2011-04-06
Hi everybody

I live at a college where I'm responsible for the computer in our common room. After a long fight with our network supplier we have finally gotten internet access from it. The machine has Windows Vista which doesn't go that good with a slow computer like the one in our common room. Since the internet access has made i vulnerable to attacks of different kinds and all the security software make it even slower, I have considered to change the OS to Ubuntu.

Here comes my question: As the computer is free for everybody at the college to use I need to make sure that no illegal files, or if necessary no files at all, can be downloaded of a specific user. How do I solve this?

And if you have suggestions to which security steps I can take to make sure that my neighbors don't **** up the computer I would really appreciate it. I have thought of enabling ufw and I don't yet know if I want to install clamav

---

### Post by BkkBonanza on 2011-04-06
It's very hard to prevent files from being downloaded - especially for preventing technically advanced users. You may be able to put some restrictions in place but there are always ways around them. The same methods used to view web pages are used to download files.

You may look at creating AppArmor rules that prevent Firefox from writing files outside it's own cache directory. That may make it harder. You may require users bring their own flash stick to use for their home or for writable space so they take away what they are responsible for and trust they will do that.

You definitely have to give them user accounts and no admin rights to install software. Even then they can find ways to do things even if it means booting a live cd or flash stick.

---

### Post by bodhi.zazen on 2011-04-06
I would use a kiosk type of set up (my favorite is Fedora with xguest) and trust / common sense from there.

If the privilege of internet access is abused -> loss of privileges.

If you wanted you could try using a proxy server, such as squid, privoxy, or dansguardian. You certainly could monitor internet activity with a proxy and restrict people who abuse the privilege. If yo go this route, everyone will need a unique account.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

You would need to restrict physical access to the box to prevent all abuse.

---

### Post by Menneskefernis on 2011-05-06
Hey.. thanks for the answer. I didn't see it before now because I thought an e-mail was sent to me on replies.

BUT you don't need to worry about advanced users here. I guess I'm the only one at my college that knows the word Ubuntu :-) And as you can see, even I am not that advanced.

The computer is normally only used at parties to play music either from the computer or the internet, so I just want one user profile besides the admin. Actually I'm not sure if I want another user at all because I don't quite get how it would increase the security. No matter what people would need the same password to install programs. Why would I want to have the admin profile and a user profile? And do I need it?

So I think the appArmor could be a respectable solution. Could you please tell me a bit more about that? Would it prevent people from downloading at normal use?

I hope I didn't confuse you too much with all my questions :-)

---

### Post by bodhi.zazen on 2011-05-06
It is difficult to impossible to prevent downloads of contraband.

You can block all ports but http (80) and https (443) , but people can still download on those ports.

So you would need a proxy that would filter content and block downloads based on some rule set. See the link I gave you or read up on squid.

At the end of the day, treat people as adults. Post a sign abuse the privilege -> loose the privilege.

In terms of a second account, the first account, the admin account, has full access to the system and can install stuff. You need a second non-admin account.

Again I highly suggest you read up on what is called a "kiosk" and , IMO, I would use Fedora 14 + xguest

---

### Post by Lars Noodén on 2011-05-07
+1 for the kiosk and the second, non-admin user, you can even set it to login automatically.

Also, speaking of music, if you haven't seen it already there is a good program for music in the Ubuntu repositories, called [mixxx](http://www.mixxx.org/).

---

### Post by black_cat on 2011-05-07
> **Menneskefernis said:**
> Hi everybody

I live at a college where I'm responsible for the computer in our common room. After a long fight with our network supplier we have finally gotten internet access from it. The machine has Windows Vista which doesn't go that good with a slow computer like the one in our common room. Since the internet access has made i vulnerable to attacks of different kinds and all the security software make it even slower, I have considered to change the OS to Ubuntu.

Here comes my question: As the computer is free for everybody at the college to use I need to make sure that no illegal files, or if necessary no files at all, can be downloaded of a specific user. How do I solve this?

And if you have suggestions to which security steps I can take to make sure that my neighbors don't **** up the computer I would really appreciate it. I have thought of enabling ufw and I don't yet know if I want to install clamav


bahasa inggris mu ajor cokkk...........:P

---

