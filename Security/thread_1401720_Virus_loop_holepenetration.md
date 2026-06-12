---
title: "Virus loop hole/penetration"
date: 2010-02-08
forum: Security
---

### Post by yyyc186 on 2010-02-08
Today I had IOTOP -o -d 10 running in a window trying to track down some intermittent disk usage spikes (which now appear to be some kind of battle between kjournald2 and postgres stats collector.)

I was surfing the Web with Opera 10.10 waiting for the hard drives to make their thrashing noise and for an entry to appear in that window.  I kept seeing entries like this show up:

[http://www.oaklandjobforce.com/common/track/trackgeneral.asp?tcid=106&ttid=2&cid=13667145&emid=1186&t](http://www.oaklandjobforce.com/common/track/trackgeneral.asp?tcid=106&ttid=2&cid=13667145&emid=1186&t)

Always for just a few bytes.

I hadn't been to the Oakland site in days.  Only went there because I was directed there by Indeed in an alert.  It appears this site has managed to exploit a weakness in Opera to install monitoring software once you visit it, or reply to something on it.  I haven't tracked down where the penetration actually occurs, but I do know that clearing private data lone isn't enough to clear the tracker.  You have to clear all private data _and_ shut down opera.

I believe this tracker has malicious intent as my CC company is trying to track down the source of some fraudulent charges appearing on my account.  I do run the actual Anti-virus stuff for KUbuntu and so far this is the only tracker type thing I've ever found.

---

### Post by mkvnmtr on 2010-02-08
Is it by chance a cookie responding to home?

---

### Post by Enigmapond on 2010-02-08
If you were using Opera on Ubuntu, there is no way anything can install anything on your system...It's just a tracking cookie. Delete cookies and the cache and all will be well again. Viruses can't install on your system...period.

---

### Post by Saghaulor on 2010-03-01
> **Enigmapond said:**
> If you were using Opera on Ubuntu, there is no way anything can install anything on your system...It's just a tracking cookie. Delete cookies and the cache and all will be well again. Viruses can't install on your system...period.

If the malware is made for Linux, it can very well install, if you let them. Hence the importance of sudo and not running as root.

---

### Post by Sporkman on 2010-03-02
> **Saghaulor said:**
> If the malware is made for Linux, it can very well install, if you let them. Hence the importance of sudo and not running as root.

You don't need to be root to install stuff in the home directory & have it start up on login.

---

### Post by uRock on 2010-03-02
> **yyyc186 said:**
> Today I had IOTOP -o -d 10 running in a window trying to track down some intermittent disk usage spikes (which now appear to be some kind of battle between kjournald2 and postgres stats collector.)

I was surfing the Web with Opera 10.10 waiting for the hard drives to make their thrashing noise and for an entry to appear in that window.  I kept seeing entries like this show up:

[http://www.oaklandjobforce.com/common/track/trackgeneral.asp?tcid=106&ttid=2&cid=13667145&emid=1186&t](http://www.oaklandjobforce.com/common/track/trackgeneral.asp?tcid=106&ttid=2&cid=13667145&emid=1186&t)

Always for just a few bytes.

I hadn't been to the Oakland site in days.  Only went there because I was directed there by Indeed in an alert.  It appears this site has managed to exploit a weakness in Opera to install monitoring software once you visit it, or reply to something on it.  I haven't tracked down where the penetration actually occurs, but[COLOR=Red] I do know that clearing private data lone isn't enough to clear the tracker.[/COLOR]  You have to clear all private data _and_ shut down opera.

I believe this tracker has malicious intent as my CC company is trying to track down the source of some fraudulent charges appearing on my account.  I do run the actual Anti-virus stuff for KUbuntu and so far this is the only tracker type thing I've ever found.

I noticed that the link appears to be dead now. Blank screen on the page. I guess that is another strike against Opera.

> **Enigmapond said:**
> If you were using Opera on Ubuntu, there is no way anything can install anything on your system...It's just a tracking cookie. Delete cookies and the cache and all will be well again. Viruses can't install on your system...period.

Please read the red text.

> **Sporkman said:**
> You don't need to be root to install stuff in the home directory & have it start up on login.

FUD.

---

### Post by d3v1150m471c on 2010-03-02
swiftfox/firefox addon noscript addon is your friend.

---

### Post by Sporkman on 2010-03-02
> **iRock said:**
> 
FUD.

How so? A user can edit his own .profile or .bashrc file to call an executable, and save an executable file somewhere in his own directory to be called. If a user can do it, then the user's hijacked browser can do it, right? No root password required.

---

### Post by DrMelon on 2010-03-02
> **Sporkman said:**
> How so? A user can edit his own .profile or .bashrc file to call an executable, and save an executable file somewhere in his own directory to be called. If a user can do it, then the user's hijacked browser can do it, right? No root password required.

It's true, you can do this. But the main thing is that *how can the browser be hijacked in the first place by a tracking cookie*?

You see, the cookie itself isn't able to do anything, and you can't overwrite the browser itself - because you need root access to do that. Unless all his software has been installed in the home directory AND the virus programmer KNOWS that, it's still FUD.

---

### Post by uRock on 2010-03-02
> **Sporkman said:**
> How so? A user can edit his own .profile or .bashrc file to call an executable, and save an executable file somewhere in his own directory to be called. If a user can do it, then the user's hijacked browser can do it, right? No root password required.

That is why Ubuntu ships with AppArmor.

---

### Post by FuturePilot on 2010-03-02
> **iRock said:**
> That is why Ubuntu ships with AppArmor.

Except the Firefox profile is disabled by default.

---

### Post by uRock on 2010-03-02
I know that not every person who tries a new OS does it, but when I came to Ubuntu it didn't take me long to find my way to the Security Discussions sub-forum and do some home work.

I have been to lots of those sites of which we do not speak here and have not had any problems with anything installing itself. Yes those sites include Facebook and Myspace, which are both known for their malware distribution to Windows visitors.

---

### Post by bodhi.zazen on 2010-03-02
> **iRock said:**
> That is why Ubuntu ships with AppArmor.

> **FuturePilot said:**
> Except the Firefox profile is disabled by default.

Most profiles are disabled by default, which is too bad IMHO.

Also the OP was asking about Opera , and I do not think there is a profile for opera.

Writing a profile for a browser is not so easy, and IMO, although most needed, not the place to start with apparmor.

---

### Post by uRock on 2010-03-02
Yeah, we kinda got off subject. None of what we have said helps the OP get rid of the bug he has nor avoiding it in the future.

If I weren't so buried in schoolwork right now, I would try and build an AppArmor profile for Opera. I am not sure just how secure Google Chrome's sandbox is, but it appears to be decent from what I have read on it.

---

### Post by OpSecShellshock on 2010-03-02
Could be Flash cookies. Those are persistent, frequently secreted away and generally aren't under the control of the browser. Firefox + BetterPrivacy extension will clean those right up.

---

