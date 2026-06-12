---
title: "Squid caching proxy"
date: 2010-04-30
forum: Server Platforms
---

### Post by vdpollm on 2010-04-30
Hi there,

I have a transparent squid caching proxy set up, and it works great, as here in South Africa, bandwidth is still expensive, and slow.

However, I now need to decom one server (existing proxy server) and add the squid caching proxy to an existing server (easy)

however, i have cached such a lot of data on the existing proxy server that i don't want to loose. So here is my question:

How do i transfer the cached files from the old server to the new server, to ensure that i don't "redownload" the files from the net?

Is this even possible?

Regards
Marc

---

### Post by Krijk on 2010-04-30
> **vdpollm said:**
> Hi there,

I have a transparent squid caching proxy set up, and it works great, as here in South Africa, bandwidth is still expensive, and slow.

However, I now need to decom one server (existing proxy server) and add the squid caching proxy to an existing server (easy)

however, i have cached such a lot of data on the existing proxy server that i don't want to loose. So here is my question:

How do i transfer the cached files from the old server to the new server, to ensure that i don't "redownload" the files from the net?

Is this even possible?

Regards
Marc


Hi Marc,

I sympathize with you. A few years ago I had the same issue (also in South Africa) that I had to reinstall the proxy-server.

I'm not entirely sure anymore what I did, but I transferred the squid-cache to the new install. I tried a few things and after some trial and error succeeded in preserving the old-cache. Possibly I did one of the things below.

1. Re-installe squid on other server. Re-created the squid-cache dirs and just copied the old squid-cache in it.
2. created a second squid. Created a cluster and synced the 2nd server.

I searched a litle on internet and also got the following possible solution. [http://www.pubbs.net/201001/squid/670-squid-users-use-cache-dir-in-different-server.html]("http://www.pubbs.net/201001/squid/670-squid-users-use-cache-dir-in-different-server.html")

---

