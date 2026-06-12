---
title: "oh-so-descriptive man pages"
date: 2008-10-26
forum: The Cafe
---

### Post by jerome1232 on 2008-10-26
I was just looking at the man page for xorg and saw this

```
VIDEOADAPTOR SECTION
       Nobody wants to say how this works.  Maybe nobody knows ...

```

I wonder if there's any other oh-so-helpful man pages out there.
:lolflag:

---

### Post by jimi_hendrix on 2008-10-26
linux is the only OS where the programmers hide funny quirks like this...(whens the last time you saw a joke in windows?)

---

### Post by steeleyuk on 2008-10-26
> (whens the last time you saw a joke in windows?)

That stupid dog in XP that helps you search for things.

---

### Post by LaRoza on 2008-10-26
> **jimi_hendrix said:**
> linux is the only OS where the programmers hide funny quirks like this...(whens the last time you saw a joke in windows?)

Actually..

Windows and MS are full of easter eggs. It is less now, for legal reasons, but it is there.

Google for them ;)

Programmers are programmers the world over.

---

### Post by jimi_hendrix on 2008-10-26
> **steeleyuk said:**
> That stupid dog in XP that helps you search for things.

thats not a joke...that was a serious thing to play around with in computer class (right click + animate!)

---

### Post by tdrusk on 2008-10-26
> **jimi_hendrix said:**
> linux is the only OS where the programmers hide funny quirks like this...(whens the last time you saw a joke in windows?)
*waits for witty comment*

---

### Post by JohnFH on 2008-10-26
```

sudo apt-get install funny-manpages
man party
man uubp
man rescrog
man rtfm

```

Your homework is to find the other man pages in the package.   Have fun!

---

### Post by Le-Froid on 2008-10-26
> **jimi_hendrix said:**
> (whens the last time you saw a joke in windows?)

They used to have a few easter eggs in Internet Explorer (6?) - google it.

---

### Post by jimi_hendrix on 2008-10-26
just googled it...id take cow powers over a moving background that wastes ram

---

### Post by scragar on 2008-10-26
> **JohnFH said:**
> ```

sudo apt-get install funny-manpages
man party
man uubp
man rescrog
man rtfm

```

Your homework is to find the other man pages in the package.   Have fun!

hmn, let's see:
```

usr/share/man/man1/
usr/share/man/man1/date.1fun.gz
usr/share/man/man1/echo.1fun.gz
usr/share/man/man1/gong.1fun.gz
usr/share/man/man1/grope.1fun.gz
usr/share/man/man1/party.1fun.gz
usr/share/man/man1/rescrog.1fun.gz
usr/share/man/man1/rtfm.1fun.gz
usr/share/man/man1/rm.1fun.gz
usr/share/man/man1/tm.1fun.gz
usr/share/man/man1/xkill.1fun.gz
usr/share/man/man1/baby.1fun.gz
usr/share/man/man1/celibacy.1fun.gz
usr/share/man/man1/flog.1fun.gz
usr/share/man/man1/uubp.1fun.gz
usr/share/man/man1/condom.1fun.gz
usr/share/man/man1/flame.1fun.gz
usr/share/man/man1/xlart.1fun.gz
usr/share/man/man6/
usr/share/man/man6/sex.6fun.gz
usr/share/man/man3/
usr/share/man/man3/strfry.3fun.gz
usr/share/lintian/
usr/share/lintian/overrides/
usr/share/lintian/overrides/lintian
usr/share/doc/
usr/share/doc/funny-manpages/
usr/share/doc/funny-manpages/README.Debian
usr/share/doc/funny-manpages/copyright
usr/share/doc/funny-manpages/changelog.Debian.gz
usr/share/man/man1/egrope.1fun.gz
usr/share/man/man1/fgrope.1fun.gz
```

so I'm guessing there's a number of man pages.

---

### Post by Hire on 2008-10-26
> **JohnFH said:**
> ```

sudo apt-get install funny-manpages
man party
man uubp
man rescrog
man rtfm

```

Your homework is to find the other man pages in the package.   Have fun!

hire@nicus:~$ sudo dpkg -L funny-manpages
/.
/usr
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/date.1fun.gz
/usr/share/man/man1/echo.1fun.gz
/usr/share/man/man1/gong.1fun.gz
/usr/share/man/man1/grope.1fun.gz
/usr/share/man/man1/party.1fun.gz
/usr/share/man/man1/rescrog.1fun.gz
/usr/share/man/man1/rtfm.1fun.gz
/usr/share/man/man1/rm.1fun.gz
/usr/share/man/man1/tm.1fun.gz
/usr/share/man/man1/xkill.1fun.gz
/usr/share/man/man1/baby.1fun.gz
/usr/share/man/man1/celibacy.1fun.gz
/usr/share/man/man1/flog.1fun.gz
/usr/share/man/man1/uubp.1fun.gz
/usr/share/man/man1/condom.1fun.gz
/usr/share/man/man1/flame.1fun.gz
/usr/share/man/man1/xlart.1fun.gz
/usr/share/man/man6
/usr/share/man/man6/sex.6fun.gz
/usr/share/man/man3
/usr/share/man/man3/strfry.3fun.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/lintian
/usr/share/doc
/usr/share/doc/funny-manpages
/usr/share/doc/funny-manpages/README.Debian
/usr/share/doc/funny-manpages/copyright
/usr/share/doc/funny-manpages/changelog.Debian.gz
/usr/share/man/man1/egrope.1fun.gz
/usr/share/man/man1/fgrope.1fun.gz

---

### Post by JohnFH on 2008-10-26
> **scragar said:**
> hmn, let's see:
...

so I'm guessing there's a number of man pages.

Yep, but, after first trying 'man sex' and seeing that it worked, you're meant to spend hours trying to guess other man pages are included.  ;)

---

### Post by jerome1232 on 2008-10-26
> **JohnFH said:**
> ```

sudo apt-get install funny-manpages
man party
man uubp
man rescrog
man rtfm

```

Your homework is to find the other man pages in the package.   Have fun!

Those are pretty good, lol. rtfm -ph. egrope -v /etc/X11/xorg.conf

---

### Post by MaxIBoy on 2008-10-26
```
man mount
```
>        The proc file system is not associated with a special device, and  when
       mounting  it, an arbitrary keyword, such as proc can be used instead of
       a device specification.  [i](The customary choice none is less  fortunate:
       the error message ‘none busy’ from umount **can be confusing**.)[/i]

Well *that* certainly clears things up!

Unintentional irony for the win.

---

### Post by lswb on 2008-10-26
This is from the man page for "who"


       ....   If  ARG1  ARG2  given, -m presumed: &#8216;am i&#8217; or &#8216;mom likes&#8217; are
       usual.

---

### Post by jerome1232 on 2008-10-26
What's better is it works
```
 who mom likes
jeremy   pts/1        2008-10-26 16:49 (:0.0)

```

---

### Post by nixscripter on 2008-10-26
A classic one from AIX, the **tunefs** command:

> 
NOTE: You can tune a filesystem, but you can't tune a fish.


---

