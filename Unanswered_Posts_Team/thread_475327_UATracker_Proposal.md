---
title: "UATracker Proposal"
date: 2007-06-16
forum: Unanswered Posts Team
---

### Post by kidders on 2007-06-16
Hi guys,

It's been suggested that we try to find ways of flagging & tracking the progress of the threads we reply to. It seems to me that we might want to ...[LIST]
[*]Measure how successful we are at finding viable solutions to awkward problems people are running into, and create a way of asking for help quickly, if something turns out to be more complicated than anticipated.
[*]Single out posters whose threads repeatedly go unanswered, so we can prioritise those users, and maybe make some constructive suggestions on how to go about getting quicker responses in the future.
[*]Maybe do some other things that might be interesting.[/LIST]Jacob & I have been playing around with the idea of using a third-party website, to give us a little more flexibility than would be fair to expect from ubuntuforums.org itself. It works like this ...[LIST=1]
[*]A team member submits the UID of a thread he's working on.
[*]Over time, he periodically updates the status of the thread, or perhaps asks for help.
[*]Meanwhile, the server is collecting other information that might be useful to the team (eg lists of users with multiple unanswered posts).
[*]At some point, a thread could be closed, once the poster is happy.[/LIST]The trick is to find ways of automating the process as much as possible. At the moment, Firefox users can tag threads in one click with a quick browser extension I threw together. Opera users can do the same thing by prefixing a thread's URL with a short keyword, in their address bar. I've also made requests for help into an RSS feed, so team members who want to attract each others' attention can do so easily, with things like Live Bookmarks, etc.

Anyhow, I suppose this post is sort of a general call for help. Most importantly, do we suppose we could get much mileage out of the idea ... or would it just be irritating?! Currently on the TODO list, to try to knock the tracker into shape & make something potentially useful out of it are ...[LIST=1]
[*]Try to make it look pretty. I've hacked together a rudimentary PHP/MySQL back end, but have the artistic talent of an over-ripe turnip. [[COLOR=DarkRed]**Edit:** ajmorris has kindly taken on the mantle of uateam style guru :-)[/COLOR]]
[*]Come up with a few clever ways of making the involvement of a third party site as unobtrusive as possible. Greasemonkey seems a good option for Firefox users, but it doesn't seem fair to penalise people (like me hehe) who don't use it much.
[*]Not having to worry too much about loading ubuntuforums.org with weird SQL queries or feature requests gives us the opportunity to do nice things. Any ideas?[/LIST]Anyhow, enough rambling! If anyone is interested in lending a hand, or maybe just taking a peek at what Jacob & I have done, please feel free. :-)

**[SIZE=3][COLOR=Blue]Getting started[/COLOR][/SIZE]**

A clever, automated way of syncing the user databases on ubuntuforums.org and ua.codechunk.net (our server) is still in the works, so unfortunately, anyone who wants to give it a try will have to contact me somehow. Sorry for that. Perhaps the easiest thing to do is drop me a PM, although I'm often logged into IRC & other places. [[COLOR=DarkRed]**Edit:** Jacob & ajmorris are now service admins as well.[/COLOR]]

**Firefox**
A browser toolbar extension is provided on-site at [http://ua.codechunk.net/](http://ua.codechunk.net/). Installing it lets you add a "Tag thread" toolbar button to your browser.

**Opera**
A basic HTML form is available at [http://ua.codechunk.net/](http://ua.codechunk.net/) I suggest right-clicking it, selecting "Create search", and setting up a short mnemonic (eg 'U'). That way, you can prefix any thread's URL with a 'U' & hit [ENTER] to send it to the tracker.

**[SIZE=3][COLOR=Blue]Update[/COLOR][/SIZE]**

Jacob's written an IRC interface to the tracker, which is fun. Careful not to annoy it though ... it's prone to op-ing itself and kicking people that misbehave hehe! Also, the tracker site is now localisable. If you're tired of English let me know, and we can inject a little of your native language into the tracker interface.

---

### Post by ajmorris on 2007-06-29
come on guys, this is a great idea, get registered

---

### Post by teaker1s on 2007-07-04
after 3 weeks out of things(abroad no internet access) could someone please tell me how you register for the above mentioned

---

### Post by jpeddicord on 2007-07-04
> **teaker1s said:**
> after 3 weeks out of things(abroad no internet access) could someone please tell me how you register for the above mentioned
Check your PM box. ;)

---

### Post by brennydoogles on 2007-12-13
> **teaker1s said:**
> after 3 weeks out of things(abroad no internet access) could someone please tell me how you register for the above mentioned

I am unable to register as well. Any help?

::EDIT::

Kidders helped me out, so I'm all set up!

---

### Post by ajmorris on 2007-12-14
for anyone else needing an account, you need to request one, so either head on over to #ubuntuforums-unanswered on irc.freenode.net, or pm Jacob, kidders or myself, and we can help you out.

---

