---
title: "Serving multiple SSL websites on 1 box behind 1 public IP"
date: 2012-08-30
forum: Server Platforms
---

### Post by OakRaider4Life on 2012-08-30
I maintain a small private server which I use to  serve up a personal website and serve websites for a couple of friends  as well. Currently, I do this with name based virtual hosting, but I  would like to be able to secure each of these sites with their own SSL  certificates. I understand that I can do this by switching over to IP  based virtual hosting and using IP aliases, but what I'm struggling with  is the best way to securely deliver HTTPS requests to those virtual  hosts. 
 
The option I've been exploring the most extensively is the apache  reverse proxy, but it seems to present challenges to ensuring separate,  secure, SSL connections between each host and its clients that make me  think I should start looking elsewhere (e.g., anyone connecting to any  of the websites would be sharing the same encrypted pipeline since they  connect to the same proxy). 
 
The option I've started looking at since is using Apache's redirect  rules to redirect a request to it's appropriate IP based virtual host.  However, the challenge here seems to be that redirect rules don't appear  to be intended to reroute a request coming from outside of the subnet  to a different subnet IP address. 
 
I've considered exploring the option of setting up a DNS name server and  setting up my DNS records to point to it, but this would mean I have a  lot of reading ahead of me, and a whole mess of time to invest in  setting it up. Obviously, I'd prefer to be able to play with a few  config files to make it work. 
 
Am I even on the right track? Can anyone comment on these possible solutions or point me in the direction of a better one?

---

### Post by Bachstelze on 2012-08-30
Recent Apache versions support name-based SSL virtual hosts with no problems (except maybe with very old browsers...).

---

### Post by OakRaider4Life on 2012-08-31
Ha... looks like I was pulling information from outdated sections of the Apache documentation. Sorry for troubling, and thanks for the response!

---

