---
title: "Pidgin and Yahoo"
date: 2008-09-10
forum: The Cafe
---

### Post by egwest on 2008-09-10
Probably the wrong forum for this, but I'll ask here anyway.

Ok, I was using Pidgin a couple of days ago to chat with my cousin when suddenly I was disconnected from the service. Now I cannot reconnect at all, to either of my yahoo user accounts. I have tried a couple more times to log in, but it is a no go.

The message I am getting is this:

Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com:
Name or service not known.

Does anyone know if yahoo changed their server or protocols again?

---

### Post by steveneddy on 2008-09-10
This sounds weird, but try reinstalling Pidgen.

---

### Post by egwest on 2008-09-10
> **steveneddy said:**
> This sounds weird, but try reinstalling Pidgen.

Thanks, that worked, the second time I tried it, and I found the problem. Somehow it was using the wrong port, which I have no idea how it was as I never mess with settings I know nothing about.

---

### Post by danb2 on 2008-09-11
I am sorry, but what was the port in error and what is the correct one(s)?

Is there some kind of "router attack" to open an unsolicited IM session?

Why did Gaim then Pidgin work for months for me then all the sudden become randomly erratic/ impossible to login due to:

Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com:
Name or service not known.


Thanks
danb2

---

### Post by egwest on 2008-09-11
> **danb2 said:**
> I am sorry, but what was the port in error and what is the correct one(s)?

Is there some kind of "router attack" to open an unsolicited IM session?

Why did Gaim then Pidgin work for months for me then all the sudden become randomly erratic/ impossible to login due to:

Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com:
Name or service not known.


Thanks
danb2

It was not an attack, on my computer the port is 5050, and when I checked it it was showing as 2080, when I changed it back I could log back in, but then it stopped working again. I tried Kopete and I the message I get is 'Name Look Up Fail'. It seems to be a random problem. It will work and then it will not work. It is very annoying. Pidgin seems to be having the same problem with yahoo. it will work sometimes and other times I get the message you posted above. I have no problem with AOL or MSN networks.

---

### Post by steveneddy on 2008-09-18
> **egwest said:**
> Thanks, that worked, the second time I tried it, and I found the problem. Somehow it was using the wrong port, which I have no idea how it was as I never mess with settings I know nothing about.

You're welcome.

---

### Post by dakun on 2008-09-19
the problem isnt the ports, my ports and everything are all default

pidgin returns the error most of the time, sometimes it lets me in but not alot.  my cousin had the same problem with the actual yahoo messager which suggests to me that its not pidgin itself.

---

### Post by AmyRose on 2008-09-19
Looks to me like an ISP- or connection-related problem, especially if you're seeing the problem on the official client.

---

### Post by Porter Doran on 2008-10-05
This problem has been going on for me for almost a month: very rarely can I log into Yahoo Messenger with Pidgin.

However, last week I tried logging into Yahoo using the official Yahoo client on Windows, and my connection was dropped several times -- it seemed almost as bad, but not as bad, as Pidgin.

Lastly I should mention that every time I have checked whether Meebo.com can log into Yahoo, it always has been able to. This shows the problem is unlikely to be a Yahoo server problem. Huh.

---

### Post by steve8track on 2008-11-28
This solved it for me (although I just barely "solved" it, so maybe it will disconnect later):

[http://prash-babu.blogspot.com/2008/11/how-to-fix-pidgin-yahoo-error-could-not.html](http://prash-babu.blogspot.com/2008/11/how-to-fix-pidgin-yahoo-error-could-not.html)

If you ping the server pidgin tries to connect to (scs.msg.yahoo.com), if it works (it took me two tries, and now it doesn't work at all), you will get the IP address you should use.  The site says you will get: 66.163.181.166 or 66.163.181.173, but I got 66.163.181.168.  I changed the server to the IP address in my settings, and now it's working (so far).

I hope this helps.

Steve

---

### Post by linux2512 on 2008-12-17
What worked for me was running dig:

dig scs.msg.yahoo.com

Then I was able to connect when I got a successful name resolution.

---

