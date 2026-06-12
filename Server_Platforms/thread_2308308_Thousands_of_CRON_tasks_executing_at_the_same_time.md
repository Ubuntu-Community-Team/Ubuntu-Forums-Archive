---
title: "Thousands of CRON tasks executing at the same time?"
date: 2016-01-01
forum: Server Platforms
---

### Post by toni12 on 2016-01-01
Is it possible OR how hard is it for (Digital Ocean) Ubuntu server to run 5000 .py scripts every 5 minutes (each making few HTTP requests while executing) at the same time with CRON?

How would this affect the performance?

How strong the server should be?

Regards

---

### Post by ian-weisser on 2016-01-02
Any Ubuntu system should be able to do 5000 simple http requests every 5 minutes without great stress.

I think doing it from an interpreted language like python or perl may add more overhead than I would prefer.
Especially if you need to parse and manipulate the responses.
Python includes benchmarking tools to help you size your system. Try it in a VM.

---

### Post by toni12 on 2016-01-02
What about 25000 tasks/files each making 150 requests inside file? All scripts are web scrapers.

I know the time of how long does it take for my script to execute. One script takes ~3.5 minutes. Worst case scenario.

What I would like to know is how long would it take for CRON to start all 25k tasks? And would they all finish in 3.5 min at max from when they are started? Or better yet, would they all finish in 5 minutes time before new CRON cycle begins. (CRON runs every 5mins)?

---

### Post by Habitual on 2016-01-02
Ask DO?

---

