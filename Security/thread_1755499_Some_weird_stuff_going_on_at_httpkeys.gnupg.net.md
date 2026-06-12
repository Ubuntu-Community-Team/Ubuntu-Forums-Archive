---
title: "Some weird stuff going on at http://keys.gnupg.net"
date: 2011-05-11
forum: Security
---

### Post by desire.linux on 2011-05-11
I'm using [http://keys.gnupg.net](http://keys.gnupg.net) to search for pgp keys by using my browser. But sometimes the browser redirects me to [http://mud.stack.nl/](http://mud.stack.nl/) when I try to access [http://keys.gnupg.net](http://keys.gnupg.net) from my FF favorites. It kind of freaks me out a little bit. I did a Google search and found another instance of the same issue:[ http://www.mail-archive.com/gpgtools-users@lists.gpgtools.org/msg00196.html]("http://www.mail-archive.com/gpgtools-users@lists.gpgtools.org/msg00196.html").

If you want to try the same, go to [http://keys.gnupg.net](http://keys.gnupg.net) in your browser. Then close the browser, and use your history bar to reload [http://keys.gnupg.net](http://keys.gnupg.net). Usually it loads [http://keys.gnupg.net](http://keys.gnupg.net) as it should, but sometimes you go straight to [http://mud.stack.nl/](http://mud.stack.nl/).

Are anyone able to explain this?

---

### Post by Joe of loath on 2011-05-11
Could be a DNS problem?

---

### Post by timothy48342 on 2011-05-12
When I go to [http://keys.gnupg.net/](http://keys.gnupg.net/) it loads a keyserver page that looks identicle to the one at [http://zimmermann.mayfirst.org/](http://zimmermann.mayfirst.org/) (It might take you somewhere else.) On the zimmerman page it mentions something about being able to set up a way to go to a random keyserver. 

I realize your using your browser, not the random setup they talk about but consider just the fact that there exists a way to go to a random keyserver. Now take that info along with the following...

The webpage you landed on at [http://mud.stack.nl](http://mud.stack.nl) is on a domain that ALSO just happens to have a subdomain for a PGPkeyserver at [http://keyserver.stack.nl/](http://keyserver.stack.nl/)

Waaaay too much of a coincidence for me. I am thinking that [http://keys.gnupg.net/](http://keys.gnupg.net/) was doing some sort of redirection and then stack.nl had their mud and keyserver subdomains screwed up. Or like Joe said, a DNS problem, but in this case with the resolution and updating of subdomains within stack.nl

Or maybe it was something else...

-tim

---

### Post by lisati on 2011-05-12
When I went to [http://keys.gnupg.net/](http://keys.gnupg.net/) all I got was the default Apache "It Works!" index page.

---

### Post by 3602 on 2011-05-12
Goes to a MUD page: Confirmed on XP SP3, Novell server and ZENworks computer.

---

### Post by desire.linux on 2011-05-13
> **lisati said:**
> When I went to [http://keys.gnupg.net/](http://keys.gnupg.net/) all I got was the default Apache "It Works!" index page.

I forgot to mention that the same happens to me****.

The MUD page seems legitimate enough, and timothy48342 explains that the same domain has a key mirror. It might be that there's a problem with the server setup at gnupg or something.

---

### Post by 3602 on 2011-05-13
OK within the two previous days I have got:
MUD page - Once
Actual Keys page - Once
It Works! - Once

Interesting. In the mean time I'll go play that MUD (within VBox Fedora)...

---

