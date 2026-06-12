---
title: "Apache 2.2 mod_proxy_http/mod_disk_cache continue downloading after connection closed"
date: 2008-11-11
forum: Server Platforms
---

### Post by Sydius on 2008-11-11
The company I work for hosts a web site that has, well, a lot of large files (videos) that people tend to start downloading but not finish (well, I guess the people finish before the videos do...).

They were using a modified Apache 1.3 HTTP reverse proxy to help speed things up.  They had to modify it for two reasons.  The first is because mod_proxy_http and mod_disk_cache seemed to not cache the file if the connection was closed by the client before it could be downloaded completely.  The second is because they wanted to make sure mod_proxy_http would only make a single request to the content server if two people tried to access the same file before it could be completely cached.

Now they are upgrading to Apache 2.2 and have assigned me the job of upgrading their modules (which is mostly done) and making the same changes to Apache's core to support the above.  Given that the documented changes to the core are all in Japanese and I don't speak Japanese, and given the fact that a lot has probably changed in the core anyway, I'd really rather not have to do it.  Especially since it will make upgrading again in the future a pain.

**Question 1)** Is there a way, using Apache 2.2 and mod_proxy_http and mod_disk_cache to have the reverse proxy server continue downloading/caching a requested file even if the connection that instantiated the request is closed?

**Question 2)** Is it possible to have mod_proxy_http and mod_disk_cache make a single request to the content server if two requests are made to the reverse proxy before the file could be completely cached?

**Question 3)** If the answer to the above is no, is it possible to implement it by changing modules, or would it require changes to the core?

My initial testing seems to indicate that mod_disk_cache deletes the file if it could not be completely cached and mod_proxy_http stops transferring the file as soon as the connection is closed, but I may be missing a configuration option or something.

---

### Post by oneloveamaru on 2008-11-11
Apache is not known to be a good Proxy nor is it known for performance. Also mod_disk_cache is still beta.

You might want to look into using a different Proxy, Nginx or Pound. Caching doesn't sound very helpful anyways if multiple people are connecting to download a large file. Whichever server serves the large file is on is going to need to be fast, IO fast and have a lot of bandwidth between the Proxy and itself. 

If you don't want the app server pushing that large file all the time, put the large file on a different server and serve it from there. I know you can use Pound to point certain content to a different location, which you can also do on the back end in apache. You will just need to update that server when the content changes.

What you are asking may be possible with a lot of Apache tweaking but I think it would be a waste of time. There are better programs out there for doing Proxy. I would look at Nginx and Pound for the Proxy and maybe Squid if you want Proxy and Acceleration. I set up Apache to act as an http proxy once for my company which serves a lot of pictures and it was horrible performance with Apache. Pound works much better for us and one of these days I'll look into Nginx which everyone is raving about.

---

### Post by Sydius on 2008-11-11
There is no app server involved in this case.  Just content servers.  The reason they use reverse proxies for this is because the content is on servers in the Netherlands and many of the clients are in Japan, so they have a reverse proxy system in Japan.

Another problem is that they are using a custom authentication module with the proxy servers that checks a cookie before serving a file from the proxy.

---

