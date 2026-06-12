---
title: "**help I Think I Found A Virus**"
date: 2008-03-18
forum: Security Discussions
---

### Post by dresman on 2008-03-18
Im  scared to use my linux desktop cause I was browsing through my temp folder and found some wierd file I have never seen in my life.It was titled [COLOR="Red"]agent.5304[/COLOR]I looked at the properties of this and it said it was some sort of socket thing:confused:There is only one lead up that I can think of how it happened.I had to charge my microsoft handheld one day from a usb on my system.The phone has been acting a bit odd itself lately(ex:downgrading firmware form 6.0 to 5.0 I think).

---

### Post by Dr Small on 2008-03-18
Umm, I don't think that would be a virus, but would you care to post the owner?
```
ls -l /tmp | grep agent.5304
```

---

### Post by dresman on 2008-03-18
Oh crap I think its malicious.Im getting random things loaded to the folder.I just got some wierd zip file.

---

### Post by NightwishFan on 2008-03-18
Gotta be more specific man.

---

### Post by JoshuaRL on 2008-03-18
> **dresman said:**
> Oh crap I think its malicious.Im getting random things loaded to the folder.I just got some wierd zip file.

And that is your temp folder, if you're doing stuff online and with programs it can be used.  So that doesn't in and of itself mean that you have malware.  And let me tell you, it is really hard to get a Windows Mobile device to sync with Linux, let alone install malware from it.

Try puting the command from Dr Small in and post the output.

---

### Post by dresman on 2008-03-21
I dont get any output it just stays there and nothing happens.:confused:

---

### Post by Dr Small on 2008-03-21
Then apparently the file doesn't exist.

---

### Post by bhavi on 2008-03-22
Viruses arent easy to program in linux because of Ubuntu/Linux has very **CLEAR** defenitions of groups and users, file ownerships and permissions.. So In ubuntu/linux if at all a virus is there it can affect only the user who ran the program.. And because of the file ownerships and permissions the **USER** will have a control over the system unlike in windows where the OS has control over the machine.. This makes Virus development in linux difficult to say the least.. ;)

---

### Post by nutz on 2008-03-22
I know this is a little old but it still holds true and is straight to the point...

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by Dr Small on 2008-03-23
> **bhavi said:**
> Viruses arent easy to program in linux because of Ubuntu/Linux has very **CLEAR** defenitions of groups and users, file ownerships and permissions.. So In ubuntu/linux if at all a virus is there it can affect only the user who ran the program.. And because of the file ownerships and permissions the **USER** will have a control over the system unlike in windows where the OS has control over the machine.. This makes Virus development in linux difficult to say the least.. ;)
It is still rather easy if you mix a little social egineering in with this virus + sudo.

---

### Post by nutz on 2008-03-23
> **Dr Small said:**
> It is still rather **easy **if you mix a little social egineering in with this virus + sudo.


Anything is possible with the right social engineering. All the 419ers over in Nigeria are perfect examples of that. But saying it is easy assumes way too much about the user. If you don't question a program when it needs administrative privileges then you are probably not the kind of user any means of security can protect. However if you do give careful consideration to the privilege levels of your programs then a virus infection becomes much less likely.

The 419ers in Nigeria prey on the kind of the people that are really just born suckers anyway. And those are the same computer users that no means of security will ever protect. As for the other users that do question the sources of their programs and the permissions they run with I don’t think it would be easy to compromise these systems with some sort of malware. In fact I think even the best malware author would find it quite difficult.

So to end this I think your statement that it is **easy **to compromise a Linux system with the right social engineering is false and unfounded because you are assuming the user will fall for it. To word it correctly you could say it is **possible**, but **easy **and **possible **are not the same thing.

---

### Post by bhavi on 2008-03-24
> **nutz said:**
> Anything is possible with the right social engineering. All the 419ers over in Nigeria are perfect examples of that. But saying it is easy assumes way too much about the user. If you don't question a program when it needs administrative privileges then you are probably not the kind of user any means of security can protect. However if you do give careful consideration to the privilege levels of your programs then a virus infection becomes much less likely.

The 419ers in Nigeria prey on the kind of the people that are really just born suckers anyway. And those are the same computer users that no means of security will ever protect. As for the other users that do question the sources of their programs and the permissions they run with I don’t think it would be easy to compromise these systems with some sort of malware. In fact I think even the best malware author would find it quite difficult.

So to end this I think your statement that it is **easy **to compromise a Linux system with the right social engineering is false and unfounded because you are assuming the user will fall for it. To word it correctly you could say it is **possible**, but **easy **and **possible **are not the same thing.
Yes... But user awareness is the only way out.. and the 419ers are rampant here in india.. Thats a whole sort of a different aspect.. It involves the weakest security link i.e human security.. And more over How many people would be aware of all these things digging their nose deeply into it.. esp here in India technology is evolved only from past 10 to 12 years.. Prior to that computer technology was as a newborn child.. Because of various factors here.. Even today I am an Electrical Engineering student and there is no computer science related subjects in the curricula for 2 years.. Here the elective starts from the 3 rd year onwards... In such a situation how would any user be aware of all these things except those who are in this field studying or as a professional...?

---

