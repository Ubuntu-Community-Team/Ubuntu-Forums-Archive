---
title: "FYI: docker says &quot;Error response from daemon: Unexepected status code 502&quot;"
date: 2015-01-05
forum: Virtualisation
---

### Post by sanderj on 2015-01-05
FYI: I got this:

```
$ sudo docker search ubuntu

Error response from daemon: Unexepected status code 502
```

I couldn't find "Error response from daemon: Unexepected status code 502" via Google.

Thanks to a tweet I found [http://status.docker.com/](http://status.docker.com/) which said:


> Full platform disruptionFull Service Disruption

Incident Status
Full Service Disruption

Components
Docker.com Web, Docker Hub Web, Docker Hub Oauth and Accounts API, Docker Registry Hub WEB, Docker Registry Hub API, Docker Hub Automated Builds, Docker Registry API, Docker Docs

Locations
IAD3


January 5, 2015 6:09PM UTC[Investigating] We're dealing with a network issue on our side and working to resolve it asap

So I'm posting this so that from now on you can Google "Error response from daemon: Unexepected status code 502" ...

(And hopefully docker / Docker in the future will tell something more useful than this strange status code 502)

Update: Docker Hub is up again!

---

