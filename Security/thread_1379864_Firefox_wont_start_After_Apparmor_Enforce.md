---
title: "Firefox wont start After Apparmor Enforce"
date: 2010-01-13
forum: Security
---

### Post by donato roque on 2010-01-13
I am trying apparmor on my desktop.  I enable apparmor and change mode to enforce on most available profile.  Everything is fine until...

I downloaded an add-on called FirefoxNotify for Firefox-3.5.7.  This addon is suppose to use the current notification scheme for 9.10 instead of the default notification for Firefox.  

So I figured the profile had to be modified and went to Terminal and issued:```
sudo genprof firefox
```
answered questions, deny, inherit,profile,etc.

Saved the configuration. Reloaded apparmor with:
```
sudo /etc/init.d/apparmor reload
```
```
sudo enforce firefox
``` to change mode to enforce.

Started firefox several times and tried several ways to start it.  No go.

Thoughts?

---

### Post by q.dinar on 2010-01-13
see man genprof. it creates empty profile, which does not allow anything.
default profile for firefox is already created and configured but just disabled. you should enforce it.
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5

but before this you can disable profile you generated and delete its file.

---

### Post by bodhi.zazen on 2010-01-13
> **donato roque said:**
> I am trying apparmor on my desktop.  I enable apparmor and change mode to enforce on most available profile.  Everything is fine until...

I downloaded an add-on called FirefoxNotify for Firefox-3.5.7.  This addon is suppose to use the current notification scheme for 9.10 instead of the default notification for Firefox.  

So I figured the profile had to be modified and went to Terminal and issued:```
sudo genprof firefox
```
answered questions, deny, inherit,profile,etc.

Saved the configuration. Reloaded apparmor with:
```
sudo /etc/init.d/apparmor reload
```
```
sudo enforce firefox
``` to change mode to enforce.

Started firefox several times and tried several ways to start it.  No go.

Thoughts?

First, read the apparmor thread , it is a sticky for a reason.

Second, to debug a profile you need to read the logs. I usually open /var/log/messages and debug as many messages a possible.

When you feel you are close, 

```
tail -F /var/log/messages
```

and debug the messages as they appear. 

Once you make a change to an aa profile, you need to reload the profile, and restart firefox, the aa thread reviews all this.

Finally, firefox is not such a good application to start with, mainly because firefox is complex and is not a simple web browser, we have things like sound, video, flash, opening PDF documents, opening Openoffice documents, etc, etc.

I suggest you start with a few examples of profiles for firefox, I have several listed here:

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

---

