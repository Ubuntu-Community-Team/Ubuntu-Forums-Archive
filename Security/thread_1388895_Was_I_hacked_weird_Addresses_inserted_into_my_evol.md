---
title: "Was I hacked? weird Addresses inserted into my evolution contact list?"
date: 2010-01-23
forum: Security
---

### Post by skelooth on 2010-01-23
At work I'm running an older version of ubuntu (either 7.10 or 8.x or something like that, I'm just too busy to update). One day I broke xul runner so I've been using evolution mail.... 

There was one port open, 22, for me to ssh in past the router.

A week or so ago I was sending an email and noticed auto complete filled out a weird email address, it was a variation of my coworkers address. His is [email]jay@company.com[/email] and autocomplete gave preference to [email]jayjaytoo@verizon.net[/email] 

I just kinda shrugged, whatever.

The other day I tried to send an email to some clients, and auto complete did its thing like normal, or at least I thought. The email bounced back saying the email addresses were invalid... they were similar 'goofed up' variations of my client's emails! I had just sent a file full of coldfusion to two random addresses! 

So I look in my evolution address book, and all of my 'important' email addresses have variations that take preference in auto complete. For example, if there were a client address of 'bob@some.company.com' it would have another one added that's either like 'bob@company.com' or 'bobber@ny.rr.com' etc. 

I was kinda freaked, so I closed the port on the router. chkrootkit came back clean, there were no weird users in my /etc/passwd file, but when I type last, all of the IP addresses are 0'd out. 

Not sure wtf is going on. If someone was trying to steal info they wouldn't have left a trace? The only way in was to crack my password via ssh but I don't think that was the case, I use a solid unix style password. I was thinking maybe they got in via malware on someone else's machine on the network? I don't know. There's nothing about something like this on the googles. 

I'm gonna wipe the drive asap just in case something's dormant, but.... any ideas?

---

### Post by noway2 on 2010-01-23
I am a rather firm believer in the interpretation of Occam's razor that says that the simplest solution is most like the correct one.

Could there be someone entering these email addresses into the system by typing them in at their terminal and then you imported them?

The likelihood that you have been hacked is pretty remote.

---

### Post by skelooth on 2010-01-24
> **noway2 said:**
> I am a rather firm believer in the interpretation of Occam's razor that says that the simplest solution is most like the correct one.

Could there be someone entering these email addresses into the system by typing them in at their terminal and then you imported them?

The likelihood that you have been hacked is pretty remote.


I'd prefer a simple explanation too, but there's no possible scenario like that. This is my work station, and I'm the only one who uses it. These email addresses do not show up anywhere in my emails sent/recvd either, so it's not like evolution would have been able to finger them. They are ... truly random goofed up versions of my important email addresses. The unimportant addresses seem to be left alone... 

For example, the emails of my boss and manager, and all of the state employee emails, all have weird variations that pop up in autocomplete.

I'm really not sure what to think of it. There's nothing overly sensitive on my machine, just code and lolcat pictures. 

If I wasn't hacked/intruded, what possible other reasons could there be? And even if I was hacked, how could they get in, and why would they do something like that? 

I've seen malware do dumb stuff like that before, but never on a linux box.

---

### Post by noway2 on 2010-01-24
Fascinating.  Yes, if someone were to hack your system, the first question would be how.  The second question is why would they do that? I imagine that the idea that your computer was possibly leaves you feeling somewhat violated and you want answers.  It seems that VNC is a common source of hacking.  SSH with an insecure password would be another (RSA key is a much better option with password auth turned off).  I also certainly hope that you don't have root privileges enabled for SSH.  

One question I have is how do the names get into the Evolution contacts?  Specifically, is the contacts list shared?  I looked at my contact lists and it only has one so obviously it doesn't add them automatically when I send email.  It did have a section for my Ubuntu One contacts, so apparently it can pull them from other sources.  What is happening in your case, is probably something along these lines.  Someone was probably F'ing around with funny names for co-workers and they got stored somehow.  The trick will be in figuring it out.

Perhaps the evolution documentation or the website will have some information on the contacts?  If not, maybe someone here knows.

In the mean time, keep a close watch on your logs.  If you haven't consider installing the Snort + Ossec (see the sticky at the top of this forum).  That will most likely show you if any monkey business is happening in the network.

---

### Post by skelooth on 2010-01-25
Thank you noway2 for the ideas. I've definitely learned a valuable lesson about security... that no matter how tight I think my ship is, it really isn't. 

I still haven't wiped the drive, but I will soon, and I'll be installing/watching snort and ossec on all my machines from now on.

---

