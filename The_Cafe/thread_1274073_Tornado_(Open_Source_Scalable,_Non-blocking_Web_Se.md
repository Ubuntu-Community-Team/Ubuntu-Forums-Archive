---
title: "Tornado (Open Source Scalable, Non-blocking Web Server)"
date: 2009-09-24
forum: The Cafe
---

### Post by HappinessNow on 2009-09-24
> [Tornado]("http://www.tornadoweb.org/") is an open source version of the scalable, non-blocking web server and tools that power [FriendFeed]("http://friendfeed.com/"). The FriendFeed application is written using a web framework that looks a bit like [web.py]("http://webpy.org/") or [Google's webapp]("http://code.google.com/appengine/docs/python/tools/webapp/"), but with additional tools and optimizations to take advantage of the underlying non-blocking infrastructure.
   The framework is distinct from most mainstream web server frameworks (and certainly most Python frameworks) because it is non-blocking and reasonably fast. Because it is non-blocking and uses [epoll]("http://www.kernel.org/doc/man-pages/online/pages/man4/epoll.4.html"), it can handle thousands of simultaneous standing connections, which means it is ideal for real-time web services. We built the web server specifically to handle FriendFeed's real-time features — every active user of FriendFeed maintains an open connection to the FriendFeed servers. (For more information on scaling servers to support thousands of clients, see The [C10K problem]("http://www.kegel.com/c10k.html").)
   See the [Tornado documentation]("http://www.tornadoweb.org/documentation") for a detailed walkthrough of the framework.

**Download and install**

   **Download:** [tornado-0.2.tar.gz]("http://www.tornadoweb.org/static/tornado-0.2.tar.gz")
   ```
tar xvzf tornado-0.2.tar.gz
cd tornado-0.2
python setup.py build
sudo python setup.py install   
```The Tornado source code is [hosted on GitHub]("http://github.com/facebook/tornado").

**Prerequisites**

 Tornado has been tested on Python 2.5 and 2.6. To use all of the features of Tornado, you need to have [PycURL]("http://pycurl.sourceforge.net/") and a JSON library like [simplejson]("http://pypi.python.org/pypi/simplejson/") installed. Complete installation instructions for...Ubuntu are included below for convenience.



**Ubuntu Linux**
   ```
sudo apt-get install python-dev python-pycurl python-simplejson
```[http://www.tornadoweb.org/](http://www.tornadoweb.org/)

> **Performance**

 Web application performance is generally bound by architecture, not frontend performance. That said, Tornado is pretty fast relative to most popular Python web frameworks.
 We ran a few remedial load tests on a simple "Hello, world" application  in each of the most popular Python web frameworks ([Django]("http://www.djangoproject.com/"), [web.py]("http://webpy.org/"), and [CherryPy]("http://www.cherrypy.org/")) to get the baseline performance of each relative to Tornado. We used Apache/mod_wsgi for Django and web.py and ran CherryPy as a standalone server, which was our impression of how each framework is typically run in production environments. We ran 4 single-threaded Tornado frontends behind an [nginx]("http://nginx.net/") reverse proxy, which is how we recommend running Tornado in production (our load test machine had four cores, and we recommend 1 frontend per core).
 We load tested each with Apache Benchmark (ab) on the a separate machine with the command
 
```
ab -n 100000 -c 25 http://10.0.1.x/
```The results (requests per second) on a 2.4GHz AMD Opteron processor with 4 cores:
 [CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=129580&d=1253778621[/IMG]
[/CENTER]
  In our tests, Tornado consistently had 4X the throughput of the next fastest framework, and even a single standalone Tornado frontend got 33% more throughput even though it only used one of the four cores.
 Not very scientific, but at a high level, it should give you a sense that we have cared about performance as we built Tornado, and it shouldn't add too much latency to your apps relative to most Python web development frameworks.[http://www.tornadoweb.org/documentation](http://www.tornadoweb.org/documentation)

---

