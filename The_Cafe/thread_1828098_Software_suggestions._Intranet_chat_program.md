---
title: "Software suggestions. Intranet chat program"
date: 2011-08-18
forum: The Cafe
---

### Post by weasel fierce on 2011-08-18
I need some software recommendations:


I am looking for a piece of software to set up an internal real time chat room in a work situation.


The software must:

Be open source, or at least under a "free to use" license

It needs to be able to set up distinct chatrooms

Ideally, you can restrict a specific user to only access a specific, given chatroom.

Private messaging facility would be great, especially if it includes an option to enable or disable this feature for specific users.



Any suggestions?

---

### Post by sanderd17 on 2011-08-18
Setting up an IRC server will be the best thing.

That way you have complete control over the chatroom while the users can use interfaces they want (web interface or a separate client).

---

### Post by cgroza on 2011-08-18
> **sanderd17 said:**
> Setting up an IRC server will be the best thing.

That way you have complete control over the chatroom while the users can use interfaces they want (web interface or a separate client).
+1

You will have to learn a few IRC commands to control the chatroom, or get a client such as XChat that has that allows to send these commands via a GUI.

---

### Post by raja.genupula on 2011-08-18
for IRC chat you can use 
Xchat
pidgin
empathy

my choice is pidgin

---

### Post by weasel fierce on 2011-08-18
oh, I forgot.. it needs to run on windows XP :0 Just in case that makes a difference.

---

### Post by LowSky on 2011-08-18
Pidgin is a great choice. It can be used over different OSes including Windows so it will easily integrate into a business environment.

I would take a look at Jabber/XMPP too. Many server solutions are free and since they will all work with Pidgin set up for users is a breeze.

[http://xmpp.org/xmpp-software/servers/](http://xmpp.org/xmpp-software/servers/)

---

### Post by Thewhistlingwind on 2011-08-18
> **weasel fierce said:**
> oh, I forgot.. it needs to run on windows XP :0 Just in case that makes a difference.

[http://serverfault.com/questions/9132/irc-server-for-windows](http://serverfault.com/questions/9132/irc-server-for-windows)

Have fun.

---

### Post by weasel fierce on 2011-08-18
Could pidgin be configured to ONLY work on an intranet ?

---

### Post by FuturePilot on 2011-08-18
Jabber (XMPP). There are a number of open source clients. IMO the best one is Gajim.

---

### Post by ve4cib on 2011-08-18
> **weasel fierce said:**
> Could pidgin be configured to ONLY work on an intranet ?

Probably not easily on the client-side.  But you could set up a content filter to block access to external protocols that Pidgin might use.

---

### Post by johnnybgoode83 on 2011-08-18
Pidgin gets my vote.  We use it at work for our chat solution

---

### Post by vehemoth on 2011-08-19
You could try pidgin with bonjour (an intranet chat protocol), there are probably some other protocols that will work, pidgin is cross compatible.

---

### Post by Tibuda on 2011-08-19
+1 for bonjour

---

### Post by zengrz on 2011-08-19
Sounds like a fun project to work on :o

---

### Post by ki4jgt on 2011-08-19
> **vehemoth said:**
> You could try pidgin with bonjour (an intranet chat protocol), there are probably some other protocols that will work, pidgin is cross compatible.

+ 1 though it's not a chatroom setting in it's original set (list of rooms which users can join) it is capable.

It works by listing user who are on the network. Those users talk directly to each other, or can group themselves with other users to make what is seemingly the same thing as a chat room. It's more like a conference setting though, where each user who wants a chatroom merely brings more people into the conversation. When the conversation is over, there is no room left.

---

### Post by graabein on 2011-08-19
Something like jabber?

---

### Post by ugm6hr on 2011-08-19
Bit confused - do you need an intranet server for work, or a software messaging client?
If the former, you can google "open source groupware" - a number of options are available. Citadel [http://www.citadel.org/](http://www.citadel.org/) has good reports, and is accessible from any web-browser (and has lots more functions than you require).
If the latter - it depends on what protocol you use.

---

### Post by jerenept on 2011-08-19
Pidgin has local chat system.

---

