---
title: "Metasploit?"
date: 2010-06-28
forum: Security
---

### Post by GrantStoner on 2010-06-28
Does anyone know how to install Metasploit (on 10.04)? And does anyone know of they still support a GUI or if they dropped that? I heard they were gonna drop it after 3.-something.

---

### Post by fbnaia on 2010-06-28
You can find install instructions at the metasploit website here: **[Installation on Ubuntu Linux]("http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu")**, you can still run the web gui, but it's not actively supported. As a little advice, you're better off learning the Metasploit console in the long run, you have more control and learn stuff alot quicker. Also checkout the [Metasploit Unleashed website]("http://www.offensive-security.com/metasploit-unleashed/").

---

### Post by GrantStoner on 2010-06-28
Thanks, I've got it installed and running now, and I've been reading some about working with it in the console. Do you know where the GUI is for it? I can't find it online.

---

### Post by yeleek on 2010-06-29
You should use MSFCONSOLE, rather than the gui.  Read below will advise why.

[http://www.offensive-security.com/metasploit-unleashed/](http://www.offensive-security.com/metasploit-unleashed/)

---

### Post by GrantStoner on 2010-06-29
> **yeleek said:**
> You should use MSFCONSOLE, rather than the gui.  Read below will advise why.
As I said, I've been learning about using the console, but I'd like to at least have the GUI for practicality. Using the GUI won't take anything away from me learning to use Metasploit. Using the console just allows me to learn more and do more. But I'd still like to have the GUI available for myself even if I never use it. So where can it be found?

---

### Post by yeleek on 2010-06-29
[http://www.offensive-security.com/metasploit-unleashed/msfgui](http://www.offensive-security.com/metasploit-unleashed/msfgui)

Which is from the original link you were given.

---

### Post by GrantStoner on 2010-06-29
That link only gives you the benefits and drawbacks to using it (as well as a picture with it), not how/where to get it.

---

### Post by LiQuidAiR on 2010-06-29
Give this a try:

[http://www.metasploit.com/redmine/projects/framework/wiki/UserGuide](http://www.metasploit.com/redmine/projects/framework/wiki/UserGuide)


This link is bomb-diggity...W0rd up!

---

### Post by GrantStoner on 2010-06-29
That document is awesome. Looks great. I'm assuming not too much has changed from 3.2 to 3.4

---

### Post by LiQuidAiR on 2010-06-29
wish i could answer that.  I played around with MetaSpl01t but haven't started learning Python to write my own exploits.  Gotta learn how to read ASM fluently first. BOOM!

---

### Post by yeleek on 2010-06-30
> **GrantStoner said:**
> That link only gives you the benefits and drawbacks to using it (as well as a picture with it), not how/where to get it.

Type msfgui - the image gave the executable name.  I have to say, I do find it strange why if you are trying to learn a exploitation framework (metasploit) you didn't feel able to google this yourself?

[http://www.google.com/search?client=ubuntu&channel=fs&q=metasploit+gui&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=metasploit+gui&ie=utf-8&oe=utf-8)

First result shows what the gui is called...  msfgui.

---

### Post by LiQuidAiR on 2010-06-30
> **yeleek said:**
> Type msfgui - the image gave the executable name.  I have to say, I do find it strange why if you are trying to learn a exploitation framework (metasploit) you didn't feel able to google this yourself?

[http://www.google.com/search?client=ubuntu&channel=fs&q=metasploit+gui&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=metasploit+gui&ie=utf-8&oe=utf-8)

First result shows what the gui is called...  msfgui.


Maybe he wants to interact with the community. I wouldn't question the motives. The internet is about helping people and sharing information. I love how every main stream forum has post nazis.

---

### Post by yeleek on 2010-06-30
> **LiQuidAiR said:**
> Maybe he wants to interact with the community. I wouldn't question the motives.
Fair enough

> **LiQuidAiR said:**
> The internet is about helping people and sharing information. 
:lol:

> **LiQuidAiR said:**
> I love how every main stream forum has post nazis.
1) You shouldn't throw that word around
2) Security is a complex field.  People want to know about firewalls, av or if they've been compromised etc.  Yeah I expect and would answer any question on it.  

People want to learn about an exploitation framework (which I do use in a professional capacity) - then I'd at least expect an ability of self reliance and researching of ones own requirements.  The answer of msfgui was given, perhaps not as directly as the OP wanted but as I also pointed out, the first result on a simple google research gave the answer....  

Do developers, coders, engineering professionals, security professionals or other complex IT individuals get their experience/knowledge by;
A) having info given to them on a plate
or
B) given hints, but made to look/research themselves.

I was always taught B - and its served me in the IT industry very well for the last 16 years.

---

### Post by LiQuidAiR on 2010-06-30
Makes sense.  That seems to be a good way to learn.  His question was overly simple and yes, he could have done a simple [http://metasploit.com](http://metasploit.com) and received all his answers.

I agree with you.  I think people just take it over board sometimes.  They act like it's such a headache to answer a simple question.  

I'm sorry for assuming....

---

### Post by yeleek on 2010-06-30
NP - Its forgotten :D

---

### Post by GrantStoner on 2010-06-30
I did google it myself, first of all. And second, the name on the picture doesn't help. I already knew what it was called. I just don't know where to get it. "./msfgui" does not work. And not to mention, Ubuntu Forums is somewhere anyone using Ubuntu should feel free to ask any question he/she has. The community is supposed to be here to help people, not tear them down. I just want to know how to get the GUI working. And also, the metasploit website has nothing about the GUI. Google was my first step. Always is, as it's my homepage. Nothing.

---

### Post by yeleek on 2010-06-30
Does not work how?  Whats the error?  Cannot find it?  Complains about missing Ruby? 

[http://backtrack.offensive-security.com/index.php/Howto:Run_MsfGui](http://backtrack.offensive-security.com/index.php/Howto:Run_MsfGui)
Lists the requirements/dependencies which msfgui requires.

---

### Post by GrantStoner on 2010-06-30
Thanks yeleek, that was exactly what I was looking for. I didn't know it needed dependencies that weren't installed along with msfconsole, msfcli, and msfweb.

---

### Post by yeleek on 2010-06-30
I run BT4 in a vm and msfgui advises specifically what dependencies it has when it fails to run...

---

### Post by LiQuidAiR on 2010-06-30
To save yourself headache.  Try to always read all available information.  You would think that asking questions would resolve something but in general software is multi-tier in design. Especially in Linux.  

Which means,  dependencies must be accounted for.  Most Linux software developers will post all that information on their websites.  The 'how to' install guides usually provide good enough information on how to install everything needed.

It sounded like a pain to me, when I first started using Linux.  But, the over time saved by reading through all available text is easier than asking questions.  Not that asking is bad.

---

