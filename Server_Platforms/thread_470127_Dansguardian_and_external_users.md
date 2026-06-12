---
title: "Dansguardian and external users"
date: 2007-06-10
forum: Server Platforms
---

### Post by johng4 on 2007-06-10
Here's what I'm trying to do...

I have a proxy server setup for my internal network, but, I also want to allow a select few external users to use my proxy server for their computers at home.

I want this for the simple reason that it allows me to have virus scans on downloads, and allow for some content control for these users.  Not to mention that it will also serve as a web cache so it will accelerate a good bit of websites.

My clients have had serious problems with viruses and malware, so this is a measure I'm putting in place for them, and me so that I can help track the source of their constant infections.  

Here's the setup...

Client comes into the proxy through port 8080, and after its processed through Dansguardian, its passed on to Squid, and then to the internet.

Here's the problem...

When coming through Dansguardian, the ip of the requester is reported as localhost.

I've tried setting ACLs in Squid to allow specific ranges, but once they come through Dans, they are treated as if they are on my local network.

Potential solution...
I would like to have some basic level of authentication setup, but the reading material on this is limited, or just not applicable.  Not to mention, that I want the internal network, to not have to authenticate at all.

Any ideas?

---

### Post by johng4 on 2007-06-11
Update...

I tried using PAM and NCSA authentication with Squid, but it ended up breaking squid.. so I'm a little gun shy at this point.

However, I did find something out...


Ideally, if I can get authentication to prompt for a password (not sure if it does this) I can isolate the Dansguardian traffic for authentication.  This is the ideal solution, since the machines on the network that are using Dansguardian, and the machines outside the network that are using Dansguardian are considered to be fairly high-risk machines - so I want them authenticating to get web access.

I just have no idea how the squid basic authentication works.

---

### Post by airtonix on 2007-06-15
tried using virtual machines? forwarding traffice to that virtual machines IP address?

---

