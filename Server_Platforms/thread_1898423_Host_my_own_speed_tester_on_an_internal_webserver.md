---
title: "Host my own speed tester on an internal webserver"
date: 2011-12-21
forum: Server Platforms
---

### Post by jonobr on 2011-12-21
Hi all

Im doing a demo on some vendor wireless devices,

I also have ubuntu on a server -10:04 
Im running apache on there and have a demo page
with embedded video to show how streaming works to the devices.
I would like to embed a speedtester on the page so we could show that also.

I normally use iperf and jperf , but my audience are not technical and need more of a point and click solition.
I would also use dslreports or speedtester.com but the network wont have internet access


Does anyone have any recommendations or links to simple and accurate software?

thanks

jonobr

---

### Post by SaintDanBert on 2011-12-21
Which **speed** are you trying to measure?

An end-user sees "speed" as:
[list]
[*]upload something -- click a button; send file(s); report how long
[*]download something -- click a button; retrieve file(s); report how long
[*]transaction -- click a button; do some work; display results; report how long
[/list]

In the last case, my favorite "some work" is to compile some application.
The typical "build" does some disk operations on multiple files and some cpu chewing on the bits and bytes. Not unlike business processing and very repeatable.  My favorite "display" is a static web page mock-up of a common-use report or query.  **Be Careful!** If your report page sets a response time expectation for a complex database action, it could bite you later. Remember that you are showing the download-and-render time for that page in the fake transaction.

Cheers,
~~~ 0;-Dan

---

### Post by jonobr on 2011-12-21
Hello


Thanks for the reponse,
I was hoping to have something along the lines of dslreport.com or speedtester.com

both of those sites, I think, will upload and download a piece of data and calculate speed as a meacure of mbps and also give you link latency.

Iperf gives  a lot more but is not really demo-able to an end user person.

Both of the above sites run some kind of java app that shows a dashboard or speedo showing reswults.

Ive never done this kind of page before so any recommendations or further reading apprecited/

Thanks

---

### Post by aeiah on 2011-12-21
why not [http://www.speedtest.net/mini.php](http://www.speedtest.net/mini.php) ?

---

### Post by elliotbeken on 2011-12-21
Yes i have what [aeiah]("http://ubuntuforums.org/member.php?u=71962") said found here ([http://ks36740.kimsufi.com/speedtest/](http://ks36740.kimsufi.com/speedtest/))

just a nice simple upload and download test tool

---

### Post by jonobr on 2011-12-21
sweet

ill give them a whirl folks

thanks!!

jonobr

---

### Post by jonobr on 2011-12-21
[http://www.speedtest.net/mini.php](http://www.speedtest.net/mini.php) is exactly what I needed
Its easy to install and seems to be reporting fairly accurately.

I am having some trouble with upload, but from what I can tell using tcpdump, this is a firewall issue.

Thanks for your help folks!!


jonobr

---

### Post by jonobr on 2011-12-21
Issue resolved...THANKS!

---

