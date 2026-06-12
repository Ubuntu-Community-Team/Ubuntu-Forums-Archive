---
title: "security threat with tor on ubunut 12.04?"
date: 2014-12-06
forum: Security
---

### Post by deb2014 on 2014-12-06
Hello,

At my work office, I have one ubuntu 12.04 computer, one day the security of my company went to see me and told me there was a security threat on my computer,that is to say they detected a data flux from my computer to the exterior and that flux was due to the tor daemon (according to them).

I never paid attention to this daemon before, it actually appeared to be installed on my machine, I never explicitely used it before this threat detection and
never modified the configuration of tor before, anyway I was not aware of it being installed before.

So, I come to you in order to understand what may have happened on my computer, I did not discovered this data flux, because it was certainly small and did not slower down my computer.

The company has of course one firewall which prevents new connexions to my computer.

How come that the tor service be activated alone ? that is to say send and/or receive data ?

since this discover, I learned a few about tor, especially that it could run as a relay even if not explicitely
used by anyone on the computer.

Does the default ubuntu 12.04 configuration of tor allows this ? Can tor run by default as a relay
even behind a firewall ?

My personal opinion is that maybe tor has something like a default working routine which makes it
contact and  keep in touch with other tor instances, but without really exchanging data ???
Then, the security members of my company (a little paranoid of course :-)) took it very seriously.

Otherwise, I do not see the point in hacking my computer, I have no sensible information and it is not possible
to reach other computers from mine.

Do you have any ideas of what could have happened ?

Thanks for your help

Best regards

---

### Post by newbie-user on 2014-12-06
Are you in full control over your computer, or is it managed by the IT staff? If you don't know anything about tor, then someone else probably installed it and is using it, all while making you the scapegoat. Conspiracy theories aside, tor by itself is not a security threat. It might suck up bandwidth if used as a relay, which is probably what your company is having a fit about.

---

### Post by deb2014 on 2014-12-06
thanks for your reply,

I was in full control of this computer, of course I cannot garanty it has not been hacked, I wanted to figure out if by default  tor on ubuntu 12.04 works as a relay or not, and if not, does it make something ?

---

### Post by PondPuppy on 2014-12-06
I do not believe that TOR is automatically activated on Ubuntu 12.04. In fact, as I understand, TOR is not included in the default Ubuntu 12.04 installation. It must be installed by a user. 

This page may give you some information, including how to stop TOR from running at startup: [http://ubuntuguide.org/wiki/Tor](http://ubuntuguide.org/wiki/Tor)

There may be ways that TOR could have gotten installed other than by installing the basic package: by installing the TOR browser bundle, or possibly by installing the TORButton plugin for Firefox, or the TORBirdy plugin for Thunderbird. I'm not an expert in this, just saying that something may have been done which got TOR onto your machine without you knowing it.

But it should not be acting as a relay unless you -- or something else -- has told it to do so. Again, I'm not an expert, but I do not believe that TOR is configured to automatically act as a relay under most circumstances.

This page gives information on configuring TOR as a relay: [https://www.torproject.org/docs/tor-relay-debian.html.en](https://www.torproject.org/docs/tor-relay-debian.html.en)

It does not seem to me that this could have been done by accident, or be part of a standard Ubuntu installation.

Here's a snippet to check if TOR is actually running on port 9050 (default):

```
ss -aln | grep 9050
```

[COLOR=#333333][FONT=Ubuntu]You should see either or both lines of the following output:
[/FONT][/COLOR]
```
0  0  :::950  :::*
0  0   *:950   *:*
```

This is from [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

It would seem unusual for a hacker to use a machine for running a TOR relay. It would be more usual to use it as part of a bot-net for spamming or other purposes. For what it's worth.

---

