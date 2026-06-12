---
title: "#ubuntu"
date: 2005-02-15
forum: The Cafe
---

### Post by ubuntu_fan on 2005-02-15
What am I missing?

Unfortunately, my firewall at work doesn't allow IRC through.

Are there any people who frequent #ubuntu that can tell me what sort of things get discussed there?

Anyone know of a FW-friendly way (Java applet?) that does IRC?

a.

---

### Post by lao_V on 2005-02-15
If you want to just 'see' what sort of things gets discussed here then try the following irc log link.
 
 [http://irclog.workaround.org/]("http://http://irclog.workaround.org/")

---

### Post by ubuntu_fan on 2005-02-15
Thanks!

---

### Post by JsPr on 2005-02-15
[QUOTE=lao_V]If you want to just 'see' what sort of things gets discussed here then try the following irc log link.
 
 [http://irclog.workaround.org/]("http://http://irclog.workaround.org/")[/QUOTE]


This link redirects to microsoft. This is a joke , right???

---

### Post by lao_V on 2005-02-15
I'm not sure why it redirects (and microsoft would be the last option I would want it to redirect to), try typing it manually in the address bar
 
 [http://irclog.workaround.org/](http://irclog.workaround.org/)

---

### Post by JsPr on 2005-02-15
[QUOTE=lao_V]I'm not sure why it redirects (and microsoft would be the last option I would want it to redirect to), try typing it manually in the address bar
 
 [http://irclog.workaround.org/](http://irclog.workaround.org/)[/QUOTE]

This link works fine. Strange? Conspiracy theories anyone?? :-)

---

### Post by lao_V on 2005-02-15
Yeah, I'm actually an undercover microsoft agent. Wow that is a scary thought!

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=JsPr]This link works fine. Strange? Conspiracy theories anyone?? :-)[/QUOTE]

Yeah, the original link has two lots of 'http://' in front of it...

a.

---

### Post by lao_V on 2005-02-15
Oh..That's quite strange. Are you using Firefox as your browser? In firefox its redirecting to Microsfot (why microsoft?) but in IE it displays page cannot be displayed.
 
 Is this a bug in firefox?

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=lao_V]Oh..That's quite strange. Are you using Firefox as your browser? In firefox its redirecting to Microsfot (why microsoft?) but in IE it displays page cannot be displayed.
 
 Is this a bug in firefox?[/QUOTE]

Yes, I got the same in Firefox...

If I open a new Firefox tab and enter the url "http://http://" it redirects to MS.

Weird!

I'm wondering if it's something to do with Firefox's default protocol handlers...?

The behaviour doesn't happen with IE.

a.

---

### Post by lao_V on 2005-02-15
I'm registering this as a bug (maybe its not). Hope to get some resolution..Will update here

---

### Post by JsPr on 2005-02-15
fyi,
Opera redirects to [http://www.http.com/](http://www.http.com/).

---

### Post by ubuntu_fan on 2005-02-15
I've just ethereal'ed it...

It occurs because firefox can't find the server http. It then sends this to Google as a "I'm feeling lucky" entry.

This is the equivalent to entering "http" into a Google search box and then hitting "I'm feeling lucky" - which brings up [www.microsoft.com](www.microsoft.com).

It's not a bug, just that MS appears first in the search results...

---

### Post by JsPr on 2005-02-15
[QUOTE=ubuntu_fan]I've just ethereal'ed it...

It occurs because firefox can't find the server http. It then sends this to Google as a "I'm feeling lucky" entry.

This is the equivalent to entering "http" into a Google search box and then hitting "I'm feeling lucky" - which brings up [www.microsoft.com](www.microsoft.com).

It's not a bug, just that MS appears first in the search results...[/QUOTE]

Good, I was beginning to believe that there was a MS trojan inside firefox..

---

### Post by lao_V on 2005-02-15
I've just looked up the bugzilla for firefox..
 
 [https://bugzilla.mozilla.org/show_bug.cgi?id=231720](https://bugzilla.mozilla.org/show_bug.cgi?id=231720)
 
 I find the additional comment # 39 very convincing.

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=lao_V]I've just looked up the bugzilla for firefox..
 
 [https://bugzilla.mozilla.org/show_bug.cgi?id=231720](https://bugzilla.mozilla.org/show_bug.cgi?id=231720)
 
 I find the additional comment # 39 very convincing.[/QUOTE]

Hmmm... I can feel some sort of phishing attack here...

Create a dodgy link ([http://bestbank](http://bestbank)), then make sure my term comes back first in a google searchfor "bestbank" and the user is automatically redirected to my dodgy site...

Not sure that it's the best behaviour. Maybe the default should be to search google rather than just taking you to the first result.

---

### Post by lao_V on 2005-02-15
The phishing vulnerability has already been covered here...
 
 [http://www.ubuntuforums.org/showthread.php?t=14527&highlight=firefox+phishing](http://www.ubuntuforums.org/showthread.php?t=14527&highlight=firefox+phishing)

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=lao_V]The phishing vulnerability has already been covered here...
 
 [http://www.ubuntuforums.org/showthread.php?t=14527&highlight=firefox+phishing](http://www.ubuntuforums.org/showthread.php?t=14527&highlight=firefox+phishing)[/QUOTE]

I'm not sure that's correct - the exploit details are [here](http://www.shmoo.com/idn/homograph.txt), but I think it's something different in this case?

---

### Post by Jad on 2005-02-15
for Java irc client try [http://www.PjIRC.com/](http://www.PjIRC.com/)

---

