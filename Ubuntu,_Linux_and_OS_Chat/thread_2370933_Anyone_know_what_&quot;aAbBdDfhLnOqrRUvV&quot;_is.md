---
title: "Anyone know what &quot;aAbBdDfhLnOqrRUvV&quot; is?"
date: 2017-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by 45yoyos on 2017-09-08
So I was fooling around on my home server, just recently reinstalled Ubuntu after a hardware update, and I noticed something odd: On the ping command, if you look at the arguments available, you see the very first one is "-aAbBdDfhLnOqrRUvV"...

It even made its way onto the manual for the ping command ( [http://manpages.ubuntu.com/manpages/xenial/man8/ping.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ping.8.html) ), though there is no indication of what it is or why its there?

If you use ping with this argument, it just brings up the ping command help again.

It's not really a technical issue, since it doesn't really matter. But I just googled it and couldn't find anything and was super curious about the origin.

---

### Post by pauljw on 2017-09-08
> **45yoyos said:**
> So I was fooling around on my home server, just recently reinstalled Ubuntu after a hardware update, and I noticed something odd: On the ping command, if you look at the arguments available, you see the very first one is "-aAbBdDfhLnOqrRUvV"...

It even made its way onto the manual for the ping command ( [http://manpages.ubuntu.com/manpages/xenial/man8/ping.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ping.8.html) ), though there is no indication of what it is or why its there?

If you use ping with this argument, it just brings up the ping command help again.

It's not really a technical issue, since it doesn't really matter. But I just googled it and couldn't find anything and was super curious about the origin.

That's just all the options available to the ping utility.  Go to 'man ping' and it first listed like that, but as you progress further in the document each of those options is listed separately with an explanation as to what it is used for.  Nothing cryptic or ominous about it.  :)

---

### Post by 45yoyos on 2017-09-08
Ahh. Okay. That's a weird... feature? Thanks for the help though :)

---

