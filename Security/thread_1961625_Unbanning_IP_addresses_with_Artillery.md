---
title: "Unbanning IP addresses with Artillery"
date: 2012-04-19
forum: Security
---

### Post by Juliia on 2012-04-19
Hello, I am trying to run Artillery and I need to un ban some IP addresses. However, updating the banlist.txt will not un ban and IP nor will running their script. If I use the command from IP tables it work but if I restart the app it will re ban the IP.

---

### Post by rookcifer on 2012-04-20
I never have understood the point in banning IP's.  If you have a good firewall, just let them scan.  Who cares?

---

### Post by wacky_sung on 2012-04-21
> **rookcifer said:**
> I never have understood the point in banning IP's.  If you have a good firewall, just let them scan.  Who cares?

I bet you never run any servers. If not, lamers will be happy to visit your server to plant as C&C.

---

### Post by rookcifer on 2012-04-21
> **wacky_sung said:**
> I bet you never run any servers. If not, lamers will be happy to visit your server to plant as C&C.

Still doesn't answer my question of how banning an IP does anything whatsoever to stop this?  If your firewall is setup properly, it shouldn't matter one way or the other.

---

### Post by wacky_sung on 2012-04-21
> **rookcifer said:**
> Still doesn't answer my question of how banning an IP does anything whatsoever to stop this?  If your firewall is setup properly, it shouldn't matter one way or the other.

Banned IP help to prevent dictionary attack by brute force your login on your web application. This is totally nothing related to your firewall.

---

### Post by rookcifer on 2012-04-21
> **wacky_sung said:**
> Banned IP help to prevent dictionary attack by brute force your login on your web application. This is totally nothing related to your firewall.

So make your password stronger. Also, make it so it times out after so many wrong attempts.

Basically what I am saying is that "banning IP's" is security through obscurity measure and is not worth doing in most cases.

---

### Post by wacky_sung on 2012-04-21
> **rookcifer said:**
> So make your password stronger. Also, make it so it times out after so many wrong attempts.

Basically what I am saying is that "banning IP's" is security through obscurity measure and is not worth doing in most cases.

I think you still cannot get my point. The OP may be providing a service to people such as web hosting,FTP, etc. He cannot set how people input their password by filter it with certain parameter. Thus this does not stop attackers to brute force OP clients password. Software like Fail2ban/others help to secure the web application from further dictionary attacks.I hope you can see it now.

---

### Post by rookcifer on 2012-04-21
> **wacky_sung said:**
> I think you still cannot get my point. The OP may be providing a service to people such as web hosting,FTP, etc. He cannot set how people input their password by filter it with certain parameter.

Why can't he?  Websites do it all the time.

 > Thus this does not stop attackers to brute force OP clients password. Software like Fail2ban/others help to secure the web application from further dictionary attacks.I hope you can see it now.

It's a game of whack a mole.  You ban one IP, another one pops up.  I see no point really.  It's best to secure your system so that these malicious botnets can't do any harm regardless.

Oh well, you see things your way, I see them mine.  You prefer security through obscurity.  I don't.

---

### Post by wacky_sung on 2012-04-21
> **rookcifer said:**
> Why can't he?  Websites do it all the time.

 

It's a game of whack a mole.  You ban one IP, another one pops up.  I see no point really.  It's best to secure your system so that these malicious botnets can't do any harm regardless.

Oh well, you see things your way, I see them mine.  You prefer security through obscurity.  I don't.

Are you aware that if you are running a server and very high potential that your clients have a massive accounts getting compromised especially using same method of attack.

You can refer to [Zone-H.org]("http://www.zone-h.org/archive") for your mass defacement which can be applied using dictionary attack/exploits.

---

### Post by plumcode on 2013-03-28
Did anyone ever answer this?  I have the same problem as Juliia.

---

### Post by Elludium_Q-36 on 2013-03-29
Nope!

One poster turned the thread into a soapbox, to argue AGAINST using a security tool.  

Maybe (s)he runs a bot-net or is a cracker.  Why ELSE would you argue AGAINST security?

In medieval times, castle walls and gates were strong, but adding a moat, with a drawbridge added an extra layer of security.
Why allow the hoards to come right up to the door, with a battering ram, or to the walls, with a ladder?

Or does that one poster think there should not be a moat, and no walls around the castle?  Just let them come in and do as they please.

---

### Post by ex_isp on 2013-03-30
> **Elludium_Q-36 said:**
> Nope!

One poster turned the thread into a soapbox, to argue AGAINST using a security tool.  

Maybe (s)he runs a bot-net or is a cracker.  Why ELSE would you argue AGAINST security?

In medieval times, castle walls and gates were strong, but adding a moat, with a drawbridge added an extra layer of security.
Why allow the hoards to come right up to the door, with a battering ram, or to the walls, with a ladder?

Or does that one poster think there should not be a moat, and no walls around the castle?  Just let them come in and do as they please.

Very well put!  Layered security is always the best approach.

---

### Post by haqking on 2013-03-31
You run the ```
remove_ban.py
``` script

---

