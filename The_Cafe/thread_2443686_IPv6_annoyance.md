---
title: "IPv6 annoyance"
date: 2020-05-18
forum: The Cafe
---

### Post by Skaperen on 2020-05-18
rsync has --ipv6 and --ipv4 not as a preference but as an exclusive use.  i want to use IPv6 when i can because the heavy video loads we have these days are primarily on IPv4.  many sites i have scripts connect to don't have IPv6 or they have DNS without server setup or routing done right.  without those options rsync gives up on certain failures.  for connection refused, it does work right but that's a less common failure mode.  so i had to code my scripts to look for other failure modes on exit, and try again.  so i have it try with --ipv6 and if that fails, try again with --ipv4.

where is the best place to chat about various scripting and programming specifically on Linux?

---

### Post by EuclideanCoffee on 2020-05-19
I think this is a decent place to talk about scripting for Linux. I write applications for a living for Linux specifically.

When I'm dealing with bash, I use bash -e for catching errors. Otherwise Python has a powerful exception handling.

Error handling is a common step you should be taking in all scripts, as your script will fail, and you should have a reasonable way to end the script without breaking your system.

Concerning your IPv6 annoyance, DNS works on the client. When you query a DNS server, it will provide you IPv4 or IPv6 depending on the table configured. IPv6 is actually a less efficient than IPv4 since the data packets are larger in IPv6, which is likely why you are seeing less distributors using IPv6 for media content... if what you say is true, you're addressing many informal servers with your script.

---

### Post by The Cog on 2020-05-19
There is a "Programming talk" sub-forum of "Development and programming" that you could choose to use. Some programmers don't read in the cafe, and your posts might take longer to get buried there.

The man page for rsync says "prefer" the chosen protocol, but I agree that in practice it simply fails if the "preferred" protocol is not available. I would regard this as a bug in either rsync or the manual.
You could use something like this to test whether the target has an IPv6 address:
```
if host ubuntuforums.org | grep 'IPv6' > /dev/null ; then ipver=6 ; else ipver=4 ; fi
rsync --ipv$ipver etc...
```
but it will still fail if you don't have a routing entry for the chosen protocol. I can't think of anything better than what you are doing - try v6 and then try v4 if v6 fails.

---

### Post by Hwæt on 2020-05-19
> **EuclideanCoffee said:**
> I think this is a decent place to talk about scripting for Linux. I write applications for a living for Linux specifically.

These types of jobs are fairly rare where I'm at. What kind of stack do you work with?

> where is the best place to chat about various scripting and programming specifically on Linux? 

I shudder to say reddit's /r/bash /r/perl /r/node (since I've abandoned that site due to the excessive amount of astroturfing in all subs from technology to religious), but you would have the highest reach there.

This forum is probably one of the higher traffic ones. IIRC back in the day the C Programming channel on Freenode was pretty active. I imagine those channels still are.

---

### Post by Skaperen on 2020-05-19
i suspect most of the traffic on video conversation sites is on IPv4 because the vast majority of the client computers are (e.g the schools and their kids).  even today i would use IPv4 on a service site meant to be accessible by everyone in the USA or some fraction thereof (e.g a local district).  yet i put extra stuff on IPv6-only in some places.  i have been intending to work up some Apache configs to do this on a directory by directory basis.  i hear that some porn sites do this.

i suspect the rsync man page author just has a different understanding of the word "prefer".  that's what it felt like, anyway.

i would most prefer (there's that word, again) to confine my programming talk to Linux or at least Unix or POSIX environments.  i think all non-Windows cloud environments are Linux.  but there are some BSD AMIs on AWS.

i have been checking in on /r/aws some.  but reddit does seem like a noisier place.  twitter doesn't fit the need at all (i have multiple accounts there which they do allow). IRC just invites various attacks at times.  and LinkedIn just isn't in enough for me (i'm retired, so the place just doesn't feel very in to me).

---

