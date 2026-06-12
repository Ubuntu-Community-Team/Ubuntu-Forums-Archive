---
title: "IRC Noob Here"
date: 2006-10-27
forum: The Cafe
---

### Post by DevNull11 on 2006-10-27
I'm defiantly a IRC noob. In fact I just heard about it today. How do you get a irc.freenode.net username. Plus How do you setup Gaim and Xchat because I plain to use both.

---

### Post by PriceChild on 2006-10-27
You don't need to register a username... you can just jump right in!

You can password your username later though if you like it and stick with it. I can't remember the commands off-hand, but i'm sure anyone in #ubuntuforums would be happy to help.

---

### Post by John.Michael.Kane on 2006-10-27
[http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup)

---

### Post by DevNull11 on 2006-10-27
How do you just jump right in my gAim sayes it need a Screen Name and a password.

---

### Post by John.Michael.Kane on 2006-10-27
Don't use gaim.

```
**sudo aptitude install xchat**
```

---

### Post by DevNull11 on 2006-10-27
I was going to use xchat for my ubuntu what can I use for my windows xp computer?

---

### Post by PriceChild on 2006-10-27
or xchat-gnome

---

### Post by ice60 on 2006-10-27
> **DevNull11 said:**
> I was going to use xchat for my ubuntu what can I use for my windows xp computer?
you can use this :)
[http://www.silverex.org/news/](http://www.silverex.org/news/)

make sure you use that version, there's a paid version too.

if you decide to setup a username on freenode, make sure you don't use your username as the password. it will automatically make the password for the name you are using.

/msg nickserv register <your-password>

not this 

/msg nickserv register <your-nick>

maybe that's obvious, but i have made that mistake a few times ](*,) lol

then when you open xchat find freenode,right when it has just opened, **highlight freenode** and select **edit** then put your password where it says -
**Nickserv Password**

but, maybe don't do that straight away, wait until you are happy using IRC first.

---

### Post by pmj on 2006-10-27
For Gaim, just pick a name. Any name will do, as long as nobody else on Freenode has it. Don't fill in a password at all, it's only needed if your name is registered. Gaim is fine if you don't use IRC often and don't want to be in many channels. A good thing about Gaim is an IRC channel will look like a regular user in your buddy list, and joining the channel is as easy as double-clicking the name of it. But if you need more functionality, you should try a more advanced client.

---

### Post by user1397 on 2006-10-27
i just use gaim for irc, i don't need anything more complicated.  in gaim, after you have already registered your nick, you should put your password in your irc account, so that you can basically sign on, and your password will be automatically recognized by nickserv

edit:  you have to tick "remember password" in your irc account for this to work.

---

### Post by DevNull11 on 2006-10-28
Thanks I guss the nicknames I tryed before where being used.

---

### Post by bionnaki on 2006-10-28
for windows, use mirc or xchat for windows

[www.mirc.com](www.mirc.com)
[http://www.xchat.org/windows/](http://www.xchat.org/windows/)

---

### Post by flajus on 2006-11-03
Please help i'm tryin to install xchat and i get the following error:
/usr/bin# ./xchat
./xchat: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory


I need this file "libdbus-glib-1.so.2" from where i can get that file? is there any command in terminal that he finds that needed file and install it for me or something like that.

HELP!

---

### Post by OffHand on 2006-11-03
> **flajus said:**
> Please help i'm tryin to install xchat and i get the following error:
/usr/bin# ./xchat
./xchat: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory


I need this file "libdbus-glib-1.so.2" from where i can get that file? is there any command in terminal that he finds that needed file and install it for me or something like that.

HELP!

Try:
```
sudo aptitude install xchat
```

---

### Post by puppy on 2006-11-03
There's a quicker alternative (and one that won't need another icon on your desktop :rolleyes: ). Why not try Chatzilla? It's  firefox's IRC extension  :-D

---

### Post by flajus on 2006-11-03
> **OffHand said:**
> Try:
```
sudo aptitude install xchat
```


sudo aptitude install xchat << it doeasnt work i tried this command in terminal it install and everything looks OK but when i try to run xchat ir displays to me: ./xchat: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

and i want to ask is there chatzilla for linux version ?
Please saombody help!:)

---

### Post by ice60 on 2006-11-03
hi, you should be able to run it by doing one of these -

browsing though the menus, then clicking from there.

or, Alt-F2 xchat

or, from a terminal

xchat &

---

### Post by ice60 on 2006-11-03
i can't delete this post. it's a mistake anyway!!

---

### Post by KaroSHi on 2006-11-03
[http://www.karoshi.me.uk/irc](http://www.karoshi.me.uk/irc) is something i wrote a while back for a irc network i support, just change accessirc to freenode and you are in :) hope its of some use!

---

### Post by OffHand on 2006-11-03
> **flajus said:**
> sudo aptitude install xchat << it doeasnt work i tried this command in terminal it install and everything looks OK but when i try to run xchat ir displays to me: ./xchat: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

and i want to ask is there chatzilla for linux version ?
Please saombody help!:)

```
sudo aptitude install libdbus-glib-1-2
```

Also you can just type xchat instead of ./chat

---

### Post by .t. on 2006-11-03
xchat-gnome

Plus, when I try to use IRC it just hates me help me plz im dieing here help help help.

No, seriously:[quote=it hates me] Connecting to chat.freenode.net (213.92.8.4) port 6667..
 Connected. Now logging in..
 *** Looking up your hostname...
 *** Found your hostname, welcome back
 *** Checking ident
 *** No identd (auth) response
 .t. already in use. Retrying with .t._..
 .t._ already in use. Retrying with .t.__..
 Nickname already in use. Use /NICK to try another.
 JOIN :Register first.[/quote]

Every time, I have to register. I don't want to. I have. What more do you want!?

Edit: Fixed. Used /nick. Who else is using my nick? I've used it fine before!

---

