---
title: "cURL extremely slow for api.facebook - how to debug/upgrade/fix?"
date: 2011-10-14
forum: Server Platforms
---

### Post by Zoxa on 2011-10-14
Hello,

I'm running a Ubuntu 10.04.1 server with a Drupal 7 website on it. This website should now get integrated in Facebook with the "Drupal for Facebook" module. And as soon as the module is active and set up every page load takes about 12-15 seconds. With the default setting of the facebook php sdk "CURLOPT_CONNECTTIMEOUT => 10," you even get a curlexception 6 "name lookoup timed out".

I don't think this is a problem of my server host as the data center has a very good infrastructur and resides in the middle of Germany. (It's also a quite big host, it would be known if there are problems connection to facebook.) I also don't think this is a problem of the facebook servers as I'm having this for 2 days now and there is absolutely no variance. So there is/was not a single page load under 10 seconds.
When i ping api.facebook.com and api-read.facebook.com from the server I normally get about 90ms and the highest value was 170ms.
To eliminate DNS problems I also changed the facebook php sdk to use the IPs of the API servers and not the domain names but this didn't change anything.

So I guess there is something in curl which causes this problem but I don't know how to troubleshoot/debug it...
The curl packages installed are:
```
curl                               7.19.7-1ubuntu1.1
gnupg-curl                         1.4.10-2ubuntu1
libcurl3                           7.19.7-1ubuntu1.1
libcurl3-gnutls                    7.19.7-1ubuntu1.1
libcurl4-openssl-dev               7.19.7-1ubuntu1.1
php5-curl                          5.3.2-1ubuntu4.9

```

Any ideas what I could do? I would be grateful for anything!

---

### Post by figure002 on 2012-04-04
I have the same problem. My web server is running Ubuntu 11.10 Server Edition. On this server I have a custom PHP script which displays a map from Google Maps using a Google API.

The PHP script uses PHP's cURL functions to obtain map data from maps.googleapis.com. Every time I load the page, it takes about 15 seconds before the Google map is displayed. I have CURLOPT_CONNECTTIMEOUT set to 5 seconds. So my case is very similar to Zoxa's.

This can't be a problem in my PHP script, because I run the same script on my laptop running Ubuntu 11.10 Desktop Edition. There it only takes around 3 seconds for the Google map to load. Note that my server and the laptop are behind the same network.

I don't think this is a DNS problem either, because when I `ping' to maps.googleapis.com from the server I get about 37 ms. And to completely rule out DNS problems, I also used the IP addresses of the API servers instead of the domain names. No difference.

Since this only happens on my server, and not on my laptop, I'm guessing something on my server is causing this. Could it be a firewall problem?

Update: I just created a little test script which uses cURL to obtain the contents from another website. This script takes less than 1 second to load. So it doesn't look like it's a firewall problem. I still don't understand why the Google maps script consistently takes 15 seconds to load.

Version info:
php5-curl 5.3.6-13ubuntu3.6
curl 7.21.6-3ubuntu3.2

Does anyone have an idea how to solve this?

---

### Post by figure002 on 2012-04-26
I finally figured out the problem for my case. The problem wasn't related to DNS or internet connection. The problem was related to my server hardware, my application, and the database design for my application.

Let me explain. In my previous post I explained that on my laptop it took 3 seconds to load a Google map, whereas on my server it took around 15 seconds. The difference in loading time is caused by the difference in hardware. I have a pretty high-end laptop with a fast dual-core CPU and 4GB of RAM. My server on the other end is very cheap and is built to consume as little power as possible. It has an energy efficient single-core CPU and only 2GB of RAM.

Now I'll explain the software + database part. The reason for the large difference in performance between the two machines is because of the inefficient design of the SQL query involved and the design of the database. What the application does, is obtain coordinates for a driving route from the database which are then drawn on the Google map. I just managed to optimize both the SQL query and my database. The PostgreSQL database was optimized by creating indexes for fields that are used often in queries. For example:

```
CREATE INDEX ON task_to_route (from_postcode);
```

The increase in performance was huge. Now, each query takes milliseconds (instead of seconds) to execute. And with this increase in performance of my application, loading a Google map takes less than a second to load (on both my laptop and my server)!

---

