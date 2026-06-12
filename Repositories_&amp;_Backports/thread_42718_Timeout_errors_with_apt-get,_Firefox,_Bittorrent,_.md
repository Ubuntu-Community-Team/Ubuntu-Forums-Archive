---
title: "Timeout errors with apt-get, Firefox, Bittorrent, etc."
date: 2005-06-19
forum: Repositories &amp; Backports
---

### Post by jack_mottram on 2005-06-19
I've just installed Ubuntu 5.04 from a CD on a clamshell iBook, and am getting lots of timeout errors.

For example, when I run apt-get update, I get the following:

```
Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
```

and so on for the various servers in the sources.list file. Doing the same using the Synaptic Package Manager also times out.

The same goes for Firefox and Bittorrent - attempting to load a web page or connect to a tracker throws a timeout error.

I can however ping websites succesfully, and was able to install samba with apt-get, so I must have a (almost) working connection.

So, I'm a bit stuck - is there perhaps a file I can edit to set a longer period before apt-get , Firefox, etc. time out? Or have I missed some step in the install process to properly set up my internet connection?

The only hint I'm getting is that I "may want to run apt-get update to correct these problems", which of course I can't do because apt-get update always times out. I've also tried changing my sources.list file as per the instructions at ubuntuguide.org/#extrarepositories, but to no avail.

(Sorry for the vague wording/incorrect terminology - I'm completely new to Linux, bar a bit of tinkering on the command line in OS X)

---

### Post by IchBin on 2005-06-24
I'm having the same exact problem only I'm on a PC. My problem with apt-get was solved when I quit using my wireless connection and started using my wired connection. I still have the firefox problem though. I can't surf anything in FF, but I can in Konquerer.

---

### Post by jack_mottram on 2005-06-24
Thanks for the Konqueror tip - I'll give that a go.

The iBook suffers the timeout problems whether I'm wired or wireless, though - frustrating, as I'm otherwise really impressed with Ubuntu - much, much snappier than OS 10.4 on the clunky old laptop.

---

### Post by RossC0 on 2005-06-30
Re: the firefox problem - have you turned IPV6 off ?

in firefox (or Mozilla) surf to: about:config

Search for IPV6 and set it to true  - and you should be able to surf away!

---

