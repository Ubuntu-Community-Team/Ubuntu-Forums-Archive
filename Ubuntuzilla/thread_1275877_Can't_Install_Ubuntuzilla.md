---
title: "Can't Install Ubuntuzilla"
date: 2009-09-26
forum: Ubuntuzilla
---

### Post by sports fan Matt on 2009-09-26
When I try..it gives: Error: Dependency is not satisfiable: libstdc++5

---

### Post by nanotube on 2009-09-26
Hi
which version of ubuntu? and do you have the universe repo enabled?

---

### Post by sports fan Matt on 2009-09-26
Karmic and I do have them installed..Furthermore..when I tried to install thunderbird (I deleted the folder as to start fresh) I was presented with /opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.  That was from the terminal.

---

### Post by nanotube on 2009-09-26
Hi

well... that package /did/ exist in all prior versions of ubuntu, so i don't know what happened to it with karmic.

it is also required to run the mozilla builds of firefox/thunderbird, so the error message you're getting about the missing library is no surprise.

don't know what's going on with the karmic repos, but... nothing i can do about it. suggest you ask someone who might know what's going on. maybe on irc in #ubuntu-dev, or something like that. or maybe on launchpad.

---

### Post by sports fan Matt on 2009-09-26
Thanks for the help..I started a new topic..Yeah this does seem odd...6 is installed..

---

### Post by kansasnoob on 2009-09-30
I've been doing some looking. I had installed Ubuntuzilla in Karmic alpha 4 (and 5 I think).

The change was made upstream in Debian Sid:

[http://www.debianhelp.org/node/15792](http://www.debianhelp.org/node/15792)

I did a lot of looking and this has been somewhat of a recurring issue since as far back as 2006.

Anyway in that link they recommend:

> just giving a soft link from /usr/lib/libstdc++.so.6 to /usr/lib/libstdc++.so.5 and see if it works for you.

No idea how to do that but I'd be glad to give it a try if someone knows how to create such a link.

No sweat if I break things!

I have tried installing libstdc++5 from Jaunty and it's a no go!

---

### Post by kansasnoob on 2009-09-30
Thought this was funny from Debian:

> Please remove the gcc-3.3 source and binaries (gcc-3.3-base, libstdc++5); The
compiler isn't built anymore, and libstdc++5 isn't used as a dependency anymore.


A simple google search proves that wrong.

---

### Post by kansasnoob on 2009-09-30
I also have an ongoing discussion here:

[http://ubuntuforums.org/showthread.php?p=8028911#post8028911](http://ubuntuforums.org/showthread.php?p=8028911#post8028911)

---

### Post by kansasnoob on 2009-09-30
Just learned from mc4man that Gdebi is broken in Karmic. I installed the libstdc++5 .deb from the Jaunty package list using dpkg with no problem.

I then used dpkg to install Ubuntuzilla (failed because I needed to install libnotify-bin from repos), after installing libnotify-bin Ubuntuzilla installed properly and the script ran OK.

I say OK, but I have noticed for a while that I get the plugin path warning but I just hit enter and everything still works afterwards.

Anyway, until the devs get Karmic straightened out, it can be worked around.

It might be wise to let me run this for a couple of days to make sure I didn't break anything. Nothing apparent, but something could crop up.

---

### Post by nanotube on 2009-09-30
> **kansasnoob said:**
> 
just giving a soft link from /usr/lib/libstdc++.so.6 to /usr/lib/libstdc++.so.5 and see if it works for you. 


no idea if this would actually help... but to create that link, run the following command:

```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```

so if you are up for it, try uninstalling the libstdc++5 package that you installed from jaunty, making that link, and running the ubuntuzilla-installed version of firefox, and see if it complains of anything.

---

### Post by kansasnoob on 2009-09-30
> **nanotube said:**
> no idea if this would actually help... but to create that link, run the following command:

```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```

so if you are up for it, try uninstalling the libstdc++5 package that you installed from jaunty, making that link, and running the ubuntuzilla-installed version of firefox, and see if it complains of anything.

I had tried that:

> lance@lance-desktop:~$ sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
ln: creating symbolic link `/usr/lib/libstdc++.so.5': File exists 

All's working well after installing the Jaunty package, I'd bet libstdc++5 finds it's way back in just as it has since Dapper time:)

I should send you a full output of that plugin path error, but later. I've been testing the Karmic beta iso and I'm broiling over the lack of ability to file a decent bug report regarding gdm.

But I see I missed the ability to do some testing for you. Always feel free to contact me via PM for testing.

---

### Post by nanotube on 2009-10-01
> **kansasnoob said:**
> 
I should send you a full output of that plugin path error, but later. 


whenever you have a chance :) no hurry.

> 
But I see I missed the ability to do some testing for you. Always feel free to contact me via PM for testing.

appreciate the offer! will do :)

---

