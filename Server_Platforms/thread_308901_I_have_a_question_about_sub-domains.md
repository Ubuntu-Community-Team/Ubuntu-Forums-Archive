---
title: "I have a question about sub-domains"
date: 2006-11-28
forum: Server Platforms
---

### Post by Chomp on 2006-11-28
sub.domain.com is an example. 

My question is, how quickly and easily can these be made if you owned a site? Suppose I wanted to make: sub.subA.subB.subC.domain.com, would it be easy and trivial to do? Would I have to register, or could I make them on the fly? 

OK, I want to know more than that. I've always wondered how difficult it really is to find all the pages or sub-domains on a site if you did not know them beforehand? Do you see where I'm getting at? 

This question is a big one for me, because as most of you may know, there are certain internet puzzles out there that ask you to solve them before you get the next url for the puzzle. I constantly ask myself, "Couldn't someone just hack into the parent directory and see all the domains?"

But is it that simple? 

If I (or you, the user) could make ANY random sub-domain or directory instantaneously on a site and delete it at will, how could anyone malicious find them during or after the fact?

---

### Post by Joe_CoT on 2006-11-28
Sub-domains are set on two different levels: the nameserver level, and the apache level. On the nameserver level, subdomains (usually called aliases) can be set to any ip you want; you could have site.com and [www.site.com](www.site.com) point to one server, irc.site.com point to another, mail.site.com point to another, etc. You can also simply set a wildcard alias (*.site.com) which picks up any subdomain not otherwise specified and sends it to the ip of your choice. The latter is what the game is probably using. To answer your "how easily" question: it's either a line in bind if they're running their own nameserver, or a change in a webmin somewhere if somebody else is hosting it.

The other half, however, is on the apache level. The nameserver simply tells the ip address to send the request to; apache's virtual hosts decide what information is displayed depending on which domain you came from. This, combined with the wildcard alias which they probably set up, makes it very hard to find out what subdomains they use: were they all registered with the nameserver, you could probably find out by WHOISing the domain (though I'm not sure you can do that either); since it's probably not, the only way of telling is to simply brute force every possible subdomain (which could take quite a while), or become a drinking buddy of the admin, and convince him to show you his httdp.conf :D

---

### Post by Chomp on 2006-11-28
Wow! That was a very technical and informative answer. Cheers. :)

---

