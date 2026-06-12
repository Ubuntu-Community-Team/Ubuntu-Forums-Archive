---
title: "Options for limited internet availability?"
date: 2007-05-05
forum: Ubuntu Christian Edition
---

### Post by naked on 2007-05-05
I know some filtering software that will only enable access during defined times.  Is there such a way to do this?  

Or even possibly a way to lock the computer after 'x' time?  Or during 'x' hours?

Just trying to think something through.

L

---

### Post by urukrama on 2007-05-05
There is something, called ACEPT, but it isn't well know. You can find the source files and installation instructions [here]("http://forja.guadalinex.org/repositorio/projects/acept"). You can filter the internet, set allowable times for accessing the internet, certain pograms, or logging in with a specific username. If I remember correctly you can even specify the amount of hours xyz username can be logged in, use abc application, or surf the internet.

And now the downside: the program is entirely in Spanish, though, but you can use [Google Translate]("http://translate.google.com/translate_t") to translate the installation instructions/manual, which helps enormously. :-) It is a bit of a pain to set up if you don't speak Spanish, but might be worth it if this is what you are looking for.

I've installed it once on a Dapper machine, but didn't keep it long enough to seriously test it. What I saw, though, looked good. 

Perhaps someone should start getting this thing translated. It is part of Guadalinex, a Ubuntu-based Linux distro designed by the government of Andalucia (Spain). I don't know, though, if Guadalinex comes with ACEPT pre-installed.

---

### Post by dakotadare2b on 2007-05-05
> **naked said:**
> I know some filtering software that will only enable access during defined times.  Is there such a way to do this?  

Or even possibly a way to lock the computer after 'x' time?  Or during 'x' hours?

Just trying to think something through.

L

One simple and effective way I do this in my home, is to set up an Access Restrictions policy in my main router (Linksys WRT54G) which my broadband modem is plugged in to. I configure the hours that I don't want my child accessing the Internet. The limitation on this is that it affects every user on the Internet, as it cannot be pc specific.

Dansguardian has been great for content filtering, but I don't see that it has parental controls for locking down the Internet at specified times. There might be a firewall product that will allow you to control this on a pc by pc basis.

---

### Post by jonathonblake on 2007-05-05
[QUOTE=dakotadare] There might be a firewall product that will allow you to control this on a pc by pc basis.[/QUOTE]

If each computer on the network has a static IP address, and you have a [COLOR="Red"]*good*[/COLOR] [COLOR="RoyalBlue"]**hardware**[/COLOR] firewall, then you can control what goes to, and from that computer.

[LIST]
[*]This only works for ethernet connections; (It might work with wireless, but the issue here is that with a wireless connection, the net can be surfed on connections other than one's own connection.)
[*]You might have to make your own hardware firewall appliance;(The last time I looked at firewall appliances was in 1999.  Things  have changed since then.  *The Linux Router Project* has been "abandoned",but makes / made a useful tool for blocking by IP address.)
[*]You need to be comfortable using the command line;You might also need to compile your own kernel.  This isn't as hard as it sounds --- if you do things carefully, and keep backups of everything. For the first couple of times, I'd suggest using a computer with a hard drive you can reformat every time you make a mistake.)
[/LIST]

I'd also suggest setting up a system within the firewall that runs a DNS and web server.  This is so that you can block "bad" URLs within the network, and either supplement, or replace the Firefox extensions that block adds, cookie tracking, and other "bad" things.  

xan

jonathon

---

