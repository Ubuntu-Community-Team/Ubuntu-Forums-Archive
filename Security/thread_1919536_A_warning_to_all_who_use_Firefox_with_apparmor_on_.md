---
title: "A warning to all who use Firefox with apparmor on 10.04!"
date: 2012-02-03
forum: Security
---

### Post by desire.linux on 2012-02-03
It seems to be a bug in the Firefox profile (Ln11) after the Firefox 9 upgrade, so apparmor no longer protects Firefox.

You'll have to do some editing to make it work again:

```

$ sudo vim /etc/apparmor.d/usr.bin.firefox

```Replace:

```

/usr/lib/firefox-9.0.1/firefox-*bin {

```With:

```

/usr/lib/firefox-9.0.1/firefox {

```

And don't forget to run this command at the end:

```

$ sudo /etc/init.d/apparmor restart

```

This fix makes it work again.

**Use at your own responsibility!**

If you got a better fix for this, please let me know.

---

### Post by Dave_L on 2012-02-03
Thanks.  That seems to work.

Has this been officially reported as a bug?

---

### Post by Lampi on 2012-02-03
firefox 10 is already out in the field as lucid-proposed package

it's fixed in there:

```
# We want to confine the binaries that match:
#  /usr/lib/firefox-10.0/firefox
/usr/lib/firefox-10.0/firefox
# but not:
#  /usr/lib/firefox-10.0/firefox.sh
/usr/lib/firefox-10.0/firefox{,*[^s][^h]} {
```

---

### Post by Dave_L on 2012-02-04
[Ubuntu 10.04]

I upgraded to firefox 10.0 yesterday (it's in lucid-updates now).

That changed line in the apparmor profile is not getting expanded properly, and the profile is not working.

```
$ sudo apparmor_parser -d /etc/apparmor.d/usr.bin.firefox

----- Debugging built structures -----
Name:		/usr/lib/firefox-10.0/firefox{,*[^s][^h]}
Profile Mode:	Enforce
Capabilities: net_bind_service
...
Name:		firefox_java
Local To:	/usr/lib/firefox-10.0/firefox{,*[^s][^h]}
Profile Mode:	Enforce
Capabilities: net_bind_service
...
Name:		firefox_openjdk
Local To:	/usr/lib/firefox-10.0/firefox{,*[^s][^h]}
Profile Mode:	Enforce
Capabilities: net_bind_service
...
```

Notice that in the above output, there's no entry for "firefox". The "{,*[^s][^h]}" seems to be taken as a literal string, rather than an expression to be expanded.

---

### Post by desire.linux on 2012-02-05
Firefox 10 works here with apparmor after the latest update. It's in enforce mode when I run **apparmor_status**.

---

### Post by Dave_L on 2012-02-05
desire.linux:

You're on Ubuntu 10.04?  And /etc/apparmor.d/usr.bin.firefox has the "{,*[^s][^h]}" notation?

That's strange. I wonder why it doesn't work for me.  I had to use the change you suggested in your first post.

---

### Post by desire.linux on 2012-02-05
That's correct, Dave_L.

It's indeed strange that you still experience this problem after the latest update, if you haven't done any alterations yourself. :/

---

### Post by Dusenberg on 2012-02-05
I am on 11.10 and just updated to Firefox 10.

However I also have the 'correct'  coding in /etc/apparmor.d/usr.bin.firefox
```
/usr/lib/firefox-10.0/firefox{,*[^s][^h]} {
```
but firefox doesn't appear in output of sudo apparmor-status.

---

### Post by kostkon on 2012-02-05
> **Dusenberg said:**
> I am on 11.10 and just updated to Firefox 10.

However I also have the 'correct'  coding in /etc/apparmor.d/usr.bin.firefox
```
/usr/lib/firefox-10.0/firefox{,*[^s][^h]} {
```
but firefox doesn't appear in output of sudo apparmor-status.
The apparmor profile for firefox is disabled by default. See [here]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles").

---

