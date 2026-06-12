---
title: "Lock down wireless"
date: 2010-02-07
forum: Security
---

### Post by bgard6977 on 2010-02-07
My g/f is a teacher and her school is trialing netbooks in the classroom, but the students keep switching WIFI networks and browsing on sites they shouldn't.

Is there a way to setup just one wireless network, then prevent the default user from changing it? 

If so we could lock the netbooks down to the school network which has filtering to keep them working on school instead of playing on Facebook.

---

### Post by Gouki on 2010-02-07
> **bgard6977 said:**
> My g/f is a teacher and her school is trialing netbooks in the classroom, but the students keep switching WIFI networks and browsing on sites they shouldn't.

Is there a way to setup just one wireless network, then prevent the default user from changing it? 

If so we could lock the netbooks down to the school network which has filtering to keep them working on school instead of playing on Facebook.

The school is using netbooks with Ubuntu? Sweet!

One thing that came to mind was using [pessulus]("http://live.gnome.org/Pessulus") (on the repositories), in the case you're using Ubuntu/Gnome, on those netbooks.

You can restrict access to just the browser, if you want.

---

### Post by CharlesA on 2010-02-08
Perhaps set up a proxy of some sort and tunnel the browser thru it? I don't know tbh. pessulus sounds interesting.

Check this thread out: [http://ubuntuforums.org/showthread.php?t=1213468](http://ubuntuforums.org/showthread.php?t=1213468)

---

### Post by ubunterooster on 2010-02-08
The vast majority of modern routers allow the blocking of sites. It may be laborious to block many individual sites so check if your router allows you to keep users TO certain sites. (Router settings are accessed by entering the router's IP address in a web browser of an attached computer)

---

### Post by bgard6977 on 2010-02-08
> **Gouki said:**
> The school is using netbooks with Ubuntu? Sweet!

One thing that came to mind was using [pessulus]("http://live.gnome.org/Pessulus") (on the repositories), in the case you're using Ubuntu/Gnome, on those netbooks.

You can restrict access to just the browser, if you want.


Thanks Gouki,

The netbooks are indeed using Gnome. I tried pessulus, and it is indeed able to remove the wireless applet from the notification area.

So, the next steps would be:


[LIST=1]
[*]Log in as the default user
[*]Remove any undesireable WIFI networks the students have added
[*]Setup the school network and store the password in the default keyring
[*]Logout and log back in as root
[*]Run the lockdown tool, and remove the WIFI applet
[/LIST]
So if I am correct, then the default user would be allowed to use the network I've set up, but since they couldn't run the WIFI applet, they couldn't connect to any new ones?

(pardon my Ubuntu ignorance, I'm still learning)

- Brent

---

### Post by ubunterooster on 2010-02-08
Just put the network on password protection. I love passwords! I have over thirty different ones!

---

