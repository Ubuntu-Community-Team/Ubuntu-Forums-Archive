---
title: "security risk of universe in practice"
date: 2004-11-23
forum: Server Platforms
---

### Post by ubuntu_demon on 2004-11-23
How much of a security risk is using universe/multiverse packages in practice ?

I'm using at the moment things like :

amsn (I want to be able to easily switch between "see all contacts that are online" and "groups" and I don't think that's possible with gaim)
firestarter (easy firewall)
vncserver
xdiskusage
mozilla-mplayer
flashplayer-mozilla
acroread
abiword
grubconf
gftp
uligo
gnugo

Also is hoary going to have a bigger main repository ? And what about after hoary ?

---

### Post by jdong on 2004-11-23
Universe packages aren't monitored as closely for security updates as Main. Actually, I don't think they receive security updates period.

---

### Post by ubuntu_demon on 2004-11-23
I knew that already. I think my question wasn't very clear.

I want to know more about how everyone(the users) is handling this (practical advice and experiences). How big of a security risk am I taking by using these packages ? What choices is everyone making ?

And I want to know what ubuntu is going to do in the future about it.  Ubuntu is great but I think the main repository has a bit too less packagages.

---

### Post by jdong on 2004-11-24
> I knew that already. I think my question wasn't very clear.  Sorry for the misunderstanding :oops:
  
  > 
 I want to know more about how everyone(the users) is handling this (practical advice and experiences). How big of a security risk am I taking by using these packages ?   I try to avoid universe daemons/servers. Universe desktop apps are fine for me, but not universe daemons.
  
 How much of a security risk depends on which packages you're specifically referring to. The ones you listed are more of clients -- I associate little/no risk with those.
  > 
  What choices is everyone making ?
    I already touched on that. In addition, I regularly monitor security sites for possible flaws...
  
  > 
 And I want to know what ubuntu is going to do in the future about it. Ubuntu is great but I think the main repository has a bit too less packagages. Definitely there's going to be more packages supported in the future. How many? I can't tell you... and I don't think the devs are telepathic either!
  
 You have to remember that this is a first release by a team vastly smaller than Debian's. And you have to remember how long it takes Debian to get new releases out due to their large number of packages to support!

---

### Post by jdodson on 2004-11-24
more packages would rock.  i think they are going to add in more, i would really love that if they did.

---

### Post by ubuntu_demon on 2004-11-25
Yeah it would rock!

And Jdong I think you're right when you are talking about services/deamons I would never run those out of universe/multiverse.

---

### Post by quixotic-cynic on 2007-10-06
I think it also matters whether it is a net-facing app with ports open to outside. As such, I try to keep web browsers, jabber clients, e-mail clients etc within main - or pay attention to the developer's site for security updates.

---

### Post by MJN on 2007-10-06
Holy smoke quixotic-cynic, are you stuck in some sort of time warp? This thread is nearly 3 years old! :shock:

(it did seem a little strange reading the first post from a forum staff member with 4000+ beans asking a relatively-newbie question... but of course it makes sense now as when they wrote it back in '04 they obviously were!)

Mathew

---

### Post by netlogic on 2007-10-06
It is a good idea. It seems like the same questions are repeating every 2months now.  It is good to recycle. It isn't easy to make a shampoo that cleans Python and C

---

### Post by MJN on 2007-10-07
Eh?!

Your posts keep sounding like the randomly-generated spam I keep getting - it's certainly English but doesn't quite seem to make sense! ;)

Mathew

---

### Post by netlogic on 2007-10-07
I am sorry you forgot to install a sense of humor.
apt-get install sense-of-humor more-real-linux-knowledge 
apt-get remove distro-specific-knowledge

It was funny to watch you so far. you act like some interns here.

---

### Post by quixotic-cynic on 2007-10-07
> **netlogic said:**
> I am sorry you forgot to install a sense of humor.
apt-get install sense-of-humor more-real-linux-knowledge 
apt-get remove distro-specific-knowledge

It was funny to watch you so far. you act like some interns here.

Edit: removed sarcasm

I don't have that much "distro-specific-knowledge" *or* "more-real-linux-knowledge" since I have been using Ubuntu just under two months. However, with what I know about OSs in general, you are only vulnerable to attacks via open ports - ensuring that software using those ports is up to date reduces the probability of there being any un-patched vulnerabilities. So please, either explain what is incorrect about that or leave ppl alone, rather than mocking people doing their best to try to understand something.

I don't understand why you said that anyway, since your other posts are usually quite helpful.

Edit (re below): Okay, I still think the last post was a little harsh, but I have calmed down now. Sorry for reacting quite so sarcastically.

---

### Post by netlogic on 2007-10-07
It wasn't you. I forgot to quote the original post. It was a comment I made for the post above me. I am glad you are recycling the old post. We need to do it more. I was indicating that questions are recycling too much. Every questions seem like they were recycled from two months ago. That was my statement.

---

### Post by MJN on 2007-10-08
Chill out netlogic - take that chip off your shoulder. I just didn't understand the bit about *'shampoo that cleans Python and C'* (Still dont' actually! Explain it to me and I'm sure we can have a good laugh together about it!)
 
Quixotic, there's nothing wrong with bringing old threads back to life - I was just surprised to see one that was 3 years old! :)
 
Mathew

---

