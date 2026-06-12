---
title: "Run local apps from web page"
date: 2008-07-27
forum: Server Platforms
---

### Post by jombeewoof on 2008-07-27
I want to be able to serve a web page with buttons that will launch local apps. 
I specifically want to be able to launch amarok, mplayer and vmware, but I figure the basic principle will be the same no matter what app I want to run.

So... how do I do it? I know it's posible but not sure how.

---

### Post by scragar on 2008-07-27
hmn, interesting. I quickly tried using exec to try and get konqueror to run via a PHP script, however that died because it was unable to connect to the users X-system.

Not so sure what to do about that, there may be a way to get such scripts to run right, although I can't guarantee it.

---

### Post by RuleMaker on 2008-07-27
It surely can't be done by php or any other server side language, if it's possible anyhow it could only be done by some client side language like JavaScript.
However, I think that's not possible because it would be a security hole if you could launch any application on client's machine.
You can only execute plug-ins, by using "embed" and "object" tags.

---

### Post by jombeewoof on 2008-07-27
what about just running a script. can I get cgi to run a bash script?

---

### Post by cariboo on 2008-07-28
Vlc will do what you want as far as media apps are concerned and vmware installs a remote access console when you install it.

Jim

---

