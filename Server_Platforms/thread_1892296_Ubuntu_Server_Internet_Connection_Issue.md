---
title: "Ubuntu Server Internet Connection Issue"
date: 2011-12-07
forum: Server Platforms
---

### Post by lrachar on 2011-12-07
Hello all
 
We have two web servers running Ubuntu server and apache (sorry, I don't have the version numbers at hand, but will update when I do).
 
Yesterday we moved them from my classroom, where they have been working just fine since June, into our secure server room, where they replaced our old web servers. Same subnet, same gateway, same everything, as far as we can tell.
 
One server restarted and is working properly. The other server, however, while available to the outside, is not connecting properly to other servers (e.g., we use a Google Calendar embed to coordinate with a Moodle server that is also running on the main machine).
 
We have checked the IP settings on both machines and they are identical. One of our senior technicians has checked out the hardware and can find no problem with any of the equipment. We are working on checking out the port settings, though we can't imagine how that would have been changed during the move. 
 
If anyone has any ideas about what else we should be looking at, we'd love to hear from you.
 
Lee

---

### Post by jonobr on 2011-12-07
A stuuuuupiidddd way out there guess here,
but any chance something is remember a mac address?

Ie it thinks your not where you say you are?


Or any chance you could switch cables if server A goes to port 10 and server B goes to port 11 swap them over?
Plug A into 11 and B into 10
Does it follow the port or the server

If it follows the port could it be the port is on a different vlan or if the port is not up or blocked.

---

### Post by lrachar on 2011-12-07
OK, we solved the problem.  I'm almost too embarrassed to say what it was, it was so elementary and in hind sight, so obvious.  Somehow the DNS address disappeared from the configuration file.  Gremlins, I guess.

Thanks for you suggestions.

Lee

---

### Post by CharlesA on 2011-12-07
> **lrachar said:**
> OK, we solved the problem.  I'm almost too embarrassed to say what it was, it was so elementary and in hind sight, so obvious.  Somehow the DNS address disappeared from the configuration file.  Gremlins, I guess.

Thanks for you suggestions.

Lee
It's those silly little things that cause problems.

Darn gremlins!

---

### Post by jonobr on 2011-12-07
Well thanks for saying it,

theres a lot of posts where people dont respond to suggestions and you get the feeling,
they forgot to plug it in, or the monitor cable fell out, or they didnt connect their ethernet cable.

Good on you!

---

### Post by CharlesA on 2011-12-07
> **jonobr said:**
> Well thanks for saying it,

theres a lot of posts where people dont respond to suggestions and you get the feeling,
they forgot to plug it in, or the monitor cable fell out, or they didnt connect their ethernet cable.

Good on you!
Lol yep. I've had moments like that where I've felt stupid, but you learn from your mistakes, after all. :)

---

### Post by jonobr on 2011-12-07
> but you learn from your mistakes, after all.

Amen to that brother :wink:

---

