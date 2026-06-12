---
title: "Realtime data collection. How?"
date: 2008-07-03
forum: Server Platforms
---

### Post by Ionix on 2008-07-03
Hi

I am troubled by a server-client model issue, and hope to seek advice from experts here.

I have a unix server that run a few critical applications. They will produce log files on application performances. I have developed a windows-based monitoring software.

My initial idea was:

[LIST=1]
[*]Run a cron job that copy the log files to another /tmp directory
[*]then my monitor application will FTP into the server to grab the logs, at maybe 5 or 10 mins interval.
[/LIST]

Although this solution can solve part of my problems, but it is still not efficient. I need to get up-to-date logs from the server, but I must try to cut down the need to FTP into the server, so as not to cause any performance burden to the server.

I hope to find any way to get a more real time or close to real time data solution. Hope to get help here. Thanks.

---

### Post by Ionix on 2008-07-06
Push++

Hi any tips is good. Thanks.

---

### Post by tamoneya on 2008-07-06
There are many possible work arounds for ftp that can be closer to realtime.  However we need to know a little bit more about your situation.  How many servers are there?  I see two so far.  What is each server doing and how often.  How often are the logs generated.  About how large are they.

Anyways the first thing I would look into is using ssh and just writing directly through the ssh tunnel instead of into /tmp

---

### Post by Ionix on 2008-07-06
There's going to be 1 unix-based server.
1 windows-based workstation.

The server is running the centralized database and accessed by many services or application on other servers (not sure of the figure yet), and its very busy.

The log file is typically a alert warning log file for the system. So basically only when the network face unknown problems, the updating of the log will be frequent. So when everything is peace, the log can go un-updated for a week or more, but when there is problem, then the update of log can reach up to 4MB per day.

---

### Post by tamoneya on 2008-07-06
i may be totally wrong and going in the wrong direction but I think the simplest way would be to have your windows log file monitoring application go and query the server when you run the application.  This shouldnt be to hard when you consider that you wrote the application and therefore have the source code to be edited.  If for some reason that is totally impossible have the application call a script on the server to push the most recent data over to the windows box and then read it locally.  Or you could just run the windows app under wine on the linux server and then just shell into the linux server and do everything local.  I think all of these solutions are an improvement on your current methods but let me know what you think of them and what works and what doesnt in your situation and we can revise them.

---

### Post by Ionix on 2008-07-06
Thinking through your suggestions

- log file monitoring application go and query the server when you run the application

This is possible through ftp, and I believe I can only use it the same way as I have described in the first post.

- the application call a script on the server to push the most recent data over to the windows box and then read it locally

This is abit difficult as I cannot think of anything other than having the server run web server, and have a php script do the data "pushing". Depolying the web server is difficult due to environment constraints.

-run the windows app under wine on the linux server and then just shell into the linux server and do everything local

Not applicable. It's going to be purely a unix database server.

---

### Post by windependence on 2008-07-06
This is actually very simple. If you are using a log analyzer, just use the web interface and open a browser on the Windoze machine to view real time information. Log analyzers like Webalizer work this way and analyze the logs in real time. Information is accessed through a browser on the client machine, and the log analyzer runs on the server.

-Tim

---

### Post by tamoneya on 2008-07-06
> **Ionix said:**
> Thinking through your suggestions

- log file monitoring application go and query the server when you run the application

This is possible through ftp, and I believe I can only use it the same way as I have described in the first post.

- the application call a script on the server to push the most recent data over to the windows box and then read it locally

This is abit difficult as I cannot think of anything other than having the server run web server, and have a php script do the data "pushing". Depolying the web server is difficult due to environment constraints.

-run the windows app under wine on the linux server and then just shell into the linux server and do everything local

Not applicable. It's going to be purely a unix database server.

You could just through it in a web directory and make an http request for the files necessary.  Since this is all local network stuff it should be quick enough even if you have 4 MB per day.

---

