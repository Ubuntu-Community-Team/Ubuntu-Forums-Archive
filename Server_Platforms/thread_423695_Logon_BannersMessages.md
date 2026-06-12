---
title: "Logon Banners/Messages"
date: 2007-04-26
forum: Server Platforms
---

### Post by Catsworth on 2007-04-26
Hi Guys,

I'm trying to create a logon banner such as is often found in a corporate environment, something that is shown to users before they log in to Ubuntu that will give them a warning that unauthorised access may be illegal.

I found some instructions suggesting that I needed to edit /etc/issue but that hasn't helped.

Any ideas?

---

### Post by Jussi Kukkonen on 2007-04-26
That's for local logins. Try /etc/issue.net

---

### Post by Catsworth on 2007-04-26
It's local logons that I want to display the message for.

---

### Post by Catsworth on 2007-04-26
Anybody?

---

### Post by rsermilik on 2007-04-26
Normally the message during telnet and ssh login is from /etc/motd

---

### Post by jtc on 2007-04-26
No, /etc/motd is first shown when you'r already logged in.

To get a pre-login banner you ought to set the Banner directive in /etc/ssh/sshd_config

---

### Post by rickyjones on 2007-04-26
I think he is looking to display a message BEFORE you log in on the LOCAL machine - using a GUI. Personally I don't know how to do this but I'd be interested in it as well.

-Richard

---

### Post by Catsworth on 2007-04-26
A lot of corporate environments have a setup that goes something like this:

1.  Workstation is switched on and boots Windows
2.  User gets Ctrl+Alt+Del prompt to login and presses Ctrl+Alt+Del
3.  A message is displayed warning them that their activities are going to be monitored, and that unauthorised access is illegal
4.  They click ok, and then get the user/password prompt

I would like to know how to accomplish this in Ubuntu.

So, yes - I want to display a dialogue of some sort *before* the user is asked for their username and password when logging into the local machine.  I'll need to do it for remote logins eventually,but I need to get local logins sorted first.

Thanks guys.

---

### Post by Jussi Kukkonen on 2007-04-28
So you are talking about a graphical login (GDM)? You mentioning /etc/issue threw me off...

Try changing the Welcome message in *System --> Admin. --> Login Window*

---

### Post by Catsworth on 2007-04-30
The reason I mentioned /etc/issue is that some instructions I found on the Internet suggested editing that as a general way of enabling these banners within Linux - I'm actually trying to put together an instruction sheet regarding login banners, but the users are not *specifically* Ubuntu users (although some may be) but they are all going to be using some flavour of Linux or another.

I guess more detail in the original question would have been better, sorry.

---

