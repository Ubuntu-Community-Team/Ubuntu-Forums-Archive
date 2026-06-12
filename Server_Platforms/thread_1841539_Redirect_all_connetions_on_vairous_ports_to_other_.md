---
title: "Redirect all connetions on vairous ports to other URLs/IPs"
date: 2011-09-09
forum: Server Platforms
---

### Post by vzybilly on 2011-09-09
I'm trying to set up a man in the middle kind of server, I'm not sure what exactly needs to happen but I have a domain name, let's call it vzy.domain.com that domain connects up to my router which i have a few ports going to a single computer, 10.0.0.4 (lan only ip)

All server computers on running Ubuntu server 10.04 installed fresh a few months ago
10.0.0.4 got gnome installed for a vnc server as a test for the new server coming in in a month.

now this is what I have for my network:

10.0.0.3:X (forgot port, will look up when setting up)
10.0.0.4:22
[www.vzy-domain.com/another/domain/for/website/hidden-home.html](www.vzy-domain.com/another/domain/for/website/hidden-home.html)

I'm trying to get computer ~.4 to get all connections and send them to the other connections

computer ~.4 accepts Ports 22, X, 80, 8080, and 5900+y (localhost only service, y is it's number, first is 1 and second is 2 and so forth, ssh on port 22 to access)
computer ~.3 accepts only ports 22, and X

my other domain is not in my lan and I only have the url to work with...

I've tried rinetd and pound, rinetd didn't work with urls, pound gives me "Unable to connect" from firefox on a lan computer connecting to it, as well as on my domain.

Please help me to set up this server, I'm trying to get everything to one domain so when I can upgrade my server I will be able to close my other domain down without waiting, at that point I would just change the port 80, 8080 redirects to the new lan IP instead of a URL

also, a small snag, I would like to keep the traffic down on my lan so is it possible that in the browser people will go to vzy.domain.com and then they get redirected completely to [www.vzy-domain.com/another/domain/for/website/hidden-home.html](www.vzy-domain.com/another/domain/for/website/hidden-home.html) so my lan only has a load when someone connects to the site. (reason for this will be fixed within the year hopefully)

What I'm hopping for is a result like this for people connecting:
<what they go to> goes to <what they see/connected to>
vzy.domain.com:22 goes to vzy.domain.com:22
vzy.domain.com:X goes to vzy.domain.com:X
vzy.domain.com:80 goes to [www.vzy-domain.com/another/domain/for/website/hidden-home.html](www.vzy-domain.com/another/domain/for/website/hidden-home.html)
vzy.domain.com:8080 goes to [www.vzy-domain.com/another/domain/for/website/hidden-home.html](www.vzy-domain.com/another/domain/for/website/hidden-home.html)

If this is to confusing just ask a question.
(I program in Java and I'm trying to set up a new web server by my self)

---

